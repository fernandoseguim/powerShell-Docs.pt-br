---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,instalação
title: Melhorias da DSC no WMF 5.1
ms.openlocfilehash: 32bdde6d43d17cc76c454fe10b00097753a9eebe
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34309535"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="b1781-103">Melhorias na DSC (Configuração de Estado Desejado) no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b1781-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="b1781-104">Melhorias de recursos de classe da DSC</span><span class="sxs-lookup"><span data-stu-id="b1781-104">DSC class resource improvements</span></span>

<span data-ttu-id="b1781-105">No 5.1 WMF, corrigimos os seguintes problemas conhecidos:</span><span class="sxs-lookup"><span data-stu-id="b1781-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="b1781-106">O Get-DscConfiguration poderá retornar valores vazios (nulos) ou erros se um tipo complexo/de tabela de hash for retornado pela função Get() de um recurso DSC baseado em classe.</span><span class="sxs-lookup"><span data-stu-id="b1781-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="b1781-107">O Get-DscConfiguration retornará um erro se a credencial RunAs for usada na configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="b1781-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="b1781-108">Os recursos baseados em classe não podem ser usados em uma configuração de composição.</span><span class="sxs-lookup"><span data-stu-id="b1781-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="b1781-109">O Start-DscConfiguration será suspenso se o recurso baseado em classe tiver uma propriedade de seu próprio tipo.</span><span class="sxs-lookup"><span data-stu-id="b1781-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="b1781-110">O recurso baseado em classe não pode ser usado como um recurso exclusivo.</span><span class="sxs-lookup"><span data-stu-id="b1781-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="b1781-111">Melhorias de depuração de recursos da DSC</span><span class="sxs-lookup"><span data-stu-id="b1781-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="b1781-112">No WMF 5.0, o depurador do PowerShell não interrompeu o método de recurso baseado em classe (Get/Set/Test) diretamente.</span><span class="sxs-lookup"><span data-stu-id="b1781-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="b1781-113">No WMF 5.1, o depurador interrompe o método de recurso baseado em classe da mesma forma que faz com os métodos de recursos baseados em MOF.</span><span class="sxs-lookup"><span data-stu-id="b1781-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="b1781-114">O cliente pull da DSC dá suporte para TLS 1.1 e para TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="b1781-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="b1781-115">Anteriormente, o cliente pull da DSC dava suporte apenas para SSL3.0 e TLS1.0 por meio de conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b1781-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="b1781-116">Se fosse forçado a usar protocolos mais seguros, o cliente pull pararia de funcionar.</span><span class="sxs-lookup"><span data-stu-id="b1781-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="b1781-117">No WMF 5.1, o cliente pull da DSC não dá mais suporte a SSL 3.0 e adiciona suporte a protocolos mais seguros TLS 1.1 e TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="b1781-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="b1781-118">Registro do servidor de pull aprimorado</span><span class="sxs-lookup"><span data-stu-id="b1781-118">Improved pull server registration</span></span>

<span data-ttu-id="b1781-119">Nas versões anteriores do WMF, as solicitações simultâneas de registros/relatórios em um servidor de pull da DSC durante o uso do banco de dados ESENT provocavam uma falha de registro e/ou relatório do LCM.</span><span class="sxs-lookup"><span data-stu-id="b1781-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="b1781-120">Nesses casos, os logs de eventos no servidor de pull têm o erro "O nome da instância já está em uso."</span><span class="sxs-lookup"><span data-stu-id="b1781-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="b1781-121">Isso ocorria porque um padrão incorreto era usado para acessar o banco de dados ESENT em um cenário Multi-Threaded.</span><span class="sxs-lookup"><span data-stu-id="b1781-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="b1781-122">No WMF 5.1, esse problema foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="b1781-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="b1781-123">Os registros ou relatórios simultâneos (que envolvem o banco de dados ESENT) funcionam bem no WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="b1781-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="b1781-124">Esse problema é aplicável somente ao banco de dados ESENT e não se aplica ao banco de dados OLEDB.</span><span class="sxs-lookup"><span data-stu-id="b1781-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="b1781-125">Habilitar o log Circular na instância do banco de dados ESENT</span><span class="sxs-lookup"><span data-stu-id="b1781-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="b1781-126">Na versão anterior da DSC-PullServer, os arquivos de log do banco de dados ESENT preenchiam o espaço em disco do pullserver porque a instância do banco de dados estava sendo criada sem log circular.</span><span class="sxs-lookup"><span data-stu-id="b1781-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="b1781-127">Nesta versão, você tem a opção de controlar o comportamento de log circular da instância usando o web.config do pullserver.</span><span class="sxs-lookup"><span data-stu-id="b1781-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="b1781-128">Por padrão, o CircularLogging está definido como VERDADEIRO.</span><span class="sxs-lookup"><span data-stu-id="b1781-128">By default CircularLogging is set to TRUE.</span></span>

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="b1781-129">Convenção de nomenclatura de configuração parcial de pull</span><span class="sxs-lookup"><span data-stu-id="b1781-129">Pull partial configuration naming convention</span></span>

