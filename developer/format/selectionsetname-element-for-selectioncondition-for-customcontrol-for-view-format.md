---
title: Elemento SelectionSetName para SelectionCondition para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862762"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Elemento SelectionSetName para SelectionCondition para CustomControl para View (formato)

Especifica o conjunto de tipos do .NET que disparam a condição. Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando o controle. Esse elemento é usado ao definir uma exibição de controle personalizado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Define uma condição que deve existir para a definição de controle a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome do conjunto de seleção.

## <a name="remarks"></a>Comentários

Conjuntos de seleção são grupos comuns de objetos .NET que podem ser usados por qualquer exibição que define o arquivo de formatação. Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).

A condição de seleção pode especificar um conjunto de seleção ou um tipo .NET, mas não é possível especificar ambos. Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Consulte Também

[Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Definir condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md)

[Definindo conjuntos de seleção](./defining-selection-sets.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
