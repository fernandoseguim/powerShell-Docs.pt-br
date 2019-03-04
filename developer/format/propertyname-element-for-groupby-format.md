---
title: Elemento PropertyName para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863262"
---
# <a name="propertyname-element-for-groupby-format"></a>Elemento PropertyName para GroupBy (formato)

Especifica a propriedade do .NET que inicia um novo grupo sempre que seu valor é alterado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) PropertyName elemento GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)|Define como um grupo de objetos do .NET é exibido.|

## <a name="text-value"></a>Valor de texto

Especifique o nome de propriedade do .NET.

## <a name="remarks"></a>Comentários

Windows PowerShell inicia um novo grupo, sempre que o valor dessa propriedade é alterado.

Quando esse elemento for especificado, é possível especificar o [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento para iniciar um novo grupo.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como iniciar um novo grupo quando o valor de uma propriedade é alterado.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Para obter um exemplo de um arquivo de formatação completo que inclui esse elemento, consulte [exibição ampla (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Consulte Também

[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)

[Elemento ScriptBlock para GroupBy (formato)](./scriptblock-element-for-groupby-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
