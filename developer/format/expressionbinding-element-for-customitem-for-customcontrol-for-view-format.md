---
title: Elemento ExpressionBinding para CustomItem para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860682"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>Elemento ExpressionBinding para CustomItem para CustomControl para View (formato)

Define os dados que são exibidos pelo controle. Esse elemento é usado ao definir uma exibição de controle personalizado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento de configuração para elemento de exibição (formato) CustomEntries CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para CustomControl para exibição ( Elemento de CustomItem Format) para CustomEntry para CustomControl para elemento de exibição (formato) ExpressionBinding CustomItem para CustomControl para exibição (formato)

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
|[Elemento CustomControlName para ExpressionBinding para CustomControl para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o nome de um controle comum ou um controle de exibição.|
|[Elemento EnumerateCollection para ExpressionBinding para CustomControl para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especificado que os elementos das coleções são exibidos.|
|[Elemento ItemSelectionCondition para ExpressionBinding para CustomControl para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Elemento opcional.<br /><br /> Define a condição que deve existir para esse controle a ser usado.|
|[Elemento PropertyName para ExpressionBinding para CustomControl para exibição (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade .NET cujo valor é exibido pelo controle.|
|[Elemento ScriptBlock para ExpressionBinding para CustomCustomControl para exibição (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o script cujo valor é exibido pelo controle.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para CustomControl para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Define quais dados são exibidos com o modo de exibição do controle personalizado e como ele é exibido.|

## <a name="remarks"></a>Comentários

## <a name="see-also"></a>Consulte Também

[Elemento CustomControlName para ExpressionBinding para CustomControl para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento EnumerateCollection para ExpressionBinding para CustomControl para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento ItemSelectionCondition para ExpressionBinding para CustomControl para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Elemento PropertyName para ExpressionBinding para CustomControl para exibição (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento ScriptBlock para ExpressionBinding para CustomControl para exibição (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento CustomItem para CustomEntry para CustomControl para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
