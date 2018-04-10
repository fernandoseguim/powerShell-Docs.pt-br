---
ms.date: 02/02/2018
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Serviço de Pull de DSC
ms.openlocfilehash: 1547092d5ea6733296bf89f05dd96f70c0a000ac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="22a49-103">Serviço de Pull de Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="22a49-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="22a49-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="22a49-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="22a49-105">O Gerenciador de Configurações Local pode ser gerenciado centralmente por uma solução de Serviço de Pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-105">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="22a49-106">Ao usar essa abordagem, o nó que está sendo gerenciado é registrado com um serviço e uma configuração é atribuída a ele em configurações de LCM.</span><span class="sxs-lookup"><span data-stu-id="22a49-106">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="22a49-107">A configuração e todos os recursos de DSC necessários como dependências para a configuração são baixados para o computador e usados pelo LCM para gerenciar a configuração.</span><span class="sxs-lookup"><span data-stu-id="22a49-107">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="22a49-108">As informações sobre o estado do computador que está sendo gerenciado são carregadas no serviço para relatório.</span><span class="sxs-lookup"><span data-stu-id="22a49-108">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="22a49-109">Esse conceito é conhecido como "serviço de pull".</span><span class="sxs-lookup"><span data-stu-id="22a49-109">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="22a49-110">As opções atuais para o serviço de pull incluem:</span><span class="sxs-lookup"><span data-stu-id="22a49-110">The current options for pull service include:</span></span>

- <span data-ttu-id="22a49-111">Serviço de Configuração de Estado Desejado da Automação do Azure</span><span class="sxs-lookup"><span data-stu-id="22a49-111">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="22a49-112">Um serviço de pull em execução no Windows Server</span><span class="sxs-lookup"><span data-stu-id="22a49-112">A pull service running on Windows Server</span></span>
- <span data-ttu-id="22a49-113">Soluções de software livre mantidas pela comunidade</span><span class="sxs-lookup"><span data-stu-id="22a49-113">Community maintained open source solutions</span></span>
- <span data-ttu-id="22a49-114">Um compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="22a49-114">An SMB share</span></span>

