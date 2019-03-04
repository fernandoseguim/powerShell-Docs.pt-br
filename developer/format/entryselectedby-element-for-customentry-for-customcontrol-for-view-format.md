---
title: Elemento EntrySelectedBy para CustomEntry para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859582"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Elemento EntrySelectedBy para CustomEntry para CustomControl para View (formato)

Define os tipos de .NET que usam essa entrada personalizada ou a condição que deve existir para essa entrada a ser usado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `EntrySelectedBy` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para CustomEntry (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Elemento opcional.<br /><br /> Define a condição que deve existir para essa definição a ser usado.|
|[Elemento SelectionSetName para EntrySelectedBy para CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que usam essa definição da exibição de controle.|
|[Elemento TypeName para EntrySelectedBy para CustomEntry (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que usa essa definição da exibição de controle.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Define os controles usados por objetos específicos do .NET.|

## <a name="remarks"></a>Comentários

Você deve especificar pelo menos um critério de seleção para uma entrada, conjunto de seleção ou tipo. Não há nenhum limite máximo ao número de elementos filho que você pode usar.

Condições de seleção são usadas para definir uma condição que deve existir para a entrada a ser usado, como quando um objeto tem uma propriedade específica ou quando um valor de propriedade específica ou script avalia para `true`. Para obter mais informações sobre condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os componentes de uma exibição de controle personalizado, consulte [modo de exibição de controle personalizado](./creating-custom-controls.md).

## <a name="see-also"></a>Consulte Também

[Elemento SelectionCondition para EntrySelectedBy para CustomEntry (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Elemento TypeName para EntrySelectedBy para CustomEntry (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento CustomEntry para CustomEntries para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Modo de exibição de controle personalizado](./creating-custom-controls.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
