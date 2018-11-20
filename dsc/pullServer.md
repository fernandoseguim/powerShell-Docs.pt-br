---
ms.date: 04/11/2018
keywords: DSC,powershell,configuração,instalação
title: Serviço de Pull de DSC
ms.openlocfilehash: 2ef48b88cc9e14da452e0d19e5a0f43fc8a95ab2
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619153"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="b484d-103">Serviço de Pull de Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="b484d-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="b484d-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b484d-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b484d-105">O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="b484d-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b484d-106">É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="b484d-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b484d-107">O Gerenciador de Configurações Local pode ser gerenciado centralmente por uma solução de Serviço de Pull.</span><span class="sxs-lookup"><span data-stu-id="b484d-107">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="b484d-108">Ao usar essa abordagem, o nó que está sendo gerenciado é registrado com um serviço e uma configuração é atribuída a ele em configurações de LCM.</span><span class="sxs-lookup"><span data-stu-id="b484d-108">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="b484d-109">A configuração e todos os recursos de DSC necessários como dependências para a configuração são baixados para o computador e usados pelo LCM para gerenciar a configuração.</span><span class="sxs-lookup"><span data-stu-id="b484d-109">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="b484d-110">As informações sobre o estado do computador que está sendo gerenciado são carregadas no serviço para relatório.</span><span class="sxs-lookup"><span data-stu-id="b484d-110">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="b484d-111">Esse conceito é conhecido como "serviço de pull".</span><span class="sxs-lookup"><span data-stu-id="b484d-111">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="b484d-112">As opções atuais para o serviço de pull incluem:</span><span class="sxs-lookup"><span data-stu-id="b484d-112">The current options for pull service include:</span></span>

- <span data-ttu-id="b484d-113">Serviço de Configuração de Estado Desejado da Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="b484d-113">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="b484d-114">Um serviço de pull em execução no Windows Server</span><span class="sxs-lookup"><span data-stu-id="b484d-114">A pull service running on Windows Server</span></span>
- <span data-ttu-id="b484d-115">Soluções de software livre mantidas pela comunidade</span><span class="sxs-lookup"><span data-stu-id="b484d-115">Community maintained open-source solutions</span></span>
- <span data-ttu-id="b484d-116">Um compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="b484d-116">An SMB share</span></span>

