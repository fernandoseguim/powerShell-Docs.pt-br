---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Usando DSC no Nano Server
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400207"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="b1d41-103">Usando DSC no Nano Server</span><span class="sxs-lookup"><span data-stu-id="b1d41-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="b1d41-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b1d41-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b1d41-105">**DSC no Nano Server** é um pacote opcional na pasta `NanoServer\Packages` de mídia do Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="b1d41-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="b1d41-106">O pacote pode ser instalado quando você cria um VHD para um Nano Server especificando **Microsoft-NanoServer-DSC-Package** como o valor do parâmetro **Packages** da função **New-NanoServerImage**.</span><span class="sxs-lookup"><span data-stu-id="b1d41-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="b1d41-107">Por exemplo, se você estivesse criando um VHD para uma máquina virtual, o comando seria semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="b1d41-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="b1d41-108">Para saber mais sobre como instalar e usar o Nano Server, bem como gerenciar o Nano Server com a comunicação remota do PowerShell, confira [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server) (Introdução ao Nano Server).</span><span class="sxs-lookup"><span data-stu-id="b1d41-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="b1d41-109">Recursos de DSC disponíveis no Nano Server</span><span class="sxs-lookup"><span data-stu-id="b1d41-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="b1d41-110">Como o Nano Server dá suporte a apenas um conjunto limitado de APIs em comparação com uma versão completa do Windows Server, por enquanto, o DSC no Nano Server não tem paridade funcional completa com DSC em execução em SKUs completas.</span><span class="sxs-lookup"><span data-stu-id="b1d41-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="b1d41-111">O DSC no Nano Server está em desenvolvimento ativo e ainda não é um recurso completo.</span><span class="sxs-lookup"><span data-stu-id="b1d41-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="b1d41-112">Os recursos de DSC a seguir estão disponíveis atualmente no Nano Server:</span><span class="sxs-lookup"><span data-stu-id="b1d41-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="b1d41-113">Nos modos push e pull</span><span class="sxs-lookup"><span data-stu-id="b1d41-113">Both push and pull modes</span></span>

