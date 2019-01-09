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
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="270c4-103">Configurar um cliente de Pull usando IDs de configuração no PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="270c4-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="270c4-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="270c4-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="270c4-105">O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="270c4-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="270c4-106">É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="270c4-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="270c4-107">Antes de configurar um cliente de pull, você deve configurar um servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="270c4-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="270c4-108">Embora essa ordem não for necessária, ele ajuda na solução de problemas e ajuda a garantir que o registro foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="270c4-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="270c4-109">Para configurar um servidor de pull, você pode usar os guias a seguir:</span><span class="sxs-lookup"><span data-stu-id="270c4-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="270c4-110">Configurar um servidor de pull SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="270c4-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="270c4-111">Configurar um servidor de pull HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="270c4-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="270c4-112">Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status.</span><span class="sxs-lookup"><span data-stu-id="270c4-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="270c4-113">As seções a seguir mostram como configurar um cliente de pull com um compartilhamento SMB ou o servidor de Pull de DSC do HTTP.</span><span class="sxs-lookup"><span data-stu-id="270c4-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="270c4-114">Quando o LCM do nó for atualizado, ele entrará em contato para o local configurado para baixar qualquer configurações designadas.</span><span class="sxs-lookup"><span data-stu-id="270c4-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="270c4-115">Se todos os recursos necessários não existirem no nó, ele será automaticamente baixá-los do local configurado.</span><span class="sxs-lookup"><span data-stu-id="270c4-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="270c4-116">Se o nó é configurado com um [servidor de relatório](reportServer.md), em seguida, ele relatará o status da operação.</span><span class="sxs-lookup"><span data-stu-id="270c4-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="270c4-117">**Observação**: Este tópico se aplica ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="270c4-117">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="270c4-118">Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="270c4-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="270c4-119">Configurar o LCM do cliente de pull</span><span class="sxs-lookup"><span data-stu-id="270c4-119">Configure the pull client LCM</span></span>

<span data-ttu-id="270c4-120">Executar qualquer um dos exemplos a seguir cria uma nova pasta de saída denominada **PullClientConfigID** e coloca um arquivo MOF de metaconfiguração nela.</span><span class="sxs-lookup"><span data-stu-id="270c4-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="270c4-121">Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="270c4-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="270c4-122">Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração.</span><span class="sxs-lookup"><span data-stu-id="270c4-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="270c4-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="270c4-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="270c4-124">ID de configuração</span><span class="sxs-lookup"><span data-stu-id="270c4-124">Configuration ID</span></span>

