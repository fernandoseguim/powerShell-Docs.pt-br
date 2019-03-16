---
title: Elemento de rótulo para TableColumnHeader para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054502"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Label para TableColumnHeader para TableControl (formato)

Define o rótulo que é exibido na parte superior de uma coluna. Esse elemento é usado ao definir uma exibição de tabela.

Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento TableControl (formato) TableHeaders elemento de configuração para elemento de TableColumnHeader TableControl (formato) TableHeaders para elemento de rótulo TableControl (formato) TableColumnHeader para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Label` elemento. Apenas um rótulo é permitido para cada coluna.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TableColumnHeader para TableHeaders para TableControl (formato)](./tablecolumnheader-element-format.md)|Define um rótulo, a largura e o alinhamento dos dados para uma coluna da tabela.|

## <a name="text-value"></a>Valor de texto

Especifique o texto que é exibido na parte superior da coluna da tabela. Não há nenhum caractere restrito para o rótulo de coluna.

## <a name="remarks"></a>Comentários

Se nenhum rótulo for especificado, o nome da propriedade cujo valor é exibido nas linhas é usado.

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra um `TableColumnHeader` elemento cujo rótulo é "Coluna 1".

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Elemento TableColumnHeader (formato)](./tablecolumnheader-element-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
