---
title: Elemento FirstLineIndent para quadro de GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858552"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>Elemento FirstLineIndent para Frame para GroupBy (formato)

Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita. Esse elemento é usado ao definir como um novo grupo de objetos é exibido.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) CustomItem CustomEntry para elemento de quadro GroupBy (formato) CustomItem para elemento GroupBy (formato) FirstLineIndent de quadro para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `FirstLineIndent` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de quadro para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)|Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.|

## <a name="text-value"></a>Valor de texto

Especifique o número de caracteres que você deseja deslocar a primeira linha dos dados.

## <a name="remarks"></a>Comentários

Se esse elemento for especificado, não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) elemento.

## <a name="see-also"></a>Consulte Também

[Elemento FirstLineHanging para quadro de GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Elemento de quadro para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