<span data-ttu-id="b484d-117">**A solução recomendada**, e a opção com a maioria dos recursos disponíveis, é [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="b484d-117">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="b484d-118">O serviço do Azure pode gerenciar nós localmente em datacenters privados ou em nuvens públicas, como AWS e o Azure.</span><span class="sxs-lookup"><span data-stu-id="b484d-118">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="b484d-119">Para ambientes privados, onde os servidores não podem se conectar diretamente à Internet, considere limitar o tráfego de saída apenas ao intervalo de IPs do Azure publicado (consulte [Intervalos de IP de Datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="b484d-119">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="b484d-120">Entre os recursos do serviço online que não estão disponíveis no serviço de pull no Windows Server estão:</span><span class="sxs-lookup"><span data-stu-id="b484d-120">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="b484d-121">Todos os dados são criptografados em trânsito e em repouso</span><span class="sxs-lookup"><span data-stu-id="b484d-121">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="b484d-122">Certificados de cliente são criados e gerenciados automaticamente</span><span class="sxs-lookup"><span data-stu-id="b484d-122">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="b484d-123">Armazenamento de segredos para gerenciar centralmente [senhas/credenciais](/azure/automation/automation-credentials), ou [variáveis](/azure/automation/automation-variables) como nomes de servidor ou cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="b484d-123">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="b484d-124">Gerenciar centralmente o nó [Configuração do LCM](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="b484d-124">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="b484d-125">Atribuir centralmente configurações a nós do cliente</span><span class="sxs-lookup"><span data-stu-id="b484d-125">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="b484d-126">Alterações na configuração de versão de "grupos canário" para teste antes de chegar à produção</span><span class="sxs-lookup"><span data-stu-id="b484d-126">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="b484d-127">Relatório gráfico</span><span class="sxs-lookup"><span data-stu-id="b484d-127">Graphical reporting</span></span>
  - <span data-ttu-id="b484d-128">Detalhes de status no nível de granularidade de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="b484d-128">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="b484d-129">Mensagens de erro detalhadas de computadores cliente para solução de problemas</span><span class="sxs-lookup"><span data-stu-id="b484d-129">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="b484d-130">[Integração com o Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) para alertas, tarefas automatizadas, aplicativo para Android/iOS para relatórios e alertas</span><span class="sxs-lookup"><span data-stu-id="b484d-130">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="b484d-131">Serviço de pull de DSC no Windows Server</span><span class="sxs-lookup"><span data-stu-id="b484d-131">DSC pull service in Windows Server</span></span>

<span data-ttu-id="b484d-132">É possível configurar um serviço de pull para ser executado no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="b484d-132">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="b484d-133">Fique ciente de que a solução de serviço de pull incluída no Windows Server inclui apenas as funcionalidades de armazenamento de configurações/módulos para download e de captura de dados de relatório para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b484d-133">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="b484d-134">Ela não inclui muitas das funcionalidades oferecidas pelo serviço no Azure e, portanto, não é uma boa ferramenta para avaliar o modo como o serviço seria usado.</span><span class="sxs-lookup"><span data-stu-id="b484d-134">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="b484d-135">O serviço de pull oferecido no Windows Server é um serviço Web no IIS que utiliza uma interface OData para disponibilizar arquivos de configuração DSC para nós de destino quando são pedidos por tais nós.</span><span class="sxs-lookup"><span data-stu-id="b484d-135">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="b484d-136">Requisitos para usar um servidor de pull:</span><span class="sxs-lookup"><span data-stu-id="b484d-136">Requirements for using a pull server:</span></span>

- <span data-ttu-id="b484d-137">Um servidor que execute:</span><span class="sxs-lookup"><span data-stu-id="b484d-137">A server running:</span></span>
  - <span data-ttu-id="b484d-138">WMF/PowerShell 5.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="b484d-138">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="b484d-139">Função de servidor do IIS</span><span class="sxs-lookup"><span data-stu-id="b484d-139">IIS server role</span></span>
  - <span data-ttu-id="b484d-140">Serviço de DSC</span><span class="sxs-lookup"><span data-stu-id="b484d-140">DSC Service</span></span>
- <span data-ttu-id="b484d-141">Idealmente, alguns meios de gerar um certificado para proteger as credenciais passadas para o Gerenciador de Configurações Local (LCM) em nós de destino</span><span class="sxs-lookup"><span data-stu-id="b484d-141">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="b484d-142">A melhor maneira de configurar o Windows Server para hospedar o serviço de pull é usar uma configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="b484d-142">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="b484d-143">Um script de exemplo é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="b484d-143">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="b484d-144">Sistemas de banco de dados com suporte</span><span class="sxs-lookup"><span data-stu-id="b484d-144">Supported database systems</span></span>

|<span data-ttu-id="b484d-145">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="b484d-145">WMF 4.0</span></span>   |<span data-ttu-id="b484d-146">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="b484d-146">WMF 5.0</span></span>  |<span data-ttu-id="b484d-147">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b484d-147">WMF 5.1</span></span> |<span data-ttu-id="b484d-148">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="b484d-148">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="b484d-149">MDB</span><span class="sxs-lookup"><span data-stu-id="b484d-149">MDB</span></span>     |<span data-ttu-id="b484d-150">ESENT (padrão), MDB</span><span class="sxs-lookup"><span data-stu-id="b484d-150">ESENT (Default), MDB</span></span> |<span data-ttu-id="b484d-151">ESENT (padrão), MDB</span><span class="sxs-lookup"><span data-stu-id="b484d-151">ESENT (Default), MDB</span></span>|<span data-ttu-id="b484d-152">ESENT (padrão), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="b484d-152">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="b484d-153">Começando na versão 17090 do [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), o SQL Server é uma opção compatível com o serviço de pull (Recurso do Windows *Serviço de DSC*).</span><span class="sxs-lookup"><span data-stu-id="b484d-153">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span>  <span data-ttu-id="b484d-154">Essa é uma nova opção para dimensionar grandes ambientes de DSC que não foram migrados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="b484d-154">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> <span data-ttu-id="b484d-155">**Observação**: o suporte ao SQL Server não será adicionado às versões anteriores do WMF 5.1 (ou mais antigas) e só estará disponível nas versões do Windows Server maiores ou iguais à 17090.</span><span class="sxs-lookup"><span data-stu-id="b484d-155">**Note**: SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="b484d-156">Para configurar o servidor de recepção para usar o SQL Server, defina **SqlProvider** para `$true` e **SqlConnectionString** para uma cadeia de conexão válida do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b484d-156">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span>  <span data-ttu-id="b484d-157">Para obter mais informações, confira [Cadeias de conexão SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="b484d-157">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="b484d-158">Para obter um exemplo de configuração do SQL Server com **xDscWebService**, primeiro leia [Usando o recurso xDscWebService](#using-the-xdscwebservice-resource) e, em seguida, examine [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 no GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="b484d-158">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="b484d-159">Usando o recurso xDscWebService</span><span class="sxs-lookup"><span data-stu-id="b484d-159">Using the xDscWebService resource</span></span>

<span data-ttu-id="b484d-160">A maneira mais fácil de configurar um servidor de recepção Web é usar o recurso **xDscWebService**, incluído no módulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="b484d-160">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="b484d-161">As etapas a seguir explicam como usar o recurso em uma configuração que configure o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="b484d-161">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="b484d-162">Chame o cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) para instalar o módulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="b484d-162">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="b484d-163">**Observação**: **Install-Module** está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="b484d-163">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="b484d-164">É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="b484d-164">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
1. <span data-ttu-id="b484d-165">Obtenha um certificado SSL para o servidor de Pull de DSC de uma Autoridade de Certificação confiável, seja de dentro de sua organização ou de uma autoridade pública.</span><span class="sxs-lookup"><span data-stu-id="b484d-165">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="b484d-166">O certificado recebido da autoridade geralmente está no formato PFX.</span><span class="sxs-lookup"><span data-stu-id="b484d-166">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="b484d-167">Instale o certificado no nó que se tornará o servidor de recepção de DSC no local padrão, que deve ser CERT:\LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="b484d-167">Install the certificate on the node that will become the DSC Pull server in the default location, which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="b484d-168">Anote a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="b484d-168">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="b484d-169">Selecione um GUID a ser usado como a Chave de Registro.</span><span class="sxs-lookup"><span data-stu-id="b484d-169">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="b484d-170">Para gerar um, usando o PowerShell, insira o seguinte no prompt do PS e pressione enter: '``` [guid]::newGuid()```' ou '```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="b484d-170">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="b484d-171">Essa chave será usada por nós de cliente como uma chave compartilhada para autenticação durante o registro.</span><span class="sxs-lookup"><span data-stu-id="b484d-171">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="b484d-172">Para obter mais informações, confira a seção Chave de registro abaixo.</span><span class="sxs-lookup"><span data-stu-id="b484d-172">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="b484d-173">No ISE do PowerShell, inicie (F5) o script de configuração a seguir (incluído na pasta Exemplos do módulo **xPSDesiredStateConfiguration** como Sample_xDscWebServiceRegistration.ps1).</span><span class="sxs-lookup"><span data-stu-id="b484d-173">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebServiceRegistration.ps1).</span></span> <span data-ttu-id="b484d-174">Esse script configura o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="b484d-174">This script sets up the pull server.</span></span>

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

1. <span data-ttu-id="b484d-175">Execute a configuração, passando a impressão digital do certificado SSL como o parâmetro **certificateThumbPrint** e uma chave de Registro GUID como o parâmetro **RegistrationKey**:</span><span class="sxs-lookup"><span data-stu-id="b484d-175">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="b484d-176">Chave de Registro</span><span class="sxs-lookup"><span data-stu-id="b484d-176">Registration Key</span></span>

<span data-ttu-id="b484d-177">Para permitir que os nós clientes sejam registrados no servidor para poderem usar nomes de configuração em vez de uma ID de configuração, uma chave de registro que foi criada pela configuração acima é salva em um arquivo chamado `RegistrationKeys.txt` em `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="b484d-177">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="b484d-178">A chave de registro funciona como um segredo compartilhado usado durante o registro inicial pelo cliente com o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="b484d-178">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="b484d-179">O cliente gerará um certificado autoassinado, que será usado para realizar uma autenticação exclusiva no servidor de recepção depois que o registro for concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="b484d-179">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="b484d-180">A impressão digital do certificado é armazenada localmente e associada à URL do servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="b484d-180">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="b484d-181">**Observação**: não há suporte para chaves do registro no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="b484d-181">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="b484d-182">Para configurar um nó para ser autenticado no servidor de recepção, a chave de registro deverá estar na metaconfiguração do nó de destino que será registrado nesse servidor de recepção.</span><span class="sxs-lookup"><span data-stu-id="b484d-182">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="b484d-183">Observe que a **RegistrationKey** na metaconfiguração abaixo é removida depois de o computador de destino ser registrado com sucesso, e o valor “140a952b-b9d6-406b-b416-e0f759c9c0e4” deve corresponder ao valor armazenado no arquivo RegistrationKeys.txt no servidor pull.</span><span class="sxs-lookup"><span data-stu-id="b484d-183">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="b484d-184">Sempre trate o valor da chave do registro com segurança, porque o conhecimento permite que qualquer computador de destino seja registrado com o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="b484d-184">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> <span data-ttu-id="b484d-185">**Observação**: a seção **ReportServerWeb** permite que dados de relatório sejam enviados ao servidor pull.</span><span class="sxs-lookup"><span data-stu-id="b484d-185">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="b484d-186">A falta da propriedade **ConfigurationID** no arquivo de metaconfiguração significa implicitamente que esse servidor pull dá suporte à versão V2 do protocolo de servidor pull, de modo que um registro inicial é necessário.</span><span class="sxs-lookup"><span data-stu-id="b484d-186">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="b484d-187">Por outro lado, a presença de uma **ConfigurationID** significa que a versão V1 do protocolo do servidor de pull é usada e não há nenhum processamento de registro.</span><span class="sxs-lookup"><span data-stu-id="b484d-187">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="b484d-188">**Observação**: em um cenário de PUSH, existe um bug na versão atual que exige a definição de uma propriedade ConfigurationID no arquivo de metaconfiguração para nós que nunca foram registrados em um servidor recepção.</span><span class="sxs-lookup"><span data-stu-id="b484d-188">**Note**: In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="b484d-189">Isso forçará o uso do protocolo de Servidor de Pull V1 e evitará mensagens de falha de registro.</span><span class="sxs-lookup"><span data-stu-id="b484d-189">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="b484d-190">Colocando configurações e recursos</span><span class="sxs-lookup"><span data-stu-id="b484d-190">Placing configurations and resources</span></span>

<span data-ttu-id="b484d-191">Após a instalação do servidor pull ser concluída, as pastas definidas pelas propriedades **ConfigurationPath** e **ModulePath** na configuração do servidor pull são onde você colocará módulos e configurações que estarão disponíveis para pull pelos nós de destino.</span><span class="sxs-lookup"><span data-stu-id="b484d-191">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="b484d-192">Esses arquivos precisam estar em um formato específico para que o servidor de recepção processe-os corretamente.</span><span class="sxs-lookup"><span data-stu-id="b484d-192">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="b484d-193">Formato de pacote do módulo de recursos DSC</span><span class="sxs-lookup"><span data-stu-id="b484d-193">DSC resource module package format</span></span>

<span data-ttu-id="b484d-194">Cada módulo de recurso precisa ser compactado e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="b484d-194">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="b484d-195">Por exemplo, um módulo chamado xWebAdminstration com uma versão do módulo correspondente a 3.1.2.0 seria nomeado 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="b484d-195">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="b484d-196">Cada versão de um módulo deve estar contido em um único arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="b484d-196">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="b484d-197">Como há apenas uma única versão de um recurso em cada arquivo zip, não há suporte para o formato do módulo adicionado ao WMF 5.0 com suporte para várias versões de módulo em um único diretório.</span><span class="sxs-lookup"><span data-stu-id="b484d-197">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="b484d-198">Isso significa que antes de empacotar módulos de recursos DSC para uso com o servidor de pull, você precisará fazer uma pequena alteração na estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="b484d-198">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="b484d-199">O formato padrão dos módulos contendo o recurso DSC no WMF 5.0 é '{Pasta do Módulo}\{{Versão do Módulo}\DscResources\{{Pasta do Recurso DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="b484d-199">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="b484d-200">Antes de realizar o empacotamento para o servidor de recepção, remova a pasta **{Module version}** para que o caminho se torne '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span><span class="sxs-lookup"><span data-stu-id="b484d-200">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="b484d-201">Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="b484d-201">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="b484d-202">Use `New-DscChecksum {module zip file}` para criar um arquivo de soma de verificação para o módulo recém-adicionado.</span><span class="sxs-lookup"><span data-stu-id="b484d-202">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="b484d-203">Formato MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="b484d-203">Configuration MOF format</span></span>

<span data-ttu-id="b484d-204">Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="b484d-204">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="b484d-205">Para criar uma soma de verificação, chame o cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum).</span><span class="sxs-lookup"><span data-stu-id="b484d-205">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="b484d-206">O cmdlet usa um parâmetro **Path** que especifica a pasta na qual se encontra o MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="b484d-206">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="b484d-207">O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="b484d-207">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="b484d-208">Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="b484d-208">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="b484d-209">Coloque os arquivos MOF e os arquivos de soma de verificação associados na pasta **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="b484d-209">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="b484d-210">**Observação**: se alterar o arquivo MOF de configuração de qualquer forma, você também deverá recriar o arquivo de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="b484d-210">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="b484d-211">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="b484d-211">Tooling</span></span>

<span data-ttu-id="b484d-212">Para facilitar a configuração, validação e gerenciamento do servidor de pull, as ferramentas a seguir são incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="b484d-212">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="b484d-213">Um módulo que ajudará com empacotamento de módulos de recursos DSC e arquivos de configuração para uso no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="b484d-213">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="b484d-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="b484d-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="b484d-215">Exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="b484d-215">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="b484d-216">Um script que valida o Servidor de Pull está configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="b484d-216">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="b484d-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="b484d-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="b484d-218">Soluções da comunidade para o Serviço de Pull</span><span class="sxs-lookup"><span data-stu-id="b484d-218">Community Solutions for Pull Service</span></span>

<span data-ttu-id="b484d-219">A comunidade de DSC criou várias soluções para implementar o protocolo de serviço de pull.</span><span class="sxs-lookup"><span data-stu-id="b484d-219">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="b484d-220">Para ambientes locais, elas oferecem funcionalidades de serviço de pull e uma oportunidade de retribuir à comunidade, contribuindo com melhorias incrementais.</span><span class="sxs-lookup"><span data-stu-id="b484d-220">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="b484d-221">Tug</span><span class="sxs-lookup"><span data-stu-id="b484d-221">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="b484d-222">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="b484d-222">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="b484d-223">Configuração do cliente de pull</span><span class="sxs-lookup"><span data-stu-id="b484d-223">Pull client configuration</span></span>

<span data-ttu-id="b484d-224">Os tópicos a seguir descrevem em detalhes a configuração de clientes de pull:</span><span class="sxs-lookup"><span data-stu-id="b484d-224">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="b484d-225">Configurando um cliente de pull de DSC usando uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="b484d-225">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="b484d-226">Configurando um cliente de pull de DSC usando nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="b484d-226">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="b484d-227">Configurações parciais</span><span class="sxs-lookup"><span data-stu-id="b484d-227">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="b484d-228">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b484d-228">See also</span></span>

- [<span data-ttu-id="b484d-229">Visão Geral da Configuração de Estado Desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b484d-229">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="b484d-230">Aplicando configurações</span><span class="sxs-lookup"><span data-stu-id="b484d-230">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="b484d-231">Usando um servidor de relatório de DSC</span><span class="sxs-lookup"><span data-stu-id="b484d-231">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="b484d-232">[[MS-DSCPM]: protocolo Desired State Configuration Pull Model](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="b484d-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="b484d-233">[[MS-DSCPM]: errata do protocolo Desired State Configuration Pull Model](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="b484d-233">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
