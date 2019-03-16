---
title: Elemento de quadro para CustomItem para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054774"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Elemento Frame para CustomItem para CustomControl para View (formato)

Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita. Esse elemento é usado ao definir uma exibição de controle personalizado.

Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de quadro CustomControlView (formato) CustomItem para CustomControl para exibição (formato)

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
|[Elemento FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda.|
|[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita.|
|[Elemento LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de caracteres de dados são deslocados da margem esquerda.|
|[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de caracteres de dados são deslocados da margem direita.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Define quais dados são exibidos pelo controle e como ele é exibido.|

## <a name="remarks"></a>Comentários

Não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementos no mesmo `Frame` elemento.

## <a name="see-also"></a>Consulte Também

[Elemento FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento CustomItem para CustomEntry para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
