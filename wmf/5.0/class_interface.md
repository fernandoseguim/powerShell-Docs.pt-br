---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="c5531-102">Declarar a interface implementada</span><span class="sxs-lookup"><span data-stu-id="c5531-102">Declare Implemented Interface</span></span>

<span data-ttu-id="c5531-103">Será possível declarar interfaces implementadas após tipos base, ou imediatamente após dois-pontos (:), se não houver nenhum tipo base especificado.</span><span class="sxs-lookup"><span data-stu-id="c5531-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="c5531-104">Separe todos os nomes de tipo usando vírgulas.</span><span class="sxs-lookup"><span data-stu-id="c5531-104">Separate all type names by using commas.</span></span> <span data-ttu-id="c5531-105">Isso é muito semelhante à sintaxe do C#.</span><span class="sxs-lookup"><span data-stu-id="c5531-105">It’s very similar to C# syntax.</span></span>

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