- <span data-ttu-id="b1d41-114">Todos os cmdlets de DSC que existem em uma versão completa do Windows Server, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b1d41-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="b1d41-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b1d41-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="b1d41-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b1d41-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="b1d41-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="b1d41-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="b1d41-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="b1d41-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="b1d41-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1d41-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="b1d41-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1d41-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="b1d41-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1d41-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="b1d41-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1d41-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="b1d41-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="b1d41-123">Publish-DscConfiguraiton</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="b1d41-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1d41-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="b1d41-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1d41-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="b1d41-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="b1d41-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="b1d41-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b1d41-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="b1d41-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="b1d41-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="b1d41-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="b1d41-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="b1d41-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="b1d41-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="b1d41-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="b1d41-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="b1d41-132">Compilação de configurações (confira [Configurações DSC](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="b1d41-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="b1d41-133">**Edição #1629** Criptografia de senha (veja [protegendo o arquivo MOF](../pull-server/secureMOF.md)) durante a configuração de compilação não funciona.</span><span class="sxs-lookup"><span data-stu-id="b1d41-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="b1d41-134">Compilação de metaconfigurações (confira [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="b1d41-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="b1d41-135">Execução de um recurso no contexto do usuário (confira [Executar DSC com as credenciais do usuário (RunAs)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="b1d41-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="b1d41-136">Recursos baseados em classe (confira [Escrevendo um recurso personalizado de DSC com classes do PowerShell](../resources/authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="b1d41-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="b1d41-137">Depuração dos recursos de DSC (confira [Depurando os recursos de DSC](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="b1d41-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="b1d41-138">**Edição #1629** Não funcionará se um recurso estiver usando PsDscRunAsCredential (Confira [executar DSC com credenciais de usuário](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="b1d41-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="b1d41-139">Especificando dependências de nó cruzado</span><span class="sxs-lookup"><span data-stu-id="b1d41-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="b1d41-140">Controle de versão do recurso</span><span class="sxs-lookup"><span data-stu-id="b1d41-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="b1d41-141">Cliente de pull (configurações e recursos) (confira [Configurando um cliente de pull usando nomes de configuração](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="b1d41-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="b1d41-142">Configurações parciais (pull e push)</span><span class="sxs-lookup"><span data-stu-id="b1d41-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="b1d41-143">Relatórios para o servidor de pull</span><span class="sxs-lookup"><span data-stu-id="b1d41-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="b1d41-144">Criptografia do MOF</span><span class="sxs-lookup"><span data-stu-id="b1d41-144">MOF encryption</span></span>

- <span data-ttu-id="b1d41-145">Registro em log de eventos</span><span class="sxs-lookup"><span data-stu-id="b1d41-145">Event logging</span></span>

- <span data-ttu-id="b1d41-146">Relatórios de DSC de automação do Azure</span><span class="sxs-lookup"><span data-stu-id="b1d41-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="b1d41-147">Recursos que são totalmente funcionais</span><span class="sxs-lookup"><span data-stu-id="b1d41-147">Resources that are fully functional</span></span>

- <span data-ttu-id="b1d41-148">**Archive**</span><span class="sxs-lookup"><span data-stu-id="b1d41-148">**Archive**</span></span>
- <span data-ttu-id="b1d41-149">**Environment**</span><span class="sxs-lookup"><span data-stu-id="b1d41-149">**Environment**</span></span>
- <span data-ttu-id="b1d41-150">**File**</span><span class="sxs-lookup"><span data-stu-id="b1d41-150">**File**</span></span>
- <span data-ttu-id="b1d41-151">**Log**</span><span class="sxs-lookup"><span data-stu-id="b1d41-151">**Log**</span></span>
- <span data-ttu-id="b1d41-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="b1d41-152">**ProcessSet**</span></span>
- <span data-ttu-id="b1d41-153">**Registry**</span><span class="sxs-lookup"><span data-stu-id="b1d41-153">**Registry**</span></span>
- <span data-ttu-id="b1d41-154">**Script**</span><span class="sxs-lookup"><span data-stu-id="b1d41-154">**Script**</span></span>
- <span data-ttu-id="b1d41-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="b1d41-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="b1d41-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="b1d41-156">**WindowsProcess**</span></span>
- <span data-ttu-id="b1d41-157">**WaitForAll** (confira [Especificação de dependências de nó cruzado](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="b1d41-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="b1d41-158">**WaitForAny** (confira [Especificação de dependências de nó cruzado](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="b1d41-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="b1d41-159">**WaitForSome** (confira [Especificação de dependências de nó cruzado](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="b1d41-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="b1d41-160">Recursos que são parcialmente funcionais</span><span class="sxs-lookup"><span data-stu-id="b1d41-160">Resources that are partially functional</span></span>
- <span data-ttu-id="b1d41-161">**Grupo**</span><span class="sxs-lookup"><span data-stu-id="b1d41-161">**Group**</span></span>
- <span data-ttu-id="b1d41-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="b1d41-162">**GroupSet**</span></span>

  <span data-ttu-id="b1d41-163">**Edição #1629** Recursos acima falharão se a instância específica é chamada duas vezes (executando a mesma configuração duas vezes)</span><span class="sxs-lookup"><span data-stu-id="b1d41-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="b1d41-164">**Service**</span><span class="sxs-lookup"><span data-stu-id="b1d41-164">**Service**</span></span>
- <span data-ttu-id="b1d41-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="b1d41-165">**ServiceSet**</span></span>

  <span data-ttu-id="b1d41-166">**Edição #1629** Funciona somente para iniciar/parar serviço (status).</span><span class="sxs-lookup"><span data-stu-id="b1d41-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="b1d41-167">Falha, se alguém tentar alterar outros atributos de serviço como startuptype, credenciais, descrição etc.</span><span class="sxs-lookup"><span data-stu-id="b1d41-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="b1d41-168">O erro emitido é semelhante a:</span><span class="sxs-lookup"><span data-stu-id="b1d41-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="b1d41-169">*Não é possível localizar o tipo [management.managementobject]: verifique se o assembly que contém esse tipo é carregado.*</span><span class="sxs-lookup"><span data-stu-id="b1d41-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="b1d41-170">Recursos que não são funcionais</span><span class="sxs-lookup"><span data-stu-id="b1d41-170">Resources that are not functional</span></span>
- <span data-ttu-id="b1d41-171">**User**</span><span class="sxs-lookup"><span data-stu-id="b1d41-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="b1d41-172">Recursos de DSC não disponíveis no Nano Server</span><span class="sxs-lookup"><span data-stu-id="b1d41-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="b1d41-173">Os recursos de DSC a seguir não estão disponíveis atualmente no Nano Server:</span><span class="sxs-lookup"><span data-stu-id="b1d41-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="b1d41-174">Descriptografando documento MOF com senhas criptografadas</span><span class="sxs-lookup"><span data-stu-id="b1d41-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="b1d41-175">Servidor de pull -- no momento não é possível definir um servidor de pull no Nano Server</span><span class="sxs-lookup"><span data-stu-id="b1d41-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="b1d41-176">Tudo o que não está na lista de recursos funciona</span><span class="sxs-lookup"><span data-stu-id="b1d41-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="b1d41-177">Usando recursos personalizados de DSC no Nano Server</span><span class="sxs-lookup"><span data-stu-id="b1d41-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="b1d41-178">Devido a conjuntos limitados de APIs do Windows e bibliotecas CLR disponíveis no Nano Server, os recursos de DSC que funcionam com a versão CLR completa do Windows não funcionam necessariamente no Nano Server.</span><span class="sxs-lookup"><span data-stu-id="b1d41-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="b1d41-179">Conclua completamente o teste antes de implantar qualquer recurso personalizado de DSC em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="b1d41-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1d41-180">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b1d41-180">See Also</span></span>

- [<span data-ttu-id="b1d41-181">Introdução ao Nano Server</span><span class="sxs-lookup"><span data-stu-id="b1d41-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
