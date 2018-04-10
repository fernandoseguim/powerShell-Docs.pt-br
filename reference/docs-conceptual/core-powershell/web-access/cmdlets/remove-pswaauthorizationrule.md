---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: remove pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 28dbfe84827d6ccb99dce1ebb520cae66dc8c50e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="5e812-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="5e812-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="5e812-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="5e812-104">SYNOPSIS</span></span>

<span data-ttu-id="5e812-105">Remove uma regra de autorização especificada do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="5e812-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="5e812-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="5e812-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="5e812-107">Id</span><span class="sxs-lookup"><span data-stu-id="5e812-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="5e812-108">Regra</span><span class="sxs-lookup"><span data-stu-id="5e812-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="5e812-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="5e812-109">DESCRIPTION</span></span>

<span data-ttu-id="5e812-110">Remove uma regra de autorização especificada do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="5e812-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="5e812-111">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="5e812-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="5e812-112">-Force</span><span class="sxs-lookup"><span data-stu-id="5e812-112">-Force</span></span>

<span data-ttu-id="5e812-113">Executa o cmdlet sem solicitar confirmação.</span><span class="sxs-lookup"><span data-stu-id="5e812-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="5e812-114">Por padrão, o cmdlet solicita confirmação antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5e812-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="5e812-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="5e812-115">Aliases</span></span>                              | <span data-ttu-id="5e812-116">none</span><span class="sxs-lookup"><span data-stu-id="5e812-116">none</span></span>                                 |
| <span data-ttu-id="5e812-117">Necessário?</span><span class="sxs-lookup"><span data-stu-id="5e812-117">Required?</span></span>                            | <span data-ttu-id="5e812-118">false</span><span class="sxs-lookup"><span data-stu-id="5e812-118">false</span></span>                                |
| <span data-ttu-id="5e812-119">Posição?</span><span class="sxs-lookup"><span data-stu-id="5e812-119">Position?</span></span>                            | <span data-ttu-id="5e812-120">chamada</span><span class="sxs-lookup"><span data-stu-id="5e812-120">named</span></span>                                |
| <span data-ttu-id="5e812-121">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="5e812-121">Default Value</span></span>                        | <span data-ttu-id="5e812-122">none</span><span class="sxs-lookup"><span data-stu-id="5e812-122">none</span></span>                                 |
| <span data-ttu-id="5e812-123">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="5e812-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5e812-124">false</span><span class="sxs-lookup"><span data-stu-id="5e812-124">false</span></span>                                |
| <span data-ttu-id="5e812-125">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="5e812-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5e812-126">false</span><span class="sxs-lookup"><span data-stu-id="5e812-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="5e812-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="5e812-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="5e812-128">Especifica as IDs (identificadores) de uma ou mais regras a serem removidas.</span><span class="sxs-lookup"><span data-stu-id="5e812-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="5e812-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="5e812-129">Aliases</span></span>                              | <span data-ttu-id="5e812-130">none</span><span class="sxs-lookup"><span data-stu-id="5e812-130">none</span></span>                                 |
| <span data-ttu-id="5e812-131">Necessário?</span><span class="sxs-lookup"><span data-stu-id="5e812-131">Required?</span></span>                            | <span data-ttu-id="5e812-132">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="5e812-132">true</span></span>                                 |
| <span data-ttu-id="5e812-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="5e812-133">Position?</span></span>                            | <span data-ttu-id="5e812-134">2</span><span class="sxs-lookup"><span data-stu-id="5e812-134">2</span></span>                                    |
| <span data-ttu-id="5e812-135">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="5e812-135">Default Value</span></span>                        | <span data-ttu-id="5e812-136">none</span><span class="sxs-lookup"><span data-stu-id="5e812-136">none</span></span>                                 |
| <span data-ttu-id="5e812-137">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="5e812-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5e812-138">Verdadeiro (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="5e812-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="5e812-139">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="5e812-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5e812-140">false</span><span class="sxs-lookup"><span data-stu-id="5e812-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="5e812-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="5e812-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="5e812-142">Especifica as regras a serem removidas.</span><span class="sxs-lookup"><span data-stu-id="5e812-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="5e812-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="5e812-143">Aliases</span></span>                              | <span data-ttu-id="5e812-144">none</span><span class="sxs-lookup"><span data-stu-id="5e812-144">none</span></span>                                 |
| <span data-ttu-id="5e812-145">Necessário?</span><span class="sxs-lookup"><span data-stu-id="5e812-145">Required?</span></span>                            | <span data-ttu-id="5e812-146">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="5e812-146">true</span></span>                                 |
| <span data-ttu-id="5e812-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="5e812-147">Position?</span></span>                            | <span data-ttu-id="5e812-148">2</span><span class="sxs-lookup"><span data-stu-id="5e812-148">2</span></span>                                    |
| <span data-ttu-id="5e812-149">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="5e812-149">Default Value</span></span>                        | <span data-ttu-id="5e812-150">none</span><span class="sxs-lookup"><span data-stu-id="5e812-150">none</span></span>                                 |
| <span data-ttu-id="5e812-151">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="5e812-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5e812-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="5e812-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="5e812-153">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="5e812-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5e812-154">false</span><span class="sxs-lookup"><span data-stu-id="5e812-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="5e812-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5e812-155">-Confirm</span></span>

<span data-ttu-id="5e812-156">Solicita que você confirme antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e812-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="5e812-157">Necessário?</span><span class="sxs-lookup"><span data-stu-id="5e812-157">Required?</span></span>                            | <span data-ttu-id="5e812-158">false</span><span class="sxs-lookup"><span data-stu-id="5e812-158">false</span></span>                                |
| <span data-ttu-id="5e812-159">Posição?</span><span class="sxs-lookup"><span data-stu-id="5e812-159">Position?</span></span>                            | <span data-ttu-id="5e812-160">chamada</span><span class="sxs-lookup"><span data-stu-id="5e812-160">named</span></span>                                |
| <span data-ttu-id="5e812-161">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="5e812-161">Default Value</span></span>                        | <span data-ttu-id="5e812-162">false</span><span class="sxs-lookup"><span data-stu-id="5e812-162">false</span></span>                                |
| <span data-ttu-id="5e812-163">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="5e812-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5e812-164">false</span><span class="sxs-lookup"><span data-stu-id="5e812-164">false</span></span>                                |
| <span data-ttu-id="5e812-165">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="5e812-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5e812-166">false</span><span class="sxs-lookup"><span data-stu-id="5e812-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="5e812-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5e812-167">-WhatIf</span></span>

<span data-ttu-id="5e812-168">Mostra o que aconteceria se o cmdlet fosse executado.</span><span class="sxs-lookup"><span data-stu-id="5e812-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5e812-169">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="5e812-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="5e812-170">Necessário?</span><span class="sxs-lookup"><span data-stu-id="5e812-170">Required?</span></span>                            | <span data-ttu-id="5e812-171">false</span><span class="sxs-lookup"><span data-stu-id="5e812-171">false</span></span>                                |
| <span data-ttu-id="5e812-172">Posição?</span><span class="sxs-lookup"><span data-stu-id="5e812-172">Position?</span></span>                            | <span data-ttu-id="5e812-173">chamada</span><span class="sxs-lookup"><span data-stu-id="5e812-173">named</span></span>                                |
| <span data-ttu-id="5e812-174">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="5e812-174">Default Value</span></span>                        | <span data-ttu-id="5e812-175">false</span><span class="sxs-lookup"><span data-stu-id="5e812-175">false</span></span>                                |
| <span data-ttu-id="5e812-176">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="5e812-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5e812-177">false</span><span class="sxs-lookup"><span data-stu-id="5e812-177">false</span></span>                                |
| <span data-ttu-id="5e812-178">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="5e812-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5e812-179">false</span><span class="sxs-lookup"><span data-stu-id="5e812-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="5e812-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="5e812-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="5e812-181">Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="5e812-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="5e812-182">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5e812-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="5e812-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="5e812-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="5e812-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="5e812-184">int\[\]</span></span>

<span data-ttu-id="5e812-185">Este cmdlet aceita uma matriz de inteiros ou uma matriz de objetos PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="5e812-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="5e812-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="5e812-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="5e812-187">Este cmdlet aceita uma matriz de inteiros ou uma matriz de objetos PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="5e812-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="5e812-188">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="5e812-188">OUTPUTS</span></span>

<span data-ttu-id="5e812-189">Este cmdlet não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="5e812-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="5e812-190">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="5e812-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="5e812-191">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="5e812-191">EXAMPLE 1</span></span>

<span data-ttu-id="5e812-192">Este exemplo remove a regra de autorização com a ID *2*.</span><span class="sxs-lookup"><span data-stu-id="5e812-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="5e812-193">EXAMPLE 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="5e812-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="5e812-194">Este exemplo remove todas as regras de autorização e também requer a confirmação do usuário.</span><span class="sxs-lookup"><span data-stu-id="5e812-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="5e812-195">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="5e812-195">Related topics</span></span>

- [<span data-ttu-id="5e812-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="5e812-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="5e812-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="5e812-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="5e812-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="5e812-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="5e812-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="5e812-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)