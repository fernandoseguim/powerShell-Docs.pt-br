---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 89e908969641afd9ad9541dcfedcc8eb6315d07c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="280b1-102">Suporte aos módulos para declaração dos intervalos de versão (1.\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="280b1-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="280b1-103">Combinado com **-MinimumVersion**, **-MaximumVersion** agora permite que o usuário obtenha/importe o módulo dentro de um intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="280b1-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="280b1-104">O parâmetro também dá suporte **.** \*.</span><span class="sxs-lookup"><span data-stu-id="280b1-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="280b1-105">O seguinte exemplo mostra como isso funciona:</span><span class="sxs-lookup"><span data-stu-id="280b1-105">The following example shows how it works:</span></span>

<span data-ttu-id="280b1-106">Agora, você pode combinar **- MinimumVersion** e **- MaximumVersion** para importar o módulo dentro de um intervalo específico:</span><span class="sxs-lookup"><span data-stu-id="280b1-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
