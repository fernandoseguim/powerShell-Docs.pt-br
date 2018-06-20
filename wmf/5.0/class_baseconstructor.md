---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225599"
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="5f063-102">Chamar o construtor de classe base</span><span class="sxs-lookup"><span data-stu-id="5f063-102">Call Base Class Constructor</span></span>

<span data-ttu-id="5f063-103">Para chamar um construtor de classe base desde uma subclasse, use a palavra-chave **base**:</span><span class="sxs-lookup"><span data-stu-id="5f063-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="5f063-104">Se uma classe base tiver um construtor padrão (sem parâmetros), será possível omitir uma chamada explícita de construtor:</span><span class="sxs-lookup"><span data-stu-id="5f063-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
