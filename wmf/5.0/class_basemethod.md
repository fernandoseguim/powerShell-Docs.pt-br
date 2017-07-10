---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: 28da6d12d3f7a59777425e1cc4531a609a793ddb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="call-base-class-method" class="xliff"></a>
# Chamar o método de classe base

É possível substituir os métodos existentes nas subclasses. Para fazer isso, declare métodos usando o mesmo nome e a mesma assinatura:

```PowerShell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

Para chamar métodos de classe base desde implementações substituídas, transmita para a classe base ([baseClass]$this) na invocação:

```PowerShell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

Todos os métodos do PowerShell são virtuais. É possível ocultar métodos não virtuais do .NET em uma subclasse usando a mesma sintaxe que você usaria para uma substituição: basta declarar os métodos com o mesmo nome e a mesma assinatura.

```PowerShell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

