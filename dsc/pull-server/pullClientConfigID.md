---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Configurar um cliente de Pull usando IDs de configuração no PowerShell 5.0 e posterior
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400262"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Configurar um cliente de Pull usando IDs de configuração no PowerShell 5.0 e posterior

> Aplica-se a: Windows PowerShell 5.0

> [!IMPORTANT]
> O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

Antes de configurar um cliente de pull, você deve configurar um servidor de pull. Embora essa ordem não for necessária, ele ajuda na solução de problemas e ajuda a garantir que o registro foi bem-sucedido. Para configurar um servidor de pull, você pode usar os guias a seguir:

- [Configurar um servidor de pull SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status. As seções a seguir mostram como configurar um cliente de pull com um compartilhamento SMB ou o servidor de Pull de DSC do HTTP. Quando o LCM do nó for atualizado, ele entrará em contato para o local configurado para baixar qualquer configurações designadas. Se todos os recursos necessários não existirem no nó, ele será automaticamente baixá-los do local configurado. Se o nó é configurado com um [servidor de relatório](reportServer.md), em seguida, ele relatará o status da operação.

> **Observação**: Este tópico se aplica ao PowerShell 5.0. Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurar o LCM do cliente de pull

Executar qualquer um dos exemplos a seguir cria uma nova pasta de saída denominada **PullClientConfigID** e coloca um arquivo MOF de metaconfiguração nela. Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.

Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração. Por exemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID de configuração

Os exemplos a seguir define o **ConfigurationID** propriedades do LCM para um **Guid** que criado anteriormente para essa finalidade. O **ConfigurationID** é usado pelo LCM para localizar a configuração apropriada no servidor de pull. O arquivo MOF de configuração no servidor de pull deve ser nomeado como `ConfigurationID.mof`, em que *ConfigurationID* é o valor da propriedade **ConfigurationID** do nó de destino do LCM. Para obter mais informações, consulte [configurações de publicação para um servidor de recepção (v4/v5)](publishConfigs.md).

Você pode criar um aleatório **Guid** usando o exemplo abaixo, ou usando o [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Para obter mais informações sobre como usar **Guids** em seu ambiente, consulte [planejar Guids](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar um cliente de Pull para baixar configurações

Cada cliente deve ser configurado no **Pull** modo e recebe a url do servidor de pull onde sua configuração está armazenada. Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias. Para configurar o LCM, é criado um tipo especial de configuração, decorada com o atributo **DSCLocalConfigurationManager**. Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>Servidor de Pull de DSC de HTTP

O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "CONTOSO-PullSrv".

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull. O **ServerUrl** Especifica a url do Pull de DSC

### <a name="smb-share"></a>Compartilhamento SMB

O script a seguir configura o LCM para efetuar pull de configurações de compartilhamento SMB `\\SMBPullServer\Pull`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

No script, o **ConfigurationRepositoryShare** bloco define o servidor de pull, que nesse caso, é apenas um compartilhamento SMB.

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurar um cliente de Pull para baixar recursos

Se você especificar apenas o **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquear em sua configuração LCM (como nos exemplos anteriores), o cliente de pull efetuará pull dos recursos da mesma ele recupera suas configurações de local. Você também pode especificar locais separados para os recursos. Para especificar uma localização de recursos como um servidor separado, use o **ResourceRepositoryWeb** bloco. Para especificar uma localização de recursos como um compartilhamento SMB, use o **ResourceRepositoryShare** bloco.

> [!NOTE]
> Você pode combinar **ConfigurationRepositoryWeb** com **ResourceRepositoryShare** ou **ConfigurationRepositoryShare** com **ResourceRepositoryWeb** . Exemplos disso não são mostrados abaixo.

### <a name="http-dsc-pull-server"></a>Servidor de Pull de DSC de HTTP

A metaconfiguração a seguir configura um cliente de pull para obter suas configurações de **CONTOSO-PullSrv** e seus recursos de **CONTOSO-ResourceSrv**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>Compartilhamento SMB

O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de configurações do compartilhamento de SMB `\\SMBPullServer\Configurations`e os recursos de compartilhamento SMB `\\SMBPullServer\Resources`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>Baixar automaticamente os recursos no modo de Push

A partir do PowerShell 5.0, seus clientes de pull podem baixar os módulos de um compartilhamento SMB, mesmo quando eles são configurados para **Push** modo. Isso é especialmente útil em cenários em que você deseja configurar um servidor de recepção. O **ResourceRepositoryShare** bloco pode ser usado sem especificar um **ConfigurationRepositoryShare**. O exemplo a seguir mostra uma metaconfiguração que configura um cliente para receber recursos de um compartilhamento SMB `\\SMBPullServer\Resources`. Quando o nó está **PUSHED** uma configuração, ele baixará automaticamente todos os recursos necessários, do compartilhamento especificado.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>Configurar um cliente de Pull para relatar o status

Por padrão, nós não enviará relatórios a um servidor de Pull configurado. Você pode usar um único servidor de pull para emissão de relatórios, recursos e configurações, mas é preciso criar um bloco **ReportRepositoryWeb** para configurar o relatório.

### <a name="http-dsc-pull-server"></a>Servidor de Pull de DSC de HTTP

O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de recursos e configurações, além de enviar dados de relatórios, para um único servidor de pull.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

Para especificar um servidor de relatório, utilize um bloco **ReportRepositoryWeb**. Um servidor de relatório não pode ser um servidor de SMB.
A metaconfiguração a seguir configura um cliente de pull para obter suas configurações de **CONTOSO PullSrv** e seus recursos de **CONTOSO ResourceSrv**, bem como enviar relatórios de status para **CONTOSO ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>Compartilhamento SMB

Um servidor de relatório não pode ser um compartilhamento SMB.

## <a name="next-steps"></a>Próximas etapas

Depois que o cliente de pull foi configurado, você pode usar os guias a seguir para executar as próximas etapas:

- [Publicar configurações em um servidor de pull (v4/v5)](publishConfigs.md)
- [Empacotar e carregar recursos em um servidor de pull (v4)](package-upload-resources.md)

## <a name="see-also"></a>Consulte Também

* [Configurando um cliente de pull com nomes de configuração](pullClientConfigNames.md)
