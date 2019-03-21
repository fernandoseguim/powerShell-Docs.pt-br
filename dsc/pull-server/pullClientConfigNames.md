---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Configurar um cliente de pull usando nomes de configuração no PowerShell 5.0 e posterior
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58058174"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Configurar um cliente de pull usando nomes de configuração no PowerShell 5.0 e posterior

> Aplica-se a: Windows PowerShell 5.0

> [!IMPORTANT]
> O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

Antes de configurar um cliente de pull, você deve configurar um servidor de pull. Embora essa ordem não seja obrigatória, ela ajuda na solução de problemas e ajuda a garantir que o registro seja bem-sucedido. Para configurar um servidor de pull, você pode usar os guias a seguir:

- [Configurar um servidor de pull SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para baixar configurações, recursos e até mesmo relatar seu status. As seções a seguir mostram como configurar um cliente de pull com um compartilhamento SMB ou servidor de pull de DSC HTTP. Quando o nó do LCM for atualizado, ele entrará em contato com a localização configurada para baixar as configurações atribuídas. Se algum dos recursos necessários não existir no nó, ele será baixado automaticamente da localização configurada. Se o nó for configurado com um [Servidor de relatório](reportServer.md), ele relatará o status da operação.

> [!NOTE]
> Este tópico se aplica ao PowerShell 5.0.
> Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, confira [Configurar um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurar o LCM do cliente de pull

A execução de qualquer um dos exemplos abaixo cria uma nova pasta de saída denominada **PullClientConfigName** e coloca nela um arquivo MOF de metaconfiguração. Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.

Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração. Por exemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Nome da configuração

Os exemplos a seguir definem a propriedade **ConfigurationName** do LCM como o nome de uma configuração compilada anteriormente, criada para essa finalidade. O **ConfigurationName** é usado pelo LCM para localizar a configuração apropriada no servidor de pull. O arquivo MOF da configuração no servidor de pull deve ser denominado `<ConfigurationName>.mof`, nesse caso, "ClientConfig.mof". Para obter mais informações, confira [Publicar configurações em um servidor de pull (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar um cliente de pull para baixar configurações

Cada cliente deve ser configurado no modo **Pull** e receber a URL do servidor de pull em que sua configuração está armazenada. Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias. Para configurar o LCM, é criado um tipo especial de configuração, decorada com o atributo **DSCLocalConfigurationManager**. Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md).

O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "CONTOSO-PullSrv".

- No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull. A propriedade **ServerURL** especifica o ponto de extremidade para o servidor de pull.

- A propriedade **RegistrationKey** é uma chave compartilhada entre todos os nós de cliente para um servidor de pull e esse servidor de pull. O mesmo valor é armazenado em um arquivo no servidor de pull.
  > [!NOTE]
  > As chaves de registro funcionam apenas com servidores de pull da **Web**. Você ainda deve usar **ConfigurationID** com um servidor de pull de **SMB**.
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

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurar um cliente de pull para baixar recursos

Se você especificar apenas um bloco **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** em sua configuração LCM (como no exemplo anterior), o cliente de pull efetuará pull dos recursos na mesma localização em que seus arquivos “.mof” estão armazenados. Você também pode especificar locais diferentes nos quais os clientes podem baixar recursos. Para especificar um servidor de recurso, utilize um bloco **ResourceRepositoryWeb** (para um servidor de pull da Web) ou um bloco **ResourceRepositoryShare** (para um servidor de pull de SMB).

O exemplo a seguir mostra uma metaconfiguração que configura um cliente para baixar configurações de um servidor de pull e recursos de um compartilhamento SMB.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Configurar um cliente de pull para relatar o status

Você pode usar um único servidor de pull para emissão de relatórios, recursos e configurações. A emissão de relatórios não está configurada para os clientes por padrão. Para configurar um cliente para relatar o status, você precisa criar um bloco **ReportRepositoryWeb**. O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de recursos e configurações, além de enviar dados de relatórios, para um único servidor de pull.

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
