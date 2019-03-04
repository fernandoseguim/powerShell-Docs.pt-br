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
# <a name="cmdlet-parameters"></a><span data-ttu-id="40937-102">Parâmetros de cmdlets</span><span class="sxs-lookup"><span data-stu-id="40937-102">Cmdlet Parameters</span></span>

<span data-ttu-id="40937-103">Parâmetros do cmdlet fornecem o mecanismo que permite que um cmdlet aceitar a entrada.</span><span class="sxs-lookup"><span data-stu-id="40937-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="40937-104">Parâmetros podem aceitar diretamente da linha de comando ou de objetos passados para o cmdlet por meio do pipeline, os argumentos de entrada (também conhecido como *valores*) desses parâmetros pode especificar a entrada que o cmdlet aceita, como o cmdlet deve executar suas ações e os dados que o cmdlet retorna para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="40937-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="40937-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="40937-105">In This Section</span></span>

<span data-ttu-id="40937-106">[Declarando propriedades como parâmetros](./declaring-properties-as-parameters.md) fornece informações básicas, você deve compreender antes de você declarar os parâmetros de um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40937-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="40937-107">[Tipos de parâmetros do Cmdlet](./types-of-cmdlet-parameters.md) descreve os diferentes tipos de parâmetros que você pode declarar nos cmdlets.</span><span class="sxs-lookup"><span data-stu-id="40937-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="40937-108">[Nome do parâmetro de cmdlet e diretrizes de funcionalidade](./standard-cmdlet-parameter-names-and-types.md) descreve os nomes, tipo de dados e a funcionalidade dos parâmetros padrão recomendados.</span><span class="sxs-lookup"><span data-stu-id="40937-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="40937-109">[Aliases de parâmetro](./parameter-aliases.md) discute os aliases que você pode definir para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="40937-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="40937-110">[Os nomes de parâmetro comuns](./common-parameter-names.md) este tópico descreve os parâmetros que o Windows PowerShell adiciona aos cmdlets.</span><span class="sxs-lookup"><span data-stu-id="40937-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="40937-111">[Conjuntos de parâmetros do cmdlet](./cmdlet-parameter-sets.md) discute como conjuntos de parâmetros permitem escrever um único cmdlet que pode executar ações diferentes para diferentes cenários.</span><span class="sxs-lookup"><span data-stu-id="40937-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="40937-112">[Parâmetros dinâmicos de cmdlet](./cmdlet-dynamic-parameters.md) aborda os parâmetros que estão disponíveis para o usuário sob condições especiais.</span><span class="sxs-lookup"><span data-stu-id="40937-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="40937-113">[Suporte a caracteres curinga em parâmetros do Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) descreve como fornecer suporte para caracteres curinga, quando você projeta um cmdlet que será executado em relação a um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="40937-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="40937-114">[Validação de parâmetro de entrada](./validating-parameter-input.md) descreve como o Windows PowerShell valida os argumentos passados para os parâmetros do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40937-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="40937-115">[Parâmetros de filtro de entrada](./input-filter-parameters.md) aborda o `Filter`, `Include`, e `Exclude` parâmetros que filtram o conjunto de objetos de entrada que afeta o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40937-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="40937-116">Seções pertinentes</span><span class="sxs-lookup"><span data-stu-id="40937-116">Related Sections</span></span>

[<span data-ttu-id="40937-117">Como validar a entrada de parâmetro</span><span class="sxs-lookup"><span data-stu-id="40937-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="40937-118">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="40937-118">See Also</span></span>

[<span data-ttu-id="40937-119">Declaração de atributo de parâmetro</span><span class="sxs-lookup"><span data-stu-id="40937-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="40937-120">Cmdlets do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="40937-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
