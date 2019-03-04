---
title: Elemento de rótulo para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862392"
---
# <a name="label-element-for-groupby-format"></a>Elemento Label para GroupBy (formato)

Especifica um rótulo que é exibido quando um novo grupo é encontrado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o elemento de exibição (formato) do rótulo para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Label` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)|Define como um novo grupo de objetos é exibido.|

## <a name="text-value"></a>Valor de texto

Especifique o texto que é exibido sempre que o Windows PowerShell encontra uma nova propriedade ou o valor de script.

## <a name="remarks"></a>Comentários

Além do texto especificado por esse elemento, o Windows PowerShell exibe o novo valor que inicia o grupo e adiciona uma linha em branco antes e depois que o grupo.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra o rótulo para um novo grupo. Rótulo exibido teria uma aparência semelhante a esta: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Para obter um exemplo de um arquivo de formatação completo que inclui esse elemento, consulte [exibição ampla (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Consulte Também

[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
