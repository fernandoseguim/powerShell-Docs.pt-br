---
title: Elemento EntrySelectedBy para TableRowEntry para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058752"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>Elemento EntrySelectedBy para TableRowEntry para TableControl (formato)

Define os tipos de .NET que usam essa definição de exibição de tabela ou a condição que deve existir para essa definição a ser usado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuração (formato)

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
|[Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Define a condição que deve existir para essa definição de exibição de tabela a ser usado.|
|[Elemento SelectionSetName para EntrySelectedBy para TableControl (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que usam essa definição de exibição de tabela.|
|[Elemento TypeName para EntrySelectedBy para TableControl (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que usa essa definição de exibição de tabela.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TableRowEntry para TableControl (formato)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Define os dados que são exibidos em uma linha da tabela.|

## <a name="remarks"></a>Comentários

Você deve especificar pelo menos um critério de seleção para uma definição de exibição de tabela, conjunto de seleção ou tipo. Não há nenhum limite máximo ao número de elementos filho que você pode usar.

Condições de seleção são usadas para definir uma condição que deve existir para a definição a serem usadas, como quando um objeto tem uma propriedade específica ou um valor de propriedade específico ou um script que é avaliada como `true`. Para obter mais informações sobre condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `TableRowEntry` que é usado para exibir as propriedades do elemento de [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento SelectionSetName para EntrySelectedBy para TableControl (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[Elemento TableRowEntry para TableControl (formato)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Elemento TypeName para EntrySelectedBy para TableControl (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
