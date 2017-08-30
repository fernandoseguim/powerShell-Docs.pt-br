---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Configurando um servidor de pull da Web de DSC
ms.openlocfilehash: 865b4a871a75dab18071904983f6b14a10ff7e96
ms.sourcegitcommit: 4ccf1a64e7a8335797daef6152244a9d4b9a89b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2017
---
# <a name="setting-up-a-dsc-web-pull-server"></a><span data-ttu-id="77c64-103">Configurando um servidor de pull da Web de DSC</span><span class="sxs-lookup"><span data-stu-id="77c64-103">Setting up a DSC web pull server</span></span>

> <span data-ttu-id="77c64-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="77c64-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="77c64-105">Um servidor de pull da Web de DSC é um serviço Web no IIS que utiliza uma interface OData para disponibilizar arquivos de configuração DSC para nós de destino quando são pedidos por tais nós.</span><span class="sxs-lookup"><span data-stu-id="77c64-105">A DSC web pull server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="77c64-106">Requisitos para usar um servidor de pull:</span><span class="sxs-lookup"><span data-stu-id="77c64-106">Requirements for using a pull server:</span></span>

* <span data-ttu-id="77c64-107">Um servidor que execute:</span><span class="sxs-lookup"><span data-stu-id="77c64-107">A server running:</span></span>
  - <span data-ttu-id="77c64-108">WMF/PowerShell 5.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="77c64-108">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="77c64-109">Função de servidor do IIS</span><span class="sxs-lookup"><span data-stu-id="77c64-109">IIS server role</span></span>
  - <span data-ttu-id="77c64-110">Serviço de DSC</span><span class="sxs-lookup"><span data-stu-id="77c64-110">DSC Service</span></span>
* <span data-ttu-id="77c64-111">Idealmente, alguns meios de gerar um certificado para proteger as credenciais passadas para o Gerenciador de Configurações Local (LCM) em nós de destino</span><span class="sxs-lookup"><span data-stu-id="77c64-111">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="77c64-112">É possível adicionar a função de servidor do IIS e o Serviço de DSC com o assistente Adicionar funções e recursos no Gerenciador do Servidor ou usando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77c64-112">You can add the IIS server role and DSC Service with the Add Roles and Features wizard in Server Manager, or by using PowerShell.</span></span> <span data-ttu-id="77c64-113">Os scripts de exemplo incluídos neste tópico também cuidarão dessas duas etapas.</span><span class="sxs-lookup"><span data-stu-id="77c64-113">The sample scripts included in this topic will handle both of these steps for you as well.</span></span>

## <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="77c64-114">Usando o recurso xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="77c64-114">Using the xDSCWebService resource</span></span>
<span data-ttu-id="77c64-115">A maneira mais fácil de configurar um servidor de pull da Web é usar o recurso xWebService, incluído no módulo xPSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="77c64-115">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span> <span data-ttu-id="77c64-116">As etapas a seguir explicam como usar o recurso em uma configuração que configure o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="77c64-116">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="77c64-117">Chame o cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) para instalar o módulo **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="77c64-117">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="77c64-118">**Observação**: **Install-Module** está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="77c64-118">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="77c64-119">É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="77c64-119">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="77c64-120">Obtenha um certificado SSL para o servidor de Pull de DSC de uma Autoridade de Certificação confiável, seja de dentro de sua organização ou de uma autoridade pública.</span><span class="sxs-lookup"><span data-stu-id="77c64-120">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="77c64-121">O certificado recebido da autoridade geralmente está no formato PFX.</span><span class="sxs-lookup"><span data-stu-id="77c64-121">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="77c64-122">Instale o certificado no nó que se tornará o servidor de Pull de DSC no local padrão, que deve ser CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="77c64-122">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="77c64-123">Anote a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="77c64-123">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="77c64-124">Selecione um GUID a ser usado como a Chave de Registro.</span><span class="sxs-lookup"><span data-stu-id="77c64-124">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="77c64-125">Para gerar um, usando o PowerShell, insira o seguinte no prompt do PS e pressione enter: '``` [guid]::newGuid()```' ou '```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="77c64-125">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="77c64-126">Essa chave será usada por nós de cliente como uma chave compartilhada para autenticação durante o registro.</span><span class="sxs-lookup"><span data-stu-id="77c64-126">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="77c64-127">Para saber mais, veja a seção Chave de Registro abaixo.</span><span class="sxs-lookup"><span data-stu-id="77c64-127">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="77c64-128">No ISE do PowerShell, inicie (F5) o script de configuração a seguir (incluído na pasta Example do módulo **xPSDesiredStateConfiguration** como Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="77c64-128">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="77c64-129">Esse script configura o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="77c64-129">This script sets up the pull server.</span></span>
  
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

