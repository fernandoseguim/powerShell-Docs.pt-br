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
# <a name="convert-string"></a><span data-ttu-id="36821-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="36821-102">Convert-String</span></span>
<span data-ttu-id="36821-103">**Convert-String** expõe a funcionalidade “replace by magic”.</span><span class="sxs-lookup"><span data-stu-id="36821-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="36821-104">Forneça exemplos do tipo “antes e depois” de como deseja que o texto se assemelhe, e **Convert-String** formatará o texto automaticamente.</span><span class="sxs-lookup"><span data-stu-id="36821-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="36821-105">Aqui está uma demonstração: usar o nome e sobrenome de alguém e substituí-lo pelo sobrenome, uma vírgula, a primeira inicial do sobrenome e um ponto.</span><span class="sxs-lookup"><span data-stu-id="36821-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="36821-106">Experimente com um regex e veja quanto tempo isso leva.</span><span class="sxs-lookup"><span data-stu-id="36821-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```