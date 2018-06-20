---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225480"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="7b07e-102">Declarar a interface implementada</span><span class="sxs-lookup"><span data-stu-id="7b07e-102">Declare Implemented Interface</span></span>

<span data-ttu-id="7b07e-103">Será possível declarar interfaces implementadas após tipos base, ou imediatamente após dois-pontos (:), se não houver nenhum tipo base especificado.</span><span class="sxs-lookup"><span data-stu-id="7b07e-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="7b07e-104">Separe todos os nomes de tipo usando vírgulas.</span><span class="sxs-lookup"><span data-stu-id="7b07e-104">Separate all type names by using commas.</span></span> <span data-ttu-id="7b07e-105">Isso é muito semelhante à sintaxe do C#.</span><span class="sxs-lookup"><span data-stu-id="7b07e-105">It’s very similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```
