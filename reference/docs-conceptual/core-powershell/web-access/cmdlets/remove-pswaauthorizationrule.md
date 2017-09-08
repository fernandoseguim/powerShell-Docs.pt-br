---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: remove pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: d316cb98efc730ed3e99f6a5dac2b969e3437129
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2017
---
#  <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="91d5a-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="91d5a-103">Remove-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="91d5a-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="91d5a-104">SYNOPSIS</span></span>

<span data-ttu-id="91d5a-105">Remove uma regra de autorização especificada do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="91d5a-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="91d5a-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="91d5a-106">SYNTAX</span></span>

###  <a name="id"></a><span data-ttu-id="91d5a-107">Id</span><span class="sxs-lookup"><span data-stu-id="91d5a-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="91d5a-108">Regra</span><span class="sxs-lookup"><span data-stu-id="91d5a-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="91d5a-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="91d5a-109">DESCRIPTION</span></span>

<span data-ttu-id="91d5a-110">Remove uma regra de autorização especificada do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="91d5a-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="91d5a-111">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="91d5a-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="91d5a-112">-Force</span><span class="sxs-lookup"><span data-stu-id="91d5a-112">-Force</span></span>

<span data-ttu-id="91d5a-113">Executa o cmdlet sem solicitar confirmação.</span><span class="sxs-lookup"><span data-stu-id="91d5a-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="91d5a-114">Por padrão, o cmdlet solicita confirmação antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="91d5a-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="91d5a-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="91d5a-115">Aliases</span></span>                              | <span data-ttu-id="91d5a-116">none</span><span class="sxs-lookup"><span data-stu-id="91d5a-116">none</span></span>                                 |
| <span data-ttu-id="91d5a-117">Necessário?</span><span class="sxs-lookup"><span data-stu-id="91d5a-117">Required?</span></span>                            | <span data-ttu-id="91d5a-118">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-118">false</span></span>                                |
| <span data-ttu-id="91d5a-119">Posição?</span><span class="sxs-lookup"><span data-stu-id="91d5a-119">Position?</span></span>                            | <span data-ttu-id="91d5a-120">chamada</span><span class="sxs-lookup"><span data-stu-id="91d5a-120">named</span></span>                                |
| <span data-ttu-id="91d5a-121">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="91d5a-121">Default Value</span></span>                        | <span data-ttu-id="91d5a-122">none</span><span class="sxs-lookup"><span data-stu-id="91d5a-122">none</span></span>                                 |
| <span data-ttu-id="91d5a-123">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="91d5a-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="91d5a-124">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-124">false</span></span>                                |
| <span data-ttu-id="91d5a-125">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="91d5a-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="91d5a-126">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="91d5a-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="91d5a-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="91d5a-128">Especifica as IDs (identificadores) de uma ou mais regras a serem removidas.</span><span class="sxs-lookup"><span data-stu-id="91d5a-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="91d5a-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="91d5a-129">Aliases</span></span>                              | <span data-ttu-id="91d5a-130">none</span><span class="sxs-lookup"><span data-stu-id="91d5a-130">none</span></span>                                 |
| <span data-ttu-id="91d5a-131">Necessário?</span><span class="sxs-lookup"><span data-stu-id="91d5a-131">Required?</span></span>                            | <span data-ttu-id="91d5a-132">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="91d5a-132">true</span></span>                                 |
| <span data-ttu-id="91d5a-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="91d5a-133">Position?</span></span>                            | <span data-ttu-id="91d5a-134">2</span><span class="sxs-lookup"><span data-stu-id="91d5a-134">2</span></span>                                    |
| <span data-ttu-id="91d5a-135">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="91d5a-135">Default Value</span></span>                        | <span data-ttu-id="91d5a-136">none</span><span class="sxs-lookup"><span data-stu-id="91d5a-136">none</span></span>                                 |
| <span data-ttu-id="91d5a-137">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="91d5a-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="91d5a-138">Verdadeiro (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="91d5a-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="91d5a-139">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="91d5a-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="91d5a-140">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="91d5a-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="91d5a-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="91d5a-142">Especifica as regras a serem removidas.</span><span class="sxs-lookup"><span data-stu-id="91d5a-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="91d5a-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="91d5a-143">Aliases</span></span>                              | <span data-ttu-id="91d5a-144">none</span><span class="sxs-lookup"><span data-stu-id="91d5a-144">none</span></span>                                 |
| <span data-ttu-id="91d5a-145">Necessário?</span><span class="sxs-lookup"><span data-stu-id="91d5a-145">Required?</span></span>                            | <span data-ttu-id="91d5a-146">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="91d5a-146">true</span></span>                                 |
| <span data-ttu-id="91d5a-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="91d5a-147">Position?</span></span>                            | <span data-ttu-id="91d5a-148">2</span><span class="sxs-lookup"><span data-stu-id="91d5a-148">2</span></span>                                    |
| <span data-ttu-id="91d5a-149">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="91d5a-149">Default Value</span></span>                        | <span data-ttu-id="91d5a-150">none</span><span class="sxs-lookup"><span data-stu-id="91d5a-150">none</span></span>                                 |
| <span data-ttu-id="91d5a-151">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="91d5a-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="91d5a-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="91d5a-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="91d5a-153">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="91d5a-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="91d5a-154">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="91d5a-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="91d5a-155">-Confirm</span></span>

