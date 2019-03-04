---
title: Elemento de quadro para CustomItem para controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859812"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Elemento Frame para CustomItem para Controls para View (formato)

Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita. Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) CustomItem CustomEntry controles para o elemento de exibição (formato) do quadro para CustomItem controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Frame` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|`CustomItem Element`|Elemento necessário|
|[Elemento FirstLineHanging do quadro de controles de exibição (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica quantos caracteres da primeira linha é deslocada para a esquerda.|
|[Elemento FirstLineIndent do quadro de controles de exibição (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica quantos caracteres da primeira linha é deslocada para a direita.|
|[Elemento LeftIndent do quadro de controles de exibição (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de caracteres de dados são deslocados da margem esquerda.|
|[Elemento RightIndent do quadro de controles de exibição (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de caracteres de dados são deslocados da margem direita.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry controles para exibição (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Define quais dados são exibidos pelo controle e como ele é exibido.|

## <a name="remarks"></a>Comentários

Não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementos no mesmo `Frame` elemento.

## <a name="see-also"></a>Consulte Também

[Elemento FirstLineHanging do quadro de controles de exibição (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Elemento FirstLineIndent do quadro de controles de exibição (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Elemento LeftIndent do quadro de controles de exibição (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[Elemento RightIndent do quadro de controles de exibição (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[Elemento CustomItem para CustomEntry controles para exibição (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
