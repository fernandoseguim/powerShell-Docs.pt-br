---
title: Elemento de quadro para CustomItem para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854842"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Elemento Frame para CustomItem para GroupBy (formato)

Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) CustomItem CustomEntry para elemento de quadro GroupBy (formato) CustomItem para GroupBy (formato)

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
|[Elemento FirstLineHanging para quadro de GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda.|
|[Elemento FirstLineIndent para quadro de GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita.|
|[Elemento LeftIndent para quadro de GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica o número de caracteres de dados são deslocados da margem esquerda.|
|[Elemento RightIndent para quadro de GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent elemento|Elemento opcional.<br /><br /> Especifica o número de caracteres de dados são deslocados da margem direita.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)|Define quais dados são exibidos pelo controle e como ele é exibido.|

## <a name="remarks"></a>Comentários

Não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementos no mesmo `Frame` elemento.

## <a name="see-also"></a>Consulte Também

[Elemento FirstLineHanging para quadro de GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Elemento FirstLineIndent para quadro de GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Elemento LeftIndent para quadro de GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md)

[Elemento RightIndent para quadro de GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)

[Elemento CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
