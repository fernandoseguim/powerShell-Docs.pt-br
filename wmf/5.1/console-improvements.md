---
title: Melhorias do Console no WMF 5.1 (Preview)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 574fec8e1f4948021988d8489532d7325277fed6
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: pt-BR
---
# <a name="console-improvements-in-wmf-51-preview"></a><span data-ttu-id="0f2ce-103">Melhorias do Console no WMF 5.1 (Preview)</span><span class="sxs-lookup"><span data-stu-id="0f2ce-103">Console Improvements in WMF 5.1 (Preview)</span></span>#

## <a name="powershell-console-improvements"></a><span data-ttu-id="0f2ce-104">Melhorias do console do PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f2ce-104">PowerShell console improvements</span></span>

<span data-ttu-id="0f2ce-105">As seguintes alterações foram feitas ao powershell.exe no WMF 5.1 para melhorar a experiência do console:</span><span class="sxs-lookup"><span data-stu-id="0f2ce-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

###<a name="vt100-support"></a><span data-ttu-id="0f2ce-106">Suporte a VT100</span><span class="sxs-lookup"><span data-stu-id="0f2ce-106">VT100 support</span></span>

<span data-ttu-id="0f2ce-107">O Windows 10 adicionou suporte para [sequências de escape VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="0f2ce-107">Windows 10 added support for [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span></span>
<span data-ttu-id="0f2ce-108">PowerShell ignorará determinadas sequências de escape de formatação do VT100 ao calcular larguras da tabela.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="0f2ce-109">O PowerShell também adicionou uma nova API que pode ser usada no código de formatação para determinar se há suporte para VT100.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="0f2ce-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0f2ce-110">For example:</span></span>

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
<span data-ttu-id="0f2ce-111">Aqui está um [exemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo que pode ser usado para realçar correspondências de Select-String.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from Select-String.</span></span>
<span data-ttu-id="0f2ce-112">Salve o exemplo em um arquivo chamado `MatchInfo.format.ps1xml`, então, para usá-lo em seu perfil ou em outro local, execute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="0f2ce-113">Observe que as sequências de escape do VT100 têm suporte apenas a partir da atualização de Aniversário do Windows 10; elas não têm suporte em sistemas anteriores.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>   

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="0f2ce-114">Suporte ao modo vi em PSReadline</span><span class="sxs-lookup"><span data-stu-id="0f2ce-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="0f2ce-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adiciona suporte para o modo vi.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="0f2ce-116">Para usar o modo vi, execute `Set-PSReadline -EditMode vi`.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-116">To use vi mode, run `Set-PSReadline -EditMode vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="0f2ce-117">STDIN redirecionada com entrada interativa</span><span class="sxs-lookup"><span data-stu-id="0f2ce-117">Redirected stdin with interactive input</span></span> 

<span data-ttu-id="0f2ce-118">Em versões anteriores, iniciar o PowerShell com `powershell -File -` era necessário quando stdin era redirecionado e você queria inserir comandos interativamente.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="0f2ce-119">Com o WMF 5.1, essa opção difícil de descobrir não é mais necessária.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="0f2ce-120">Você pode iniciar o PowerShell sem nenhuma opção, por exemplo, `powershell`.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="0f2ce-121">Observe que, atualmente, o PSReadline não dá suporte à STDIN redirecionada, e a experiência de edição de linha de comando interna com STDIN redirecionada é extremamente limitada, por exemplo, as teclas de direção não funcionam.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="0f2ce-122">Uma versão futura do PSReadline deve resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-122">A future release of PSReadline should address this issue.</span></span>   
