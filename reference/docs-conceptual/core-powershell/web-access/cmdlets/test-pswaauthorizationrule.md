---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 1b480b68c7ce2064f42281d8c5d76156a39e0222
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2017
---
#  <a name="test-pswaauthorizationrule"></a><span data-ttu-id="44d50-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="44d50-103">Test-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="44d50-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="44d50-104">SYNOPSIS</span></span>

<span data-ttu-id="44d50-105">Verifica se existe uma regra para um usuário, computador ou ponto de extremidade especificado.</span><span class="sxs-lookup"><span data-stu-id="44d50-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="44d50-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="44d50-106">SYNTAX</span></span>

###  <a name="computername"></a><span data-ttu-id="44d50-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="44d50-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

###  <a name="connectionuri"></a><span data-ttu-id="44d50-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="44d50-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="44d50-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="44d50-109">DESCRIPTION</span></span>

<span data-ttu-id="44d50-110">O cmdlet **Test-PswaAuthorizationRule** verifica se existe uma regra para um usuário, computador ou ponto de extremidade especificado.</span><span class="sxs-lookup"><span data-stu-id="44d50-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="44d50-111">Esse cmdlet também pode ser usado para testa as regras de autorização a fim de validar se uma determinada solicitação de acesso de usuário, de computador ou de ponto de extremidade está autorizada.</span><span class="sxs-lookup"><span data-stu-id="44d50-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="44d50-112">Por padrão, esse cmdlet avalia todas as regras no arquivo de autorização.</span><span class="sxs-lookup"><span data-stu-id="44d50-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="44d50-113">No entanto, você pode especificar um subconjunto de regras a serem testadas.</span><span class="sxs-lookup"><span data-stu-id="44d50-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="44d50-114">Você pode usar este cmdlet para ajudar a solucionar problemas de falhas de autenticação.</span><span class="sxs-lookup"><span data-stu-id="44d50-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="44d50-115">Os parâmetros desse cmdlet correspondem aos campos na página de logon do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="44d50-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="44d50-116">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="44d50-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="44d50-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="44d50-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="44d50-118">Especifica o nome do computador a ser testado.</span><span class="sxs-lookup"><span data-stu-id="44d50-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="44d50-119">Aliases</span><span class="sxs-lookup"><span data-stu-id="44d50-119">Aliases</span></span>                              | <span data-ttu-id="44d50-120">none</span><span class="sxs-lookup"><span data-stu-id="44d50-120">none</span></span>                                 |
| <span data-ttu-id="44d50-121">Necessário?</span><span class="sxs-lookup"><span data-stu-id="44d50-121">Required?</span></span>                            | <span data-ttu-id="44d50-122">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="44d50-122">true</span></span>                                 |
| <span data-ttu-id="44d50-123">Posição?</span><span class="sxs-lookup"><span data-stu-id="44d50-123">Position?</span></span>                            | <span data-ttu-id="44d50-124">2</span><span class="sxs-lookup"><span data-stu-id="44d50-124">2</span></span>                                    |
| <span data-ttu-id="44d50-125">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="44d50-125">Default Value</span></span>                        | <span data-ttu-id="44d50-126">none</span><span class="sxs-lookup"><span data-stu-id="44d50-126">none</span></span>                                 |
| <span data-ttu-id="44d50-127">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="44d50-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="44d50-128">false</span><span class="sxs-lookup"><span data-stu-id="44d50-128">false</span></span>                                |
| <span data-ttu-id="44d50-129">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="44d50-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="44d50-130">false</span><span class="sxs-lookup"><span data-stu-id="44d50-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="44d50-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="44d50-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="44d50-132">Especifica o nome da configuração de sessão do Windows PowerShell, também conhecida como ponto de extremidade ou runspace, a ser testada.</span><span class="sxs-lookup"><span data-stu-id="44d50-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="44d50-133">Aliases</span><span class="sxs-lookup"><span data-stu-id="44d50-133">Aliases</span></span>                              | <span data-ttu-id="44d50-134">none</span><span class="sxs-lookup"><span data-stu-id="44d50-134">none</span></span>                                 |
| <span data-ttu-id="44d50-135">Necessário?</span><span class="sxs-lookup"><span data-stu-id="44d50-135">Required?</span></span>                            | <span data-ttu-id="44d50-136">false</span><span class="sxs-lookup"><span data-stu-id="44d50-136">false</span></span>                                |
| <span data-ttu-id="44d50-137">Posição?</span><span class="sxs-lookup"><span data-stu-id="44d50-137">Position?</span></span>                            | <span data-ttu-id="44d50-138">3</span><span class="sxs-lookup"><span data-stu-id="44d50-138">3</span></span>                                    |
| <span data-ttu-id="44d50-139">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="44d50-139">Default Value</span></span>                        | <span data-ttu-id="44d50-140">none</span><span class="sxs-lookup"><span data-stu-id="44d50-140">none</span></span>                                 |
| <span data-ttu-id="44d50-141">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="44d50-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="44d50-142">false</span><span class="sxs-lookup"><span data-stu-id="44d50-142">false</span></span>                                |
| <span data-ttu-id="44d50-143">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="44d50-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="44d50-144">false</span><span class="sxs-lookup"><span data-stu-id="44d50-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="44d50-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="44d50-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="44d50-146">Especifica o URI de conexão a ser testado.</span><span class="sxs-lookup"><span data-stu-id="44d50-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="44d50-147">Aliases</span><span class="sxs-lookup"><span data-stu-id="44d50-147">Aliases</span></span>                              | <span data-ttu-id="44d50-148">none</span><span class="sxs-lookup"><span data-stu-id="44d50-148">none</span></span>                                 |
| <span data-ttu-id="44d50-149">Necessário?</span><span class="sxs-lookup"><span data-stu-id="44d50-149">Required?</span></span>                            | <span data-ttu-id="44d50-150">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="44d50-150">true</span></span>                                 |
| <span data-ttu-id="44d50-151">Posição?</span><span class="sxs-lookup"><span data-stu-id="44d50-151">Position?</span></span>                            | <span data-ttu-id="44d50-152">2</span><span class="sxs-lookup"><span data-stu-id="44d50-152">2</span></span>                                    |
| <span data-ttu-id="44d50-153">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="44d50-153">Default Value</span></span>                        | <span data-ttu-id="44d50-154">none</span><span class="sxs-lookup"><span data-stu-id="44d50-154">none</span></span>                                 |
| <span data-ttu-id="44d50-155">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="44d50-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="44d50-156">false</span><span class="sxs-lookup"><span data-stu-id="44d50-156">false</span></span>                                |
| <span data-ttu-id="44d50-157">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="44d50-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="44d50-158">false</span><span class="sxs-lookup"><span data-stu-id="44d50-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="44d50-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="44d50-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="44d50-160">Especifica um objeto **PSCredential** para uma conta de usuário que você deseja usar para testar as regras de autorização do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="44d50-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="44d50-161">Se você não adicionar esse parâmetro, o cmdlet usará a conta do usuário conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="44d50-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="44d50-162">Para obter um objeto **PSCredential**, que é necessário para testar as regras de autorização remotamente, execute o cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).</span><span class="sxs-lookup"><span data-stu-id="44d50-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="44d50-163">Aliases</span><span class="sxs-lookup"><span data-stu-id="44d50-163">Aliases</span></span>                              | <span data-ttu-id="44d50-164">none</span><span class="sxs-lookup"><span data-stu-id="44d50-164">none</span></span>                                 |
| <span data-ttu-id="44d50-165">Necessário?</span><span class="sxs-lookup"><span data-stu-id="44d50-165">Required?</span></span>                            | <span data-ttu-id="44d50-166">false</span><span class="sxs-lookup"><span data-stu-id="44d50-166">false</span></span>                                |
| <span data-ttu-id="44d50-167">Posição?</span><span class="sxs-lookup"><span data-stu-id="44d50-167">Position?</span></span>                            | <span data-ttu-id="44d50-168">chamada</span><span class="sxs-lookup"><span data-stu-id="44d50-168">named</span></span>                                |
| <span data-ttu-id="44d50-169">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="44d50-169">Default Value</span></span>                        | <span data-ttu-id="44d50-170">none</span><span class="sxs-lookup"><span data-stu-id="44d50-170">none</span></span>                                 |
| <span data-ttu-id="44d50-171">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="44d50-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="44d50-172">false</span><span class="sxs-lookup"><span data-stu-id="44d50-172">false</span></span>                                |
| <span data-ttu-id="44d50-173">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="44d50-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="44d50-174">false</span><span class="sxs-lookup"><span data-stu-id="44d50-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="44d50-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="44d50-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="44d50-176">Especifica um subconjunto de regras a serem testadas.</span><span class="sxs-lookup"><span data-stu-id="44d50-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="44d50-177">Se esse parâmetro não for especificado, esse cmdlet testará todas as regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="44d50-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="44d50-178">Aliases</span><span class="sxs-lookup"><span data-stu-id="44d50-178">Aliases</span></span>                              | <span data-ttu-id="44d50-179">none</span><span class="sxs-lookup"><span data-stu-id="44d50-179">none</span></span>                                 |
| <span data-ttu-id="44d50-180">Necessário?</span><span class="sxs-lookup"><span data-stu-id="44d50-180">Required?</span></span>                            | <span data-ttu-id="44d50-181">false</span><span class="sxs-lookup"><span data-stu-id="44d50-181">false</span></span>                                |
| <span data-ttu-id="44d50-182">Posição?</span><span class="sxs-lookup"><span data-stu-id="44d50-182">Position?</span></span>                            | <span data-ttu-id="44d50-183">chamada</span><span class="sxs-lookup"><span data-stu-id="44d50-183">named</span></span>                                |
| <span data-ttu-id="44d50-184">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="44d50-184">Default Value</span></span>                        | <span data-ttu-id="44d50-185">none</span><span class="sxs-lookup"><span data-stu-id="44d50-185">none</span></span>                                 |
| <span data-ttu-id="44d50-186">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="44d50-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="44d50-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="44d50-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="44d50-188">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="44d50-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="44d50-189">false</span><span class="sxs-lookup"><span data-stu-id="44d50-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="44d50-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="44d50-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="44d50-191">Especifica o nome do usuário a ser testado.</span><span class="sxs-lookup"><span data-stu-id="44d50-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="44d50-192">Aliases</span><span class="sxs-lookup"><span data-stu-id="44d50-192">Aliases</span></span>                              | <span data-ttu-id="44d50-193">none</span><span class="sxs-lookup"><span data-stu-id="44d50-193">none</span></span>                                 |
| <span data-ttu-id="44d50-194">Necessário?</span><span class="sxs-lookup"><span data-stu-id="44d50-194">Required?</span></span>                            | <span data-ttu-id="44d50-195">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="44d50-195">true</span></span>                                 |
| <span data-ttu-id="44d50-196">Posição?</span><span class="sxs-lookup"><span data-stu-id="44d50-196">Position?</span></span>                            | <span data-ttu-id="44d50-197">1</span><span class="sxs-lookup"><span data-stu-id="44d50-197">1</span></span>                                    |
| <span data-ttu-id="44d50-198">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="44d50-198">Default Value</span></span>                        | <span data-ttu-id="44d50-199">none</span><span class="sxs-lookup"><span data-stu-id="44d50-199">none</span></span>                                 |
| <span data-ttu-id="44d50-200">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="44d50-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="44d50-201">false</span><span class="sxs-lookup"><span data-stu-id="44d50-201">false</span></span>                                |
| <span data-ttu-id="44d50-202">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="44d50-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="44d50-203">false</span><span class="sxs-lookup"><span data-stu-id="44d50-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="44d50-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="44d50-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="44d50-205">Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="44d50-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="44d50-206">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="44d50-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="44d50-207">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="44d50-207">INPUTS</span></span>

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="44d50-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="44d50-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="44d50-209">Este cmdlet aceita uma matriz de objetos PswaAuthorizationRule como entrada.</span><span class="sxs-lookup"><span data-stu-id="44d50-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="44d50-210">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="44d50-210">OUTPUTS</span></span>

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="44d50-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="44d50-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="44d50-212">Esse cmdlet gera uma matriz de objetos PswaAuthorizationRule como saída.</span><span class="sxs-lookup"><span data-stu-id="44d50-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="44d50-213">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="44d50-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="44d50-214">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="44d50-214">EXAMPLE 1</span></span>

<span data-ttu-id="44d50-215">Este exemplo testa todas as regras de autorização para exibir todas as regras que permitem que o usuário *contoso\\mhanson* se conecte ao computador *srv2* e use uma configuração de sessão do Windows PowerShell chamada *teste*.</span><span class="sxs-lookup"><span data-stu-id="44d50-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="44d50-216">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="44d50-216">EXAMPLE 2</span></span>

<span data-ttu-id="44d50-217">Este exemplo testa todas as regras de autorização para verificar quais regras de autorização se aplicam ao usuário *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="44d50-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

##  <a name="related-topics"></a><span data-ttu-id="44d50-218">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="44d50-218">Related topics</span></span>

-  [<span data-ttu-id="44d50-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="44d50-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="44d50-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="44d50-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
-  [<span data-ttu-id="44d50-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="44d50-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
-  [<span data-ttu-id="44d50-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="44d50-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
