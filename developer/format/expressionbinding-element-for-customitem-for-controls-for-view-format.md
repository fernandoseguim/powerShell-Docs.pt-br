---
title: Elemento ExpressionBinding para CustomItem controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858292"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Elemento ExpressionBinding para CustomItem para Controls para View (formato)

Define os dados que são exibidos pelo controle. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) CustomItem CustomEntry para controles para elemento de exibição (formato) ExpressionBinding CustomItem controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ExpressionBinding` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|`CustomControl Element`|Elemento opcional.<br /><br /> Define um controle que é usado por esse controle.|
|[Elemento CustomControlName para ExpressionBinding controles para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o nome de um controle comum ou um controle de exibição.|
|[Elemento EnumerateCollection para ExpressionBinding controles para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica que os elementos das coleções são exibidos.|
|[Elemento ItemSelectionCondition de ExpressionBinding controles para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define a condição que deve existir para esse controle a ser usado.|
|[Elemento PropertyName para ExpressionBinding controles para exibição (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade .NET cujo valor é exibido pelo controle.|
|[Elemento ScriptBlock para ExpressionBinding controles para exibição (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o script cujo valor é exibido pelo controle.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry controles para exibição (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Define quais dados são exibidos pelo controle e como ele é exibido.|

## <a name="remarks"></a>Comentários

## <a name="see-also"></a>Consulte Também

[Elemento CustomItem para CustomEntry controles para exibição (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Elemento CustomControlName para ExpressionBinding controles para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento EnumerateCollection para ExpressionBinding controles para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento ItemSelectionCondition de ExpressionBinding controles para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento PropertyName para ExpressionBinding controles para exibição (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento ScriptBlock para ExpressionBinding controles para exibição (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
