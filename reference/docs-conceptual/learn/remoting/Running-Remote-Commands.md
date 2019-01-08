---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Executando comandos remotos
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400537"
---
# <a name="running-remote-commands"></a><span data-ttu-id="1cea0-103">Executando comandos remotos</span><span class="sxs-lookup"><span data-stu-id="1cea0-103">Running Remote Commands</span></span>

<span data-ttu-id="1cea0-104">Você pode executar comandos em uma ou centenas de computadores com um único comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1cea0-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="1cea0-105">O Windows PowerShell oferece suporte à computação remota usando diversas tecnologias, incluindo WMI, RPC e WS-Management.</span><span class="sxs-lookup"><span data-stu-id="1cea0-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="1cea0-106">O PowerShell Core dá suporte a WMI, WS-Management e comunicação remota de SSH.</span><span class="sxs-lookup"><span data-stu-id="1cea0-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="1cea0-107">Não há mais suporte para RPC.</span><span class="sxs-lookup"><span data-stu-id="1cea0-107">RPC is no longer supported.</span></span>

<span data-ttu-id="1cea0-108">Para saber mais sobre a comunicação remota no PowerShell Core, consulte os seguintes artigos:</span><span class="sxs-lookup"><span data-stu-id="1cea0-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="1cea0-109">[Comunicação remota do SSH no PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="1cea0-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="1cea0-110">[Comunicação remota do WSMan no PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="1cea0-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="1cea0-111">Comunicação remota do Windows PowerShell sem configuração</span><span class="sxs-lookup"><span data-stu-id="1cea0-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="1cea0-112">Muitos cmdlets do Windows PowerShell têm o parâmetro ComputerName que permite coletar dados e alterar as configurações de um ou mais computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="1cea0-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="1cea0-113">Esses cmdlets usam protocolos de comunicação variados e funcionam em todos os sistemas operacionais Windows sem qualquer configuração especial.</span><span class="sxs-lookup"><span data-stu-id="1cea0-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="1cea0-114">Esses cmdlets incluem:</span><span class="sxs-lookup"><span data-stu-id="1cea0-114">These cmdlets include:</span></span>

- [<span data-ttu-id="1cea0-115">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="1cea0-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="1cea0-116">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="1cea0-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="1cea0-117">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="1cea0-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="1cea0-118">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="1cea0-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="1cea0-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="1cea0-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="1cea0-120">Get-Process</span><span class="sxs-lookup"><span data-stu-id="1cea0-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="1cea0-121">Get-Service</span><span class="sxs-lookup"><span data-stu-id="1cea0-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="1cea0-122">Set-Service</span><span class="sxs-lookup"><span data-stu-id="1cea0-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="1cea0-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="1cea0-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="1cea0-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="1cea0-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="1cea0-125">Normalmente, os cmdlets que dão suporte à comunicação remota sem configuração especial têm um parâmetro ComputerName, e não um parâmetro Session.</span><span class="sxs-lookup"><span data-stu-id="1cea0-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="1cea0-126">Para localizar esses cmdlets em sua sessão, digite:</span><span class="sxs-lookup"><span data-stu-id="1cea0-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="1cea0-127">Comunicação remota do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1cea0-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="1cea0-128">Usando o protocolo WS-Management, a comunicação remota do Windows PowerShell permite executar qualquer comando do Windows PowerShell em um ou vários computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="1cea0-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="1cea0-129">Você pode estabelecer conexões persistentes, iniciar sessões interativas e executar scripts em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="1cea0-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="1cea0-130">Para usar a comunicação remota do Windows PowerShell, o computador remoto deve ser configurado para gerenciamento remoto.</span><span class="sxs-lookup"><span data-stu-id="1cea0-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="1cea0-131">Para obter mas informações, incluindo instruções consulte [Sobre requisitos remotos](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="1cea0-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="1cea0-132">Depois de configurar a comunicação remota do Windows PowerShell, muitas estratégias de comunicação remota ficam disponíveis para você.</span><span class="sxs-lookup"><span data-stu-id="1cea0-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="1cea0-133">Este artigo lista algumas delas.</span><span class="sxs-lookup"><span data-stu-id="1cea0-133">This article lists just a few of them.</span></span> <span data-ttu-id="1cea0-134">Saiba mais em [Sobre comunicação remota](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="1cea0-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="1cea0-135">Iniciar uma sessão interativa</span><span class="sxs-lookup"><span data-stu-id="1cea0-135">Start an Interactive Session</span></span>

<span data-ttu-id="1cea0-136">Para iniciar uma sessão interativa com um único computador remoto, use o cmdlet [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="1cea0-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="1cea0-137">Por exemplo, para iniciar uma sessão interativa com o computador remoto Server01, digite:</span><span class="sxs-lookup"><span data-stu-id="1cea0-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="1cea0-138">O prompt de comando muda para exibir o nome do computador remoto.</span><span class="sxs-lookup"><span data-stu-id="1cea0-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="1cea0-139">Quaisquer comandos digitados no prompt são executados no computador remoto, e os resultados são exibidos no computador local.</span><span class="sxs-lookup"><span data-stu-id="1cea0-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="1cea0-140">Para encerrar a sessão interativa, digite:</span><span class="sxs-lookup"><span data-stu-id="1cea0-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="1cea0-141">Para saber mais sobre os cmdlets Enter-PSSession e Exit-PSSession, consulte:</span><span class="sxs-lookup"><span data-stu-id="1cea0-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="1cea0-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="1cea0-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="1cea0-143">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="1cea0-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="1cea0-144">Executar um comando remoto</span><span class="sxs-lookup"><span data-stu-id="1cea0-144">Run a Remote Command</span></span>

<span data-ttu-id="1cea0-145">Para executar um comando em um ou mais computadores, use o cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="1cea0-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="1cea0-146">Por exemplo, para executar um comando [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) nos computadores remotos Server01 e Server02, digite:</span><span class="sxs-lookup"><span data-stu-id="1cea0-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="1cea0-147">O resultado é retornado no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1cea0-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="1cea0-148">Executar um script</span><span class="sxs-lookup"><span data-stu-id="1cea0-148">Run a Script</span></span>

<span data-ttu-id="1cea0-149">Para executar um script em um ou vários computadores remotos, use o parâmetro FilePath do cmdlet `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="1cea0-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="1cea0-150">O script deve estar ativado ou acessível para o computador local.</span><span class="sxs-lookup"><span data-stu-id="1cea0-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="1cea0-151">Os resultados são retornados no computador local.</span><span class="sxs-lookup"><span data-stu-id="1cea0-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="1cea0-152">Por exemplo, o comando a seguir executa o script DiskCollect.ps1 nos computadores remotos Server01 e Server02.</span><span class="sxs-lookup"><span data-stu-id="1cea0-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="1cea0-153">Estabelecer uma conexão persistente</span><span class="sxs-lookup"><span data-stu-id="1cea0-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="1cea0-154">Use o cmdlet `New-PSSession` para criar uma sessão persistente em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="1cea0-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="1cea0-155">O exemplo a seguir cria sessões remotas no Server01 e Server02.</span><span class="sxs-lookup"><span data-stu-id="1cea0-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="1cea0-156">Os objetos de sessão são armazenados na variável `$s`.</span><span class="sxs-lookup"><span data-stu-id="1cea0-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="1cea0-157">Agora que as sessões foram estabelecidas, você pode executar qualquer comando nelas.</span><span class="sxs-lookup"><span data-stu-id="1cea0-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="1cea0-158">E como as sessões são persistentes, você pode coletar dados de um comando e usá-los em outro comando.</span><span class="sxs-lookup"><span data-stu-id="1cea0-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="1cea0-159">Por exemplo, o comando a seguir executa um comando Get-HotFix em sessões na variável $s e salva os resultados na variável $h.</span><span class="sxs-lookup"><span data-stu-id="1cea0-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="1cea0-160">A variável $h é criada em cada uma das sessões em $s, mas não existe na sessão local.</span><span class="sxs-lookup"><span data-stu-id="1cea0-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="1cea0-161">Agora você pode usar os dados na variável `$h` com outros comandos na mesma sessão.</span><span class="sxs-lookup"><span data-stu-id="1cea0-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="1cea0-162">Os resultados são exibidos no computador local.</span><span class="sxs-lookup"><span data-stu-id="1cea0-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="1cea0-163">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1cea0-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="1cea0-164">Comunicação remota avançada</span><span class="sxs-lookup"><span data-stu-id="1cea0-164">Advanced Remoting</span></span>

<span data-ttu-id="1cea0-165">O gerenciamento remoto do Windows PowerShell começa aqui.</span><span class="sxs-lookup"><span data-stu-id="1cea0-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="1cea0-166">Usando os cmdlets instalados com o Windows PowerShell, você pode estabelecer e configurar sessões remotas tanto de extremidades locais quanto remotas, criar sessões personalizadas e restritas, permitir que os usuários importem os comandos de uma sessão remota executado implicitamente na própria sessão remota, configurar a segurança de uma sessão remota e muito mais.</span><span class="sxs-lookup"><span data-stu-id="1cea0-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="1cea0-167">O Windows PowerShell inclui um provedor de WSMan.</span><span class="sxs-lookup"><span data-stu-id="1cea0-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="1cea0-168">O provedor cria uma unidade `WSMAN:` que permite a navegação por uma hierarquia de definições de configuração no computador local e nos computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="1cea0-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="1cea0-169">Para saber mais sobre o provedor WSMan, confira [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) e [Sobre cmdlets WS-Management](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets) ou, no console do Windows PowerShell, digite `Get-Help wsman`.</span><span class="sxs-lookup"><span data-stu-id="1cea0-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="1cea0-170">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="1cea0-170">For more information, see:</span></span>

- [<span data-ttu-id="1cea0-171">Perguntas frequentes sobre comunicação remota</span><span class="sxs-lookup"><span data-stu-id="1cea0-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="1cea0-172">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1cea0-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="1cea0-173">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="1cea0-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="1cea0-174">Para obter ajuda com erros de comunicação remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="1cea0-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="1cea0-175">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="1cea0-175">See Also</span></span>

- [<span data-ttu-id="1cea0-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="1cea0-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="1cea0-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="1cea0-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="1cea0-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="1cea0-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="1cea0-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="1cea0-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="1cea0-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="1cea0-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="1cea0-181">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="1cea0-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="1cea0-182">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="1cea0-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="1cea0-183">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="1cea0-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="1cea0-184">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="1cea0-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="1cea0-185">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1cea0-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="1cea0-186">Provedor WSMan</span><span class="sxs-lookup"><span data-stu-id="1cea0-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md