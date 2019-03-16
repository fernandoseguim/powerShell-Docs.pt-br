---
title: Elemento SelectionCondition para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 633204f3b181316761746ea2679910216fb74657
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058956"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)

Define a condição que deve existir para usar essa definição da exibição de lista. Não há nenhum limite para o número de condições de seleção que pode ser especificado para uma definição de lista.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento ListControl (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition ListEntry (formato) EntrySelectedBy para ListEntry (formato)

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
|[Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade do .NET que dispara a condição.|
|[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica o script que dispara a condição.|
|[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Elemento opcional.<br /><br /> Especifica o conjunto de tipos do .NET que disparam a condição.|
|[Elemento TypeName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que dispara a condição.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para TableRowEntry (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Define os tipos de .NET que usam essa entrada de tabela ou a condição que deve existir para essa entrada a ser usado.|

## <a name="remarks"></a>Comentários

lWhen você está definindo uma condição de seleção, os seguintes requisitos se aplicam:

- A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.

- Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre outros componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de lista](./creating-a-list-view.md)

[Definir condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md)

[Elemento ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento TypeName para EntrySelectedBy para ListEntry (formato)](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
