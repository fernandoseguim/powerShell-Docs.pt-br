---
title: Elemento SelectionSetName para EntrySelectedBy controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860992"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a>Elemento SelectionSetName para EntrySelectedBy para Controls para View (formato)

Especifica um conjunto de tipos do .NET que usam essa definição do controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para controles para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) EntrySelectedBy CustomEntry para controles para elemento de exibição (formato) SelectionSetName EntrySelectedBy para controles para exibição ( Formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.

### <a name="attributes"></a>Atributos

Não

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para CustomEntry controles para exibição (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome do conjunto de seleção.

## <a name="remarks"></a>Comentários

Cada definição de controle deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.

Conjuntos de seleção normalmente são usados quando você deseja definir um grupo de objetos que são usados em vários modos de exibição. Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).

## <a name="see-also"></a>Consulte Também

[Elemento EntrySelectedBy para CustomEntry controles para exibição (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