<span data-ttu-id="22a49-115">**A solução recomendada**, e a opção com a maioria dos recursos disponíveis, é [DSC de Automação do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="22a49-115">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="22a49-116">O serviço do Azure pode gerenciar nós localmente em datacenters privados ou em nuvens públicas, como AWS e o Azure.</span><span class="sxs-lookup"><span data-stu-id="22a49-116">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="22a49-117">Para ambientes privados, onde os servidores não podem se conectar diretamente à Internet, considere limitar o tráfego de saída apenas ao intervalo de IPs do Azure publicado (consulte [Intervalos de IP de Datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="22a49-117">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="22a49-118">Entre os recursos do serviço online que não estão disponíveis no serviço de pull no Windows Server estão:</span><span class="sxs-lookup"><span data-stu-id="22a49-118">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="22a49-119">Todos os dados são criptografados em trânsito e em repouso</span><span class="sxs-lookup"><span data-stu-id="22a49-119">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="22a49-120">Certificados de cliente são criados e gerenciados automaticamente</span><span class="sxs-lookup"><span data-stu-id="22a49-120">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="22a49-121">Armazenamento de segredos para gerenciar centralmente [senhas/credenciais](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), ou [variáveis](https://docs.microsoft.com/en-us/azure/automation/automation-variables) como nomes de servidor ou cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="22a49-121">Secrets store for centrally managing [passwords/credentials](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), or [variables](https://docs.microsoft.com/en-us/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="22a49-122">Gerenciar centralmente o nó [Configuração do LCM](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="22a49-122">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="22a49-123">Atribuir centralmente configurações a nós do cliente</span><span class="sxs-lookup"><span data-stu-id="22a49-123">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="22a49-124">Alterações na configuração de versão de "grupos canário" para teste antes de chegar à produção</span><span class="sxs-lookup"><span data-stu-id="22a49-124">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="22a49-125">Relatório gráfico</span><span class="sxs-lookup"><span data-stu-id="22a49-125">Graphical reporting</span></span>
  - <span data-ttu-id="22a49-126">Detalhes de status no nível de granularidade de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="22a49-126">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="22a49-127">Mensagens de erro detalhadas de computadores cliente para solução de problemas</span><span class="sxs-lookup"><span data-stu-id="22a49-127">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="22a49-128">[Integração com o Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) para alertas, tarefas automatizadas, aplicativo para Android/iOS para relatórios e alertas</span><span class="sxs-lookup"><span data-stu-id="22a49-128">[Integration with Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="22a49-129">Serviço de pull de DSC no Windows Server</span><span class="sxs-lookup"><span data-stu-id="22a49-129">DSC pull service in Windows Server</span></span>

<span data-ttu-id="22a49-130">É possível configurar um serviço de pull para ser executado no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="22a49-130">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="22a49-131">Lembre-se de que a solução de serviço de pull incluída no Windows Server inclui apenas funcionalidades de armazenamento de configurações/módulos para download e de captura de dados de relatório no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="22a49-131">Please be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="22a49-132">Ela não inclui muitas das funcionalidades oferecidas pelo serviço no Azure e, portanto, não é uma boa ferramenta para avaliar o modo como o serviço seria usado.</span><span class="sxs-lookup"><span data-stu-id="22a49-132">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="22a49-133">O serviço de pull oferecido no Windows Server é um serviço Web no IIS que utiliza uma interface OData para disponibilizar arquivos de configuração DSC para nós de destino quando são pedidos por tais nós.</span><span class="sxs-lookup"><span data-stu-id="22a49-133">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="22a49-134">Requisitos para usar um servidor de pull:</span><span class="sxs-lookup"><span data-stu-id="22a49-134">Requirements for using a pull server:</span></span>

- <span data-ttu-id="22a49-135">Um servidor que execute:</span><span class="sxs-lookup"><span data-stu-id="22a49-135">A server running:</span></span>
  - <span data-ttu-id="22a49-136">WMF/PowerShell 5.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="22a49-136">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="22a49-137">Função de servidor do IIS</span><span class="sxs-lookup"><span data-stu-id="22a49-137">IIS server role</span></span>
  - <span data-ttu-id="22a49-138">Serviço de DSC</span><span class="sxs-lookup"><span data-stu-id="22a49-138">DSC Service</span></span>
- <span data-ttu-id="22a49-139">Idealmente, alguns meios de gerar um certificado para proteger as credenciais passadas para o Gerenciador de Configurações Local (LCM) em nós de destino</span><span class="sxs-lookup"><span data-stu-id="22a49-139">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="22a49-140">A melhor maneira de configurar o Windows Server para hospedar o serviço de pull é usar uma configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="22a49-140">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="22a49-141">Um script de exemplo é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="22a49-141">An example script is provided below.</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="22a49-142">Usando o recurso xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="22a49-142">Using the xDSCWebService resource</span></span>

<span data-ttu-id="22a49-143">A maneira mais fácil de configurar um servidor de pull da Web é usar o recurso xWebService, incluído no módulo xPSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="22a49-143">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="22a49-144">As etapas a seguir explicam como usar o recurso em uma configuração que configure o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="22a49-144">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="22a49-145">Chame o cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) para instalar o módulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="22a49-145">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="22a49-146">**Observação**: **Install-Module** está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="22a49-146">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="22a49-147">É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="22a49-147">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
1. <span data-ttu-id="22a49-148">Obtenha um certificado SSL para o servidor de Pull de DSC de uma Autoridade de Certificação confiável, seja de dentro de sua organização ou de uma autoridade pública.</span><span class="sxs-lookup"><span data-stu-id="22a49-148">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="22a49-149">O certificado recebido da autoridade geralmente está no formato PFX.</span><span class="sxs-lookup"><span data-stu-id="22a49-149">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="22a49-150">Instale o certificado no nó que se tornará o servidor de Pull de DSC no local padrão, que deve ser CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="22a49-150">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="22a49-151">Anote a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="22a49-151">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="22a49-152">Selecione um GUID a ser usado como a Chave de Registro.</span><span class="sxs-lookup"><span data-stu-id="22a49-152">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="22a49-153">Para gerar um, usando o PowerShell, insira o seguinte no prompt do PS e pressione enter: '``` [guid]::newGuid()```' ou '```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="22a49-153">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="22a49-154">Essa chave será usada por nós de cliente como uma chave compartilhada para autenticação durante o registro.</span><span class="sxs-lookup"><span data-stu-id="22a49-154">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="22a49-155">Para saber mais, veja a seção Chave de Registro abaixo.</span><span class="sxs-lookup"><span data-stu-id="22a49-155">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="22a49-156">No ISE do PowerShell, inicie (F5) o script de configuração a seguir (incluído na pasta Example do módulo **xPSDesiredStateConfiguration** como Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="22a49-156">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="22a49-157">Esse script configura o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-157">This script sets up the pull server.</span></span>

```powershell
    configuration Sample_xDscPullServer
    {
        param
        (
                [string[]]$NodeName = 'localhost',

                [ValidateNotNullOrEmpty()]
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey
         )

         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName
         {
             WindowsFeature DSCServiceFeature
             {
                 Ensure = 'Present'
                 Name   = 'DSC-Service'
             }

             xDscWebService PSDSCPullServer
             {
                 Ensure                   = 'Present'
                 EndpointName             = 'PSDSCPullServer'
                 Port                     = 8080
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer"
                 CertificateThumbPrint    = $certificateThumbPrint
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'
                 UseSecurityBestPractices = $false
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

1. <span data-ttu-id="22a49-158">Execute a configuração, passando a impressão digital do certificado SSL como o parâmetro **certificateThumbPrint** e uma chave de Registro GUID como o parâmetro **RegistrationKey**:</span><span class="sxs-lookup"><span data-stu-id="22a49-158">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose

```

#### <a name="registration-key"></a><span data-ttu-id="22a49-159">Chave de Registro</span><span class="sxs-lookup"><span data-stu-id="22a49-159">Registration Key</span></span>

<span data-ttu-id="22a49-160">Para permitir que nós clientes sejam registrados com o servidor para poderem utilizar nomes de configuração em vez de uma ID de configuração, uma chave de registro que foi criada pela configuração acima é salva em um arquivo chamado `RegistrationKeys.txt` em `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="22a49-160">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="22a49-161">A chave de registro funciona como um segredo compartilhado usado durante o registro inicial pelo cliente com o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-161">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="22a49-162">O cliente gerará um certificado autoassinado, que será usado para autenticar de modo exclusivo com o servidor de pull depois que o registro for concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="22a49-162">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="22a49-163">A impressão digital do certificado é armazenada localmente e associada à URL do servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-163">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="22a49-164">**Observação**: não há suporte para chaves do registro no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="22a49-164">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="22a49-165">Para configurar um nó para ser autenticado no servidor de pull, a chave de registro deverá estar na metaconfiguração do nó de destino que será registrado nesse servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-165">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="22a49-166">Observe que a **RegistrationKey** na metaconfiguração abaixo é removida depois de o computador de destino ser registrado com sucesso, e o valor “140a952b-b9d6-406b-b416-e0f759c9c0e4” deve corresponder ao valor armazenado no arquivo RegistrationKeys.txt no servidor pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-166">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="22a49-167">Sempre trate o valor da chave do registro com segurança, porque o conhecimento permite que qualquer computador de destino seja registrado com o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-167">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes


```

> <span data-ttu-id="22a49-168">**Observação**: a seção **ReportServerWeb** permite que dados de relatório sejam enviados ao servidor pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-168">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="22a49-169">A falta da propriedade **ConfigurationID** no arquivo de metaconfiguração significa implicitamente que esse servidor pull dá suporte à versão V2 do protocolo de servidor pull, de modo que um registro inicial é necessário.</span><span class="sxs-lookup"><span data-stu-id="22a49-169">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="22a49-170">Por outro lado, a presença de uma **ConfigurationID** significa que a versão V1 do protocolo do servidor de pull é usada e não há nenhum processamento de registro.</span><span class="sxs-lookup"><span data-stu-id="22a49-170">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="22a49-171">**Observação**: em um cenário PUSH, existe um bug na versão atual que torna necessário definir uma propriedade ConfigurationID no arquivo de metaconfiguração para nós que nunca foram registrados com um servidor pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-171">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="22a49-172">Isso forçará o uso do protocolo de Servidor de Pull V1 e evitará mensagens de falha de registro.</span><span class="sxs-lookup"><span data-stu-id="22a49-172">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="22a49-173">Colocando configurações e recursos</span><span class="sxs-lookup"><span data-stu-id="22a49-173">Placing configurations and resources</span></span>

<span data-ttu-id="22a49-174">Após a instalação do servidor pull ser concluída, as pastas definidas pelas propriedades **ConfigurationPath** e **ModulePath** na configuração do servidor pull são onde você colocará módulos e configurações que estarão disponíveis para pull pelos nós de destino.</span><span class="sxs-lookup"><span data-stu-id="22a49-174">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="22a49-175">Esses arquivos precisam estar em um formato específico para que o servidor de recepção processe-os corretamente.</span><span class="sxs-lookup"><span data-stu-id="22a49-175">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="22a49-176">Formato de pacote do módulo de recursos DSC</span><span class="sxs-lookup"><span data-stu-id="22a49-176">DSC resource module package format</span></span>

<span data-ttu-id="22a49-177">Cada módulo de recurso precisa ser compactado e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="22a49-177">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="22a49-178">Por exemplo, um módulo chamado xWebAdminstration com uma versão do módulo correspondente a 3.1.2.0 seria nomeado 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="22a49-178">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="22a49-179">Cada versão de um módulo deve estar contido em um único arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="22a49-179">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="22a49-180">Como há apenas uma única versão de um recurso em cada arquivo zip, não há suporte para o formato do módulo adicionado ao WMF 5.0 com suporte para várias versões de módulo em um único diretório.</span><span class="sxs-lookup"><span data-stu-id="22a49-180">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="22a49-181">Isso significa que antes de empacotar módulos de recursos DSC para uso com o servidor de pull, você precisará fazer uma pequena alteração na estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="22a49-181">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="22a49-182">O formato padrão dos módulos contendo o recurso DSC no WMF 5.0 é '{Pasta do Módulo}\{{Versão do Módulo}\DscResources\{{Pasta do Recurso DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="22a49-182">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="22a49-183">Antes do empacotamento para o servidor de pull, simplesmente remova a pasta **{Versão do módulo}** de modo que o caminho se torne '{Pasta do Módulo}\DscResources\{{Pasta do Recurso DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="22a49-183">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="22a49-184">Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="22a49-184">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="22a49-185">Use `new-dscchecksum {module zip file}` para criar um arquivo de soma de verificação para o módulo adicionado recentemente.</span><span class="sxs-lookup"><span data-stu-id="22a49-185">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="22a49-186">Formato MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="22a49-186">Configuration MOF format</span></span>

<span data-ttu-id="22a49-187">Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="22a49-187">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="22a49-188">Para criar uma soma de verificação, chame o cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx).</span><span class="sxs-lookup"><span data-stu-id="22a49-188">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span>
<span data-ttu-id="22a49-189">O cmdlet usa um parâmetro **Path** que especifica a pasta na qual se encontra o MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="22a49-189">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="22a49-190">O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="22a49-190">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="22a49-191">Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="22a49-191">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="22a49-192">Coloque os arquivos MOF e os arquivos de soma de verificação associados na pasta **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="22a49-192">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="22a49-193">**Observação**: se alterar o arquivo MOF de configuração de qualquer forma, você também deverá recriar o arquivo de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="22a49-193">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="22a49-194">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="22a49-194">Tooling</span></span>

<span data-ttu-id="22a49-195">Para facilitar a configuração, validação e gerenciamento do servidor de pull, as ferramentas a seguir são incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="22a49-195">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="22a49-196">Um módulo que ajudará com empacotamento de módulos de recursos DSC e arquivos de configuração para uso no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-196">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="22a49-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="22a49-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="22a49-198">Exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="22a49-198">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp")
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="22a49-199">Um script que valida o Servidor de Pull está configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="22a49-199">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="22a49-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="22a49-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="22a49-201">Soluções da comunidade para o Serviço de Pull</span><span class="sxs-lookup"><span data-stu-id="22a49-201">Community Solutions for Pull Service</span></span>

<span data-ttu-id="22a49-202">A comunidade de DSC criou várias soluções para implementar o protocolo de serviço de pull.</span><span class="sxs-lookup"><span data-stu-id="22a49-202">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="22a49-203">Para ambientes locais, elas oferecem funcionalidades de serviço de pull e uma oportunidade de retribuir à comunidade, contribuindo com melhorias incrementais.</span><span class="sxs-lookup"><span data-stu-id="22a49-203">For on-premises environments these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="22a49-204">Tug</span><span class="sxs-lookup"><span data-stu-id="22a49-204">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="22a49-205">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="22a49-205">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="22a49-206">Configuração do cliente de pull</span><span class="sxs-lookup"><span data-stu-id="22a49-206">Pull client configuration</span></span>

<span data-ttu-id="22a49-207">Os tópicos a seguir descrevem em detalhes a configuração de clientes de pull:</span><span class="sxs-lookup"><span data-stu-id="22a49-207">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="22a49-208">Configurando um cliente de pull de DSC usando uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="22a49-208">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="22a49-209">Configurando um cliente de pull de DSC usando nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="22a49-209">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="22a49-210">Configurações parciais</span><span class="sxs-lookup"><span data-stu-id="22a49-210">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="22a49-211">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22a49-211">See also</span></span>

- [<span data-ttu-id="22a49-212">Visão Geral da Configuração de Estado Desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="22a49-212">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="22a49-213">Aplicando configurações</span><span class="sxs-lookup"><span data-stu-id="22a49-213">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="22a49-214">Usando um servidor de relatório de DSC</span><span class="sxs-lookup"><span data-stu-id="22a49-214">Using a DSC report server</span></span>](reportServer.md)