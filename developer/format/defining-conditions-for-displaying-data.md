---
title: Definir condições para a exibição de dados | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855642"
---
# <a name="defining-conditions-for-displaying-data"></a>Definir condições para a exibição de dados

Ao definir quais dados são exibidos em uma exibição ou um controle, você pode especificar uma condição que deve existir para os dados a serem exibidos. A condição pode ser disparada por uma propriedade específica, ou quando um script ou o valor da propriedade é avaliada como `true`. Quando a seleção de condição for atendida, a definição da exibição ou controle é usada.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Especificando um critério de seleção para uma definição

Ao criar uma definição para um modo de exibição ou controle, o `EntrySelectedBy` elemento é usado para especificar quais objetos usará a definição ou qual condição deve existir para a definição a ser usado. A condição é especificada pelo `SelectionCondition` elemento.

No exemplo a seguir, uma condição de seleção é especificada para uma definição de uma exibição de tabela. Neste exemplo, a definição é usada somente quando o script especificado é avaliado para `true`.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

Não há nenhum limite para o número de condições de seleção que você pode especificar para uma definição de um modo de exibição ou controle. Os únicos requisitos são os seguintes:

- A condição de seleção deve especificar um nome de propriedade ou script para disparar a condição, mas não é possível especificar ambos.

- Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

## <a name="specifying-a-selection-condition-for-an-item"></a>Especificando um critério de seleção para um Item

Você também pode especificar quando um item de um modo de exibição de lista ou um controle é usado, incluindo o `ItemSelectionCondition` elemento na definição de item. No exemplo a seguir, uma condição de seleção é especificada para um item de uma exibição de lista. Neste exemplo, o item é usado somente quando o script é avaliado como `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Você pode especificar a condição somente uma seleção de um item. E a condição deve especificar um nome de propriedade ou script para disparar a condição, mas não é possível especificar ambos.

## <a name="xml-elements"></a>Elementos XML

 Os seguintes elementos XML são usados para criar uma condição de seleção.

- Os seguintes elementos especificam critérios de seleção para definições de exibição:

    - [Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para WideControl (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy para CustomControl (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Seleção de especificar os seguintes elementos condições comuns e modo de exibição de controle de definições:

    - [Elemento SelectionCondition para EntrySelectedBy para controles de configuração (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- O elemento a seguir especifica o critério de seleção para expansão de objetos de coleção:

    - [Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- O elemento a seguir especifica o critério de seleção para exibir um novo grupo de dados:

    - [Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- O elemento a seguir especifica uma condição de seleção de item para uma exibição de lista:

    - [Elemento ItemSelectionCondition para ListItem para ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Os seguintes elementos deve especificar um critério de seleção de item para controles:

    - [Elemento ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [Elemento ItemSelectionCondition para ExpressionBinding controles para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Elemento ItemSelectionCondition para ExpressionBinding para CustomControl (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Consulte Também

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
