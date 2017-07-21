---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Usando DSC no Nano Server
ms.openlocfilehash: 2233106bfd07144132f95ea7957ebfa3248ca219
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="d59d3-103">Usando DSC no Nano Server</span><span class="sxs-lookup"><span data-stu-id="d59d3-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="d59d3-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d59d3-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d59d3-105">**DSC no Nano Server** é um pacote opcional na pasta `NanoServer\Packages` de mídia do Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="d59d3-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="d59d3-106">O pacote pode ser instalado quando você cria um VHD para um Nano Server especificando **Microsoft-NanoServer-DSC-Package** como o valor do parâmetro **Packages** da função **New-NanoServerImage**.</span><span class="sxs-lookup"><span data-stu-id="d59d3-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="d59d3-107">Por exemplo, se você estivesse criando um VHD para uma máquina virtual, o comando seria semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="d59d3-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="d59d3-108">Para saber mais sobre como instalar e usar o Nano Server, bem como gerenciar o Nano Server com a comunicação remota do PowerShell, confira [Getting Started with Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx) (Introdução ao Nano Server).</span><span class="sxs-lookup"><span data-stu-id="d59d3-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="d59d3-109">Recursos de DSC disponíveis no Nano Server</span><span class="sxs-lookup"><span data-stu-id="d59d3-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="d59d3-110">Como o Nano Server dá suporte a apenas um conjunto limitado de APIs em comparação com uma versão completa do Windows Server, por enquanto, o DSC no Nano Server não tem paridade funcional completa com DSC em execução em SKUs completas.</span><span class="sxs-lookup"><span data-stu-id="d59d3-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="d59d3-111">O DSC no Nano Server está em desenvolvimento ativo e ainda não é um recurso completo.</span><span class="sxs-lookup"><span data-stu-id="d59d3-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>
 
 <span data-ttu-id="d59d3-112">Os recursos de DSC a seguir estão disponíveis atualmente no Nano Server:</span><span class="sxs-lookup"><span data-stu-id="d59d3-112">The following DSC features are currently available on Nano Server:</span></span> 


* <span data-ttu-id="d59d3-113">Nos modos push e pull</span><span class="sxs-lookup"><span data-stu-id="d59d3-113">Both push and pull modes</span></span>

