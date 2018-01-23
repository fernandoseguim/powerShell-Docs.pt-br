---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Configurando um cliente de pull usando nomes de configuração"
ms.openlocfilehash: 11de53fc349ce0ebacf0d4855d82fa8a22d55c99
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="74f80-103">Configurando um cliente de pull usando nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="74f80-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="74f80-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="74f80-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="74f80-105">Cada nó de destino deve ser instruído a usar o modo de pull e receber a URL em que possa contatar o servidor de pull para obter as configurações.</span><span class="sxs-lookup"><span data-stu-id="74f80-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="74f80-106">Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="74f80-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="74f80-107">Para configurar o LCM, é criado um tipo especial de configuração, decorada com o atributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="74f80-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="74f80-108">Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="74f80-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="74f80-109">**Observação**: este tópico se aplica ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="74f80-109">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="74f80-110">Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="74f80-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="74f80-111">O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "CONTOSO-PullSrv":</span><span class="sxs-lookup"><span data-stu-id="74f80-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

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

<span data-ttu-id="74f80-112">No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="74f80-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="74f80-113">A propriedade **ServerURL** especifica o ponto de extremidade para o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="74f80-113">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="74f80-114">A propriedade **RegistrationKey** é uma chave compartilhada entre todos os nós de cliente para um servidor de pull e esse servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="74f80-114">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="74f80-115">O mesmo valor é armazenado em um arquivo no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="74f80-115">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="74f80-116">A propriedade **ConfigurationNames** em uma matriz que especifica os nomes das configurações destinadas ao nó do cliente.</span><span class="sxs-lookup"><span data-stu-id="74f80-116">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="74f80-117">No servidor de pull, o arquivo MOF de configuração para esse nó do cliente deve ser nomeado *ConfigurationNames*.mof, em que *ConfigurationNames* corresponde ao valor da propriedade **ConfigurationNames** definida nessa metaconfiguração.</span><span class="sxs-lookup"><span data-stu-id="74f80-117">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="74f80-118">**Observação:** se você especificar mais de um valor em **ConfigurationNames**, também será necessário especificar blocos **PartialConfiguration** na configuração.</span><span class="sxs-lookup"><span data-stu-id="74f80-118">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="74f80-119">Para obter informações sobre configurações parciais, veja [Configurações parciais da Configuração de Estado Desejado do PowerShell](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="74f80-119">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="74f80-120">Depois de ser executado, esse script cria uma nova pasta de saída chamada **PullClientConfigNames** e coloca um arquivo MOF de metaconfiguração nela.</span><span class="sxs-lookup"><span data-stu-id="74f80-120">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="74f80-121">Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="74f80-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="74f80-122">Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração.</span><span class="sxs-lookup"><span data-stu-id="74f80-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="74f80-123">**Observação**: as chaves de registro funcionam apenas com servidores de pull da Web.</span><span class="sxs-lookup"><span data-stu-id="74f80-123">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="74f80-124">Você ainda deve usar **ConfigurationID** com um servidor de pull de SMB.</span><span class="sxs-lookup"><span data-stu-id="74f80-124">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="74f80-125">Para obter informações sobre como configurar um servidor de pull usando **ConfigurationID**, consulte [Configurando um cliente de pull usando uma ID de configuração](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="74f80-125">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="74f80-126">Servidores de recurso e relatório</span><span class="sxs-lookup"><span data-stu-id="74f80-126">Resource and report servers</span></span>

<span data-ttu-id="74f80-127">Se você especificar apenas um bloco **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** em sua configuração LCM (como no exemplo anterior), o cliente de pull efetuará pull dos recursos do servidor especificado, mas não enviará relatórios a ele.</span><span class="sxs-lookup"><span data-stu-id="74f80-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="74f80-128">Você pode usar um único servidor de pull para emissão de relatórios, recursos e configurações, mas é preciso criar um bloco **ReportRepositoryWeb** para configurar o relatório.</span><span class="sxs-lookup"><span data-stu-id="74f80-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="74f80-129">O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de recursos e configurações, além de enviar dados de relatórios, para um único servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="74f80-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="74f80-130">Também é possível especificar servidores de pull diferentes para recursos e relatórios.</span><span class="sxs-lookup"><span data-stu-id="74f80-130">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="74f80-131">Para especificar um servidor de recurso, utilize um bloco **ResourceRepositoryWeb** (para um servidor de pull da Web) ou um bloco **ResourceRepositoryShare** (para um servidor de pull de SMB).</span><span class="sxs-lookup"><span data-stu-id="74f80-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="74f80-132">Para especificar um servidor de relatório, utilize um bloco **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="74f80-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="74f80-133">Um servidor de relatório não pode ser um servidor de SMB.</span><span class="sxs-lookup"><span data-stu-id="74f80-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="74f80-134">A metaconfiguração a seguir configura um cliente de pull para obter suas configurações de **CONTOSO PullSrv** e seus recursos de **CONTOSO ResourceSrv**, bem como enviar relatórios de status para **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="74f80-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="74f80-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="74f80-135">See Also</span></span>

* [<span data-ttu-id="74f80-136">Configurando um cliente de pull com uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="74f80-136">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="74f80-137">Configurando um servidor de pull da Web de DSC</span><span class="sxs-lookup"><span data-stu-id="74f80-137">Setting up a DSC web pull server</span></span>](pullServer.md)

