---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: ad1d19eeb70a19cd3d1493b9a09b115af755feb4
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="112db-102">Limitações e problemas conhecidos do DSC (Configuração de Estado Desejado)</span><span class="sxs-lookup"><span data-stu-id="112db-102">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

<a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="112db-103">Alteração interruptiva: os certificados usados para criptografar/descriptografar senhas em configurações DSC podem não funcionar após a instalação do WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="112db-103">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>
--------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="112db-104">Em versões da Preview do WMF 4.0 e 5.0, o DSC não permite que as senhas na configuração tenham um tamanho maior que 121 caracteres.</span><span class="sxs-lookup"><span data-stu-id="112db-104">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="112db-105">O DSC forçava o uso de senhas curtas, mesmo que fosse desejável usar senhas longas e fortes.</span><span class="sxs-lookup"><span data-stu-id="112db-105">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="112db-106">Essa alteração interruptiva permite que as senhas tenham um tamanho arbitrário na configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="112db-106">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="112db-107">**Resolução:** crie novamente o certificado com o uso da Chave de Codificação de Dados ou de Codificação de Chave, bem como o uso Avançado de Chave de Criptografia de Documento (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="112db-107">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="112db-108">O artigo do TechNet <https://technet.microsoft.com/library/dn807171.aspx> traz mais informações.</span><span class="sxs-lookup"><span data-stu-id="112db-108">Technet article <https://technet.microsoft.com/library/dn807171.aspx> has more information.</span></span>


<a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="112db-109">Os cmdlets do DSC poderão falhar após a instalação do WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="112db-109">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>
------------------------------------------------------------------------------------
<span data-ttu-id="112db-110">Start-DscConfiguration e outros cmdlets do DSC poderão falhar após a instalação do WMF 5.0 RTM com o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="112db-110">Start-DscConfiguration and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

<span data-ttu-id="112db-111">**Resolução:** exclua DSCEngineCache.mof executando o seguinte comando em uma sessão do PowerShell com privilégios elevados (Executar como Administrador):</span><span class="sxs-lookup"><span data-stu-id="112db-111">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>
    
```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


<a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="112db-112">Os cmdlets do DSC poderão não funcionar se o WMF 5.0 RTM estiver instalado, além da Preview de Produção do WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="112db-112">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>
------------------------------------------------------
<span data-ttu-id="112db-113">**Resolução:** execute o seguinte comando em uma sessão do PowerShell com privilégios elevados (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="112db-113">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


<a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="112db-114">O LCM pode entrar em um estado instável durante o uso de Get-DscConfiguration em DebugMode</span><span class="sxs-lookup"><span data-stu-id="112db-114">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>
-------------------------------------------------------------------------------

<span data-ttu-id="112db-115">Se o LCM estiver em DebugMode, pressionar CTRL+C para interromper o processamento de Get-DscConfiguration poderá fazer com que o LCM entre em um estado instável, a tal ponto em que a maioria dos cmdlets do DSC não funcionará.</span><span class="sxs-lookup"><span data-stu-id="112db-115">If LCM is in DebugMode, pressing CTRL+C to stop the processing of Get-DscConfiguration can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="112db-116">**Resolução:** não pressione CTRL+C durante a depuração do cmdlet Get-DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="112db-116">**Resolution:** Don’t press CTRL+C while debugging Get-DscConfiguration cmdlet.</span></span>


<a name="stop-dscconfiguration-may-hang-in-debugmode"></a><span data-ttu-id="112db-117">Stop-DscConfiguration poderá parar de responder em DebugMode</span><span class="sxs-lookup"><span data-stu-id="112db-117">Stop-DscConfiguration may hang in DebugMode</span></span>
------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="112db-118">Se o LCM estiver em DebugMode, Stop-DscConfiguration poderá parar de responder durante a tentativa de interromper uma operação iniciada por Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="112db-118">If LCM is in DebugMode, Stop-DscConfiguration may hang while trying to stop an operation started by Get-DscConfiguration</span></span>

<span data-ttu-id="112db-119">**Resolução:** conclua a depuração da operação iniciada por Get-DscConfiguration, conforme descrito na seção "[Depurando recursos DSC](https://msdn.microsoft.com/powershell/dsc/debugresource)".</span><span class="sxs-lookup"><span data-stu-id="112db-119">**Resolution:** Finish the debugging of the operation started by Get-DscConfiguration as outlined in section ‘[Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource)’.</span></span>


<a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="112db-120">Nenhuma mensagem de erro detalhada é mostrada em DebugMode</span><span class="sxs-lookup"><span data-stu-id="112db-120">No Verbose Error Messages are shown in DebugMode</span></span>
-----------------------------------------------------------------------------------
<span data-ttu-id="112db-121">Se o LCM estiver em DebugMode, nenhuma mensagem de erro detalhada será exibida nos Recursos DSC.</span><span class="sxs-lookup"><span data-stu-id="112db-121">If LCM is in DebugMode, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="112db-122">**Resolução:** desabilite *DebugMode* para ver as mensagens detalhadas no recurso</span><span class="sxs-lookup"><span data-stu-id="112db-122">**Resolution:** Disable *DebugMode* to see verbose messages from the resource</span></span>


<a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="112db-123">As operações Invoke-DscResource não podem ser recuperadas pelo cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="112db-123">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>
--------------------------------------------------------------------------------------
<span data-ttu-id="112db-124">Depois de usar o cmdlet Invoke-DscResource para invocar diretamente os métodos de qualquer recurso, os registros dessa operação não poderão ser recuperados por meio de Get-DscConfigurationStatus em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="112db-124">After using Invoke-DscResource cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through Get-DscConfigurationStatus at a later time.</span></span>

<span data-ttu-id="112db-125">**Resolução:** nenhuma.</span><span class="sxs-lookup"><span data-stu-id="112db-125">**Resolution:** None.</span></span>


<a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="112db-126">Get-DscConfigurationStatus retorna operações de ciclo de pull como o tipo *Consistência*</span><span class="sxs-lookup"><span data-stu-id="112db-126">Get-DscConfigurationStatus returns pull cycle operations as type *Consistency*</span></span>
---------------------------------------------------------------------------------
<span data-ttu-id="112db-127">Quando um nó é definido como o modo de atualização por PULL, para cada operação de recepção realizada, o cmdlet Get-DscConfigurationStatus relata o tipo de operação como *Consistência* em vez de *Inicial*</span><span class="sxs-lookup"><span data-stu-id="112db-127">When a node is set to PULL refresh mode, for each pull operation performed, Get-DscConfigurationStatus cmdlet reports the operation type as *Consistency* instead of *Initial*</span></span>

<span data-ttu-id="112db-128">**Resolução:** nenhuma.</span><span class="sxs-lookup"><span data-stu-id="112db-128">**Resolution:** None.</span></span>

<a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="112db-129">O cmdlet Invoke-DscResource não retorna as mensagens na ordem em que foram produzidas</span><span class="sxs-lookup"><span data-stu-id="112db-129">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>
---------------------------------------------------------------------------------
<span data-ttu-id="112db-130">O cmdlet Invoke-DscResource não retorna mensagens detalhadas, de aviso e de erro na ordem em que foram produzidas pelo LCM ou pelo recurso DSC.</span><span class="sxs-lookup"><span data-stu-id="112db-130">The Invoke-DscResource cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="112db-131">**Resolução:** nenhuma.</span><span class="sxs-lookup"><span data-stu-id="112db-131">**Resolution:** None.</span></span>


<a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="112db-132">Os Recursos DSC não podem ser depurados com facilidade quando usados com Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="112db-132">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>
-----------------------------------------------------------------------
<span data-ttu-id="112db-133">Quando o LCM estiver sendo executado no modo de depuração (veja [Depurando recursos DSC](https://msdn.microsoft.com/powershell/dsc/debugresource) para obter mais detalhes), o cmdlet Invoke-DscResource não fornecerá informações sobre o runspace para se conectar para realizar a depuração.</span><span class="sxs-lookup"><span data-stu-id="112db-133">When LCM is running in debug mode (see [Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource) for more details), Invoke-DscResource cmdlet does not give information about runspace to connect to for debugging.</span></span>
<span data-ttu-id="112db-134">**Resolução:** descubra e anexe-se ao runspace usando os cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess**, **Get-Runspace** e **Debug-Runspace** para depurar o recurso DSC.</span><span class="sxs-lookup"><span data-stu-id="112db-134">**Resolution:** Discover and attach to the runspace using cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** and **Debug-Runspace** to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```


<a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="112db-135">Vários documentos de Configuração Parcial para o mesmo nó não podem ter nomes de recursos idênticos</span><span class="sxs-lookup"><span data-stu-id="112db-135">Various Partial Configuration documents for same node cannot have identical resource names</span></span>
------------------------------------------------------------------------------------------

<span data-ttu-id="112db-136">Para várias configurações parciais que são implantadas em um único nó, nomes idênticos de recursos causam um erro de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="112db-136">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="112db-137">**Resolução:** use nomes diferentes até para os mesmos recursos em configurações parciais diferentes.</span><span class="sxs-lookup"><span data-stu-id="112db-137">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>


<a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="112db-138">–UseExisting de Start-DscConfiguration não funciona com –Credential</span><span class="sxs-lookup"><span data-stu-id="112db-138">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>
------------------------------------------------------------------

<span data-ttu-id="112db-139">Ao usar Start-DscConfiguration com o parâmetro –UseExisting, o parâmetro –Credential é ignorado.</span><span class="sxs-lookup"><span data-stu-id="112db-139">When using Start-DscConfiguration with –UseExisting parameter, the –Credential parameter is ignored.</span></span> <span data-ttu-id="112db-140">O DSC usa a identidade de processo padrão para continuar a operação.</span><span class="sxs-lookup"><span data-stu-id="112db-140">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="112db-141">Isso causa erros quando uma credencial diferente é necessária para continuar no nó remoto.</span><span class="sxs-lookup"><span data-stu-id="112db-141">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="112db-142">**Resolução:** use a sessão CIM para operações do DSC remotas:</span><span class="sxs-lookup"><span data-stu-id="112db-142">**Resolution:** Use CIM session for remote DSC operations:</span></span>
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


<a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="112db-143">Endereços IPv6 como Nomes de Nó em configurações DSC</span><span class="sxs-lookup"><span data-stu-id="112db-143">IPv6 Addresses as Node Names in DSC configurations</span></span>
--------------------------------------------------
<span data-ttu-id="112db-144">Nesta versão, não há suporte para endereços IPv6 como nomes de nó em scripts de configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="112db-144">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="112db-145">**Resolução:** nenhuma.</span><span class="sxs-lookup"><span data-stu-id="112db-145">**Resolution:** None.</span></span>


<a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="112db-146">Depuração de recursos DSC baseados em classe</span><span class="sxs-lookup"><span data-stu-id="112db-146">Debugging of Class-Based DSC Resources</span></span>
--------------------------------------
<span data-ttu-id="112db-147">Nesta versão, não há suporte para a depuração de recursos DSC baseados em classe.</span><span class="sxs-lookup"><span data-stu-id="112db-147">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="112db-148">**Resolução:** nenhuma.</span><span class="sxs-lookup"><span data-stu-id="112db-148">**Resolution:** None.</span></span>


<a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="112db-149">As variáveis e funções definidas no escopo de $script no Recurso DSC Baseado em Classe não são preservadas em várias chamadas para um Recurso DSC</span><span class="sxs-lookup"><span data-stu-id="112db-149">Variables & Functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span> 
-------------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="112db-150">Várias chamadas consecutivas para Start-DSCConfiguration falharão se a configuração estiver usando qualquer recurso baseado em classe que tenha variáveis ou funções definidas no escopo de $script.</span><span class="sxs-lookup"><span data-stu-id="112db-150">Multiple consecutive calls to Start-DSCConfiguration will fail if configuration is using any class-based resource which has variables or functions defined in $script scope.</span></span>

<span data-ttu-id="112db-151">**Resolução:** defina todas as variáveis e funções na própria classe do Recurso DSC.</span><span class="sxs-lookup"><span data-stu-id="112db-151">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="112db-152">Nenhuma variável/função do escopo de $script.</span><span class="sxs-lookup"><span data-stu-id="112db-152">No $script scope variables/functions.</span></span>


<a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="112db-153">Depuração do Recurso DSC quando um recurso estiver usando PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="112db-153">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>
----------------------------------------------------------------------
<span data-ttu-id="112db-154">Nesta versão, não há suporte para a depuração do Recurso DSC quando um recurso usa a propriedade *PSDscRunAsCredential* na configuração.</span><span class="sxs-lookup"><span data-stu-id="112db-154">DSC Resource debugging when a resource is using the *PSDscRunAsCredential* property in the configuration is not suported in this release.</span></span>

<span data-ttu-id="112db-155">**Resolução:** nenhuma.</span><span class="sxs-lookup"><span data-stu-id="112db-155">**Resolution:** None.</span></span>


<a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="112db-156">Não há suporte para PsDscRunAsCredential nos recursos de composição DSC</span><span class="sxs-lookup"><span data-stu-id="112db-156">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>
----------------------------------------------------------------

<span data-ttu-id="112db-157">**Resolução:** use a propriedade Credential se estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="112db-157">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="112db-158">ServiceSet e WindowsFeatureSet de exemplo</span><span class="sxs-lookup"><span data-stu-id="112db-158">Example ServiceSet and WindowsFeatureSet</span></span>


<a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="112db-159">*Get-DscResource -Syntax* não reflete PsDscRunAsCredential corretamente</span><span class="sxs-lookup"><span data-stu-id="112db-159">*Get-DscResource -Syntax* does not reflect PsDscRunAsCredential correctly</span></span>
-------------------------------------------------------------------------
<span data-ttu-id="112db-160">Get-DscResource -Syntax não reflete PsDscRunAsCredential corretamente quando o recurso o marca como obrigatório ou não dá suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="112db-160">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="112db-161">**Resolução:** nenhuma.</span><span class="sxs-lookup"><span data-stu-id="112db-161">**Resolution:** None.</span></span> <span data-ttu-id="112db-162">No entanto, a criação de configuração no ISE reflete metadados corretos sobre a propriedade PsDscRunAsCredential ao usar o IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="112db-162">However, authoring configuration in ISE reflects correct metadata about PsDscRunAsCredential property when using IntelliSense.</span></span>


<a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="112db-163">WindowsOptionalFeature não está disponível no Windows 7</span><span class="sxs-lookup"><span data-stu-id="112db-163">WindowsOptionalFeature is not available in Windows 7</span></span>
-----------------------------------------------------

<span data-ttu-id="112db-164">O recurso DSC de WindowsOptionalFeature não está disponível no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="112db-164">The WindowsOptionalFeature DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="112db-165">Este recurso exige o módulo DISM e os cmdlets do DISM que estão disponíveis começando do Windows 8 e versões mais recentes do sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="112db-165">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

<a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="112db-166">Para obter recursos de DSC baseados em classes, Import-DscResource -ModuleVersion pode não funcionar como esperado</span><span class="sxs-lookup"><span data-stu-id="112db-166">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>   
------------------------------------------------------------------------------------------
<span data-ttu-id="112db-167">Se o nó compilação tiver várias versões de um módulo de recurso de DSC baseado em classes, o `Import-DscResource -ModuleVersion` não selecionará a versão especificada e resulta no seguinte erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="112db-167">If the compilation node has multiple version of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="112db-168">**Resolução:** importe a versão necessária definindo o objeto *ModuleSpecification* para o `-ModuleName` com a chave `RequiredVersion` especificada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="112db-168">**Resolution:** Import the required version by defining the *ModuleSpecification* object to the `-ModuleName` with `RequiredVersion` key specified as follows:</span></span>
``` PowerShell  
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}  
```  

<a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="112db-169">Alguns recursos DSC, como recursos de Registro podem começar a levar muito tempo para processar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="112db-169">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>
--------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="112db-170">**Resolution1:** criar uma tarefa agendada que limpa periodicamente a pasta a seguir.</span><span class="sxs-lookup"><span data-stu-id="112db-170">**Resolution1:** Create a schedule task that cleans up the following folder periodically.</span></span>
``` PowerShell 
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis 
```

<span data-ttu-id="112db-171">**Resolution2:** alterar a configuração DSC para limpar a pasta *CommandAnalysis* no final da configuração.</span><span class="sxs-lookup"><span data-stu-id="112db-171">**Resolution2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>
``` PowerShell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config 
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```

