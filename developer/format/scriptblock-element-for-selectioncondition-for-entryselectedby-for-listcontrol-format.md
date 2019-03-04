---
title: Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: fd708473d04a76bcf6cf3a8f8278e1d15fb9addf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858652"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListControl (formato)

Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição for atendida e a entrada da lista é usada.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento ListControl (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition ListEntry (formato) EntrySelectedBy para elemento de ScriptBlock ListEntry (formato) SelectionCondition para EntrySelectedBy para ListEntry (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Define a condição que deve existir para essa entrada de lista a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Comentários

A condição de seleção deve especificar pelo menos um script ou a propriedade nome para avaliar, mas não é possível especificar ambos. (Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).)

Para obter mais informações sobre os outros componentes de uma exibição de lista, consulte [exibição de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Consulte Também

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento PropertyName para SelectionCondition para EmtrySelectedBy para ListEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Exibição de lista](./creating-a-list-view.md)

[Definir condições para quando uma entrada de exibição ou um Item é usado](./defining-conditions-for-displaying-data.md)

[Escrevendo um formatação do Windows PowerShell e tipos de arquivo](./writing-a-powershell-formatting-file.md)
