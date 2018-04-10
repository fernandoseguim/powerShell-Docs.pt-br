---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: b440ea4a8208d5c576fa566a19e2de377bf5f475
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="31516-102">Rastreamento e registro de scripts</span><span class="sxs-lookup"><span data-stu-id="31516-102">Script Tracing and Logging</span></span>

<span data-ttu-id="31516-103">Embora o Windows PowerShell já tenha a configuração **LogPipelineExecutionDetails** da Política de Grupo para registrar em log a invocação de cmdlets, a linguagem de scripts do PowerShell traz vários recursos que talvez você queira registrar em log e/ou auditar.</span><span class="sxs-lookup"><span data-stu-id="31516-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="31516-104">O novo recurso de Rastreamento de Script Detalhado permite habilitar o acompanhamento detalhado e a análise de uso de scripts do Windows PowerShell em um sistema.</span><span class="sxs-lookup"><span data-stu-id="31516-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="31516-105">Depois de habilitar o rastreamento de script detalhado, o Windows PowerShell registra em log todos os blocos de script no log de eventos do ETW, **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="31516-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="31516-106">Caso um bloco de script crie outro bloco de script (por exemplo, um script que chama o cmdlet Invoke-Expression em uma cadeia de caracteres), esse bloco de script resultante também será registrado em log.</span><span class="sxs-lookup"><span data-stu-id="31516-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="31516-107">O registro desses eventos pode ser habilitado por meio da configuração **Ativar Registro de Bloco de Script do PowerShell** da Política de Grupo (em Modelos Administrativos -> Componentes do Windows -> Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="31516-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="31516-108">Os eventos são:</span><span class="sxs-lookup"><span data-stu-id="31516-108">The events are:</span></span>

| <span data-ttu-id="31516-109">Canal</span><span class="sxs-lookup"><span data-stu-id="31516-109">Channel</span></span> | <span data-ttu-id="31516-110">Operacional</span><span class="sxs-lookup"><span data-stu-id="31516-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="31516-111">Nível</span><span class="sxs-lookup"><span data-stu-id="31516-111">Level</span></span>   | <span data-ttu-id="31516-112">Verbose</span><span class="sxs-lookup"><span data-stu-id="31516-112">Verbose</span></span>                                     |
| <span data-ttu-id="31516-113">Opcode</span><span class="sxs-lookup"><span data-stu-id="31516-113">Opcode</span></span>  | <span data-ttu-id="31516-114">Criar</span><span class="sxs-lookup"><span data-stu-id="31516-114">Create</span></span>                                      |
| <span data-ttu-id="31516-115">Tarefa</span><span class="sxs-lookup"><span data-stu-id="31516-115">Task</span></span>    | <span data-ttu-id="31516-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="31516-116">CommandStart</span></span>                                |
| <span data-ttu-id="31516-117">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="31516-117">Keyword</span></span> | <span data-ttu-id="31516-118">Runspace</span><span class="sxs-lookup"><span data-stu-id="31516-118">Runspace</span></span>                                    |
| <span data-ttu-id="31516-119">EventId</span><span class="sxs-lookup"><span data-stu-id="31516-119">EventId</span></span> | <span data-ttu-id="31516-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="31516-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="31516-121">Mensagem</span><span class="sxs-lookup"><span data-stu-id="31516-121">Message</span></span> | <span data-ttu-id="31516-122">Criando texto Scriptblock (%1 de %2):</span><span class="sxs-lookup"><span data-stu-id="31516-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="31516-123">%3</span><span class="sxs-lookup"><span data-stu-id="31516-123">%3</span></span> </br> <span data-ttu-id="31516-124">ID de ScriptBlock: %4</span><span class="sxs-lookup"><span data-stu-id="31516-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="31516-125">O texto inserido na mensagem é a extensão do bloco de script compilado.</span><span class="sxs-lookup"><span data-stu-id="31516-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="31516-126">A ID é um GUID que é retido durante o ciclo de vida do bloco de script.</span><span class="sxs-lookup"><span data-stu-id="31516-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="31516-127">Ao habilitar o registro detalhado, o recurso escreve marcadores de início e de fim:</span><span class="sxs-lookup"><span data-stu-id="31516-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="31516-128">Canal</span><span class="sxs-lookup"><span data-stu-id="31516-128">Channel</span></span> | <span data-ttu-id="31516-129">Operacional</span><span class="sxs-lookup"><span data-stu-id="31516-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="31516-130">Nível</span><span class="sxs-lookup"><span data-stu-id="31516-130">Level</span></span>   | <span data-ttu-id="31516-131">Verbose</span><span class="sxs-lookup"><span data-stu-id="31516-131">Verbose</span></span>                                                |
| <span data-ttu-id="31516-132">Opcode</span><span class="sxs-lookup"><span data-stu-id="31516-132">Opcode</span></span>  | <span data-ttu-id="31516-133">Abrir (/ Fechar)</span><span class="sxs-lookup"><span data-stu-id="31516-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="31516-134">Tarefa</span><span class="sxs-lookup"><span data-stu-id="31516-134">Task</span></span>    | <span data-ttu-id="31516-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="31516-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="31516-136">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="31516-136">Keyword</span></span> | <span data-ttu-id="31516-137">Runspace</span><span class="sxs-lookup"><span data-stu-id="31516-137">Runspace</span></span>                                               |
| <span data-ttu-id="31516-138">EventId</span><span class="sxs-lookup"><span data-stu-id="31516-138">EventId</span></span> | <span data-ttu-id="31516-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="31516-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="31516-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="31516-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="31516-141">Mensagem</span><span class="sxs-lookup"><span data-stu-id="31516-141">Message</span></span> | <span data-ttu-id="31516-142">Iniciada (/ Concluída) a invocação da ID do ScriptBlock: %1</span><span class="sxs-lookup"><span data-stu-id="31516-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="31516-143">Runspace ID: %2</span><span class="sxs-lookup"><span data-stu-id="31516-143">Runspace ID: %2</span></span> |

<span data-ttu-id="31516-144">A ID é o GUID que representa o bloco de script (que pode ser correlacionado com a ID de evento 0x1008), e a ID do Runspace representa o runspace no qual este bloco de script foi executado.</span><span class="sxs-lookup"><span data-stu-id="31516-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="31516-145">Sinais de porcentagem na mensagem de invocação representam propriedades estruturadas do ETW.</span><span class="sxs-lookup"><span data-stu-id="31516-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="31516-146">Embora eles sejam substituídos pelos valores reais no texto da mensagem, uma maneira mais robusta de acessá-los é recuperar a mensagem com o cmdlet Get-WinEvent e depois usar a matriz **Properties** da mensagem.</span><span class="sxs-lookup"><span data-stu-id="31516-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="31516-147">Aqui está um exemplo de como essa funcionalidade pode ajudar a descodificar uma tentativa mal-intencionada de criptografar e ocultar um script:</span><span class="sxs-lookup"><span data-stu-id="31516-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="31516-148">A execução disso gera as seguintes entradas de log:</span><span class="sxs-lookup"><span data-stu-id="31516-148">Running this generates the following log entries:</span></span>

```
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Caso o tamanho do bloco de script exceda o que o ETW pode reter em um único evento, o Windows PowerShell interromperá o script em várias partes. <span data-ttu-id="31516-150">Aqui está o código de exemplo para recombinar um script desde suas mensagens de log:</span><span class="sxs-lookup"><span data-stu-id="31516-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="31516-151">Assim como acontece com todos os sistemas de registro que têm um buffer de retenção limitado (ou seja, logs do ETW), um ataque contra essa infraestrutura seria inundar o log com eventos diferentes para ocultar a evidência anterior.</span><span class="sxs-lookup"><span data-stu-id="31516-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="31516-152">Para se proteger contra esse ataque, verifique se você tem alguma forma de coleção de log de eventos configurada (ou seja, Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) para mover os logs de eventos para fora do computador assim que possível.</span><span class="sxs-lookup"><span data-stu-id="31516-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) to move event logs off of the computer as soon as possible.</span></span>