<span data-ttu-id="270c4-125">Os exemplos a seguir define o **ConfigurationID** propriedades do LCM para um **Guid** que criado anteriormente para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="270c4-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="270c4-126">O **ConfigurationID** é usado pelo LCM para localizar a configuração apropriada no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="270c4-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="270c4-127">O arquivo MOF de configuração no servidor de pull deve ser nomeado como `ConfigurationID.mof`, em que *ConfigurationID* é o valor da propriedade **ConfigurationID** do nó de destino do LCM.</span><span class="sxs-lookup"><span data-stu-id="270c4-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="270c4-128">Para obter mais informações, consulte [configurações de publicação para um servidor de recepção (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="270c4-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="270c4-129">Você pode criar um aleatório **Guid** usando o exemplo abaixo, ou usando o [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="270c4-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="270c4-130">Para obter mais informações sobre como usar **Guids** em seu ambiente, consulte [planejar Guids](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="270c4-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="270c4-131">Configurar um cliente de Pull para baixar configurações</span><span class="sxs-lookup"><span data-stu-id="270c4-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="270c4-132">Cada cliente deve ser configurado no **Pull** modo e recebe a url do servidor de pull onde sua configuração está armazenada.</span><span class="sxs-lookup"><span data-stu-id="270c4-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="270c4-133">Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="270c4-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="270c4-134">Para configurar o LCM, é criado um tipo especial de configuração, decorada com o atributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="270c4-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="270c4-135">Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="270c4-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="270c4-136">Servidor de Pull de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="270c4-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="270c4-137">O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="270c4-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="270c4-138">No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="270c4-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="270c4-139">O **ServerUrl** Especifica a url do Pull de DSC</span><span class="sxs-lookup"><span data-stu-id="270c4-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="270c4-140">Compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="270c4-140">SMB Share</span></span>

<span data-ttu-id="270c4-141">O script a seguir configura o LCM para efetuar pull de configurações de compartilhamento SMB `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="270c4-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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

<span data-ttu-id="270c4-142">No script, o **ConfigurationRepositoryShare** bloco define o servidor de pull, que nesse caso, é apenas um compartilhamento SMB.</span><span class="sxs-lookup"><span data-stu-id="270c4-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="270c4-143">Configurar um cliente de Pull para baixar recursos</span><span class="sxs-lookup"><span data-stu-id="270c4-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="270c4-144">Se você especificar apenas o **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquear em sua configuração LCM (como nos exemplos anteriores), o cliente de pull efetuará pull dos recursos da mesma ele recupera suas configurações de local.</span><span class="sxs-lookup"><span data-stu-id="270c4-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="270c4-145">Você também pode especificar locais separados para os recursos.</span><span class="sxs-lookup"><span data-stu-id="270c4-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="270c4-146">Para especificar uma localização de recursos como um servidor separado, use o **ResourceRepositoryWeb** bloco.</span><span class="sxs-lookup"><span data-stu-id="270c4-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="270c4-147">Para especificar uma localização de recursos como um compartilhamento SMB, use o **ResourceRepositoryShare** bloco.</span><span class="sxs-lookup"><span data-stu-id="270c4-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="270c4-148">Você pode combinar **ConfigurationRepositoryWeb** com **ResourceRepositoryShare** ou **ConfigurationRepositoryShare** com **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="270c4-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="270c4-149">Exemplos disso não são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="270c4-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="270c4-150">Servidor de Pull de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="270c4-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="270c4-151">A metaconfiguração a seguir configura um cliente de pull para obter suas configurações de **CONTOSO-PullSrv** e seus recursos de **CONTOSO-ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="270c4-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="270c4-152">Compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="270c4-152">SMB Share</span></span>

<span data-ttu-id="270c4-153">O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de configurações do compartilhamento de SMB `\\SMBPullServer\Configurations`e os recursos de compartilhamento SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="270c4-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="270c4-154">Baixar automaticamente os recursos no modo de Push</span><span class="sxs-lookup"><span data-stu-id="270c4-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="270c4-155">A partir do PowerShell 5.0, seus clientes de pull podem baixar os módulos de um compartilhamento SMB, mesmo quando eles são configurados para **Push** modo.</span><span class="sxs-lookup"><span data-stu-id="270c4-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="270c4-156">Isso é especialmente útil em cenários em que você deseja configurar um servidor de recepção.</span><span class="sxs-lookup"><span data-stu-id="270c4-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="270c4-157">O **ResourceRepositoryShare** bloco pode ser usado sem especificar um **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="270c4-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="270c4-158">O exemplo a seguir mostra uma metaconfiguração que configura um cliente para receber recursos de um compartilhamento SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="270c4-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="270c4-159">Quando o nó está **PUSHED** uma configuração, ele baixará automaticamente todos os recursos necessários, do compartilhamento especificado.</span><span class="sxs-lookup"><span data-stu-id="270c4-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="270c4-160">Configurar um cliente de Pull para relatar o status</span><span class="sxs-lookup"><span data-stu-id="270c4-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="270c4-161">Por padrão, nós não enviará relatórios a um servidor de Pull configurado.</span><span class="sxs-lookup"><span data-stu-id="270c4-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="270c4-162">Você pode usar um único servidor de pull para emissão de relatórios, recursos e configurações, mas é preciso criar um bloco **ReportRepositoryWeb** para configurar o relatório.</span><span class="sxs-lookup"><span data-stu-id="270c4-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="270c4-163">Servidor de Pull de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="270c4-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="270c4-164">O exemplo a seguir mostra uma metaconfiguração que configura um cliente para efetuar pull de recursos e configurações, além de enviar dados de relatórios, para um único servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="270c4-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="270c4-165">Para especificar um servidor de relatório, utilize um bloco **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="270c4-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="270c4-166">Um servidor de relatório não pode ser um servidor de SMB.</span><span class="sxs-lookup"><span data-stu-id="270c4-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="270c4-167">A metaconfiguração a seguir configura um cliente de pull para obter suas configurações de **CONTOSO PullSrv** e seus recursos de **CONTOSO ResourceSrv**, bem como enviar relatórios de status para **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="270c4-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="270c4-168">Compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="270c4-168">SMB Share</span></span>

<span data-ttu-id="270c4-169">Um servidor de relatório não pode ser um compartilhamento SMB.</span><span class="sxs-lookup"><span data-stu-id="270c4-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="270c4-170">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="270c4-170">Next Steps</span></span>

<span data-ttu-id="270c4-171">Depois que o cliente de pull foi configurado, você pode usar os guias a seguir para executar as próximas etapas:</span><span class="sxs-lookup"><span data-stu-id="270c4-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="270c4-172">Publicar configurações em um servidor de pull (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="270c4-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="270c4-173">Empacotar e carregar recursos em um servidor de pull (v4)</span><span class="sxs-lookup"><span data-stu-id="270c4-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="270c4-174">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="270c4-174">See Also</span></span>

* [<span data-ttu-id="270c4-175">Configurando um cliente de pull com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="270c4-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
