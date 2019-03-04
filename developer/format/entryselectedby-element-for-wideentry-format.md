---
title: Elemento EntrySelectedBy para WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854972"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>Elemento EntrySelectedBy para WideEntry (formato)

Define os tipos de .NET que usam essa definição de exibição ampla ou a condição que deve existir para essa definição a ser usado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuração para WideEntry (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Define a condição que deve existir para essa definição de exibição ampla com a ser usado.|
|[Elemento SelectionSetName para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que usam essa definição de exibição ampla.|
|[Elemento TypeName para EntrySelectedBy para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que usa essa definição de exibição ampla.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Fornece uma definição da exibição ampla.|

## <a name="remarks"></a>Comentários

Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para uma definição de exibição ampla. Não há nenhum limite máximo ao número de elementos filho que você pode usar.

Condições de seleção são usadas para definir uma condição que deve existir para a definição a serem usadas, como quando um objeto tem uma propriedade específica ou um valor de propriedade específica ou script que é avaliada como `true`. Para obter mais informações sobre condições de seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre outros componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).

## <a name="see-also"></a>Consulte Também

[Elemento WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento TypeName para EntrySelectedBy para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Definir condições para a exibição de dados](./defining-conditions-for-displaying-data.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
