---
title: Elemento PropertyName para ItemSelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858262"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>Elemento PropertyName para ItemSelectionCondition para GroupBy (formato)

Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição é atendida e o controle é usado. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) CustomItem CustomEntry para elemento de GroupBy (formato) ExpressionBinding CustomItem para elemento de GroupBy (formato) ItemSelectionCondition ExpressionBinding para elemento de PropertyName GroupBy (formato) ItemSelectionCondition para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Define a condição que deve existir para esse controle a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome da propriedade .NET que dispara a condição.

## <a name="remarks"></a>Comentários

Se esse elemento é usado, não é possível especificar o [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) elemento ao definir a condição de seleção.

## <a name="see-also"></a>Consulte Também

[Elemento ScriptBlock para ItemSelectionCondition para GroupBy (formato)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[Elemento ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
