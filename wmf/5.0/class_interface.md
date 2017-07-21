---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: e503f9a4462e94fce42ffcdcc0976d261c051f87
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="e0f9e-102">Declarar a interface implementada</span><span class="sxs-lookup"><span data-stu-id="e0f9e-102">Declare Implemented Interface</span></span>

<span data-ttu-id="e0f9e-103">Será possível declarar interfaces implementadas após tipos base, ou imediatamente após dois-pontos (:), se não houver nenhum tipo base especificado.</span><span class="sxs-lookup"><span data-stu-id="e0f9e-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="e0f9e-104">Separe todos os nomes de tipo usando vírgulas.</span><span class="sxs-lookup"><span data-stu-id="e0f9e-104">Separate all type names by using commas.</span></span> <span data-ttu-id="e0f9e-105">Isso é muito semelhante à sintaxe do C#.</span><span class="sxs-lookup"><span data-stu-id="e0f9e-105">It’s very similar to C# syntax.</span></span>

```PowerShell
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