<span data-ttu-id="91d5a-156">Solicita que você confirme antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91d5a-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="91d5a-157">Necessário?</span><span class="sxs-lookup"><span data-stu-id="91d5a-157">Required?</span></span>                            | <span data-ttu-id="91d5a-158">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-158">false</span></span>                                |
| <span data-ttu-id="91d5a-159">Posição?</span><span class="sxs-lookup"><span data-stu-id="91d5a-159">Position?</span></span>                            | <span data-ttu-id="91d5a-160">chamada</span><span class="sxs-lookup"><span data-stu-id="91d5a-160">named</span></span>                                |
| <span data-ttu-id="91d5a-161">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="91d5a-161">Default Value</span></span>                        | <span data-ttu-id="91d5a-162">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-162">false</span></span>                                |
| <span data-ttu-id="91d5a-163">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="91d5a-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="91d5a-164">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-164">false</span></span>                                |
| <span data-ttu-id="91d5a-165">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="91d5a-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="91d5a-166">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="91d5a-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="91d5a-167">-WhatIf</span></span>

<span data-ttu-id="91d5a-168">Mostra o que aconteceria se o cmdlet fosse executado.</span><span class="sxs-lookup"><span data-stu-id="91d5a-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="91d5a-169">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="91d5a-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="91d5a-170">Necessário?</span><span class="sxs-lookup"><span data-stu-id="91d5a-170">Required?</span></span>                            | <span data-ttu-id="91d5a-171">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-171">false</span></span>                                |
| <span data-ttu-id="91d5a-172">Posição?</span><span class="sxs-lookup"><span data-stu-id="91d5a-172">Position?</span></span>                            | <span data-ttu-id="91d5a-173">chamada</span><span class="sxs-lookup"><span data-stu-id="91d5a-173">named</span></span>                                |
| <span data-ttu-id="91d5a-174">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="91d5a-174">Default Value</span></span>                        | <span data-ttu-id="91d5a-175">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-175">false</span></span>                                |
| <span data-ttu-id="91d5a-176">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="91d5a-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="91d5a-177">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-177">false</span></span>                                |
| <span data-ttu-id="91d5a-178">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="91d5a-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="91d5a-179">false</span><span class="sxs-lookup"><span data-stu-id="91d5a-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="91d5a-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="91d5a-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="91d5a-181">Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="91d5a-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="91d5a-182">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="91d5a-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="91d5a-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="91d5a-183">INPUTS</span></span>

###  <a name="int"></a><span data-ttu-id="91d5a-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="91d5a-184">int\[\]</span></span>

<span data-ttu-id="91d5a-185">Este cmdlet aceita uma matriz de inteiros ou uma matriz de objetos PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="91d5a-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

###  <a name="pswaauthorizationrule"></a><span data-ttu-id="91d5a-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="91d5a-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="91d5a-187">Este cmdlet aceita uma matriz de inteiros ou uma matriz de objetos PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="91d5a-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

##  <a name="outputs"></a><span data-ttu-id="91d5a-188">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="91d5a-188">OUTPUTS</span></span>

<span data-ttu-id="91d5a-189">Este cmdlet não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="91d5a-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="91d5a-190">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="91d5a-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="91d5a-191">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="91d5a-191">EXAMPLE 1</span></span>

<span data-ttu-id="91d5a-192">Este exemplo remove a regra de autorização com a ID *2*.</span><span class="sxs-lookup"><span data-stu-id="91d5a-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="91d5a-193">EXAMPLE 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="91d5a-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="91d5a-194">Este exemplo remove todas as regras de autorização e também requer a confirmação do usuário.</span><span class="sxs-lookup"><span data-stu-id="91d5a-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

##  <a name="related-topics"></a><span data-ttu-id="91d5a-195">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="91d5a-195">Related topics</span></span>

-  [<span data-ttu-id="91d5a-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="91d5a-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="91d5a-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="91d5a-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
-  [<span data-ttu-id="91d5a-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="91d5a-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
-  [<span data-ttu-id="91d5a-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="91d5a-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
