---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: fa972b68015d9b6e14508ccda562cfa5ebd632ac
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2017
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="b2935-102">Suporte aos módulos para declaração dos intervalos de versão (1.*, etc.)</span><span class="sxs-lookup"><span data-stu-id="b2935-102">Modules support for declaring version ranges (1.*, etc)</span></span>
<span data-ttu-id="b2935-103">Combinado com **-MinimumVersion**, **-MaximumVersion** agora permite que o usuário obtenha/importe o módulo dentro de um intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="b2935-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="b2935-104">O parâmetro também dá suporte a **.***.</span><span class="sxs-lookup"><span data-stu-id="b2935-104">The parameter also support **.***.</span></span> <span data-ttu-id="b2935-105">O seguinte exemplo mostra como isso funciona:</span><span class="sxs-lookup"><span data-stu-id="b2935-105">The following example shows how it works:</span></span>

```powershell
Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:

PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

