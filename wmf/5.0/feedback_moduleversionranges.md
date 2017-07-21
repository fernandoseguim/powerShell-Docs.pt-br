---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: b64464eb2b4dd87ebe716e159fb916ac328b3b37
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="831c7-102">Suporte aos módulos para declaração dos intervalos de versão (1.*, etc.)</span><span class="sxs-lookup"><span data-stu-id="831c7-102">Modules support for declaring version ranges (1.*, etc)</span></span>
<span data-ttu-id="831c7-103">Combinado com **-MinimumVersion**, **-MaximumVersion** agora permite que o usuário obtenha/importe o módulo dentro de um intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="831c7-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="831c7-104">O parâmetro também dá suporte a **.***.</span><span class="sxs-lookup"><span data-stu-id="831c7-104">The parameter also support **.***.</span></span> <span data-ttu-id="831c7-105">O seguinte exemplo mostra como isso funciona:</span><span class="sxs-lookup"><span data-stu-id="831c7-105">The following example shows how it works:</span></span>

```PowerShell
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

