---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 302a347b0f4c9c322f7701e8d6a721f9ffba9b59
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="convert-string"></a>Convert-String
**Convert-String** expõe a funcionalidade “replace by magic”. Forneça exemplos do tipo “antes e depois” de como deseja que o texto se assemelhe, e **Convert-String** formatará o texto automaticamente. Aqui está uma demonstração: usar o nome e sobrenome de alguém e substituí-lo pelo sobrenome, uma vírgula, a primeira inicial do sobrenome e um ponto. Experimente com um regex e veja quanto tempo isso leva.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```