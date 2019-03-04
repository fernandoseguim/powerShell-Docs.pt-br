---
title: Elemento EntrySelectedBy para CustomEntry para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862812"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)

Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) EntrySelectedBy CustomEntry para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `EntrySelectedBy` elemento. Você deve especificar pelo menos um critério de seleção para uma definição de, conjunto de seleção ou tipo. Não há nenhum limite máximo ao número de elementos filho que você pode usar.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Elemento opcional.<br /><br /> Define a condição que deve existir para essa definição a ser usado.|
|[Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que usam essa definição do controle.|
|[Elemento TypeName para EntrySelectedBy para GroupBy (formato)](./typename-element-for-entryselectedby-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que usa essa definição do controle.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomEntry para CustomControl para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)|Fornece uma definição do controle.|

## <a name="remarks"></a>Comentários

Condições de seleção são usadas para definir uma condição que deve existir para a definição a ser usado, como quando um objeto tem uma propriedade específica ou quando um valor de propriedade específica ou script avalia para `true`. Para obter mais informações sobre condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Consulte Também

[Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[Elemento TypeName para EntrySelectedBy para GroupBy (formato)](./typename-element-for-entryselectedby-for-groupby-format.md)

[Elemento CustomEntry para CustomEntries controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
