---
title: Elemento TableColumnItems para TableRowEntry para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859442"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>Elemento TableColumnItems para TableRowEntry para TableControl (formato)

Define as propriedades ou os scripts cujos valores são exibidos em uma linha.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuração para elemento de TableRowEntry TableControl (formato) TableRowEntries para TableControl (formato) Elemento TableColumnItems para TableControlEntry para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `TableColumnItems` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TableColumnItem para TableColumnItems para TableControl (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Elemento necessário.<br /><br /> Define a propriedade ou cujo valor é exibido em uma coluna da linha do script.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TableRowEntry para TableRowEntries para TableControl (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|Define os dados que são exibidos em uma linha da tabela.|

## <a name="remarks"></a>Comentários

Um `TableColumnItem` elemento é necessário para cada coluna da linha. A primeira entrada é exibida na primeira coluna, a segunda entrada na segunda coluna e assim por diante.

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra uma `TableColumnItems` que define três propriedades do elemento de [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Elemento TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Elemento TableRowEntry (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
