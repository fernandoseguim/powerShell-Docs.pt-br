---
title: Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862942"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideControl (formato)

Especifica o script que dispara a condição. Quando esse script é avaliado para `true`, a condição for atendida e a definição ampla de entrada é usada.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition WideEntry (formato) EntrySelectedBy para elemento de ScriptBlock WideEntry (formato) SelectionCondition para EntrySelectedBy para WideEntry (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Define a condição que deve existir para essa definição a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Comentários

A condição de seleção deve especificar pelo menos um nome de script ou uma propriedade a ser avaliada, mas não é possível especificar ambos. Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre outros componentes de uma exibição ampla, consulte [exibição ampla](./creating-a-wide-view.md).

## <a name="see-also"></a>Consulte Também

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Definir condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md)

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
