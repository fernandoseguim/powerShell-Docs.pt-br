---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217984"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Às vezes, em seus scripts, é necessário criar um arquivo temporário. Você pode isso com facilidade com o cmdlet **New-TemporaryFile**:

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp
