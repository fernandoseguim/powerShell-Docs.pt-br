---
title: Elemento ScriptBlock para ItemSelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860942"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>Elemento ScriptBlock para ItemSelectionCondition para GroupBy (formato)

Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição é atendida e o controle é usado. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) CustomItem CustomEntry para elemento de GroupBy (formato) ExpressionBinding CustomItem para elemento de GroupBy (formato) ItemSelectionCondition ExpressionBinding para elemento de ScriptBlock GroupBy (formato) ItemSelectionCondition para GroupBy (formato)

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
|[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Define a condição que deve existir para esse controle a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Comentários

Se esse elemento é usado, não é possível especificar o [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) elemento ao definir a condição de seleção.

## <a name="see-also"></a>Consulte Também

[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Elemento PropertyName para ItemSelectionCondition para GroupBy (formato)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
