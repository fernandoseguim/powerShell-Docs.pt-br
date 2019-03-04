---
title: Elemento CustomItem para CustomEntry controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855602"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>Elemento CustomItem para CustomEntry para Controls para View (formato)

Define quais dados são exibidos pelo controle e como ele é exibido. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) CustomItem CustomEntry controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomItem` elemento. Para obter mais informações, consulte comentários.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define os dados que são exibidos pelo controle.|
|[Elemento de quadro para CustomItem controles para exibição (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.|
|[Elemento de nova linha para CustomItem controles para exibição (formato)](./newline-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Adiciona uma linha em branco para a exibição do controle.|
|[Elemento de texto para CustomItem controles para exibição (formato)](./text-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Adiciona texto, como parênteses ou colchetes, para a exibição do controle.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomEntry para CustomEntries controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fornece uma definição do controle.|

## <a name="remarks"></a>Comentários

Ao especificar os elementos filho do `CustomItem` elemento, tenha em mente o seguinte:

- Os elementos filho devem ser adicionados na sequência a seguir: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.

- Não há nenhum limite máximo ao número de sequências que você pode especificar.

- Em cada sequência, não há nenhum limite máximo ao número de `ExpressionBinding` elementos que você pode usar.

## <a name="see-also"></a>Consulte Também

[Elemento ExpressionBinding para CustomItem controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento de quadro para CustomItem controles para exibição (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Elemento de nova linha para CustomItem controles para exibição (formato)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Elemento de texto para CustomItem controles para exibição (formato)](./text-element-for-customitem-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
