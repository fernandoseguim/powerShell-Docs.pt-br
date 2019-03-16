---
title: Elemento TableRowEntries para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055726"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>Elemento TableRowEntries para TableControl (formato)

Define as linhas da tabela.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) TableRowEntries elemento de configuração para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `TableRowEntries` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TableRowEntry para TableRowEntries para TableControl (formato)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Elemento necessário.<br /><br /> Define os dados que são exibidos em uma linha da tabela.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TableControl (formato)](./tablecontrol-element-format.md)|Define um formato de tabela para um modo de exibição.|

## <a name="remarks"></a>Comentários

Você deve especificar um ou mais `TableRowEntry` elementos para o modo de exibição de tabela. Não há nenhum limite máximo ao número de `TableRowEntry` elementos que podem ser adicionados nem é sua ordem significativa.

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra uma `TableRowEntries` que define uma linha que exibe os valores de duas propriedades de elemento de [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Elemento TableControl (formato)](./tablecontrol-element-format.md)

[Elemento TableRowEntry (formato)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