<span data-ttu-id="b1781-130">Na versão anterior, a convenção de nomenclatura para uma configuração parcial era que o nome do arquivo MOF no servidor de pull/serviço deveria ser compatível com o nome de configuração parcial especificado nas configurações do gerenciador de configuração local que, por sua vez, deve ser compatível com o nome de configuração inserido no arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="b1781-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="b1781-131">Confira os instantâneos abaixo:</span><span class="sxs-lookup"><span data-stu-id="b1781-131">See the snapshots below:</span></span>

- <span data-ttu-id="b1781-132">Definições da configuração local, que determina uma configuração parcial que um nó está autorizado a receber.</span><span class="sxs-lookup"><span data-stu-id="b1781-132">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Metaconfiguração de exemplo](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="b1781-134">Definição da configuração parcial de exemplo</span><span class="sxs-lookup"><span data-stu-id="b1781-134">Sample partial configuration definition</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

- <span data-ttu-id="b1781-135">"ConfigurationName" inserido no arquivo MOF gerado.</span><span class="sxs-lookup"><span data-stu-id="b1781-135">'ConfigurationName' embedded in the generated MOF file.</span></span>

![Arquivo mof de exemplo gerado](../images/PartialGeneratedMof.png)

- <span data-ttu-id="b1781-137">FileName no repositório de configuração de pull</span><span class="sxs-lookup"><span data-stu-id="b1781-137">FileName in the pull configuration repository</span></span>

![FileName no Repositório de Configuração](../images/PartialInConfigRepository.png)

<span data-ttu-id="b1781-139">O nome do serviço da Automação do Azure gerou arquivos MOF como `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="b1781-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="b1781-140">Portanto, a configuração abaixo é compilada para PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="b1781-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="b1781-141">Ela tornou impossível a extração de uma de suas configurações parciais do serviço da Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="b1781-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="b1781-142">No WMF 5.1, uma configuração parcial no servidor de pull/serviço pode ser nomeada `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="b1781-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="b1781-143">Além disso, se um computador estiver extraindo uma única configuração de um servidor de pull/serviço, então, o arquivo de configuração no repositório de configuração do servidor de pull poderá ter qualquer nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="b1781-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="b1781-144">Esta flexibilidade de nomenclatura permite que você gerencie seus nós parcialmente pelo serviço da Automação do Azure, no qual algumas configurações do nó chegarão da DSC de Automação do Azure e uma configuração parcial gerenciada localmente.</span><span class="sxs-lookup"><span data-stu-id="b1781-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="b1781-145">A metaconfiguração abaixo configura um nó para ser gerenciado tanto localmente quanto pelo serviço da Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="b1781-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration RegistrationMetaConfig
{
    Settings
    {
        RefreshFrequencyMins = 30
        RefreshMode = "PULL"
    }

    ConfigurationRepositoryWeb web
    {
        ServerURL =  $endPoint
        RegistrationKey = $registrationKey
        ConfigurationNames = $configurationName
    }

    # Partial configuration managed by Azure Automation service.
    PartialConfiguration PartialConfigurationManagedByAzureAutomation
    {
        ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
    }

    # This partial configuration is managed locally.
    PartialConfiguration OnPremisesConfig
    {
        RefreshMode = "PUSH"
        ExclusiveResources = @("Script")
    }

}

RegistrationMetaConfig
Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="b1781-146">Usando a PsDscRunAsCredential com os recursos de composição da DSC</span><span class="sxs-lookup"><span data-stu-id="b1781-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="b1781-147">Adicionamos um suporte para usar a [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) com os recursos de [Composição](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) da DSC.</span><span class="sxs-lookup"><span data-stu-id="b1781-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="b1781-148">Agora, você pode especificar o valor para a PsDscRunAsCredential ao usar recursos de composição nas configurações.</span><span class="sxs-lookup"><span data-stu-id="b1781-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="b1781-149">Quando especificado, todos os recursos serão executados em um recurso de composição como um usuário RunAs.</span><span class="sxs-lookup"><span data-stu-id="b1781-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="b1781-150">Se o recurso de composição chamar outro recurso de composição, todos os seus recursos também serão executados como usuário RunAs.</span><span class="sxs-lookup"><span data-stu-id="b1781-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="b1781-151">As credenciais RunAs são propagadas para qualquer nível da hierarquia do recurso de composição.</span><span class="sxs-lookup"><span data-stu-id="b1781-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="b1781-152">Se qualquer recurso dentro de um recurso de composição especificar seu próprio valor para a PsDscRunAsCredential, ocorrerá um erro de mesclagem durante a compilação da configuração.</span><span class="sxs-lookup"><span data-stu-id="b1781-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="b1781-153">Este exemplo mostra o uso com o recurso de composição [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) incluído no módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="b1781-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="b1781-154">Validações do módulo de DSC e da assinatura de configuração</span><span class="sxs-lookup"><span data-stu-id="b1781-154">DSC module and configuration signing validations</span></span>

<span data-ttu-id="b1781-155">Na DSC, as configurações e os módulos são distribuídos para computadores gerenciados do servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="b1781-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="b1781-156">Se o servidor de pull estiver comprometido, um invasor possivelmente poderá modificar as configurações e os módulos no servidor de pull e distribuí-los para todos os nós gerenciados, comprometendo todos eles.</span><span class="sxs-lookup"><span data-stu-id="b1781-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

<span data-ttu-id="b1781-157">No WMF 5.1, a DSC dá suporte para a validação de assinaturas digitais no catálogo e nos arquivos de configuração (.MOF).</span><span class="sxs-lookup"><span data-stu-id="b1781-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="b1781-158">Este recurso evita que os nós executem as configurações ou os arquivos de módulo que não são assinados por um signatário confiável ou que foram violados depois de assinados por um signatário confiável.</span><span class="sxs-lookup"><span data-stu-id="b1781-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="b1781-159">Como assinar a configuração e o módulo</span><span class="sxs-lookup"><span data-stu-id="b1781-159">How to sign configuration and module</span></span>

***
* <span data-ttu-id="b1781-160">Arquivos de Configuração (.MOFs): o cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) existente do PowerShell é estendido para dar suporte à assinatura de arquivos MOF.</span><span class="sxs-lookup"><span data-stu-id="b1781-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="b1781-161">Módulos: a assinatura dos módulos é feita com a assinatura do catálogo do módulo correspondente por meio das seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="b1781-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="b1781-162">Crie um arquivo de catálogo: um arquivo de catálogo contém uma coleção de hashes criptográficos ou impressões digitais.</span><span class="sxs-lookup"><span data-stu-id="b1781-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="b1781-163">Cada impressão digital corresponde a um arquivo que está incluído no módulo.</span><span class="sxs-lookup"><span data-stu-id="b1781-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="b1781-164">O novo cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) foi adicionado para permitir que os usuários criem um arquivo de catálogo para seu módulo.</span><span class="sxs-lookup"><span data-stu-id="b1781-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="b1781-165">Assine o arquivo de catálogo: use a [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) para assinar o arquivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="b1781-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="b1781-166">Coloque o arquivo de catálogo dentro da pasta do módulo.</span><span class="sxs-lookup"><span data-stu-id="b1781-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="b1781-167">Por convenção, o arquivo de catálogo do módulo deve ser colocado na pasta do módulo, com o mesmo nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="b1781-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="b1781-168">Configurações de LocalConfigurationManager para habilitar as validações de assinatura</span><span class="sxs-lookup"><span data-stu-id="b1781-168">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="b1781-169">Recepção</span><span class="sxs-lookup"><span data-stu-id="b1781-169">Pull</span></span>

