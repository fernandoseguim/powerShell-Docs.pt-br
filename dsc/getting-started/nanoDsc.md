---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Usando DSC no Nano Server
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054655"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="8d6f5-103">Usando DSC no Nano Server</span><span class="sxs-lookup"><span data-stu-id="8d6f5-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="8d6f5-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8d6f5-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8d6f5-105">**DSC no Nano Server** é um pacote opcional na pasta `NanoServer\Packages` de mídia do Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="8d6f5-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="8d6f5-106">O pacote pode ser instalado quando você cria um VHD para um Nano Server especificando **Microsoft-NanoServer-DSC-Package** como o valor do parâmetro **Packages** da função **New-NanoServerImage**.</span><span class="sxs-lookup"><span data-stu-id="8d6f5-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="8d6f5-107">Por exemplo, se você estivesse criando um VHD para uma máquina virtual, o comando seria semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="8d6f5-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="8d6f5-108">Para saber mais sobre como instalar e usar o Nano Server, bem como gerenciar o Nano Server com a comunicação remota do PowerShell, confira [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server) (Introdução ao Nano Server).</span><span class="sxs-lookup"><span data-stu-id="8d6f5-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="8d6f5-109">Recursos de DSC disponíveis no Nano Server</span><span class="sxs-lookup"><span data-stu-id="8d6f5-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="8d6f5-110">Como o Nano Server dá suporte a apenas um conjunto limitado de APIs em comparação com uma versão completa do Windows Server, por enquanto, o DSC no Nano Server não tem paridade funcional completa com DSC em execução em SKUs completas.</span><span class="sxs-lookup"><span data-stu-id="8d6f5-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="8d6f5-111">O DSC no Nano Server está em desenvolvimento ativo e ainda não é um recurso completo.</span><span class="sxs-lookup"><span data-stu-id="8d6f5-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="8d6f5-112">Os recursos de DSC a seguir estão disponíveis atualmente no Nano Server:</span><span class="sxs-lookup"><span data-stu-id="8d6f5-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="8d6f5-113">Nos modos push e pull</span><span class="sxs-lookup"><span data-stu-id="8d6f5-113">Both push and pull modes</span></span>

