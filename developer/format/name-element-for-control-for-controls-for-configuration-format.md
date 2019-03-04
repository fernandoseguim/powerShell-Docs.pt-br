---
title: Nome de elemento para o controle para controles para configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860082"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Elemento Name para Control para Controls para Configuration (formato)

Especifica o nome do controle. Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.

Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de nome de configuração (formato) para o controle para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Name` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controle para controles de configuração (formato)](./control-element-for-controls-for-configuration-format.md)|Define um controle comum que pode ser usado por todas as exibições do arquivo de formatação e o nome que é usado para fazer referência ao controle.|

## <a name="text-value"></a>Valor de texto

Especifique o nome que é usado para fazer referência a esse controle.

## <a name="remarks"></a>Comentários

O nome especificado aqui pode ser usado nos elementos a seguir para fazer referência a esse controle.

- Ao criar uma tabela, a lista, o modo de exibição de controle personalizado ou ampla, o controle pode ser especificado pelo elemento a seguir: [Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)

- Ao criar outro controle comum, esse controle pode ser especificado pelo elemento a seguir: [Elemento ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Ao criar um controle que pode ser usado por um modo de exibição, esse controle pode ser especificado pelo elemento a seguir: [Elemento ExpressionBinding para CustomItem controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Consulte Também

[Elemento de controle para controles de configuração (formato)](./control-element-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento ExpressionBinding para CustomItem controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
