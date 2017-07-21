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
# <a name="convert-string"></a><span data-ttu-id="b5c3a-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="b5c3a-102">Convert-String</span></span>
<span data-ttu-id="b5c3a-103">**Convert-String** expõe a funcionalidade “replace by magic”.</span><span class="sxs-lookup"><span data-stu-id="b5c3a-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="b5c3a-104">Forneça exemplos do tipo “antes e depois” de como deseja que o texto se assemelhe, e **Convert-String** formatará o texto automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b5c3a-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="b5c3a-105">Aqui está uma demonstração: usar o nome e sobrenome de alguém e substituí-lo pelo sobrenome, uma vírgula, a primeira inicial do sobrenome e um ponto.</span><span class="sxs-lookup"><span data-stu-id="b5c3a-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="b5c3a-106">Experimente com um regex e veja quanto tempo isso leva.</span><span class="sxs-lookup"><span data-stu-id="b5c3a-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

