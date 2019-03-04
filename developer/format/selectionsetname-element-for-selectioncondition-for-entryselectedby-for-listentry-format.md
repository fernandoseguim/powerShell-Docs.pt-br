---
title: Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862192"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)

Especifica o conjunto de tipos do .NET que disparam a condição. Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando essa definição da exibição de lista.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento ListControl (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition ListEntry (formato) EntrySelectedBy para elemento de SelectionSetName ListEntry (formato) SelectionCondition para EntrySelectedBy para ListEntry (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Define a condição que deve existir para usar essa definição da exibição de lista.|

## <a name="text-value"></a>Valor de texto

Especifique o nome do conjunto de seleção.

## <a name="remarks"></a>Comentários

A condição de seleção pode especificar um conjunto de seleção ou um tipo .NET, mas não é possível especificar ambos. Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).

Conjuntos de seleção são grupos comuns de objetos .NET que podem ser usados por qualquer exibição que define o arquivo de formatação. Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).

Para obter mais informações sobre outros componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de lista](./creating-a-list-view.md)

[Definir condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md)

[Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
