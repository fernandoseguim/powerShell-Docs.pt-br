---
title: Controla o elemento de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861172"
---
# <a name="controls-element-for-configuration-format"></a>Elemento Controls para Configuration (formato)

Define os controles comuns que podem ser usados por todos os modos de exibição do arquivo de formatação.

Elemento de controles de (formato) do elemento de configuração da configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Controls` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controle para controles de configuração (formato)](./control-element-for-controls-for-configuration-format.md)|Elemento necessário.<br /><br /> Define um controle comum que pode ser usado por todos os modos de exibição do arquivo de formatação.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de configuração (formato)](./configuration-element-format.md)|Representa o elemento de nível superior de um arquivo de formatação.|

## <a name="remarks"></a>Comentários

Você pode criar qualquer número de controles comuns. Para cada controle, você deve especificar o nome que é usado para referenciar o controle e os componentes do controle.

## <a name="see-also"></a>Consulte Também

[Elemento de configuração (formato)](./configuration-element-format.md)

[Elemento de controle para controles de configuração (formato)](./control-element-for-controls-for-configuration-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
