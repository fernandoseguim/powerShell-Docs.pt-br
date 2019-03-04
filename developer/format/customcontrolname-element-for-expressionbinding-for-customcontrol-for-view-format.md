---
title: Elemento CustomControlName para ExpressionBinding para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860432"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>Elemento CustomControlName para ExpressionBinding para CustomControl para View (formato)

Especifica o nome de um controle comum ou um controle de exibição. Esse elemento é usado ao definir uma exibição de controle personalizado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento de configuração para elemento de exibição (formato) CustomEntries CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para CustomItem do modo de exibição (formato) Elemento para CustomEntry para exibição (formato) ExpressionBinding elemento do elemento CustomItem (formato) CustomControlName para associação de expressão para CustomItem (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomControlName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Define os dados que são exibidos pelo controle.|

## <a name="text-value"></a>Valor de texto

Especifique o nome do controle.

## <a name="remarks"></a>Comentários

Você pode criar controles comuns que podem ser usados por todas as exibições de um arquivo de formatação e você pode criar controles de exibição que podem ser usados por uma exibição específica. Os nomes desses controles são especificados por elementos a seguir.

- [Elemento Name para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Consulte Também

[Elemento Name para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
