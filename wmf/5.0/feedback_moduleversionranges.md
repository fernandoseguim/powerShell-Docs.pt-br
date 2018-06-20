---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225684"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Suporte aos módulos para declaração dos intervalos de versão (1.*, etc.)
Combinado com **-MinimumVersion**, **-MaximumVersion** agora permite que o usuário obtenha/importe o módulo dentro de um intervalo específico. O parâmetro também oferece suporte para **.**\*. O seguinte exemplo mostra como isso funciona:

Agora, você pode combinar **-MinimumVersion** e **-MaximumVersion** para importar o módulo dentro de um intervalo específico:

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
