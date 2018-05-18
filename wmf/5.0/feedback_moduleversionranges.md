---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="cf5b4-102">Suporte aos módulos para declaração dos intervalos de versão (1.\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="cf5b4-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="cf5b4-103">Combinado com **-MinimumVersion**, **-MaximumVersion** agora permite que o usuário obtenha/importe o módulo dentro de um intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="cf5b4-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="cf5b4-104">O parâmetro também oferece suporte para **.**\*.</span><span class="sxs-lookup"><span data-stu-id="cf5b4-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="cf5b4-105">O seguinte exemplo mostra como isso funciona:</span><span class="sxs-lookup"><span data-stu-id="cf5b4-105">The following example shows how it works:</span></span>

<span data-ttu-id="cf5b4-106">Agora, você pode combinar **-MinimumVersion** e **-MaximumVersion** para importar o módulo dentro de um intervalo específico:</span><span class="sxs-lookup"><span data-stu-id="cf5b4-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
