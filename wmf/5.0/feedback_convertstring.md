---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="convert-string"></a><span data-ttu-id="52894-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="52894-102">Convert-String</span></span>
<span data-ttu-id="52894-103">**Convert-String** expõe a funcionalidade “replace by magic”.</span><span class="sxs-lookup"><span data-stu-id="52894-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="52894-104">Forneça exemplos do tipo “antes e depois” de como deseja que o texto se assemelhe, e **Convert-String** formatará o texto automaticamente.</span><span class="sxs-lookup"><span data-stu-id="52894-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="52894-105">Aqui está uma demonstração: usar o nome e sobrenome de alguém e substituí-lo pelo sobrenome, uma vírgula, a primeira inicial do sobrenome e um ponto.</span><span class="sxs-lookup"><span data-stu-id="52894-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="52894-106">Experimente com um regex e veja quanto tempo isso leva.</span><span class="sxs-lookup"><span data-stu-id="52894-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
