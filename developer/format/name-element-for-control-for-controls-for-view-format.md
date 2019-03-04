---
title: Nome de elemento para o controle para controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862382"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Elemento Name para Control para Controls para View (formato)

Especifica o nome do controle.

Configuração elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) controla elemento de controle de elemento (formato) para controles para elemento de nome de exibição (formato) para o controle para o modo de exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Name` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controle para controles para exibição (formato)](./control-element-for-controls-for-view-format.md)|Define um controle que pode ser usado pelo modo de exibição e o nome que é usado para fazer referência ao controle.|

## <a name="text-value"></a>Valor de texto

Especifique o nome que é usado para fazer referência ao controle.

## <a name="remarks"></a>Comentários

O nome especificado aqui pode ser usado nos elementos a seguir para fazer referência a esse controle.

- Ao criar uma tabela, a lista, o modo de exibição de controle personalizado ou ampla, o controle pode ser especificado pelo elemento a seguir: [Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)

- Quando a criação de outro controle que pode ser usado por um modo de exibição, esse controle pode ser especificado pelo elemento a seguir: [Elemento ExpressionBinding para CustomItem controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Consulte Também

[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)

[Elemento ExpressionBinding para CustomItem controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento de controle para controles para exibição (formato)](./control-element-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