1. <span data-ttu-id="77c64-130">Execute a configuração, passando a impressão digital do certificado SSL como o parâmetro **certificateThumbPrint** e uma chave de Registro GUID como o parâmetro **RegistrationKey**:</span><span class="sxs-lookup"><span data-stu-id="77c64-130">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

## <a name="registration-key"></a><span data-ttu-id="77c64-131">Chave de Registro</span><span class="sxs-lookup"><span data-stu-id="77c64-131">Registration Key</span></span>
<span data-ttu-id="77c64-132">Para permitir que nós clientes sejam registrados com o servidor para poderem utilizar nomes de configuração em vez de uma ID de configuração, uma chave de registro que foi criada pela configuração acima é salva em um arquivo chamado `RegistrationKeys.txt` em `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="77c64-132">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="77c64-133">A chave de registro funciona como um segredo compartilhado usado durante o registro inicial pelo cliente com o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="77c64-133">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="77c64-134">O cliente gerará um certificado autoassinado, que será usado para autenticar de modo exclusivo com o servidor de pull depois que o registro for concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="77c64-134">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="77c64-135">A impressão digital do certificado é armazenada localmente e associada à URL do servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="77c64-135">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="77c64-136">**Observação**: não há suporte para chaves do registro no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="77c64-136">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="77c64-137">Para configurar um nó para ser autenticado no servidor de pull, a chave de registro deverá estar na metaconfiguração do nó de destino que será registrado nesse servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="77c64-137">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="77c64-138">Observe que a **RegistrationKey** na metaconfiguração abaixo é removida depois de o computador de destino ser registrado com sucesso, e o valor “140a952b-b9d6-406b-b416-e0f759c9c0e4” deve corresponder ao valor armazenado no arquivo RegistrationKeys.txt no servidor pull.</span><span class="sxs-lookup"><span data-stu-id="77c64-138">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="77c64-139">Sempre trate o valor da chave do registro com segurança, porque o conhecimento permite que qualquer computador de destino seja registrado com o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="77c64-139">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="77c64-140">**Observação**: a seção **ReportServerWeb** permite que dados de relatório sejam enviados ao servidor pull.</span><span class="sxs-lookup"><span data-stu-id="77c64-140">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span> 

<span data-ttu-id="77c64-141">A falta da propriedade **ConfigurationID** no arquivo de metaconfiguração significa implicitamente que esse servidor pull dá suporte à versão V2 do protocolo de servidor pull, de modo que um registro inicial é necessário.</span><span class="sxs-lookup"><span data-stu-id="77c64-141">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="77c64-142">Por outro lado, a presença de uma **ConfigurationID** significa que a versão V1 do protocolo do servidor de pull é usada e não há nenhum processamento de registro.</span><span class="sxs-lookup"><span data-stu-id="77c64-142">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="77c64-143">**Observação**: em um cenário PUSH, existe um bug na versão atual que torna necessário definir uma propriedade ConfigurationID no arquivo de metaconfiguração para nós que nunca foram registrados com um servidor pull.</span><span class="sxs-lookup"><span data-stu-id="77c64-143">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="77c64-144">Isso forçará o uso do protocolo de Servidor de Pull V1 e evitará mensagens de falha de registro.</span><span class="sxs-lookup"><span data-stu-id="77c64-144">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="77c64-145">Colocando configurações e recursos</span><span class="sxs-lookup"><span data-stu-id="77c64-145">Placing configurations and resources</span></span>

<span data-ttu-id="77c64-146">Após a instalação do servidor pull ser concluída, as pastas definidas pelas propriedades **ConfigurationPath** e **ModulePath** na configuração do servidor pull são onde você colocará módulos e configurações que estarão disponíveis para pull pelos nós de destino.</span><span class="sxs-lookup"><span data-stu-id="77c64-146">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="77c64-147">Esses arquivos precisam estar em um formato específico para que o servidor de recepção processe-os corretamente.</span><span class="sxs-lookup"><span data-stu-id="77c64-147">These files need to be in a specific format in order for the pull server to correctly process them.</span></span> 

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="77c64-148">Formato de pacote do módulo de recursos DSC</span><span class="sxs-lookup"><span data-stu-id="77c64-148">DSC resource module package format</span></span>

<span data-ttu-id="77c64-149">Cada módulo de recurso precisa ser compactado e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="77c64-149">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="77c64-150">Por exemplo, um módulo chamado xWebAdminstration com uma versão do módulo correspondente a 3.1.2.0 seria nomeado 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="77c64-150">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="77c64-151">Cada versão de um módulo deve estar contido em um único arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="77c64-151">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="77c64-152">Como há apenas uma única versão de um recurso em cada arquivo zip, não há suporte para o formato do módulo adicionado ao WMF 5.0 com suporte para várias versões de módulo em um único diretório.</span><span class="sxs-lookup"><span data-stu-id="77c64-152">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="77c64-153">Isso significa que antes de empacotar módulos de recursos DSC para uso com o servidor de pull, você precisará fazer uma pequena alteração na estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="77c64-153">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="77c64-154">O formato padrão dos módulos contendo o recurso DSC no WMF 5.0 é '{Pasta do Módulo}\{{Versão do Módulo}\DscResources\{{Pasta do Recurso DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="77c64-154">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="77c64-155">Antes do empacotamento para o servidor de pull, simplesmente remova a pasta **{Versão do módulo}** de modo que o caminho se torne '{Pasta do Módulo}\DscResources\{{Pasta do Recurso DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="77c64-155">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="77c64-156">Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="77c64-156">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="77c64-157">Use `new-dscchecksum {module zip file}` para criar um arquivo de soma de verificação para o módulo adicionado recentemente.</span><span class="sxs-lookup"><span data-stu-id="77c64-157">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="77c64-158">Formato MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="77c64-158">Configuration MOF format</span></span> 
<span data-ttu-id="77c64-159">Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="77c64-159">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="77c64-160">Para criar uma soma de verificação, chame o cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx).</span><span class="sxs-lookup"><span data-stu-id="77c64-160">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="77c64-161">O cmdlet usa um parâmetro **Path** que especifica a pasta na qual se encontra o MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="77c64-161">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="77c64-162">O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="77c64-162">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="77c64-163">Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="77c64-163">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="77c64-164">Coloque os arquivos MOF e seus arquivos de soma de verificação associados na pasta **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="77c64-164">Place the MOF files and their associated checksum files in the the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="77c64-165">**Observação**: se alterar o arquivo MOF de configuração de qualquer forma, você também deverá recriar o arquivo de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="77c64-165">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="tooling"></a><span data-ttu-id="77c64-166">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="77c64-166">Tooling</span></span>
<span data-ttu-id="77c64-167">Para facilitar a configuração, validação e gerenciamento do servidor de pull, as ferramentas a seguir são incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="77c64-167">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>
1. <span data-ttu-id="77c64-168">Um módulo que ajudará com empacotamento de módulos de recursos DSC e arquivos de configuração para uso no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="77c64-168">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="77c64-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="77c64-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="77c64-170">Exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="77c64-170">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="77c64-171">Um script que valida o Servidor de Pull está configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="77c64-171">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="77c64-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="77c64-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>


## <a name="pull-client-configuration"></a><span data-ttu-id="77c64-173">Configuração do cliente de pull</span><span class="sxs-lookup"><span data-stu-id="77c64-173">Pull client configuration</span></span> 
<span data-ttu-id="77c64-174">Os tópicos a seguir descrevem em detalhes a configuração de clientes de pull:</span><span class="sxs-lookup"><span data-stu-id="77c64-174">The following topics describe setting up pull clients in detail:</span></span>

* [<span data-ttu-id="77c64-175">Configurando um cliente de pull de DSC usando uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="77c64-175">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
* [<span data-ttu-id="77c64-176">Configurando um cliente de pull de DSC usando nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="77c64-176">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="77c64-177">Configurações parciais</span><span class="sxs-lookup"><span data-stu-id="77c64-177">Partial configurations</span></span>](partialConfigs.md)


## <a name="see-also"></a><span data-ttu-id="77c64-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77c64-178">See also</span></span>
* [<span data-ttu-id="77c64-179">Visão Geral da Configuração de Estado Desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="77c64-179">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="77c64-180">Aplicando configurações</span><span class="sxs-lookup"><span data-stu-id="77c64-180">Enacting configurations</span></span>](enactingConfigurations.md)
* [<span data-ttu-id="77c64-181">Usando um servidor de relatório de DSC</span><span class="sxs-lookup"><span data-stu-id="77c64-181">Using a DSC report server</span></span>](reportServer.md)

