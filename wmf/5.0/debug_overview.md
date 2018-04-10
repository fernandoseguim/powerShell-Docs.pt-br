---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: dee5e8206c61d79faadf8573a82c74d4ac0fb8e0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="2ec43-102">Melhorias na depuração de script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ec43-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="2ec43-103">Várias melhorias foram feitas no PowerShell 5.0 a fim de aprimorar a experiência de depuração:</span><span class="sxs-lookup"><span data-stu-id="2ec43-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="2ec43-104">Interromper Tudo</span><span class="sxs-lookup"><span data-stu-id="2ec43-104">Break All</span></span>

<span data-ttu-id="2ec43-105">O console do PowerShell e o ISE do Windows PowerShell agora permitem que você interrompa o depurador para executar scripts.</span><span class="sxs-lookup"><span data-stu-id="2ec43-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="2ec43-106">Isso funciona em sessões locais e remotas.</span><span class="sxs-lookup"><span data-stu-id="2ec43-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="2ec43-107">No console, pressione **Ctrl+Break**.</span><span class="sxs-lookup"><span data-stu-id="2ec43-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="2ec43-108">No ISE, pressione **Ctrl+B** ou use o comando de menu **Depurar -> Interromper Tudo**.</span><span class="sxs-lookup"><span data-stu-id="2ec43-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="2ec43-109">Depuração remota e edição de arquivos remota no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ec43-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="2ec43-110">O ISE do Windows PowerShell agora permite abrir e editar arquivos em uma sessão remota com a execução do comando PSEdit.</span><span class="sxs-lookup"><span data-stu-id="2ec43-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="2ec43-111">Por exemplo, é possível abrir um arquivo para edição desde a linha de comando em uma sessão remota da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2ec43-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="2ec43-112">Além disso, agora é possível editar e salvar alterações em um arquivo remoto aberto automaticamente no ISE do Windows PowerShell ao atingir um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="2ec43-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="2ec43-113">Agora, você pode depurar um arquivo de script que está em execução em um computador remoto, editar o arquivo para corrigir um erro e executar novamente o script modificado.</span><span class="sxs-lookup"><span data-stu-id="2ec43-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="2ec43-114">Depuração de script avançada</span><span class="sxs-lookup"><span data-stu-id="2ec43-114">Advanced Script Debugging</span></span>

<span data-ttu-id="2ec43-115">Há novos e avançados recursos de depuração que permitem anexar a qualquer processo de computador local que tenha carregado o Windows PowerShell e depurar runspaces arbitrários no processo.</span><span class="sxs-lookup"><span data-stu-id="2ec43-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="2ec43-116">Depuração de runspaces</span><span class="sxs-lookup"><span data-stu-id="2ec43-116">Runspace Debugging</span></span>

<span data-ttu-id="2ec43-117">Foram adicionados novos cmdlets que permitem listar os runspaces atuais em um processo e anexar o console do Windows PowerShell ou o depurador do ISE a esse runspace para a depuração de script:</span><span class="sxs-lookup"><span data-stu-id="2ec43-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="2ec43-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="2ec43-118">Get-Runspace</span></span>
-   <span data-ttu-id="2ec43-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="2ec43-119">Debug-Runspace</span></span>
-   <span data-ttu-id="2ec43-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2ec43-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="2ec43-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2ec43-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="2ec43-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2ec43-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="2ec43-123">Anexar a um processo que hospeda o PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ec43-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="2ec43-124">Agora é possível anexar a qualquer processo de computador que tenha o Windows PowerShell carregado.</span><span class="sxs-lookup"><span data-stu-id="2ec43-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="2ec43-125">É possível fazer isso entrando em uma sessão interativa com o processo, de forma semelhante a como você entra em uma sessão remota interativa executando o cmdlet Enter-PSSession:</span><span class="sxs-lookup"><span data-stu-id="2ec43-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="2ec43-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="2ec43-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="2ec43-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="2ec43-127">Exit-PSHostProcess</span></span>