---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Configurando um cliente de pull usando uma ID de configuração"
ms.openlocfilehash: 6e3dda1de0bfbf52fb876fdcd2dd2e99da4583dd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="a2b48-103">Configurando um cliente de pull usando uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="a2b48-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="a2b48-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a2b48-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a2b48-105">Cada nó de destino deve ser instruído a usar o modo de pull e receber a URL em que possa contatar o servidor de pull para obter as configurações.</span><span class="sxs-lookup"><span data-stu-id="a2b48-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="a2b48-106">Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="a2b48-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="a2b48-107">Para configurar o LCM, é criado um tipo especial de configuração, decorada com o atributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="a2b48-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="a2b48-108">Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="a2b48-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="a2b48-109">**Observação**: este tópico se aplica ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="a2b48-109">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="a2b48-110">Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="a2b48-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="a2b48-111">O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="a2b48-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="a2b48-112">No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a2b48-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="a2b48-113">A **ServerURL**</span><span class="sxs-lookup"><span data-stu-id="a2b48-113">The **ServerURL**</span></span>

<span data-ttu-id="a2b48-114">Depois de ser executado, esse script cria uma nova pasta de saída denominada **PullClientConfigID** e coloca nela um arquivo MOF de metaconfiguração.</span><span class="sxs-lookup"><span data-stu-id="a2b48-114">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="a2b48-115">Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="a2b48-115">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="a2b48-116">Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração.</span><span class="sxs-lookup"><span data-stu-id="a2b48-116">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="a2b48-117">Por exemplo: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="a2b48-117">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="a2b48-118">ID de configuração</span><span class="sxs-lookup"><span data-stu-id="a2b48-118">Configuration ID</span></span>

<span data-ttu-id="a2b48-119">O script define a propriedade **ConfigurationID** do LCM para um GUID criado anteriormente para essa finalidade (você pode criar um GUID usando o cmdlet **New-Guid**).</span><span class="sxs-lookup"><span data-stu-id="a2b48-119">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="a2b48-120">O **ConfigurationID** é usado pelo LCM para localizar a configuração apropriada no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a2b48-120">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="a2b48-121">O arquivo MOF de configuração no servidor de pull deve ser nomeado como _ConfigurationID_.mof, em que _ConfigurationID_ é o valor da propriedade **ConfigurationID** do nó de destino do LCM.</span><span class="sxs-lookup"><span data-stu-id="a2b48-121">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="a2b48-122">Servidor de pull de SMB</span><span class="sxs-lookup"><span data-stu-id="a2b48-122">SMB pull server</span></span>

<span data-ttu-id="a2b48-123">Para configurar um cliente para efetuar o pull de configurações de um servidor SMB, use um bloco **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="a2b48-123">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="a2b48-124">Em um bloco **ConfigurationRepositoryShare**, especifique o caminho para o servidor definindo a propriedade **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="a2b48-124">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="a2b48-125">A metaconfiguração a seguir configura o nó de destino para efetuar o pull de um servidor de pull de SMB chamado **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="a2b48-125">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

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
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="a2b48-126">Servidores de recurso e relatório</span><span class="sxs-lookup"><span data-stu-id="a2b48-126">Resource and report servers</span></span>

<span data-ttu-id="a2b48-127">Se você especificar apenas um bloco **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** em sua configuração LCM (como no exemplo anterior), o cliente de pull efetuará pull dos recursos do servidor especificado, mas não enviará relatórios a ele.</span><span class="sxs-lookup"><span data-stu-id="a2b48-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="a2b48-128">Você pode usar um único servidor de pull para emissão de relatórios, recursos e configurações, mas é preciso criar um bloco **ReportRepositoryWeb** para configurar o relatório.</span><span class="sxs-lookup"><span data-stu-id="a2b48-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span> 

<span data-ttu-id="a2b48-129">O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de recursos e configurações, além de enviar dados de relatórios, para um único servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a2b48-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="a2b48-130">Também é possível especificar servidores de pull diferentes para recursos e relatórios.</span><span class="sxs-lookup"><span data-stu-id="a2b48-130">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="a2b48-131">Para especificar um servidor de recurso, utilize um bloco **ResourceRepositoryWeb** (para um servidor de pull da Web) ou um bloco **ResourceRepositoryShare** (para um servidor de pull de SMB).</span><span class="sxs-lookup"><span data-stu-id="a2b48-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="a2b48-132">Para especificar um servidor de relatório, utilize um bloco **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="a2b48-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="a2b48-133">Um servidor de relatório não pode ser um servidor de SMB.</span><span class="sxs-lookup"><span data-stu-id="a2b48-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="a2b48-134">A metaconfiguração a seguir configura um cliente de pull para obter suas configurações de **CONTOSO PullSrv** e seus recursos de **CONTOSO ResourceSrv**, bem como enviar relatórios de status para **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="a2b48-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a2b48-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a2b48-135">See Also</span></span>

* [<span data-ttu-id="a2b48-136">Configurando um cliente de pull com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="a2b48-136">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)

