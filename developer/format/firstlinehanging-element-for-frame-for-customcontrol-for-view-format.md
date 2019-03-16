---
title: Elemento FirstLineHanging de quadro para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054213"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>Elemento FirstLineHanging para Frame para CustomControl para View (formato)

Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda. Esse elemento é usado ao definir uma exibição de controle personalizado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de quadro CustomControlView (formato) CustomItem para CustomControl para exibição (formato) FirstLineHanging elemento de quadro para CustomControl para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `FirstLineHanging` elemento.

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

Se esse elemento for especificado, não é possível especificar o [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elemento.

## <a name="see-also"></a>Consulte Também

[Elemento FirstLineIndent de quadro para CustomControl para exibição (formato)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento de quadro para CustomItem para CustomControl para exibição (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
