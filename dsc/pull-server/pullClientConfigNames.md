---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Configurar um cliente de Pull usando nomes de configuração no PowerShell 5.0 e posterior
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400324"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Configurar um cliente de Pull usando nomes de configuração no PowerShell 5.0 e posterior

> Aplica-se a: Windows PowerShell 5.0

> [!IMPORTANT]
> O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

Antes de configurar um cliente de pull, você deve configurar um servidor de pull. Embora essa ordem não for necessária, ele ajuda na solução de problemas e ajuda a garantir que o registro foi bem-sucedido. Para configurar um servidor de pull, você pode usar os guias a seguir:

- [Configurar um servidor de pull SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status. As seções a seguir mostram como configurar um cliente de pull com um compartilhamento SMB ou o servidor de Pull de DSC do HTTP. Quando o LCM do nó for atualizado, ele entrará em contato para o local configurado para baixar qualquer configurações designadas. Se todos os recursos necessários não existirem no nó, ele será automaticamente baixá-los do local configurado. Se o nó é configurado com um [servidor de relatório](reportServer.md), em seguida, ele relatará o status da operação.

> **Observação**: Este tópico se aplica ao PowerShell 5.0.
Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, consulte [configurar um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurar o LCM do cliente de pull

Executar qualquer um dos exemplos a seguir cria uma nova pasta de saída denominada **PullClientConfigName** e coloca um arquivo MOF de metaconfiguração nela. Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.

Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração. Por exemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Nome da configuração

Os exemplos a seguir define o **ConfigurationName** propriedades do LCM para o nome de uma configuração compilada anteriormente, criada para essa finalidade. O **ConfigurationName** é o que o LCM usa para localizar a configuração apropriada no servidor de pull. O arquivo MOF de configuração no servidor de pull deve ser nomeado `<ConfigurationName>.mof`, nesse caso, "ClientConfig.mof". Para obter mais informações, consulte [configurações de publicação para um servidor de recepção (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar um cliente de Pull para baixar configurações

Cada cliente deve ser configurado no **Pull** modo e recebe a url do servidor de pull onde sua configuração está armazenada. Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias. Para configurar o LCM, é criado um tipo especial de configuração, decorada com o atributo **DSCLocalConfigurationManager**. Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md).

O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "CONTOSO-PullSrv".

- No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull. A propriedade **ServerURL** especifica o ponto de extremidade para o servidor de pull.

- A propriedade **RegistrationKey** é uma chave compartilhada entre todos os nós de cliente para um servidor de pull e esse servidor de pull. O mesmo valor é armazenado em um arquivo no servidor de pull.
  > **Observação**: As chaves de registro funcionam apenas com **web** servidores de pull. Você ainda deve usar **ConfigurationID** com um servidor de pull de **SMB**.
  > Para obter informações sobre como configurar um servidor de pull usando **ConfigurationID**, consulte [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigId.md)

- A propriedade **ConfigurationNames** em uma matriz que especifica os nomes das configurações destinadas ao nó do cliente.
  >**Observação:** Se você especificar mais de um valor em **ConfigurationNames**, também será necessário especificar blocos **PartialConfiguration** na configuração.
  >Para obter informações sobre configurações parciais, veja [Configurações parciais da Configuração de Estado Desejado do PowerShell](partialConfigs.md).

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurar um cliente de Pull para baixar recursos

Se você especificar apenas um **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquear em sua configuração LCM (como no exemplo anterior), o cliente de pull efetuará pull dos recursos do mesmo local de armazenavam de seus arquivos ". MOF". Você também pode especificar diferentes locais em que os clientes podem baixar os recursos. Para especificar um servidor de recurso, utilize um bloco **ResourceRepositoryWeb** (para um servidor de pull da Web) ou um bloco **ResourceRepositoryShare** (para um servidor de pull de SMB).

O exemplo a seguir mostra uma metaconfiguração que configura um cliente para baixar as configurações de um servidor de Pull e recursos de um compartilhamento SMB.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>Configurar um cliente de Pull para relatar o status

Você pode usar um único servidor de pull para emissão de relatórios, recursos e configurações. Emissão de relatórios não está configurado para clientes por padrão. Para configurar um cliente para relatar o status, você precisa criar uma **ReportRepositoryWeb** bloco. O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de recursos e configurações, além de enviar dados de relatórios, para um único servidor de pull.

> [!NOTE]
> Um servidor de relatório não pode ser um compartilhamento SMB.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Consulte Também

* [Configurando um cliente de pull com uma ID de configuração](PullClientConfigNames.md)
* [Configurando um servidor de pull da Web de DSC](pullServer.md)
