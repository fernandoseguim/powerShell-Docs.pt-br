---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 188ede0c558210a746ad0f6c6cef6f571b280878
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="declare-base-class"></a><span data-ttu-id="b5d08-102">Declarar a classe base</span><span class="sxs-lookup"><span data-stu-id="b5d08-102">Declare Base Class</span></span>
<span data-ttu-id="b5d08-103">É possível declarar uma classe do Windows PowerShell como um tipo base para outra classe do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5d08-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="b5d08-104">Também é possível usar os tipos existentes do .NET Framework como classes base:</span><span class="sxs-lookup"><span data-stu-id="b5d08-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
