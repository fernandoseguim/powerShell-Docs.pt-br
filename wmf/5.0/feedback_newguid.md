---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="new-guid"></a>New-Guid
Geralmente, um script (ou talvez a escrita de um recurso DSC) exige um identificador exclusivo. GUIDs funcionam bem, e é fácil chamar a classe Guid do .NET Framework para gerar um; no entanto, ter um cmdlet faz com que isso seja mais detectável para os usuários finais que não ainda estão familiarizados com a classe do .NET Framework:

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
