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
# <a name="declare-implemented-interface"></a>Declarar a interface implementada

Será possível declarar interfaces implementadas após tipos base, ou imediatamente após dois-pontos (:), se não houver nenhum tipo base especificado. Separe todos os nomes de tipo usando vírgulas. Isso é muito semelhante à sintaxe do C#.

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