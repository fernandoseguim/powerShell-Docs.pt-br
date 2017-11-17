---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Executando comandos remotos
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 5cf9690b8fe4549a99186f172cb6f0de156a4dea
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="running-remote-commands"></a><span data-ttu-id="47aa3-103">Executando comandos remotos</span><span class="sxs-lookup"><span data-stu-id="47aa3-103">Running Remote Commands</span></span>
<span data-ttu-id="47aa3-104">Você pode executar comandos em uma ou centenas de computadores com um único comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47aa3-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="47aa3-105">O Windows PowerShell oferece suporte à computação remota usando diversas tecnologias, incluindo WMI, RPC e WS-Management.</span><span class="sxs-lookup"><span data-stu-id="47aa3-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="47aa3-106">Comunicação remota sem configuração</span><span class="sxs-lookup"><span data-stu-id="47aa3-106">Remoting Without Configuration</span></span>
<span data-ttu-id="47aa3-107">Muitos cmdlets do Windows PowerShell têm o parâmetro ComputerName que permite coletar dados e alterar as configurações de um ou mais computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="47aa3-107">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="47aa3-108">Eles usam uma variedade de tecnologias de comunicação e muitos funcionam em todos os sistemas operacionais Windows que oferecem suporte ao Windows PowerShell sem qualquer configuração especial.</span><span class="sxs-lookup"><span data-stu-id="47aa3-108">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="47aa3-109">Esses cmdlets incluem:</span><span class="sxs-lookup"><span data-stu-id="47aa3-109">These cmdlets include:</span></span>
* [<span data-ttu-id="47aa3-110">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="47aa3-110">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="47aa3-111">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="47aa3-111">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="47aa3-112">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="47aa3-112">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="47aa3-113">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="47aa3-113">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="47aa3-114">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="47aa3-114">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
  - [<span data-ttu-id="47aa3-115">Get-Process</span><span class="sxs-lookup"><span data-stu-id="47aa3-115">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="47aa3-116">Get-Service</span><span class="sxs-lookup"><span data-stu-id="47aa3-116">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="47aa3-117">Set-Service</span><span class="sxs-lookup"><span data-stu-id="47aa3-117">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="47aa3-118">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="47aa3-118">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="47aa3-119">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="47aa3-119">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="47aa3-120">Normalmente, os cmdlets que dão suporte à comunicação remota sem configuração especial têm um parâmetro ComputerName, e não um parâmetro Session.</span><span class="sxs-lookup"><span data-stu-id="47aa3-120">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="47aa3-121">Para localizar esses cmdlets em sua sessão, digite:</span><span class="sxs-lookup"><span data-stu-id="47aa3-121">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="47aa3-122">Comunicação remota do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="47aa3-122">Windows PowerShell Remoting</span></span>
<span data-ttu-id="47aa3-123">A comunicação remota do Windows PowerShell, que usa o protocolo WS-Management, permite executar qualquer comando do Windows PowerShell em um ou vários computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="47aa3-123">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="47aa3-124">Ela permite estabelecer conexões persistentes, iniciar sessões interativas 1:1 e executar scripts em vários computadores.</span><span class="sxs-lookup"><span data-stu-id="47aa3-124">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="47aa3-125">Para usar a comunicação remota do Windows PowerShell, o computador remoto deve ser configurado para gerenciamento remoto.</span><span class="sxs-lookup"><span data-stu-id="47aa3-125">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="47aa3-126">Para obter mas informações, incluindo instruções consulte [Sobre requisitos remotos](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="47aa3-126">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="47aa3-127">Depois de configurar a comunicação remota do Windows PowerShell, muitas estratégias de comunicação remota estão disponíveis para você.</span><span class="sxs-lookup"><span data-stu-id="47aa3-127">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="47aa3-128">O restante deste documento lista apenas algumas delas.</span><span class="sxs-lookup"><span data-stu-id="47aa3-128">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="47aa3-129">Para obter mais informações, confira [about_Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) e [Perguntas frequentes sobre about_Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="47aa3-129">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="47aa3-130">Iniciar uma sessão interativa</span><span class="sxs-lookup"><span data-stu-id="47aa3-130">Start an Interactive Session</span></span>
<span data-ttu-id="47aa3-131">Para iniciar uma sessão interativa com um único computador remoto, use o cmdlet [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477).</span><span class="sxs-lookup"><span data-stu-id="47aa3-131">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="47aa3-132">Por exemplo, para iniciar uma sessão interativa com o computador remoto Server01, digite:</span><span class="sxs-lookup"><span data-stu-id="47aa3-132">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="47aa3-133">O prompt de comando muda para exibir o nome do computador ao qual você está conectado.</span><span class="sxs-lookup"><span data-stu-id="47aa3-133">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="47aa3-134">Daí em diante, os comandos digitados no prompt são executados no computador remoto e os resultados são exibidos no computador local.</span><span class="sxs-lookup"><span data-stu-id="47aa3-134">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="47aa3-135">Para encerrar a sessão interativa, digite:</span><span class="sxs-lookup"><span data-stu-id="47aa3-135">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="47aa3-136">Para saber mais sobre os cmdlets Enter-PSSession e Exit-PSSession, confira [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) e [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="47aa3-136">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="47aa3-137">Executar um comando remoto</span><span class="sxs-lookup"><span data-stu-id="47aa3-137">Run a Remote Command</span></span>
<span data-ttu-id="47aa3-138">Para executar qualquer comando em um ou vários computadores remotos, use o cmdlet [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="47aa3-138">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="47aa3-139">Por exemplo, para executar um comando [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) nos computadores remotos Server01 e Server02, digite:</span><span class="sxs-lookup"><span data-stu-id="47aa3-139">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="47aa3-140">O resultado é retornado no seu computador.</span><span class="sxs-lookup"><span data-stu-id="47aa3-140">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="47aa3-141">Para saber mais sobre o cmdlet Invoke-Command, confira [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="47aa3-141">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="47aa3-142">Executar um script</span><span class="sxs-lookup"><span data-stu-id="47aa3-142">Run a Script</span></span>
<span data-ttu-id="47aa3-143">Para executar um script em um ou vários computadores remotos, use o parâmetro FilePath do cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="47aa3-143">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="47aa3-144">O script deve estar ativado ou acessível para o computador local.</span><span class="sxs-lookup"><span data-stu-id="47aa3-144">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="47aa3-145">Os resultados são retornados no computador local.</span><span class="sxs-lookup"><span data-stu-id="47aa3-145">The results are returned to your local computer.</span></span>

<span data-ttu-id="47aa3-146">Por exemplo, o comando a seguir executa o script DiskCollect.ps1 nos computadores remotos Server01 e Server02.</span><span class="sxs-lookup"><span data-stu-id="47aa3-146">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="47aa3-147">Para saber mais sobre o cmdlet Invoke-Command, confira [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="47aa3-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="47aa3-148">Estabelecer uma conexão persistente</span><span class="sxs-lookup"><span data-stu-id="47aa3-148">Establish a Persistent Connection</span></span>
<span data-ttu-id="47aa3-149">Para executar uma série de comandos relacionados que compartilham dados, crie uma sessão no computador remoto e, em seguida, use o cmdlet Invoke-Command para executar comandos na sessão que você criou.</span><span class="sxs-lookup"><span data-stu-id="47aa3-149">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="47aa3-150">Para criar uma sessão remota, use o cmdlet New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="47aa3-150">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="47aa3-151">Por exemplo, o comando a seguir cria uma sessão remota no computador Server01 e outra sessão remota no computador Server02.</span><span class="sxs-lookup"><span data-stu-id="47aa3-151">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="47aa3-152">Ele salva os objetos da sessão na variável $s.</span><span class="sxs-lookup"><span data-stu-id="47aa3-152">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="47aa3-153">Agora que as sessões foram estabelecidas, você pode executar qualquer comando nelas.</span><span class="sxs-lookup"><span data-stu-id="47aa3-153">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="47aa3-154">E como as sessões são persistentes, você pode coletar dados em um comando e usá-los em um comando subsequente.</span><span class="sxs-lookup"><span data-stu-id="47aa3-154">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="47aa3-155">Por exemplo, o comando a seguir executa um comando Get-HotFix em sessões na variável $s e salva os resultados na variável $h.</span><span class="sxs-lookup"><span data-stu-id="47aa3-155">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="47aa3-156">A variável $h é criada em cada uma das sessões em $s, mas não existe na sessão local.</span><span class="sxs-lookup"><span data-stu-id="47aa3-156">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="47aa3-157">Agora você pode usar os dados na variável $h em comandos subsequentes, como mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="47aa3-157">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="47aa3-158">Os resultados são exibidos no computador local.</span><span class="sxs-lookup"><span data-stu-id="47aa3-158">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="47aa3-159">Comunicação remota avançada</span><span class="sxs-lookup"><span data-stu-id="47aa3-159">Advanced Remoting</span></span>
<span data-ttu-id="47aa3-160">O gerenciamento remoto do Windows PowerShell começa aqui.</span><span class="sxs-lookup"><span data-stu-id="47aa3-160">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="47aa3-161">Usando os cmdlets instalados com o Windows PowerShell, você pode estabelecer e configurar sessões remotas tanto de extremidades locais quanto remotas, criar sessões personalizadas e restritas, permitir que os usuários importem os comandos de uma sessão remota executado implicitamente na própria sessão remota, configurar a segurança de uma sessão remota e muito mais.</span><span class="sxs-lookup"><span data-stu-id="47aa3-161">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="47aa3-162">Para facilitar a configuração remota, o Windows PowerShell inclui um provedor WSMan.</span><span class="sxs-lookup"><span data-stu-id="47aa3-162">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="47aa3-163">A unidade WSMAN: criada pelo provedor permite navegar por uma hierarquia de definições de configuração no computador local e nos computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="47aa3-163">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="47aa3-164">Para saber mais sobre o provedor WSMan, confira [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) e [about_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx) ou, no console do Windows PowerShell, digite "Get-Help wsman".</span><span class="sxs-lookup"><span data-stu-id="47aa3-164">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="47aa3-165">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="47aa3-165">For more information, see:</span></span>
- [<span data-ttu-id="47aa3-166">Perguntas frequentes sobre comunicação remota</span><span class="sxs-lookup"><span data-stu-id="47aa3-166">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="47aa3-167">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="47aa3-167">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="47aa3-168">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="47aa3-168">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="47aa3-169">Para obter ajuda com erros de comunicação remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="47aa3-169">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="47aa3-170">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="47aa3-170">See Also</span></span>
- [<span data-ttu-id="47aa3-171">about_Remote</span><span class="sxs-lookup"><span data-stu-id="47aa3-171">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="47aa3-172">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="47aa3-172">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="47aa3-173">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="47aa3-173">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="47aa3-174">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="47aa3-174">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="47aa3-175">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="47aa3-175">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="47aa3-176">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="47aa3-176">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="47aa3-177">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="47aa3-177">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="47aa3-178">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="47aa3-178">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="47aa3-179">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="47aa3-179">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="47aa3-180">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="47aa3-180">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="47aa3-181">Provedor WSMan</span><span class="sxs-lookup"><span data-stu-id="47aa3-181">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)
