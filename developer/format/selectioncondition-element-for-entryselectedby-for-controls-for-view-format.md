---
title: Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858012"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>Elemento SelectionCondition para EntrySelectedBy para Controls para View (formato)

Define uma condição que deve existir para a definição de controle a ser usado. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para controles para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) EntrySelectedBy CustomEntry para controles para elemento de exibição (formato) SelectionCondition EntrySelectedBy para controles para exibição ( Formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionCondition` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition controles para exibição (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica uma propriedade do .NET que dispara a condição.|
|[Elemento ScriptBlock para SelectionCondition controles para exibição (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o script que dispara a condição.|
|[Elemento SelectionSetName para SelectionCondition controles para exibição (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o conjunto de tipos do .NET que dispara a condição.|
|[Elemento TypeName para SelectionCondition controles para exibição (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que dispara a condição.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry controles para exibição (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado.|

## <a name="remarks"></a>Comentários

Quando você estiver definindo uma condição de seleção, os seguintes requisitos se aplicam:

- A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.

- Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Consulte Também

[Elemento PropertyName para SelectionCondition controles para exibição (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento ScriptBlock para SelectionCondition controles para exibição (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento SelectionSetName para SelectionCondition controles para exibição (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento TypeName para SelectionCondition controles para exibição (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento EntrySelectedBy para CustomEntry controles para exibição (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
