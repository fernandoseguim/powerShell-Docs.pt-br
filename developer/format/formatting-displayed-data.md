---
title: Formatando os dados exibidos | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854982"
---
# <a name="formatting-displayed-data"></a>Formatar os dados exibidos

Você pode especificar como os pontos de dados individuais em sua lista, tabela ou exibição ampla são exibidos. Você pode usar o `FormatString` elemento ao definir os itens do modo de exibição, ou você pode usar o `ScriptBlock` elemento para chamar o `FormatString` método nos dados.

## <a name="using-the-formatstring-element"></a>Usando o elemento FormatString

No exemplo a seguir, o valor da `TotalProcessorTime` propriedade do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto é formatado usando o elemento FormatString. O `TotalProcessorTime` propriedade

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



