---
title: Elemento de quadros para CustomItem para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862972"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Elemento Frame para CustomItem para Controls para Configuration (formato)

Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl controles para o elemento de configuração (formato) de CustomItem para CustomEntry controles para o elemento de quadro de configuração para CustomItem para controles de configuração (formato)

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
|[Elemento FirstLineHanging de quadro para controles de configuração (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda.|
|[Elemento FirstLineIndent de quadro para controles de configuração (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita.|
|[Elemento LeftIndent de quadro para controles de configuração (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica o número de caracteres de dados são deslocados da margem esquerda.|
|[Elemento RightIndent de quadro para controles de configuração (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica o número de caracteres de dados são deslocados da margem direita.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomItem para CustomEntry para controles de configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Define quais dados são exibidos pelo controle e como ele é exibido.|

## <a name="remarks"></a>Comentários

Não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementos no mesmo `Frame` elemento.

## <a name="see-also"></a>Consulte Também

[Elemento FirstLineHanging de quadro para controles de configuração (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Elemento FirstLineIndent de quadro para controles de configuração (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento LeftIndent de quadro para controles de configuração (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento RightIndent de quadro para controles de configuração (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento CustomItem para CustomEntry para controles de configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
