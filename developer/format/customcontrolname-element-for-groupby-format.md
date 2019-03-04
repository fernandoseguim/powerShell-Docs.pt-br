---
title: Elemento CustomControlName para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860302"
---
# <a name="customcontrolname-element-for-groupby-format"></a>Elemento CustomControlName para GroupBy (formato)

Especifica o nome de um controle personalizado que é usado para exibir o novo grupo. Esse elemento é usado durante a definição de uma tabela, a lista, o modo de exibição de controle personalizado ou largos.

Elemento (formato) elemento ViewDefinitions (formato) exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControlName elemento de GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, elementos filho e elementos pai do `CustomControlName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

Nenhum.

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)|Define como o Windows PowerShell exibe um novo grupo de objetos.|

## <a name="text-value"></a>Valor de texto

Especifique o nome do controle personalizado que é usado para exibir um novo grupo.

## <a name="remarks"></a>Comentários

Você pode criar controles comuns que podem ser usados por todas as exibições de um arquivo de formatação, e você pode criar controles de exibição que podem ser usados por uma exibição específica. Os elementos a seguir especificam os nomes desses controles personalizados:

- [Elemento Name para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento Name para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Consulte Também

[Elemento GroupBy para exibição (formato)](./groupby-element-for-view-format.md)

[Elemento Name para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento Name para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
