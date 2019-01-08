---
ms.date: 11/13/2018
keywords: powershell, cmdlet
title: Decodificar um comando do PowerShell por meio de um processo em execução
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400140"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="ad3b5-103">Decodificar um comando do PowerShell por meio de um processo em execução</span><span class="sxs-lookup"><span data-stu-id="ad3b5-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="ad3b5-104">Às vezes, você pode ter um processo em execução que está ocupando uma grande quantidade de recursos do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="ad3b5-105">Esse processo pode ser executado no contexto de um [Agendador de tarefas][] trabalho ou um [SQL Server Agent][] trabalho.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="ad3b5-106">Onde há vários processos do PowerShell em execução, pode ser difícil saber o processo que representa o problema.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="ad3b5-107">Este artigo mostra como decodificar um bloco de script que um processo do PowerShell está em execução.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="ad3b5-108">Criar um processo de execução longa</span><span class="sxs-lookup"><span data-stu-id="ad3b5-108">Create a long running process</span></span>

<span data-ttu-id="ad3b5-109">Para demonstrar esse cenário, abra uma nova janela do PowerShell e execute o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="ad3b5-110">Ele executa um comando do PowerShell que gera um número a cada minuto por 10 minutos.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a><span data-ttu-id="ad3b5-111">O processo de exibição</span><span class="sxs-lookup"><span data-stu-id="ad3b5-111">View the process</span></span>

<span data-ttu-id="ad3b5-112">O corpo do comando que o PowerShell está em execução é armazenado na **CommandLine** propriedade da [Win32_Process][] classe.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="ad3b5-113">Se o comando for um [codificada de comando][], o **CommandLine** propriedade contém a cadeia de caracteres "EncodedCommand".</span><span class="sxs-lookup"><span data-stu-id="ad3b5-113">If the command is an [encoded command][], the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="ad3b5-114">Usando essas informações, o comando codificado pode ser revelado por meio do processo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="ad3b5-115">Inicie o PowerShell como administrador.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="ad3b5-116">É essencial que o PowerShell está em execução como administrador, caso contrário, nenhum resultado é retornado ao consultar os processos em execução.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="ad3b5-117">Execute o comando a seguir para obter todos os processos do PowerShell que têm um comando codificado:</span><span class="sxs-lookup"><span data-stu-id="ad3b5-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="ad3b5-118">O comando a seguir cria um objeto personalizado do PowerShell que contém a ID de processo e o comando codificado.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

<span data-ttu-id="ad3b5-119">Agora, o comando codificado pode ser decodificado.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="ad3b5-120">O trecho a seguir efetua iterações sobre o objeto de detalhes do comando, decodifica o comando codificado e adiciona o comando decodificado volta para o objeto para uma investigação adicional.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

<span data-ttu-id="ad3b5-121">O comando decodificado agora pode ser analisado, selecionando a propriedade command decodificada.</span><span class="sxs-lookup"><span data-stu-id="ad3b5-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Agendador de Tarefas]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[codificada de comando]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
[encoded command]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
