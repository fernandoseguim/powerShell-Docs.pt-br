---
title: Elemento CustomItem para CustomEntry para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856182"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Elemento CustomItem para CustomEntry para CustomControl para View (formato)

Define quais dados são exibidos com o modo de exibição do controle personalizado e como ele é exibido. Esse elemento é usado ao definir uma exibição de controle personalizado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomItem` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para CustomControl para exibição (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define os dados que são exibidos pelo controle.|
|[Elemento de quadro para CustomItem para CustomControl para exibição (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define quais dados são exibidos com o modo de exibição do controle personalizado e como ele é exibido.|
|[Elemento de nova linha para CustomItem para um controle personalizado para o modo de exibição (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Adiciona uma linha em branco para a exibição do controle.|
|[Elemento de texto para CustomItem para CustomControl para exibição (formato)](./text-element-for-customitem-for-customview-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o texto adicional para os dados exibidos pelo controle.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries para CustomControl para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Fornece uma definição da exibição de controle personalizado.|

## <a name="remarks"></a>Comentários

## <a name="see-also"></a>Consulte Também

[Elemento CustomEntry para CustomEntries para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Elemento ExpressionBinding para CustomItem para CustomControl para exibição (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento de quadro para CustomItem para CustomControl para exibição (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento de nova linha para CustomItem para CustomControl para exibição (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento de texto para CustomItem para CustomControl para exibição (formato)](./text-element-for-customitem-for-customview-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
