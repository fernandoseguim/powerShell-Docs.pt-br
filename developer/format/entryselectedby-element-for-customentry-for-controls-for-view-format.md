---
title: Elemento EntrySelectedBy para CustomEntry controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859532"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>Elemento EntrySelectedBy para CustomEntry para Controls para View (formato)

Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para controles para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) EntrySelectedBy CustomEntry controles para exibição (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define a condição que deve existir para essa definição a ser usado.|
|[Elemento SelectionSetName para EntrySelectedBy controles para exibição (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que usam essa definição do controle.|
|[Elemento TypeName para EntrySelectedBy controles para exibição (formato)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que usa essa definição do controle.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fornece uma definição do controle.|

## <a name="remarks"></a>Comentários

Condições de seleção são usadas para definir uma condição que deve existir para a definição a ser usado, como quando um objeto tem uma propriedade específica ou quando um valor de propriedade específica ou script avalia para `true`. Para obter mais informações sobre condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Consulte Também

[Elemento CustomEntry para CustomEntries controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
