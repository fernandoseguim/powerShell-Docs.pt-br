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
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="8210b-103">Configurar um cliente de Pull usando IDs de configuração no PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="8210b-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="8210b-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8210b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8210b-105">O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="8210b-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="8210b-106">É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="8210b-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="8210b-107">Antes de configurar um cliente de pull, você deve configurar um servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="8210b-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="8210b-108">Embora essa ordem não for necessária, ele ajuda na solução de problemas e ajuda a garantir que o registro foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="8210b-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="8210b-109">Para configurar um servidor de pull, você pode usar os guias a seguir:</span><span class="sxs-lookup"><span data-stu-id="8210b-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="8210b-110">Configurar um servidor de pull SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="8210b-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="8210b-111">Configurar um servidor de pull HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="8210b-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="8210b-112">Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status.</span><span class="sxs-lookup"><span data-stu-id="8210b-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="8210b-113">As seções a seguir mostram como configurar um cliente de pull com um compartilhamento SMB ou o servidor de Pull de DSC do HTTP.</span><span class="sxs-lookup"><span data-stu-id="8210b-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="8210b-114">Quando o LCM do nó for atualizado, ele entrará em contato para o local configurado para baixar qualquer configurações designadas.</span><span class="sxs-lookup"><span data-stu-id="8210b-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="8210b-115">Se todos os recursos necessários não existirem no nó, ele será automaticamente baixá-los do local configurado.</span><span class="sxs-lookup"><span data-stu-id="8210b-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="8210b-116">Se o nó é configurado com um [servidor de relatório](reportServer.md), em seguida, ele relatará o status da operação.</span><span class="sxs-lookup"><span data-stu-id="8210b-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="8210b-117">Configurar o LCM do cliente de pull</span><span class="sxs-lookup"><span data-stu-id="8210b-117">Configure the pull client LCM</span></span>

<span data-ttu-id="8210b-118">Executar qualquer um dos exemplos a seguir cria uma nova pasta de saída denominada **PullClientConfigID** e coloca um arquivo MOF de metaconfiguração nela.</span><span class="sxs-lookup"><span data-stu-id="8210b-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="8210b-119">Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="8210b-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="8210b-120">Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração.</span><span class="sxs-lookup"><span data-stu-id="8210b-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="8210b-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8210b-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="8210b-122">ID de configuração</span><span class="sxs-lookup"><span data-stu-id="8210b-122">Configuration ID</span></span>

<span data-ttu-id="8210b-123">Os exemplos a seguir o conjunto de **ConfigurationID** propriedades do LCM para um **Guid** que criado anteriormente para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="8210b-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="8210b-124">O **ConfigurationID** é usado pelo LCM para localizar a configuração apropriada no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="8210b-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="8210b-125">O arquivo MOF de configuração no servidor de pull deve ser nomeado como `ConfigurationID.mof`, em que *ConfigurationID* é o valor da propriedade **ConfigurationID** do nó de destino do LCM.</span><span class="sxs-lookup"><span data-stu-id="8210b-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="8210b-126">Para obter mais informações, consulte [configurações de publicação para um servidor de recepção (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="8210b-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="8210b-127">Você pode criar um aleatório **Guid** usando o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8210b-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="8210b-128">Configurar um cliente de Pull para baixar configurações</span><span class="sxs-lookup"><span data-stu-id="8210b-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="8210b-129">Cada cliente deve ser configurado no **Pull** modo e recebe a url do servidor de pull onde sua configuração está armazenada.</span><span class="sxs-lookup"><span data-stu-id="8210b-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="8210b-130">Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="8210b-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="8210b-131">Para configurar o LCM, você deve criar um tipo especial de configuração, com um **LocalConfigurationManager** bloco.</span><span class="sxs-lookup"><span data-stu-id="8210b-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="8210b-132">Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="8210b-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="8210b-133">Servidor de Pull de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="8210b-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="8210b-134">Se o servidor de pull é configurado como um serviço web, você definir a **DownloadManagerName** à **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="8210b-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="8210b-135">O **WebDownloadManager** exige que você especifique uma **ServerUrl** para o **DownloadManagerCustomData** chave.</span><span class="sxs-lookup"><span data-stu-id="8210b-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="8210b-136">Você também pode especificar um valor para **AllowUnsecureConnection**, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8210b-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="8210b-137">O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "PullServer".</span><span class="sxs-lookup"><span data-stu-id="8210b-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

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

## <a name="smb-share"></a><span data-ttu-id="8210b-138">Compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="8210b-138">SMB Share</span></span>

<span data-ttu-id="8210b-139">Se o servidor de pull é configurado como um compartilhamento de arquivos SMB, em vez de um serviço web, você definir a **DownloadManagerName** à **DscFileDownloadManager** em vez de **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="8210b-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="8210b-140">O **DscFileDownloadManager** exige que você especifique uma **SourcePath** propriedade no **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="8210b-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="8210b-141">O seguinte script configura o LCM para efetuar pull de configurações de um compartilhamento SMB denominado “SmbDscShare” em um servidor denominado “CONTOSO-SERVER”.</span><span class="sxs-lookup"><span data-stu-id="8210b-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="8210b-142">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8210b-142">Next Steps</span></span>

<span data-ttu-id="8210b-143">Depois que o cliente de pull foi configurado, você pode usar os guias a seguir para executar as próximas etapas:</span><span class="sxs-lookup"><span data-stu-id="8210b-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="8210b-144">Publicar configurações em um servidor de pull (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="8210b-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="8210b-145">Empacotar e carregar recursos em um servidor de pull (v4)</span><span class="sxs-lookup"><span data-stu-id="8210b-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="8210b-146">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8210b-146">See Also</span></span>

- [<span data-ttu-id="8210b-147">Configurar um servidor de pull da web de DSC</span><span class="sxs-lookup"><span data-stu-id="8210b-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="8210b-148">Configurar um servidor de pull SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="8210b-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
