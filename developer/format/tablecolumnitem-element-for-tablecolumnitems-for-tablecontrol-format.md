---
title: Elemento TableColumnItem para TableColumnItems para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056984"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>Elemento TableColumnItem para TableColumnItems para TableControl (formato)

Define a propriedade ou cujo valor é exibido na coluna da linha do script.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuração para elemento de TableRowEntry TableControl (formato) TableRowEntries para TableControl (formato) Elemento TableColumnItems para TableControlEntry para elemento de TableColumnItem TableControl (formato) TableColumnItems para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `TableColumnItem` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de alinhamento para TableColumnItem para TableControl (formato)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Define como os dados em uma coluna da linha são exibidos.|
|[Elemento FormatString para TableColumnItem para TableControl (formato)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Especifica um padrão de formato que é usado para formatar os dados na coluna da linha.|
|[Elemento PropertyName para TableColumnItem para TableControl (formato)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica o nome da propriedade cujo valor é exibido.|
|[Elemento ScriptBlock para TableColumnItem para TableControl (formato)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica o script cujo valor é exibido na coluna de uma linha.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TableColumnItems para TableControlEntry para TableControl (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Define as propriedades ou os scripts cujos valores são exibidos na linha.|

## <a name="remarks"></a>Comentários

Você pode especificar uma propriedade de um objeto ou um script em cada coluna da linha. Se nenhum elemento filho forem especificado, o item é um espaço reservado e nenhum dado é exibido.

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra uma `TableColumnItem` que exibe o valor do elemento de `Status` propriedade da [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Elemento de alinhamento para TableColumnItem para TableControl (formato)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento TableColumnItems (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento FormatString para TableColumnItem para TableControl (formato)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento PropertyName para TableColumnItem para TableControl (formato)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento ScriptBlock para TableColumnItem para TableControl (formato)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
