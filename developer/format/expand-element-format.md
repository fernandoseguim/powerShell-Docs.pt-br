---
title: Expanda o elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858572"
---
# <a name="expand-element-format"></a>Elemento Expand (formato)

Especifica como o objeto de coleção é expandido para esta definição.

Configuração (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) EnumerableExpansion elemento (formato) expanda elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Expand` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)|Define os objetos são expandidos quando eles são exibidos em uma exibição de coleção de .NET como específica.|

## <a name="text-value"></a>Valor de texto

Especifique um dos seguintes valores:

- EnumOnly: Exibe somente as propriedades dos objetos na coleção.

- CoreOnly: Exibe apenas as propriedades do objeto da coleção.

- Ambos: Exibe as propriedades dos objetos na coleção e as propriedades do objeto da coleção.

## <a name="remarks"></a>Comentários

Esse elemento é usado para definir como os objetos de coleção e os objetos na coleção são exibidos. Nesse caso, um objeto de coleção refere-se a qualquer objeto que dá suporte a **System.Collections.ICollection** interface.

O comportamento padrão é exibir somente as propriedades dos objetos na coleção.

## <a name="see-also"></a>Consulte Também

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
