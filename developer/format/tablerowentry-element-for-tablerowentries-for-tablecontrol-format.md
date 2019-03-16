---
title: Elemento TableRowEntry para TableRowEntries para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58059867"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>Elemento TableRowEntry para TableRowEntries para TableControl (formato)

Define os dados que são exibidos em uma linha da tabela.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuração para elemento de TableRowEntry TableControl (formato) TableRowEntries para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TableRowEntry` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EntrySelectedBy para TableRowEntry para TableControl (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento necessário.<br /><br /> Define os objetos cujos valores de propriedade são exibidos na linha.|
|[Elemento TableColumnItems para TableRowEntry para TableControl (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento necessário.<br /><br /> Define as propriedades ou os scripts cujos valores são exibidos.|
|[Elemento de agrupamento para TableRowEntry para TableControl (formato)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica que o texto que excede a largura da coluna é exibido na próxima linha.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TableRowEntries para TableControl (formato)](./tablerowentries-element-for-tablecontrol-format.md)|Define as linhas da tabela.|

## <a name="remarks"></a>Comentários

Uma `TableColumnItems` e um elemento `EntrySelectedBy` elemento deve ser especificado.

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra uma `TableRowEntry` que define uma linha que exibe os valores de duas propriedades de elemento de [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Elemento EntrySelectedBy para TableRowEntry para TableControl (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento TableColumnItems para TableRowEntry para TableControl (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento TableRowEntries para TableControl (formato)](./tablerowentries-element-for-tablecontrol-format.md)

[Elemento de agrupamento para TableRowEntry para TableControl (formato)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
