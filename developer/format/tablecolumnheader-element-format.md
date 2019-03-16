---
title: Elemento TableColumnHeader (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057868"
---
# <a name="tablecolumnheader-element-format"></a>Elemento TableColumnHeader (formato)

Define o rótulo, a largura da coluna e o alinhamento do rótulo de uma coluna da tabela.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento TableControl (formato) TableHeaders elemento de configuração para elemento de TableColumnHeader TableControl (formato) TableHeaders para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TableColumnHeader` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de rótulo para TableColumnHeader para TableControl (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Define o rótulo que é exibido na parte superior da coluna. Se nenhum rótulo for especificado, o nome da propriedade cujo valor é exibido nas linhas é usado.|
|[Elemento de largura para TableColumnHeader para TableControl (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento necessário.<br /><br /> Especifica a largura (em caracteres) da coluna.|
|[Elemento de alinhamento para TableColumnHeader para TableControl (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica como o rótulo da coluna é exibido. Se nenhum alinhamento for especificado, o rótulo é alinhado à esquerda.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TableHeaders (formato)](./tableheaders-element-format.md)|Define as colunas de uma exibição de tabela.|

## <a name="remarks"></a>Comentários

Especifique um cabeçalho para cada coluna da tabela. As colunas são exibidas na ordem em que o `TableColumnHeader` elementos são definidos.

Uma tabela deve ter o mesmo número de `TableColumnHeader` elementos como `TableRowEntry` elementos. O cabeçalho da coluna define como o texto na parte superior da tabela é exibido. As entradas de linha definem quais dados são exibidos nas linhas da tabela.

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [exibição de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra dois `TableColumnHeader` elementos. O primeiro elemento define uma coluna cujo rótulo é a "Coluna 1", tem uma largura de 16 caracteres e cujo rótulo é alinhado à esquerda. O segundo elemento define uma coluna cujo rótulo é "Coluna 2", tem uma largura de 10 caracteres e cujo rótulo está centralizado na coluna.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Consulte Também

[Elemento de alinhamento para TableColumnHeader para TableControl (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Elemento de rótulo para TableColumnHeader para TableControl (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Elemento TableHeaders para TableControl (formato)](./tableheaders-element-format.md)

[Largura para TableColumnHeader para elemento TableControl (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
