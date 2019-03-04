---
title: Elemento de controle para controles para configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858882"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Elemento Control para Controls para Configuration (formato)

Define um controle comum que pode ser usado por todas as exibições do arquivo de formatação e o nome que é usado para fazer referência ao controle.

Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos e elementos filho do elemento pai o `Control` elemento. Você deve especificar apenas um de cada elemento filho.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento CustomControl para o controle para controles de configuração (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Elemento necessário.<br /><br /> Define o controle.|
|[Elemento Name para o controle para a configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)|Elemento necessário.<br /><br /> Especifica o nome usado para fazer referência ao controle.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controles de configuração (formato)](./controls-element-for-configuration-format.md)|Define os controles comuns que podem ser usados por todos os modos de exibição do arquivo de formatação ou por outros controles.|

## <a name="remarks"></a>Comentários

O nome fornecido para esse controle pode ser referenciado nos elementos a seguir:

- [Elemento ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [Elemento GroupBy para View(Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Consulte Também

[Elemento de controles de configuração (formato)](./controls-element-for-configuration-format.md)

[Elemento CustomControl para controle de configuração (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento GroupBy para View(Format)](./groupby-element-for-view-format.md)

[Elemento Name para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
