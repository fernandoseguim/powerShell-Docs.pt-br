---
title: Elemento PropertyName para SelectionCondition para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860962"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Elemento PropertyName para SelectionCondition para CustomControl para View (formato)

Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a definição é usada. Esse elemento é usado ao definir uma exibição de controle personalizado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento de configuração para elemento de exibição (formato) CustomEntries CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para CustomControl para exibição ( Elemento de CustomItem Format) para CustomEntry para CustomControl para elemento de exibição (formato) EntrySelectedBy CustomEntry para CustomControl para elemento de exibição (formato) SelectionCondition EntrySelectedBy para CustomControl para exibição (formato) PropertyName Elemento para SelectionCondition para CustomControl para exibição (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Define uma condição que deve existir para a definição de controle a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome de propriedade do .NET.

## <a name="remarks"></a>Comentários

A condição de seleção deve especificar um nome menos de uma propriedade ou um script, mas não é possível especificar ambos. Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Consulte Também

[Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
