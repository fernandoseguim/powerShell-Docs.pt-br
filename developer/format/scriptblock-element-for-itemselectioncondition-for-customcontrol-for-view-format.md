---
title: Elemento ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862232"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>Elemento ScriptBlock para ItemSelectionCondition para CustomControl para View (formato)

Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição é atendida e o controle é usado. Esse elemento é usado ao definir uma exibição de controle personalizado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de exibição (formato) ExpressionBinding CustomItem para CustomControl para exibição (formato) ItemSelectionCondition elemento de associação de expressão para CustomControl para elemento de exibição (formato) ScriptBlock ItemSelectionCondition para CustomControl para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ItemSelectionCondition para associação de expressão para CustomControl para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Define a condição que deve existir para esse controle a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Comentários

Se esse elemento é usado, não é possível especificar o [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elemento ao definir a condição de seleção.

## <a name="see-also"></a>Consulte Também

[Elemento PropertyName para ItemSelectionCondition para CustomControl para exibição (formato)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[Elemento ItemSelectionCondition para associação de expressão para CustomControl para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
