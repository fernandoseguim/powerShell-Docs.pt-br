---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="23b40-103">Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="23b40-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="23b40-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="23b40-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="23b40-105">Cada nó de destino deve ser instruído a usar o modo de pull e receber a URL em que possa contatar o servidor de pull para obter as configurações.</span><span class="sxs-lookup"><span data-stu-id="23b40-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="23b40-106">Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="23b40-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="23b40-107">Para configurar o LCM, é criado um tipo especial de configuração conhecido como "metaconfiguração".</span><span class="sxs-lookup"><span data-stu-id="23b40-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="23b40-108">Para obter mais informações sobre como configurar o LCM, consulte [Gerenciador de Configurações Local de Configuração de Estado Desejado do Windows PowerShell 4.0](metaConfig4.md)</span><span class="sxs-lookup"><span data-stu-id="23b40-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="23b40-109">O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "PullServer":</span><span class="sxs-lookup"><span data-stu-id="23b40-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="23b40-110">No script, **DownloadManagerCustomData** passa a URL do servidor de pull e (para esse exemplo) autoriza uma conexão não segura.</span><span class="sxs-lookup"><span data-stu-id="23b40-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span>

<span data-ttu-id="23b40-111">Depois de ser executado, esse script cria uma nova pasta de saída denominada **SimpleMetaConfigurationForPull** e coloca um arquivo MOF de metaconfiguração nela.</span><span class="sxs-lookup"><span data-stu-id="23b40-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="23b40-112">Para aplicar a configuração, use **Set-DscLocalConfigurationManager** com parâmetros para **ComputerName** (use "localhost") e **Path** (o caminho até o local do arquivo localhost.meta.mof do nó de destino).</span><span class="sxs-lookup"><span data-stu-id="23b40-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="23b40-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="23b40-113">For example:</span></span>
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="23b40-114">ID de configuração</span><span class="sxs-lookup"><span data-stu-id="23b40-114">Configuration ID</span></span>
<span data-ttu-id="23b40-115">O script define a propriedade **ConfigurationID** do LCM para um GUID criado anteriormente para essa finalidade (você pode criar um GUID usando o cmdlet **New-Guid**).</span><span class="sxs-lookup"><span data-stu-id="23b40-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="23b40-116">O **ConfigurationID** é usado pelo LCM para localizar a configuração apropriada no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="23b40-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="23b40-117">O arquivo MOF de configuração no servidor de pull deve ser nomeado como `ConfigurationID.mof`, em que *ConfigurationID* é o valor da propriedade **ConfigurationID** do nó de destino do LCM.</span><span class="sxs-lookup"><span data-stu-id="23b40-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="23b40-118">Efetuando pull de um servidor de SMB</span><span class="sxs-lookup"><span data-stu-id="23b40-118">Pulling from an SMB server</span></span>

<span data-ttu-id="23b40-119">Se o servidor de pull é configurado como um compartilhamento de arquivos SMB em vez de como um serviço Web, especifique o **DscFileDownloadManager** em vez de **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="23b40-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="23b40-120">O **DscFileDownloadManager** usa uma propriedade **SourcePath** em vez de **ServerUrl**.</span><span class="sxs-lookup"><span data-stu-id="23b40-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="23b40-121">O seguinte script configura o LCM para efetuar pull de configurações de um compartilhamento SMB denominado "SmbDscShare" em um servidor denominado "CONTOSO-SERVER":</span><span class="sxs-lookup"><span data-stu-id="23b40-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="23b40-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="23b40-122">See Also</span></span>

- [<span data-ttu-id="23b40-123">Configurando um servidor de pull da Web de DSC</span><span class="sxs-lookup"><span data-stu-id="23b40-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="23b40-124">Configurando um servidor de pull de SMB para DSC</span><span class="sxs-lookup"><span data-stu-id="23b40-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)