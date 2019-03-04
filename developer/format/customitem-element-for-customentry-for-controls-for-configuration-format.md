---
title: Elemento CustomItem para CustomEntry para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862932"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>Elemento CustomItem para CustomEntry para Controls para Configuration (formato)

Define quais dados são exibidos pelo controle e como ele é exibido. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl controles para o elemento de configuração (formato) de CustomItem para CustomEntry para controles de configuração

## <a name="syntax"></a>Sintaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomItem` elemento. Para obter mais informações, consulte comentários.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define os dados que são exibidos pelo controle.|
|[Elemento de quadro para CustomItem para controles de configuração (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.|
|[Elemento de nova linha para CustomItem para controles de configuração (formato)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Adiciona uma linha em branco para a exibição do controle.|
|[Elemento de texto para CustomItem para controles de configuração (formato)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Adiciona texto, como parênteses ou colchetes, para a exibição do controle.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomEntry para CustomControl para controles de configuração (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornece uma definição do controle.|

## <a name="remarks"></a>Comentários

Ao especificar os elementos filho do `CustomItem` elemento, tenha em mente o seguinte:

- Os elementos filho devem ser adicionados na sequência a seguir: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.

- Não há nenhum limite máximo ao número de sequências que você pode especificar.

- Em cada sequência, não há nenhum limite máximo ao número de `ExpressionBinding` elementos que você pode usar.

## <a name="see-also"></a>Consulte Também

[Elemento ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento de quadro para CustomItem para controles de configuração (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento de nova linha para CustomItem para controles de configuração (formato)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento de texto para CustomItem para controles de configuração (formato)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
