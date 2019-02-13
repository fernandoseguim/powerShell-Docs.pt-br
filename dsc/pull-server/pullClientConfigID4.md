---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Configurar um cliente de Pull usando IDs de configuração no PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675757"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Configurar um cliente de Pull usando IDs de configuração no PowerShell 4.0

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

Antes de configurar um cliente de pull, você deve configurar um servidor de pull. Embora essa ordem não for necessária, ele ajuda na solução de problemas e ajuda a garantir que o registro foi bem-sucedido. Para configurar um servidor de pull, você pode usar os guias a seguir:

- [Configurar um servidor de pull SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status. As seções a seguir mostram como configurar um cliente de pull com um compartilhamento SMB ou o servidor de Pull de DSC do HTTP. Quando o LCM do nó for atualizado, ele entrará em contato para o local configurado para baixar qualquer configurações designadas. Se todos os recursos necessários não existirem no nó, ele será automaticamente baixá-los do local configurado. Se o nó é configurado com um [servidor de relatório](reportServer.md), em seguida, ele relatará o status da operação.

## <a name="configure-the-pull-client-lcm"></a>Configurar o LCM do cliente de pull

Executar qualquer um dos exemplos a seguir cria uma nova pasta de saída denominada **PullClientConfigID** e coloca um arquivo MOF de metaconfiguração nela. Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.

Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração. Por exemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID de configuração

Os exemplos a seguir o conjunto de **ConfigurationID** propriedades do LCM para um **Guid** que criado anteriormente para essa finalidade. O **ConfigurationID** é usado pelo LCM para localizar a configuração apropriada no servidor de pull. O arquivo MOF de configuração no servidor de pull deve ser nomeado como `ConfigurationID.mof`, em que *ConfigurationID* é o valor da propriedade **ConfigurationID** do nó de destino do LCM. Para obter mais informações, consulte [configurações de publicação para um servidor de recepção (v4/v5)](publishConfigs.md).

Você pode criar um aleatório **Guid** usando o exemplo a seguir.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar um cliente de Pull para baixar configurações

Cada cliente deve ser configurado no **Pull** modo e recebe a url do servidor de pull onde sua configuração está armazenada. Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias. Para configurar o LCM, você deve criar um tipo especial de configuração, com um **LocalConfigurationManager** bloco. Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>Servidor de Pull de DSC de HTTP

Se o servidor de pull é configurado como um serviço web, você definir a **DownloadManagerName** à **WebDownloadManager**. O **WebDownloadManager** exige que você especifique uma **ServerUrl** para o **DownloadManagerCustomData** chave. Você também pode especificar um valor para **AllowUnsecureConnection**, conforme mostrado no exemplo a seguir. O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "PullServer".

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>Compartilhamento SMB

Se o servidor de pull é configurado como um compartilhamento de arquivos SMB, em vez de um serviço web, você definir a **DownloadManagerName** à **DscFileDownloadManager** em vez de **WebDownLoadManager**. O **DscFileDownloadManager** exige que você especifique uma **SourcePath** propriedade no **DownloadManagerCustomData**. O seguinte script configura o LCM para efetuar pull de configurações de um compartilhamento SMB denominado “SmbDscShare” em um servidor denominado “CONTOSO-SERVER”.

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>Próximas etapas

Depois que o cliente de pull foi configurado, você pode usar os guias a seguir para executar as próximas etapas:

- [Publicar configurações em um servidor de pull (v4/v5)](publishConfigs.md)
- [Empacotar e carregar recursos em um servidor de pull (v4)](package-upload-resources.md)

## <a name="see-also"></a>Consulte Também

- [Configurar um servidor de pull da web de DSC](pullServer.md)
- [Configurar um servidor de pull SMB de DSC](pullServerSMB.md)
