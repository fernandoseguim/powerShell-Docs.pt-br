---
title: Declaração de atributo de parâmetro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "56863612"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="8a045-102">Declaração de atributo de parâmetro</span><span class="sxs-lookup"><span data-stu-id="8a045-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="8a045-103">O atributo de parâmetro identifica uma propriedade pública da classe cmdlet como um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8a045-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a045-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a045-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="8a045-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a045-105">Parameters</span></span>

<span data-ttu-id="8a045-106">`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional.</span><span class="sxs-lookup"><span data-stu-id="8a045-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="8a045-107">`True` Indica se que o parâmetro de cmdlet é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8a045-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="8a045-108">Se um parâmetro obrigatório não for fornecido quando o cmdlet é invocado, o Windows PowerShell solicitará ao usuário para um valor de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a045-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="8a045-109">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="8a045-109">The default is `false`.</span></span>

<span data-ttu-id="8a045-110">`ParameterSetName` ([System. String](/dotnet/api/System.String)) parâmetro nomeado opcional.</span><span class="sxs-lookup"><span data-stu-id="8a045-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="8a045-111">Especifica que o parâmetro definido que esse parâmetro de cmdlet pertence.</span><span class="sxs-lookup"><span data-stu-id="8a045-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="8a045-112">Se nenhum conjunto de parâmetro for especificado, o parâmetro pertence a todos os conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8a045-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="8a045-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) parâmetro nomeado opcional.</span><span class="sxs-lookup"><span data-stu-id="8a045-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) Optional named parameter.</span></span> <span data-ttu-id="8a045-114">Especifica a posição do parâmetro dentro de um comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a045-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="8a045-115">`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional.</span><span class="sxs-lookup"><span data-stu-id="8a045-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="8a045-116">`True` indica que o parâmetro de cmdlet obtém seu valor de um objeto de pipeline.</span><span class="sxs-lookup"><span data-stu-id="8a045-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="8a045-117">Especifique essa palavra-chave se o cmdlet acessa o completo do objeto, não apenas uma propriedade do objeto.</span><span class="sxs-lookup"><span data-stu-id="8a045-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="8a045-118">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="8a045-118">The default is `false`.</span></span>

<span data-ttu-id="8a045-119">`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional.</span><span class="sxs-lookup"><span data-stu-id="8a045-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="8a045-120">`True` indica que o parâmetro de cmdlet obtém seu valor de uma propriedade de um objeto de pipeline que tem o mesmo nome ou o mesmo alias como este parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a045-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="8a045-121">Por exemplo, se o cmdlet tem um `Name` parâmetro e o objeto de pipeline também tem uma `Name` propriedade, o valor da `Name` propriedade é atribuída ao `Name` parâmetro do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8a045-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="8a045-122">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="8a045-122">The default is `false`.</span></span>

<span data-ttu-id="8a045-123">`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional.</span><span class="sxs-lookup"><span data-stu-id="8a045-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="8a045-124">`True` indica que o parâmetro de cmdlet aceita todos os argumentos restantes passados para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8a045-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="8a045-125">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="8a045-125">The default is `false`.</span></span>

<span data-ttu-id="8a045-126">`HelpMessage` Parâmetro nomeado opcional.</span><span class="sxs-lookup"><span data-stu-id="8a045-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="8a045-127">Especifica uma breve descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a045-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="8a045-128">Windows PowerShell exibe esta mensagem quando um cmdlet é executado e um parâmetro obrigatório não for especificado.</span><span class="sxs-lookup"><span data-stu-id="8a045-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="8a045-129">`HelpMessageBaseName` Parâmetro nomeado opcional. Especifica o local onde residem os identificadores de recurso.</span><span class="sxs-lookup"><span data-stu-id="8a045-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="8a045-130">Por exemplo, esse parâmetro pode especificar um assembly de recurso que contém mensagens de Ajuda que você deseja localizar.</span><span class="sxs-lookup"><span data-stu-id="8a045-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="8a045-131">`HelpMessageResourceId` Parâmetro nomeado opcional. Especifica o identificador de recurso para uma mensagem de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="8a045-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a045-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a045-132">Remarks</span></span>

- <span data-ttu-id="8a045-133">Para obter mais informações sobre como declarar esse atributo, consulte [como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8a045-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="8a045-134">Um cmdlet pode ter qualquer número de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8a045-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="8a045-135">No entanto, para uma melhor experiência de usuário, limite o número de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8a045-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="8a045-136">Parâmetros devem ser declarados em campos de não estáticos públicos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="8a045-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="8a045-137">Parâmetros devem ser declarados em Propriedades.</span><span class="sxs-lookup"><span data-stu-id="8a045-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="8a045-138">A propriedade deve ter um acessador set públicos e se o `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` palavra-chave for especificado, a propriedade deve ter um acessador get público.</span><span class="sxs-lookup"><span data-stu-id="8a045-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="8a045-139">Quando você especificar parâmetros posicionais, limite o número de parâmetros posicionais em um parâmetro definido para menos de cinco.</span><span class="sxs-lookup"><span data-stu-id="8a045-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="8a045-140">E, parâmetros posicionais não precisa ser contíguas.</span><span class="sxs-lookup"><span data-stu-id="8a045-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="8a045-141">Posições 5, 100 e 250 funcionam da mesma maneira posições 0, 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="8a045-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="8a045-142">Quando o `Position` palavra-chave não for especificado, o parâmetro de cmdlet deve ser referenciado por seu nome.</span><span class="sxs-lookup"><span data-stu-id="8a045-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="8a045-143">Quando você usa conjuntos de parâmetros, observe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8a045-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="8a045-144">Cada conjunto de parâmetro deve ter pelo menos um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="8a045-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="8a045-145">Cmdlet bom design indica que esse parâmetro exclusivo também é necessário obrigatório se possível.</span><span class="sxs-lookup"><span data-stu-id="8a045-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="8a045-146">Se seu cmdlet é projetado para ser executado sem parâmetros, o parâmetro unique não pode ser obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8a045-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="8a045-147">Nenhum conjunto de parâmetros deve conter mais de um parâmetro posicional com a mesma posição.</span><span class="sxs-lookup"><span data-stu-id="8a045-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="8a045-148">Apenas um parâmetro em um conjunto de parâmetros deve declarar `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="8a045-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="8a045-149">Vários parâmetros podem definir `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="8a045-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="8a045-150">Vários parâmetros podem definir `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="8a045-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="8a045-151">Para obter mais informações sobre as diretrizes para nomes de parâmetro, consulte [nomes de parâmetro de Cmdlet](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="8a045-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="8a045-152">O atributo de parâmetro é definido pela [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="8a045-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a045-153">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8a045-153">See Also</span></span>

[<span data-ttu-id="8a045-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="8a045-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="8a045-155">Nomes de parâmetro de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8a045-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

<span data-ttu-id="8a045-156">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="8a045-156">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
