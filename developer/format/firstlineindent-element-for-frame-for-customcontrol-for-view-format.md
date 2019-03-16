---
title: Elemento FirstLineIndent de quadro para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054842"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>Elemento FirstLineIndent para Frame para CustomControl para View (formato)

Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita. Esse elemento é usado ao definir uma exibição de controle personalizado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de quadro CustomControlView (formato) CustomItem para CustomControl para elemento de FirstLineIndent de exibição (formato)

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
|[Elemento de quadro para CustomItem para CustomControl para exibição (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.|

## <a name="text-value"></a>Valor de texto

Especifique o número de caracteres que você deseja deslocar a primeira linha dos dados.

## <a name="remarks"></a>Comentários

Se esse elemento for especificado, não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) elemento.

## <a name="see-also"></a>Consulte Também

[Elemento FirstLineHanging de quadro para CustomControl para exibição (formato)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento de quadro para CustomItem para CustomControl para exibição (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
