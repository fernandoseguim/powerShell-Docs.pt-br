---
title: Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858282"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)

Define a condição que deve existir para expandir os objetos da coleção desta definição.

Elemento (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition EnumerableExpansion (formato) EntrySelectedBy para EnumerableExpansion (formato)

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

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionCondition` elemento. Você deve especificar um único `PropertyName` ou `ScriptBlock` elemento. O `SelectionSetName` e `TypeName` elementos são opcionais. Você pode especificar um dos qualquer elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade do .NET que dispara a condição.|
|[Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica o script que dispara a condição.|
|[Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica o conjunto de tipos do .NET que dispara a condição.|
|[Elemento TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que dispara a condição.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)|Define quais objetos de coleção do .NET são expandidos por essa definição.|

## <a name="remarks"></a>Comentários

Cada definição deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.

Quando você estiver definindo uma condição de seleção, os seguintes requisitos se aplicam:

- A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.

- Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para dados Diplaying](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre outros componentes de uma exibição ampla, consulte [exibição ampla](./creating-a-wide-view.md).

## <a name="see-also"></a>Consulte Também

[Definir condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
