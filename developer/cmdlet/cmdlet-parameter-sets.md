---
title: Define um parâmetro de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857262"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="45bf8-102">Conjuntos de parâmetros do cmdlet</span><span class="sxs-lookup"><span data-stu-id="45bf8-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="45bf8-103">Windows PowerShell usa conjuntos de parâmetros para que você possa escrever um único cmdlet que pode executar ações diferentes para diferentes cenários.</span><span class="sxs-lookup"><span data-stu-id="45bf8-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="45bf8-104">Conjuntos de parâmetros permitem que você exponha diferentes parâmetros para o usuário e para retornar informações diferentes com base nos parâmetros especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="45bf8-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="45bf8-105">Exemplos de conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="45bf8-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="45bf8-106">Por exemplo, o `Get-EventLog` cmdlet (fornecido pelo Windows PowerShell) retorna informações diferentes dependendo se o usuário Especifica a `List` ou `LogName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="45bf8-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="45bf8-107">Se o `List` parâmetro for especificado, o cmdlet retorna informações sobre os arquivos de log em si, mas não as informações de evento que eles contêm.</span><span class="sxs-lookup"><span data-stu-id="45bf8-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="45bf8-108">Se o `LogName` parâmetro for especificado, o cmdlet retorna informações sobre os eventos em um log de eventos específico.</span><span class="sxs-lookup"><span data-stu-id="45bf8-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="45bf8-109">O `List` e `LogName` parâmetros identificam dois conjuntos de parâmetros separado.</span><span class="sxs-lookup"><span data-stu-id="45bf8-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="45bf8-110">Parâmetro exclusivo</span><span class="sxs-lookup"><span data-stu-id="45bf8-110">Unique Parameter</span></span>

<span data-ttu-id="45bf8-111">Cada conjunto de parâmetros deve ter um parâmetro exclusivo que o tempo de execução do Windows PowerShell pode usar para expor o conjunto de parâmetros apropriado.</span><span class="sxs-lookup"><span data-stu-id="45bf8-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="45bf8-112">Se possível, o parâmetro unique deve ser um parâmetro obrigatório.</span><span class="sxs-lookup"><span data-stu-id="45bf8-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="45bf8-113">Quando um parâmetro é obrigatório, o usuário é forçado para especificar o parâmetro e o tempo de execução do Windows PowerShell pode usar esse parâmetro para identificar o parâmetro definido para usar.</span><span class="sxs-lookup"><span data-stu-id="45bf8-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="45bf8-114">O parâmetro unique não pode ser obrigatório se o cmdlet foi projetado para ser executado sem especificar nenhum parâmetro.</span><span class="sxs-lookup"><span data-stu-id="45bf8-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="45bf8-115">Vários conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="45bf8-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="45bf8-116">Na ilustração a seguir, a coluna esquerda mostra três conjuntos de parâmetro válido.</span><span class="sxs-lookup"><span data-stu-id="45bf8-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="45bf8-117">Parâmetro um é exclusivo para o primeiro conjunto de parâmetros, parâmetro B é exclusivo para o segundo parâmetro definido e parâmetro C é exclusivo para o terceiro conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="45bf8-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="45bf8-118">No entanto, na coluna à direita, os conjuntos de parâmetros não tem um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="45bf8-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="45bf8-120">Requisitos do conjunto de parâmetros</span><span class="sxs-lookup"><span data-stu-id="45bf8-120">Parameter Set Requirements</span></span>

<span data-ttu-id="45bf8-121">Os seguintes requisitos se aplicam a todos os conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="45bf8-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="45bf8-122">Cada conjunto de parâmetro deve ter pelo menos um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="45bf8-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="45bf8-123">Se possível, torne este parâmetro um parâmetro obrigatório.</span><span class="sxs-lookup"><span data-stu-id="45bf8-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="45bf8-124">Um conjunto de parâmetros que contém vários parâmetros posicionais deve definir posições exclusivas para cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="45bf8-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="45bf8-125">Não há dois parâmetros posicionais podem especificar a mesma posição.</span><span class="sxs-lookup"><span data-stu-id="45bf8-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="45bf8-126">Apenas um parâmetro em um conjunto pode declarar o `ValueFromPipeline` palavra-chave com um valor de `true`.</span><span class="sxs-lookup"><span data-stu-id="45bf8-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="45bf8-127">Vários parâmetros podem definir a `ValueFromPipelineByPropertyName` palavra-chave com um valor de `true`.</span><span class="sxs-lookup"><span data-stu-id="45bf8-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="45bf8-128">Se nenhum conjunto de parâmetro for especificado para um parâmetro, o parâmetro pertence a todos os conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="45bf8-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="45bf8-129">Conjuntos de parâmetros padrão</span><span class="sxs-lookup"><span data-stu-id="45bf8-129">Default Parameter Sets</span></span>

<span data-ttu-id="45bf8-130">Quando vários conjuntos de parâmetros são definidos, você pode usar o `DefaultParameterSetName` palavra-chave do atributo Cmdlet para especificar o conjunto de parâmetros padrão.</span><span class="sxs-lookup"><span data-stu-id="45bf8-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="45bf8-131">Windows PowerShell usa o parâmetro padrão definido se não é possível determinar o parâmetro definido para usar com base nas informações fornecidas pelo comando.</span><span class="sxs-lookup"><span data-stu-id="45bf8-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="45bf8-132">Para obter mais informações sobre o atributo de Cmdlet, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="45bf8-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="45bf8-133">Declarando conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="45bf8-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="45bf8-134">Para criar um conjunto de parâmetros, você deve especificar o `ParameterSetName` palavra-chave quando você declara o atributo de parâmetro para cada parâmetro no conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="45bf8-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="45bf8-135">Para parâmetros que pertencem a vários conjuntos de parâmetros, adicione um atributo de parâmetro para cada conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="45bf8-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="45bf8-136">Isso permite que você defina o parâmetro de modo diferente para cada conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="45bf8-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="45bf8-137">Por exemplo, você pode definir um parâmetro como opcional em outra e obrigatória em um conjunto.</span><span class="sxs-lookup"><span data-stu-id="45bf8-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="45bf8-138">No entanto, cada conjunto de parâmetros deve conter um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="45bf8-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="45bf8-139">No exemplo a seguir, o `UserName` parâmetro é o parâmetro unique do conjunto de parâmetros Test01 e o `ComputerName` parâmetro é o parâmetro unique de conjunto de parâmetros Test02.</span><span class="sxs-lookup"><span data-stu-id="45bf8-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="45bf8-140">O `SharedParam` parâmetro pertence aos dois conjuntos e é obrigatório para o parâmetro de Test01 definido, mas opcional para o conjunto de parâmetros Test02.</span><span class="sxs-lookup"><span data-stu-id="45bf8-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```