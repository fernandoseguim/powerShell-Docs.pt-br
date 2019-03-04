---
title: Parâmetros do cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853842"
---
# <a name="cmdlet-parameters"></a>Parâmetros de cmdlets

Parâmetros do cmdlet fornecem o mecanismo que permite que um cmdlet aceitar a entrada. Parâmetros podem aceitar diretamente da linha de comando ou de objetos passados para o cmdlet por meio do pipeline, os argumentos de entrada (também conhecido como *valores*) desses parâmetros pode especificar a entrada que o cmdlet aceita, como o cmdlet deve executar suas ações e os dados que o cmdlet retorna para o pipeline.

## <a name="in-this-section"></a>Nesta seção

[Declarando propriedades como parâmetros](./declaring-properties-as-parameters.md) fornece informações básicas, você deve compreender antes de você declarar os parâmetros de um cmdlet.

[Tipos de parâmetros do Cmdlet](./types-of-cmdlet-parameters.md) descreve os diferentes tipos de parâmetros que você pode declarar nos cmdlets.

[Nome do parâmetro de cmdlet e diretrizes de funcionalidade](./standard-cmdlet-parameter-names-and-types.md) descreve os nomes, tipo de dados e a funcionalidade dos parâmetros padrão recomendados.

[Aliases de parâmetro](./parameter-aliases.md) discute os aliases que você pode definir para parâmetros.

[Os nomes de parâmetro comuns](./common-parameter-names.md) este tópico descreve os parâmetros que o Windows PowerShell adiciona aos cmdlets.

[Conjuntos de parâmetros do cmdlet](./cmdlet-parameter-sets.md) discute como conjuntos de parâmetros permitem escrever um único cmdlet que pode executar ações diferentes para diferentes cenários.

[Parâmetros dinâmicos de cmdlet](./cmdlet-dynamic-parameters.md) aborda os parâmetros que estão disponíveis para o usuário sob condições especiais.

[Suporte a caracteres curinga em parâmetros do Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) descreve como fornecer suporte para caracteres curinga, quando você projeta um cmdlet que será executado em relação a um grupo de recursos.

[Validação de parâmetro de entrada](./validating-parameter-input.md) descreve como o Windows PowerShell valida os argumentos passados para os parâmetros do cmdlet.

[Parâmetros de filtro de entrada](./input-filter-parameters.md) aborda o `Filter`, `Include`, e `Exclude` parâmetros que filtram o conjunto de objetos de entrada que afeta o cmdlet.

## <a name="related-sections"></a>Seções pertinentes

[Como validar a entrada de parâmetro](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Consulte Também

[Declaração de atributo de parâmetro](./parameter-attribute-declaration.md)

[Cmdlets do Windows PowerShell](./cmdlet-overview.md)
