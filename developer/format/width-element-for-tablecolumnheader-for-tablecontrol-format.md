---
title: Elemento de largura para TableColumnHeader para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055182"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Elemento Width para TableColumnHeader para TableControl (formato)

Define a largura (em caracteres) de uma coluna.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) TableHeaders elemento de configuração para TableControl (formato) elemento TableColumnHeader TableHeaders para elemento de largura TableControl (formato) TableColumnHeader para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Width` elemento usado ao definir cabeçalhos de coluna.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento TableColumnHeader para TableHeaders para TableControl (formato)](./tablecolumnheader-element-format.md)|Define um rótulo, a largura e o alinhamento dos dados para uma coluna da tabela.|

## <a name="text-value"></a>Valor de texto

Quando em todos os possíveis, especifique uma largura (em caracteres) que é maior que o tamanho dos valores de propriedade exibida.

## <a name="remarks"></a>Comentários

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `TableColumnHeader` elemento cuja largura é de 16 caracteres.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Elemento TableColumnHeader para TableHeader para TableControl (formato)](./tablecolumnheader-element-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