<span data-ttu-id="b1781-170">O LocalConfigurationManager de um nó executa a validação da assinatura dos módulos e das configurações com base em suas configurações atuais.</span><span class="sxs-lookup"><span data-stu-id="b1781-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="b1781-171">Por padrão, a validação da assinatura está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="b1781-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="b1781-172">A validação da assinatura pode ser habilitada adicionando o bloco “SignatureValidation” à definição de metaconfiguração do nó, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="b1781-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

<span data-ttu-id="b1781-173">A definição da metaconfiguração acima em um nó habilita a validação da assinatura nas configurações e nos módulos baixados.</span><span class="sxs-lookup"><span data-stu-id="b1781-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="b1781-174">O Gerenciador de Configurações Local executa as seguintes etapas para verificar as assinaturas digitais.</span><span class="sxs-lookup"><span data-stu-id="b1781-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="b1781-175">Verifique se a assinatura em um arquivo de configuração (. MOF) é válida.</span><span class="sxs-lookup"><span data-stu-id="b1781-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="b1781-176">Ela usa o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) do PowerShell, que é estendido na versão 5.1 para dar suporte à validação de assinatura do MOF.</span><span class="sxs-lookup"><span data-stu-id="b1781-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="b1781-177">Verifique se a autoridade de certificação que autorizou o signatário é confiável.</span><span class="sxs-lookup"><span data-stu-id="b1781-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="b1781-178">Baixe as dependências de módulo/recurso da configuração para uma localização temporária.</span><span class="sxs-lookup"><span data-stu-id="b1781-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="b1781-179">Verifique se a assinatura do catálogo foi incluída dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="b1781-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="b1781-180">Encontre um arquivo `<moduleName>.cat` e verifique sua assinatura usando o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="b1781-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="b1781-181">Verifique se a autoridade de certificação que autenticou o signatário é confiável.</span><span class="sxs-lookup"><span data-stu-id="b1781-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="b1781-182">Verifique se o conteúdo dos módulos não foi violado usando o novo cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="b1781-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="b1781-183">Install-Module para $env:ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="b1781-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="b1781-184">Configuração do processo</span><span class="sxs-lookup"><span data-stu-id="b1781-184">Process configuration</span></span>