* <span data-ttu-id="d59d3-114">Todos os cmdlets de DSC que existem em uma versão completa do Windows Server, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d59d3-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span> 
  * [<span data-ttu-id="d59d3-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d59d3-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [<span data-ttu-id="d59d3-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d59d3-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/en-us/library/dn521621.aspx)   
  * [<span data-ttu-id="d59d3-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="d59d3-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="d59d3-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="d59d3-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [<span data-ttu-id="d59d3-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d59d3-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="d59d3-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d59d3-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="d59d3-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d59d3-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="d59d3-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d59d3-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [<span data-ttu-id="d59d3-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="d59d3-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [<span data-ttu-id="d59d3-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d59d3-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="d59d3-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d59d3-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="d59d3-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="d59d3-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="d59d3-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d59d3-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="d59d3-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="d59d3-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="d59d3-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="d59d3-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="d59d3-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="d59d3-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="d59d3-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="d59d3-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* <span data-ttu-id="d59d3-132">Compilação de configurações (confira [Configurações DSC](configurations.md))</span><span class="sxs-lookup"><span data-stu-id="d59d3-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="d59d3-133">**Problema:** a criptografia de senha (confira [Protegendo o arquivo MOF](securemof.md)) durante a compilação da configuração não funciona.</span><span class="sxs-lookup"><span data-stu-id="d59d3-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="d59d3-134">Compilação de metaconfigurações (confira [Configurando o Gerenciador de Configurações Local](metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="d59d3-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="d59d3-135">Execução de um recurso no contexto do usuário (confira [Executar DSC com as credenciais do usuário (RunAs)](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="d59d3-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="d59d3-136">Recursos baseados em classe (confira [Escrevendo um recurso personalizado de DSC com classes do PowerShell](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="d59d3-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="d59d3-137">Depuração dos recursos de DSC (confira [Depurando os recursos de DSC](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="d59d3-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>
  
  <span data-ttu-id="d59d3-138">**Problema:** não funciona se um recurso estiver usando PsDscRunAsCredential (confira [Executar DSC com as credenciais do usuário](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="d59d3-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="d59d3-139">Especificando dependências de nó cruzado</span><span class="sxs-lookup"><span data-stu-id="d59d3-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md) 

* [<span data-ttu-id="d59d3-140">Controle de versão do recurso</span><span class="sxs-lookup"><span data-stu-id="d59d3-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="d59d3-141">Cliente de pull (configurações e recursos) (confira [Configurando um cliente de pull usando nomes de configuração](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="d59d3-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="d59d3-142">Configurações parciais (pull e push)</span><span class="sxs-lookup"><span data-stu-id="d59d3-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="d59d3-143">Relatórios para o servidor de pull</span><span class="sxs-lookup"><span data-stu-id="d59d3-143">Reporting to pull server</span></span>](reportServer.md) 

* <span data-ttu-id="d59d3-144">Criptografia do MOF</span><span class="sxs-lookup"><span data-stu-id="d59d3-144">MOF encryption</span></span>

* <span data-ttu-id="d59d3-145">Registro em log de eventos</span><span class="sxs-lookup"><span data-stu-id="d59d3-145">Event logging</span></span>

* <span data-ttu-id="d59d3-146">Relatórios de DSC de automação do Azure</span><span class="sxs-lookup"><span data-stu-id="d59d3-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="d59d3-147">Recursos que são totalmente funcionais</span><span class="sxs-lookup"><span data-stu-id="d59d3-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="d59d3-148">Archive</span><span class="sxs-lookup"><span data-stu-id="d59d3-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="d59d3-149">Environment</span><span class="sxs-lookup"><span data-stu-id="d59d3-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="d59d3-150">File</span><span class="sxs-lookup"><span data-stu-id="d59d3-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="d59d3-151">Log</span><span class="sxs-lookup"><span data-stu-id="d59d3-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="d59d3-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="d59d3-152">ProcessSet</span></span>
  * [<span data-ttu-id="d59d3-153">Registry</span><span class="sxs-lookup"><span data-stu-id="d59d3-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="d59d3-154">Script</span><span class="sxs-lookup"><span data-stu-id="d59d3-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="d59d3-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="d59d3-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="d59d3-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="d59d3-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="d59d3-157">WaitForAll (confira [Especificação de dependências de nó cruzado](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="d59d3-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="d59d3-158">WaitForAny (confira [Especificação de dependências de nó cruzado](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="d59d3-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="d59d3-159">WaitForSome (confira [Especificação de dependências de nó cruzado](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="d59d3-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="d59d3-160">Recursos que são parcialmente funcionais</span><span class="sxs-lookup"><span data-stu-id="d59d3-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="d59d3-161">Grupo</span><span class="sxs-lookup"><span data-stu-id="d59d3-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="d59d3-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="d59d3-162">GroupSet</span></span>
  
  <span data-ttu-id="d59d3-163">**Problema:** os recursos acima falharão se a instância for chamada duas vezes (executando a mesma configuração duas vezes)</span><span class="sxs-lookup"><span data-stu-id="d59d3-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>
  
  * [<span data-ttu-id="d59d3-164">Service</span><span class="sxs-lookup"><span data-stu-id="d59d3-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="d59d3-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="d59d3-165">ServiceSet</span></span>
  
  <span data-ttu-id="d59d3-166">**Problema:** só funciona para iniciar/interromper o serviço (status).</span><span class="sxs-lookup"><span data-stu-id="d59d3-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="d59d3-167">Falha, se alguém tentar alterar outros atributos de serviço como startuptype, credenciais, descrição etc.</span><span class="sxs-lookup"><span data-stu-id="d59d3-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="d59d3-168">O erro emitido é semelhante a:</span><span class="sxs-lookup"><span data-stu-id="d59d3-168">The error thrown is similar to:</span></span>
  
  <span data-ttu-id="d59d3-169">*Não é possível localizar o tipo [management.managementobject]: verifique se o assembly que contém esse tipo é carregado.*</span><span class="sxs-lookup"><span data-stu-id="d59d3-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>
  
* <span data-ttu-id="d59d3-170">Recursos que não são funcionais</span><span class="sxs-lookup"><span data-stu-id="d59d3-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="d59d3-171">User</span><span class="sxs-lookup"><span data-stu-id="d59d3-171">User</span></span>](userResource.md)
  

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="d59d3-172">Recursos de DSC não disponíveis no Nano Server</span><span class="sxs-lookup"><span data-stu-id="d59d3-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="d59d3-173">Os recursos de DSC a seguir não estão disponíveis atualmente no Nano Server:</span><span class="sxs-lookup"><span data-stu-id="d59d3-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="d59d3-174">Descriptografando documento MOF com senhas criptografadas</span><span class="sxs-lookup"><span data-stu-id="d59d3-174">Decrypting MOF document with encrypted password(s)</span></span> 
* <span data-ttu-id="d59d3-175">Servidor de pull -- no momento não é possível definir um servidor de pull no Nano Server</span><span class="sxs-lookup"><span data-stu-id="d59d3-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="d59d3-176">Tudo o que não está na lista de recursos funciona</span><span class="sxs-lookup"><span data-stu-id="d59d3-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="d59d3-177">Usando recursos personalizados de DSC no Nano Server</span><span class="sxs-lookup"><span data-stu-id="d59d3-177">Using custom DSC resources on Nano Server</span></span>
 
<span data-ttu-id="d59d3-178">Devido a conjuntos limitados de APIs do Windows e bibliotecas CLR disponíveis no Nano Server, os recursos de DSC que funcionam com a versão CLR completa do Windows não funcionam necessariamente no Nano Server.</span><span class="sxs-lookup"><span data-stu-id="d59d3-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span> <span data-ttu-id="d59d3-179">Conclua completamente o teste antes de implantar qualquer recurso personalizado de DSC em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="d59d3-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="d59d3-180">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d59d3-180">See Also</span></span>
- [<span data-ttu-id="d59d3-181">Introdução ao Nano Server</span><span class="sxs-lookup"><span data-stu-id="d59d3-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/en-us/library/mt126167.aspx)

