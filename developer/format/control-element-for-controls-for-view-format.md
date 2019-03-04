---
title: Elemento de controle para controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853722"
---
# <a name="control-element-for-controls-for-view--format"></a>Elemento Control para Controls para View (formato)

Define um controle que pode ser usado pelo modo de exibição e o nome que é usado para fazer referência ao controle.

Elemento de exibição de ViewDefinitions elemento (formato) de (formato) do elemento de configuração (formato) controla o elemento de controle de elemento (formato) para controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Control` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento Name para o controle para o modo de exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)|Elemento necessário.<br /><br /> Especifica o nome do controle.|
|[Elemento CustomControl para o controle para controles para exibição (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Elemento necessário.<br /><br /> Define o controle usado por esta exibição.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controles (formato)](./controls-element-for-view-format.md)|Define os controles de exibição podem ser usados por uma exibição específica.|

## <a name="remarks"></a>Comentários

Esse controle pode ser especificado pelos seguintes elementos:

- [Elemento CustomControlName para ExpressionBinding controles para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Elemento CustomControlName para ExpressionBinding para CustomControl para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Elemento CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Elemento CustomControlName para GroupBy (formato)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Consulte Também

[Elemento CustomControl para o controle para controles para exibição (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding controles para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding para CustomControl para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento de controles (formato)](./controls-element-for-view-format.md)

[Elemento Name para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