> <span data-ttu-id="b1781-185">Observação: a validação da assinatura no catálogo de módulo e na configuração é realizada somente quando a configuração é aplicada ao sistema pela primeira vez ou quando o módulo é baixado e instalado.</span><span class="sxs-lookup"><span data-stu-id="b1781-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="b1781-186">As execuções de consistência não validam a assinatura de Current.mof ou de suas dependências de módulo.</span><span class="sxs-lookup"><span data-stu-id="b1781-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="b1781-187">Se a verificação tiver falhado em qualquer estágio, por exemplo, se a configuração extraída do servidor de pull não estiver assinada, o processamento da configuração será encerrado com o erro mostrado abaixo e todos os arquivos temporários serão excluídos.</span><span class="sxs-lookup"><span data-stu-id="b1781-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Configuração de Saída de Erro de Exemplo](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="b1781-189">Da mesma forma, a extração de um módulo cujo catálogo não está assinado resulta no seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="b1781-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Módulo de Saída de Erro de Exemplo](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="b1781-191">Push</span><span class="sxs-lookup"><span data-stu-id="b1781-191">Push</span></span>

<span data-ttu-id="b1781-192">Uma configuração entregue com o uso de push pode ser violada em sua origem antes de ser entregue para o nó.</span><span class="sxs-lookup"><span data-stu-id="b1781-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="b1781-193">O Gerenciador de Configurações Local executa etapas semelhantes de validação de assinatura para as configurações enviadas por push ou publicadas.</span><span class="sxs-lookup"><span data-stu-id="b1781-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="b1781-194">Veja abaixo um exemplo completo de validação de assinatura para envio por push.</span><span class="sxs-lookup"><span data-stu-id="b1781-194">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="b1781-195">Habilite a validação da assinatura no nó.</span><span class="sxs-lookup"><span data-stu-id="b1781-195">Enable signature validation on the node.</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'
    }
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType =  'Configuration','Module'
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

- <span data-ttu-id="b1781-196">Crie um arquivo de configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="b1781-196">Create a sample configuration file.</span></span>

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

- <span data-ttu-id="b1781-197">Tente enviar o arquivo de configuração não assinado por push para o nó.</span><span class="sxs-lookup"><span data-stu-id="b1781-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="b1781-199">Assine o arquivo de configuração usando um certificado de assinatura de código.</span><span class="sxs-lookup"><span data-stu-id="b1781-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="b1781-201">Tente enviar o arquivo MOF assinado por push.</span><span class="sxs-lookup"><span data-stu-id="b1781-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)
