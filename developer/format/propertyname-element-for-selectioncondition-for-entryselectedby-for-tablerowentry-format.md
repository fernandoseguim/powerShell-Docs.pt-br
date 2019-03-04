---
title: Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860982"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a>Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)

Especifica a propriedade do .NET que dispara a condição. Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a entrada da tabela é usada.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para elemento de PropertyName TableRowEntry (formato) SelectionCondition para EntrySelectedBy para TableRowEntry (formato)

## <a name="syntax"></a>Sintaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Define a condição que deve existir para essa entrada de tabela a ser usado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome de propriedade do .NET.

## <a name="remarks"></a>Comentários

A condição de seleção deve especificar pelo menos um nome de propriedade ou um bloco de script, mas não é possível especificar ambos. Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Definir condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md)

[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