- <span data-ttu-id="8d6f5-114">Todos os cmdlets de DSC que existem em uma versão completa do Windows Server, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8d6f5-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="8d6f5-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8d6f5-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="8d6f5-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8d6f5-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="8d6f5-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="8d6f5-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="8d6f5-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="8d6f5-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="8d6f5-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d6f5-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="8d6f5-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d6f5-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="8d6f5-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d6f5-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="8d6f5-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d6f5-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="8d6f5-123">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d6f5-123">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="8d6f5-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d6f5-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="8d6f5-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d6f5-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="8d6f5-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="8d6f5-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="8d6f5-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="8d6f5-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="8d6f5-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="8d6f5-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="8d6f5-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="8d6f5-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="8d6f5-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="8d6f5-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="8d6f5-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="8d6f5-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="8d6f5-132">Compilação de configurações (confira [Configurações DSC](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="8d6f5-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="8d6f5-133">**Problema:** a criptografia de senha (confira [Protegendo o arquivo MOF](../pull-server/secureMOF.md)) durante a compilação da configuração não funciona.</span><span class="sxs-lookup"><span data-stu-id="8d6f5-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="8d6f5-134">Compilação de metaconfigurações (confira [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="8d6f5-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="8d6f5-135">Execução de um recurso no contexto do usuário (confira [Executar DSC com as credenciais do usuário (RunAs)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="8d6f5-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="8d6f5-136">Recursos baseados em classe (confira [Escrevendo um recurso personalizado de DSC com classes do PowerShell](../resources/authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="8d6f5-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="8d6f5-137">Depuração dos recursos de DSC (confira [Depurando os recursos de DSC](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="8d6f5-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="8d6f5-138">**Problema:** não funciona se um recurso estiver usando PsDscRunAsCredential (confira [Executar DSC com credenciais de usuário](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="8d6f5-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="8d6f5-139">Especificando dependências de nó cruzado</span><span class="sxs-lookup"><span data-stu-id="8d6f5-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="8d6f5-140">Controle de versão do recurso</span><span class="sxs-lookup"><span data-stu-id="8d6f5-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="8d6f5-141">Cliente de pull (configurações e recursos) (confira [Configurando um cliente de pull usando nomes de configuração](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="8d6f5-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="8d6f5-142">Configurações parciais (pull e push)</span><span class="sxs-lookup"><span data-stu-id="8d6f5-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="8d6f5-143">Relatórios para o servidor de pull</span><span class="sxs-lookup"><span data-stu-id="8d6f5-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="8d6f5-144">Criptografia do MOF</span><span class="sxs-lookup"><span data-stu-id="8d6f5-144">MOF encryption</span></span>

- <span data-ttu-id="8d6f5-145">Registro em log de eventos</span><span class="sxs-lookup"><span data-stu-id="8d6f5-145">Event logging</span></span>

- <span data-ttu-id="8d6f5-146">Relatórios de DSC de automação do Azure</span><span class="sxs-lookup"><span data-stu-id="8d6f5-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="8d6f5-147">Recursos que são totalmente funcionais</span><span class="sxs-lookup"><span data-stu-id="8d6f5-147">Resources that are fully functional</span></span>

- <span data-ttu-id="8d6f5-148">**Archive**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-148">**Archive**</span></span>
- <span data-ttu-id="8d6f5-149">**Environment**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-149">**Environment**</span></span>
- <span data-ttu-id="8d6f5-150">**File**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-150">**File**</span></span>
- <span data-ttu-id="8d6f5-151">**Log**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-151">**Log**</span></span>
- <span data-ttu-id="8d6f5-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-152">**ProcessSet**</span></span>
- <span data-ttu-id="8d6f5-153">**Registry**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-153">**Registry**</span></span>
- <span data-ttu-id="8d6f5-154">**Script**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-154">**Script**</span></span>
- <span data-ttu-id="8d6f5-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="8d6f5-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-156">**WindowsProcess**</span></span>
- <span data-ttu-id="8d6f5-157">**WaitForAll** (confira [Especificação de dependências de nó cruzado](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="8d6f5-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="8d6f5-158">**WaitForAny** (confira [Especificação de dependências de nó cruzado](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="8d6f5-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="8d6f5-159">**WaitForSome** (confira [Especificação de dependências de nó cruzado](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="8d6f5-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="8d6f5-160">Recursos que são parcialmente funcionais</span><span class="sxs-lookup"><span data-stu-id="8d6f5-160">Resources that are partially functional</span></span>
- <span data-ttu-id="8d6f5-161">**Grupo**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-161">**Group**</span></span>
- <span data-ttu-id="8d6f5-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-162">**GroupSet**</span></span>

  <span data-ttu-id="8d6f5-163">**Problema:** os recursos acima falharão se a instância específica for chamada duas vezes (executando a mesma configuração duas vezes)</span><span class="sxs-lookup"><span data-stu-id="8d6f5-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="8d6f5-164">**Service**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-164">**Service**</span></span>
- <span data-ttu-id="8d6f5-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-165">**ServiceSet**</span></span>

  <span data-ttu-id="8d6f5-166">**Problema:** funciona apenas para iniciar/interromper o serviço (status).</span><span class="sxs-lookup"><span data-stu-id="8d6f5-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="8d6f5-167">Falha, se alguém tentar alterar outros atributos de serviço como startuptype, credenciais, descrição etc.</span><span class="sxs-lookup"><span data-stu-id="8d6f5-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="8d6f5-168">O erro emitido é semelhante a:</span><span class="sxs-lookup"><span data-stu-id="8d6f5-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="8d6f5-169">*Não é possível localizar o tipo [management.managementobject]: verifique se o assembly que contém esse tipo é carregado.*</span><span class="sxs-lookup"><span data-stu-id="8d6f5-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="8d6f5-170">Recursos que não são funcionais</span><span class="sxs-lookup"><span data-stu-id="8d6f5-170">Resources that are not functional</span></span>
- <span data-ttu-id="8d6f5-171">**User**</span><span class="sxs-lookup"><span data-stu-id="8d6f5-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="8d6f5-172">Recursos de DSC não disponíveis no Nano Server</span><span class="sxs-lookup"><span data-stu-id="8d6f5-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="8d6f5-173">Os recursos de DSC a seguir não estão disponíveis atualmente no Nano Server:</span><span class="sxs-lookup"><span data-stu-id="8d6f5-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="8d6f5-174">Descriptografando documento MOF com senhas criptografadas</span><span class="sxs-lookup"><span data-stu-id="8d6f5-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="8d6f5-175">Servidor de pull -- no momento não é possível definir um servidor de pull no Nano Server</span><span class="sxs-lookup"><span data-stu-id="8d6f5-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="8d6f5-176">Tudo o que não está na lista de recursos funciona</span><span class="sxs-lookup"><span data-stu-id="8d6f5-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="8d6f5-177">Usando recursos personalizados de DSC no Nano Server</span><span class="sxs-lookup"><span data-stu-id="8d6f5-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="8d6f5-178">Devido a conjuntos limitados de APIs do Windows e bibliotecas CLR disponíveis no Nano Server, os recursos de DSC que funcionam com a versão CLR completa do Windows não funcionam necessariamente no Nano Server.</span><span class="sxs-lookup"><span data-stu-id="8d6f5-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="8d6f5-179">Conclua completamente o teste antes de implantar qualquer recurso personalizado de DSC em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="8d6f5-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d6f5-180">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8d6f5-180">See Also</span></span>

- [<span data-ttu-id="8d6f5-181">Introdução ao Nano Server</span><span class="sxs-lookup"><span data-stu-id="8d6f5-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
