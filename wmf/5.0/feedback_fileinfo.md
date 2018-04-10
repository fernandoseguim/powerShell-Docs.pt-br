---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 6356902193fc6ec651b2f7e53f8885cb59f17542
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="updates-to-fileinfo-object"></a>Atualizações ao objeto FileInfo
Informações de versão do arquivo podem ser confusas, especialmente nos casos em que foi aplicado patch ao arquivo. Esta versão do WMF 5.0 adiciona novas propriedades de script **FileVersionRaw** e **ProductVersionRaw** a objetos FileInfo. Aqui estão as propriedades conforme exibidas para powershell.exe (supondo que $pid é a ID do processo do PowerShell):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117