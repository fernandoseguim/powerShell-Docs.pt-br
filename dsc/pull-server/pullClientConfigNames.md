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
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="e4267-103">Configurar um cliente de Pull usando nomes de configuração no PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="e4267-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="e4267-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e4267-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4267-105">O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="e4267-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="e4267-106">É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="e4267-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="e4267-107">Antes de configurar um cliente de pull, você deve configurar um servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="e4267-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="e4267-108">Embora essa ordem não for necessária, ele ajuda na solução de problemas e ajuda a garantir que o registro foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="e4267-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="e4267-109">Para configurar um servidor de pull, você pode usar os guias a seguir:</span><span class="sxs-lookup"><span data-stu-id="e4267-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="e4267-110">Configurar um servidor de pull SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="e4267-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="e4267-111">Configurar um servidor de pull HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="e4267-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="e4267-112">Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status.</span><span class="sxs-lookup"><span data-stu-id="e4267-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="e4267-113">As seções a seguir mostram como configurar um cliente de pull com um compartilhamento SMB ou o servidor de Pull de DSC do HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4267-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="e4267-114">Quando o LCM do nó for atualizado, ele entrará em contato para o local configurado para baixar qualquer configurações designadas.</span><span class="sxs-lookup"><span data-stu-id="e4267-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="e4267-115">Se todos os recursos necessários não existirem no nó, ele será automaticamente baixá-los do local configurado.</span><span class="sxs-lookup"><span data-stu-id="e4267-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="e4267-116">Se o nó é configurado com um [servidor de relatório](reportServer.md), em seguida, ele relatará o status da operação.</span><span class="sxs-lookup"><span data-stu-id="e4267-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="e4267-117">**Observação**: Este tópico se aplica ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="e4267-117">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="e4267-118">Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, consulte [configurar um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="e4267-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="e4267-119">Configurar o LCM do cliente de pull</span><span class="sxs-lookup"><span data-stu-id="e4267-119">Configure the pull client LCM</span></span>

<span data-ttu-id="e4267-120">Executar qualquer um dos exemplos a seguir cria uma nova pasta de saída denominada **PullClientConfigName** e coloca um arquivo MOF de metaconfiguração nela.</span><span class="sxs-lookup"><span data-stu-id="e4267-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="e4267-121">Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="e4267-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="e4267-122">Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração.</span><span class="sxs-lookup"><span data-stu-id="e4267-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="e4267-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e4267-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="e4267-124">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="e4267-124">Configuration Name</span></span>

<span data-ttu-id="e4267-125">Os exemplos a seguir define o **ConfigurationName** propriedades do LCM para o nome de uma configuração compilada anteriormente, criada para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="e4267-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="e4267-126">O **ConfigurationName** é o que o LCM usa para localizar a configuração apropriada no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="e4267-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="e4267-127">O arquivo MOF de configuração no servidor de pull deve ser nomeado `<ConfigurationName>.mof`, nesse caso, "ClientConfig.mof".</span><span class="sxs-lookup"><span data-stu-id="e4267-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="e4267-128">Para obter mais informações, consulte [configurações de publicação para um servidor de recepção (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="e4267-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="e4267-129">Configurar um cliente de Pull para baixar configurações</span><span class="sxs-lookup"><span data-stu-id="e4267-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="e4267-130">Cada cliente deve ser configurado no **Pull** modo e recebe a url do servidor de pull onde sua configuração está armazenada.</span><span class="sxs-lookup"><span data-stu-id="e4267-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="e4267-131">Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="e4267-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="e4267-132">Para configurar o LCM, é criado um tipo especial de configuração, decorada com o atributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="e4267-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="e4267-133">Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="e4267-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="e4267-134">O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="e4267-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="e4267-135">No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="e4267-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="e4267-136">A propriedade **ServerURL** especifica o ponto de extremidade para o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="e4267-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="e4267-137">A propriedade **RegistrationKey** é uma chave compartilhada entre todos os nós de cliente para um servidor de pull e esse servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="e4267-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="e4267-138">O mesmo valor é armazenado em um arquivo no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="e4267-138">The same value is stored in a file on the pull server.</span></span>
  > <span data-ttu-id="e4267-139">**Observação**: As chaves de registro funcionam apenas com **web** servidores de pull.</span><span class="sxs-lookup"><span data-stu-id="e4267-139">**Note**: Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="e4267-140">Você ainda deve usar **ConfigurationID** com um servidor de pull de **SMB**.</span><span class="sxs-lookup"><span data-stu-id="e4267-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="e4267-141">Para obter informações sobre como configurar um servidor de pull usando **ConfigurationID**, consulte [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="e4267-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="e4267-142">A propriedade **ConfigurationNames** em uma matriz que especifica os nomes das configurações destinadas ao nó do cliente.</span><span class="sxs-lookup"><span data-stu-id="e4267-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="e4267-143">**Observação:** Se você especificar mais de um valor em **ConfigurationNames**, também será necessário especificar blocos **PartialConfiguration** na configuração.</span><span class="sxs-lookup"><span data-stu-id="e4267-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="e4267-144">Para obter informações sobre configurações parciais, veja [Configurações parciais da Configuração de Estado Desejado do PowerShell](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="e4267-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="e4267-145">Configurar um cliente de Pull para baixar recursos</span><span class="sxs-lookup"><span data-stu-id="e4267-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="e4267-146">Se você especificar apenas um **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquear em sua configuração LCM (como no exemplo anterior), o cliente de pull efetuará pull dos recursos do mesmo local de armazenavam de seus arquivos ". MOF".</span><span class="sxs-lookup"><span data-stu-id="e4267-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="e4267-147">Você também pode especificar diferentes locais em que os clientes podem baixar os recursos.</span><span class="sxs-lookup"><span data-stu-id="e4267-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="e4267-148">Para especificar um servidor de recurso, utilize um bloco **ResourceRepositoryWeb** (para um servidor de pull da Web) ou um bloco **ResourceRepositoryShare** (para um servidor de pull de SMB).</span><span class="sxs-lookup"><span data-stu-id="e4267-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="e4267-149">O exemplo a seguir mostra uma metaconfiguração que configura um cliente para baixar as configurações de um servidor de Pull e recursos de um compartilhamento SMB.</span><span class="sxs-lookup"><span data-stu-id="e4267-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="e4267-150">Configurar um cliente de Pull para relatar o status</span><span class="sxs-lookup"><span data-stu-id="e4267-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="e4267-151">Você pode usar um único servidor de pull para emissão de relatórios, recursos e configurações.</span><span class="sxs-lookup"><span data-stu-id="e4267-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="e4267-152">Emissão de relatórios não está configurado para clientes por padrão.</span><span class="sxs-lookup"><span data-stu-id="e4267-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="e4267-153">Para configurar um cliente para relatar o status, você precisa criar uma **ReportRepositoryWeb** bloco.</span><span class="sxs-lookup"><span data-stu-id="e4267-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="e4267-154">O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de recursos e configurações, além de enviar dados de relatórios, para um único servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="e4267-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="e4267-155">Um servidor de relatório não pode ser um compartilhamento SMB.</span><span class="sxs-lookup"><span data-stu-id="e4267-155">A report server cannot be an SMB share.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e4267-156">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="e4267-156">See Also</span></span>

* [<span data-ttu-id="e4267-157">Configurando um cliente de pull com uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="e4267-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="e4267-158">Configurando um servidor de pull da Web de DSC</span><span class="sxs-lookup"><span data-stu-id="e4267-158">Setting up a DSC web pull server</span></span>](pullServer.md)
