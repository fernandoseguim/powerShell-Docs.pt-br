---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Configurar um cliente de pull usando IDs de configuração no PowerShell 5.0 e posterior
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58055709"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Configurar um cliente de pull usando IDs de configuração no PowerShell 5.0 e posterior

> Aplica-se a: Windows PowerShell 5.0

> [!IMPORTANT]
> O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

Antes de configurar um cliente de pull, você deve configurar um servidor de pull. Embora essa ordem não seja obrigatória, ela ajuda na solução de problemas e ajuda a garantir que o registro seja bem-sucedido. Para configurar um servidor de pull, você pode usar os guias a seguir:

- [Configurar um servidor de pull SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para baixar configurações, recursos e até mesmo relatar seu status. As seções a seguir mostram como configurar um cliente de pull com um compartilhamento SMB ou servidor de pull de DSC HTTP. Quando o nó do LCM for atualizado, ele entrará em contato com a localização configurada para baixar as configurações atribuídas. Se algum dos recursos necessários não existir no nó, ele será baixado automaticamente da localização configurada. Se o nó for configurado com um [Servidor de relatório](reportServer.md), ele relatará o status da operação.

> [!NOTE]
> Este tópico se aplica ao PowerShell 5.0. Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurar o LCM do cliente de pull

A execução de qualquer um dos exemplos abaixo cria uma nova pasta de saída denominada **PullClientConfigID** e coloca nela um arquivo MOF de metaconfiguração. Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.

Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração. Por exemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID de configuração

Os exemplos abaixo definem a propriedade **ConfigurationID** do LCM para um **Guid** criado anteriormente para essa finalidade. O **ConfigurationID** é usado pelo LCM para localizar a configuração apropriada no servidor de pull. O arquivo MOF de configuração no servidor de pull deve ser nomeado como `ConfigurationID.mof`, em que *ConfigurationID* é o valor da propriedade **ConfigurationID** do nó de destino do LCM. Para obter mais informações, confira [Publicar configurações em um servidor de pull (v4/v5)](publishConfigs.md).

Você pode criar um **Guid** aleatório usando o exemplo abaixo ou usando o cmdlet [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).

```powershell
[System.Guid]::NewGuid()
```

Para obter mais informações sobre o uso de **Guids** em seu ambiente, confira [Plan for Guids](/powershell/dsc/secureserver#guids) (Planejar-se para usar Guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar um cliente de pull para baixar configurações

Cada cliente deve ser configurado no modo **Pull** e receber a URL do servidor de pull em que sua configuração está armazenada. Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias. Para configurar o LCM, é criado um tipo especial de configuração, decorada com o atributo **DSCLocalConfigurationManager**. Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>Servidor de pull de DSC HTTP

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

No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull. A **ServerUrl** especifica a URL do Pull de DSC

### <a name="smb-share"></a>Compartilhamento SMB

O script a seguir configura o LCM para efetuar o pull de configurações do Compartilhamento SMB `\\SMBPullServer\Pull`.

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

No script, o bloco **ConfigurationRepositoryShare** define o servidor de pull, que nesse caso é apenas um compartilhamento SMB.

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurar um cliente de pull para baixar recursos

Se você especificar apenas o bloco **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** em sua configuração do LCM (como no exemplo anterior), o cliente de pull efetuará pull dos recursos da mesma localização da qual recupera suas configurações. Você também pode especificar locais separados para os recursos. Para especificar uma localização de recurso como um servidor separado, use o bloco **ResourceRepositoryWeb**. Para especificar uma localização de recurso como um compartilhamento SMB, use o bloco **ResourceRepositoryShare**.

> [!NOTE]
> Você pode combinar **ConfigurationRepositoryWeb** com **ResourceRepositoryShare** ou **ConfigurationRepositoryShare** com **ResourceRepositoryWeb**. Exemplos disso não são mostrados abaixo.

### <a name="http-dsc-pull-server"></a>Servidor de pull de DSC HTTP

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

O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de configurações do compartilhamento SMB `\\SMBPullServer\Configurations` e de recursos do compartilhamento SMB `\\SMBPullServer\Resources`.

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

#### <a name="automatically-download-resources-in-push-mode"></a>Baixar recursos automaticamente no modo de envio por push

Começando no PowerShell 5.0, seus clientes de pull podem baixar módulos de um compartilhamento SMB, mesmo quando eles estão configurados para o modo de envio por **Push**. Isso é especialmente útil em cenários em que você não quer configurar um servidor de pull. O bloco **ResourceRepositoryShare** pode ser usado sem especificar um **ConfigurationRepositoryShare**. O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de recursos de um compartilhamento SMB `\\SMBPullServer\Resources`. Quando o nó é **RECEBE** uma configuração por push, ele baixa automaticamente todos os recursos necessários do compartilhamento especificado.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Configurar um cliente de pull para relatar o status

Por padrão, os nós não enviam relatórios a um servidor de pull configurado. Você pode usar um único servidor de pull para emissão de relatórios, recursos e configurações, mas é preciso criar um bloco **ReportRepositoryWeb** para configurar o relatório.

### <a name="http-dsc-pull-server"></a>Servidor de pull de DSC HTTP

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

Após o cliente de pull ser configurado, você pode usar os guias a seguir para executar as próximas etapas:

- [Publicar configurações em um servidor de pull (v4/v5)](publishConfigs.md)
- [Empacotar e carregar recursos em um servidor de pull (v4)](package-upload-resources.md)

## <a name="see-also"></a>Consulte Também

* [Configurando um cliente de pull com nomes de configuração](pullClientConfigNames.md)
