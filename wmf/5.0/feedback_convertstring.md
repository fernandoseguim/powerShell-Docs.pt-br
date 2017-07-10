---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="convert-string" class="xliff"></a>
# Convert-String
**Convert-String** expõe a funcionalidade “replace by magic”. Forneça exemplos do tipo “antes e depois” de como deseja que o texto se assemelhe, e **Convert-String** formatará o texto automaticamente. Aqui está uma demonstração: usar o nome e sobrenome de alguém e substituí-lo pelo sobrenome, uma vírgula, a primeira inicial do sobrenome e um ponto. Experimente com um regex e veja quanto tempo isso leva.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

