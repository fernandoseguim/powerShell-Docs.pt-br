---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 3269c8cc871f22488b64fb072dac72698983f360
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="call-base-class-constructor"></a>Chamar o construtor de classe base

Para chamar um construtor de classe base desde uma subclasse, use a palavra-chave **base**:

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

Se uma classe base tiver um construtor padrão (sem parâmetros), será possível omitir uma chamada explícita de construtor:

```powershell
class C : B
{
    C([int]$c) {}
}
```