---
title: Elemento SelectionCondition para EntrySelectedBy para CustomControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858822"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>Elemento SelectionCondition para EntrySelectedBy para CustomControl (formato)

Define uma condição que deve existir para uma definição de controle a ser usado. Esse elemento é usado ao definir uma exibição de controle personalizado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento de configuração para elemento de exibição (formato) CustomEntries CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para CustomControl para exibição ( Elemento de CustomItem Format) para CustomEntry para CustomControl para elemento de exibição (formato) EntrySelectedBy CustomEntry para CustomControl para elemento de exibição (formato) SelectionCondition EntrySelectedBy para CustomControl para exibição (formato)

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
|[Elemento PropertyName para SelectionCondition para CustomControl para exibição (formato)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica uma propriedade do .NET que dispara a condição.|
|[Elemento ScriptBlock para SelectionCondition para CustomControl para exibição (formato)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o script que dispara a condição.|
|[Elemento SelectionSetName para SelectionCondition para um controle personalizado para o modo de exibição (formato)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o conjunto de tipos do .NET que dispara a condição.|
|[Elemento TypeName para SelectionCondition para CustomControl para exibição (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que dispara a condição.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry para CustomControl para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado.|

## <a name="remarks"></a>Comentários

Quando você estiver definindo uma condição de seleção, os seguintes requisitos se aplicam:

- A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.

- Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Consulte Também

[Elemento PropertyName para SelectionCondition para CustomControl para exibição (formato)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento ScriptBlock para SelectionCondition para CustomControl para exibição (formato)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento SelectionSetName para SelectionCondition para um controle personalizado para o modo de exibição (formato)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento TypeName para SelectionCondition para CustomControl para exibição (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento EntrySelectedBy para CustomEntry para CustomControl para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
