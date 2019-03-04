---
title: Elemento SelectionCondition para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861232"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)

Define a condição que deve existir para usar para esta definição da exibição de tabela. Não há nenhum limite para o número de condições de seleção que pode ser especificado para uma definição de tabela.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)

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

As seções a seguir descrevem atributos, elementos filho e o elemento pai do elemento SelectionCondition.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade do .NET que dispara a condição.|
|[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica o script que dispara a condição.|
|[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica o conjunto de tipos do .NET que disparam a condição.|
|[Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que dispara a condição.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para TableRowEntry (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Define os tipos de .NET que usam essa entrada de tabela ou a condição que deve existir para essa entrada a ser usado.|

## <a name="remarks"></a>Comentários

Cada entrada da lista deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.

Quando você estiver definindo uma condição de seleção, os seguintes requisitos se aplicam:

- A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.

- Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Definir condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md)

[Elemento EntrySelectedBy (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Escrevendo um formatação do Windows PowerShell e tipos de arquivo](./writing-a-powershell-formatting-file.md)
