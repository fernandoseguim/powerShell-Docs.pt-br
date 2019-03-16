---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055965"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>Elemento TypeName para SelectionCondition para EntrySelectedBy para WideControl (formato)

Especifica um tipo .NET que dispara a condição. Quando esse tipo estiver presente, a definição é usada.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition WideEntry (formato) EntrySelectedBy para elemento de TypeName WideEntry (formato) SelectionCondition para EntrySelectedBy para WideEntry (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TypeName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Define a condição que deve existir para essa entrada larga a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome totalmente qualificado do tipo .NET, como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Comentários

Os critérios de seleção podem especificar um tipo .NET ou uma seleção definida, mas não é possível especificar ambos. Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre outros componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).

## <a name="see-also"></a>Consulte Também

[Criando uma exibição ampla](./creating-a-wide-view.md)

[Definir condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md)

[Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
