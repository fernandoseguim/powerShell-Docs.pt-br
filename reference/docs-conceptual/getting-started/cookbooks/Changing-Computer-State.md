---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Alterando o estado do computador
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: 636690c72b16bf19826b0a7e54ce00114ce30fb6
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2017
---
# <a name="changing-computer-state"></a><span data-ttu-id="5d4aa-103">Alterando o estado do computador</span><span class="sxs-lookup"><span data-stu-id="5d4aa-103">Changing Computer State</span></span>
<span data-ttu-id="5d4aa-104">Para redefinir um computador no Windows PowerShell, use uma ferramenta de linha de comando padrão ou uma classe WMI.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="5d4aa-105">Embora você esteja usando o Windows PowerShell somente para executar a ferramenta, aprender como alterar o estado de energia do computador no Windows PowerShell ilustra alguns dos detalhes importantes sobre como trabalhar com ferramentas externas no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

### <a name="locking-a-computer"></a><span data-ttu-id="5d4aa-106">Bloquear um computador</span><span class="sxs-lookup"><span data-stu-id="5d4aa-106">Locking a Computer</span></span>
<span data-ttu-id="5d4aa-107">A única maneira de bloquear um computador diretamente com as ferramentas padrão disponíveis é chamar a função **LockWorkstation ()** em **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="5d4aa-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="5d4aa-108">Esse comando bloqueia imediatamente a estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="5d4aa-109">Ele usa o *rundll32.exe*, que executa DLLs Windows (e salva suas bibliotecas para uso repetido) para executar o user32.dll, uma biblioteca de funções de gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="5d4aa-110">Quando você bloqueia uma estação de trabalho enquanto a Troca Rápida de Usuário estiver habilitada, como no Windows XP, o computador exibe a tela de logon do usuário em vez de iniciar a proteção de tela do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="5d4aa-111">Para encerrar uma sessão específica em um Servidor de Terminal, use a ferramenta de linha de comando **tsshutdn.exe**.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

### <a name="logging-off-the-current-session"></a><span data-ttu-id="5d4aa-112">Sair da sessão atual</span><span class="sxs-lookup"><span data-stu-id="5d4aa-112">Logging Off the Current Session</span></span>
<span data-ttu-id="5d4aa-113">Você pode usar várias técnicas diferentes para sair de uma sessão no sistema local.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="5d4aa-114">A maneira mais simples é usar a ferramenta de linha de comando Área de Trabalho Remota/Serviços de Terminal, **logoff.exe** (para obter mais detalhes, no prompt do Windows PowerShell, digite **logoff /?**).</span><span class="sxs-lookup"><span data-stu-id="5d4aa-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="5d4aa-115">Para fazer logoff da sessão ativa atual, digite **logoff** sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="5d4aa-116">Você também pode usar a ferramenta **shutdown.exe** com a opção de fazer logoff:</span><span class="sxs-lookup"><span data-stu-id="5d4aa-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="5d4aa-117">Uma terceira opção é usar o WMI.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-117">A third option is to use WMI.</span></span> <span data-ttu-id="5d4aa-118">A classe Win32_OperatingSystem tem um método Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="5d4aa-119">Chamar o método com o sinalizador 0 inicia o logoff:</span><span class="sxs-lookup"><span data-stu-id="5d4aa-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="5d4aa-120">Para saber mais e para localizar outros recursos do método Win32Shutdown, confira "Método Win32Shutdown da Classe Win32_OperatingSystem" no MSDN.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

### <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="5d4aa-121">Desligar ou reiniciar um computador</span><span class="sxs-lookup"><span data-stu-id="5d4aa-121">Shutting Down or Restarting a Computer</span></span>
<span data-ttu-id="5d4aa-122">Desligar e reiniciar computadores geralmente são os mesmos tipos de tarefa.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="5d4aa-123">Ferramentas que desligam um computador geralmente também o reiniciam e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="5d4aa-124">Há duas opções simples para reiniciar um computador do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="5d4aa-125">Use Tsshutdn.exe ou Shutdown.exe com os argumentos apropriados.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="5d4aa-126">Obtenha informações de uso detalhadas em **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="5d4aa-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="5d4aa-127">ou **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="5d4aa-128">Você também pode executar as operações de desligamento e reinicialização usando **Win32_OperatingSystem** diretamente do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-128">You can also perform shutdown and restart operations by using **Win32_OperatingSystem** directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="5d4aa-129">Para desligar o computador, use o método Win32Shutdown com o sinalizador **1**.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-129">To shut down the computer, use the Win32Shutdown method with the **1** flag.</span></span>

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

<span data-ttu-id="5d4aa-130">Para reiniciar sistema operacional, use o método Win32Shutdown com o sinalizador **2**.</span><span class="sxs-lookup"><span data-stu-id="5d4aa-130">To restart the operating system, use the Win32Shutdown method with the **2** flag.</span></span>

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```

