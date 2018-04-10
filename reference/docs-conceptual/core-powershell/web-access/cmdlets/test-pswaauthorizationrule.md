---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: ed6d56b2f3c4ee4ac410cdaadda312bffe506ee9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="ef717-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ef717-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="ef717-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="ef717-104">SYNOPSIS</span></span>

<span data-ttu-id="ef717-105">Verifica se existe uma regra para um usuário, computador ou ponto de extremidade especificado.</span><span class="sxs-lookup"><span data-stu-id="ef717-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef717-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="ef717-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="ef717-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="ef717-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="ef717-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="ef717-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="ef717-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="ef717-109">DESCRIPTION</span></span>

<span data-ttu-id="ef717-110">O cmdlet **Test-PswaAuthorizationRule** verifica se existe uma regra para um usuário, computador ou ponto de extremidade especificado.</span><span class="sxs-lookup"><span data-stu-id="ef717-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="ef717-111">Esse cmdlet também pode ser usado para testa as regras de autorização a fim de validar se uma determinada solicitação de acesso de usuário, de computador ou de ponto de extremidade está autorizada.</span><span class="sxs-lookup"><span data-stu-id="ef717-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="ef717-112">Por padrão, esse cmdlet avalia todas as regras no arquivo de autorização.</span><span class="sxs-lookup"><span data-stu-id="ef717-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="ef717-113">No entanto, você pode especificar um subconjunto de regras a serem testadas.</span><span class="sxs-lookup"><span data-stu-id="ef717-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="ef717-114">Você pode usar este cmdlet para ajudar a solucionar problemas de falhas de autenticação.</span><span class="sxs-lookup"><span data-stu-id="ef717-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="ef717-115">Os parâmetros desse cmdlet correspondem aos campos na página de logon do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef717-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="ef717-116">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="ef717-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="ef717-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="ef717-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="ef717-118">Especifica o nome do computador a ser testado.</span><span class="sxs-lookup"><span data-stu-id="ef717-118">Specifies the name of the computer to test.</span></span>

|||
|-|-|
| <span data-ttu-id="ef717-119">Aliases</span><span class="sxs-lookup"><span data-stu-id="ef717-119">Aliases</span></span>                              | <span data-ttu-id="ef717-120">none</span><span class="sxs-lookup"><span data-stu-id="ef717-120">none</span></span>                                 |
| <span data-ttu-id="ef717-121">Necessário?</span><span class="sxs-lookup"><span data-stu-id="ef717-121">Required?</span></span>                            | <span data-ttu-id="ef717-122">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="ef717-122">true</span></span>                                 |
| <span data-ttu-id="ef717-123">Posição?</span><span class="sxs-lookup"><span data-stu-id="ef717-123">Position?</span></span>                            | <span data-ttu-id="ef717-124">2</span><span class="sxs-lookup"><span data-stu-id="ef717-124">2</span></span>                                    |
| <span data-ttu-id="ef717-125">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="ef717-125">Default Value</span></span>                        | <span data-ttu-id="ef717-126">none</span><span class="sxs-lookup"><span data-stu-id="ef717-126">none</span></span>                                 |
| <span data-ttu-id="ef717-127">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="ef717-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ef717-128">false</span><span class="sxs-lookup"><span data-stu-id="ef717-128">false</span></span>                                |
| <span data-ttu-id="ef717-129">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="ef717-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ef717-130">false</span><span class="sxs-lookup"><span data-stu-id="ef717-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="ef717-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="ef717-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="ef717-132">Especifica o nome da configuração de sessão do Windows PowerShell, também conhecida como ponto de extremidade ou runspace, a ser testada.</span><span class="sxs-lookup"><span data-stu-id="ef717-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||
|-|-|
| <span data-ttu-id="ef717-133">Aliases</span><span class="sxs-lookup"><span data-stu-id="ef717-133">Aliases</span></span>                              | <span data-ttu-id="ef717-134">none</span><span class="sxs-lookup"><span data-stu-id="ef717-134">none</span></span>                                 |
| <span data-ttu-id="ef717-135">Necessário?</span><span class="sxs-lookup"><span data-stu-id="ef717-135">Required?</span></span>                            | <span data-ttu-id="ef717-136">false</span><span class="sxs-lookup"><span data-stu-id="ef717-136">false</span></span>                                |
| <span data-ttu-id="ef717-137">Posição?</span><span class="sxs-lookup"><span data-stu-id="ef717-137">Position?</span></span>                            | <span data-ttu-id="ef717-138">3</span><span class="sxs-lookup"><span data-stu-id="ef717-138">3</span></span>                                    |
| <span data-ttu-id="ef717-139">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="ef717-139">Default Value</span></span>                        | <span data-ttu-id="ef717-140">none</span><span class="sxs-lookup"><span data-stu-id="ef717-140">none</span></span>                                 |
| <span data-ttu-id="ef717-141">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="ef717-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ef717-142">false</span><span class="sxs-lookup"><span data-stu-id="ef717-142">false</span></span>                                |
| <span data-ttu-id="ef717-143">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="ef717-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ef717-144">false</span><span class="sxs-lookup"><span data-stu-id="ef717-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="ef717-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="ef717-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="ef717-146">Especifica o URI de conexão a ser testado.</span><span class="sxs-lookup"><span data-stu-id="ef717-146">Specifies the connection URI to test.</span></span>

|||
|-|-|
| <span data-ttu-id="ef717-147">Aliases</span><span class="sxs-lookup"><span data-stu-id="ef717-147">Aliases</span></span>                              | <span data-ttu-id="ef717-148">none</span><span class="sxs-lookup"><span data-stu-id="ef717-148">none</span></span>                                 |
| <span data-ttu-id="ef717-149">Necessário?</span><span class="sxs-lookup"><span data-stu-id="ef717-149">Required?</span></span>                            | <span data-ttu-id="ef717-150">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="ef717-150">true</span></span>                                 |
| <span data-ttu-id="ef717-151">Posição?</span><span class="sxs-lookup"><span data-stu-id="ef717-151">Position?</span></span>                            | <span data-ttu-id="ef717-152">2</span><span class="sxs-lookup"><span data-stu-id="ef717-152">2</span></span>                                    |
| <span data-ttu-id="ef717-153">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="ef717-153">Default Value</span></span>                        | <span data-ttu-id="ef717-154">none</span><span class="sxs-lookup"><span data-stu-id="ef717-154">none</span></span>                                 |
| <span data-ttu-id="ef717-155">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="ef717-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ef717-156">false</span><span class="sxs-lookup"><span data-stu-id="ef717-156">false</span></span>                                |
| <span data-ttu-id="ef717-157">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="ef717-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ef717-158">false</span><span class="sxs-lookup"><span data-stu-id="ef717-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="ef717-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="ef717-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="ef717-160">Especifica um objeto **PSCredential** para uma conta de usuário que você deseja usar para testar as regras de autorização do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ef717-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="ef717-161">Se você não adicionar esse parâmetro, o cmdlet usará a conta do usuário conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="ef717-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="ef717-162">Para obter um objeto **PSCredential**, que é necessário para testar as regras de autorização remotamente, execute o cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).</span><span class="sxs-lookup"><span data-stu-id="ef717-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="ef717-163">Aliases</span><span class="sxs-lookup"><span data-stu-id="ef717-163">Aliases</span></span>                              | <span data-ttu-id="ef717-164">none</span><span class="sxs-lookup"><span data-stu-id="ef717-164">none</span></span>                                 |
| <span data-ttu-id="ef717-165">Necessário?</span><span class="sxs-lookup"><span data-stu-id="ef717-165">Required?</span></span>                            | <span data-ttu-id="ef717-166">false</span><span class="sxs-lookup"><span data-stu-id="ef717-166">false</span></span>                                |
| <span data-ttu-id="ef717-167">Posição?</span><span class="sxs-lookup"><span data-stu-id="ef717-167">Position?</span></span>                            | <span data-ttu-id="ef717-168">chamada</span><span class="sxs-lookup"><span data-stu-id="ef717-168">named</span></span>                                |
| <span data-ttu-id="ef717-169">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="ef717-169">Default Value</span></span>                        | <span data-ttu-id="ef717-170">none</span><span class="sxs-lookup"><span data-stu-id="ef717-170">none</span></span>                                 |
| <span data-ttu-id="ef717-171">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="ef717-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ef717-172">false</span><span class="sxs-lookup"><span data-stu-id="ef717-172">false</span></span>                                |
| <span data-ttu-id="ef717-173">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="ef717-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ef717-174">false</span><span class="sxs-lookup"><span data-stu-id="ef717-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="ef717-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="ef717-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="ef717-176">Especifica um subconjunto de regras a serem testadas.</span><span class="sxs-lookup"><span data-stu-id="ef717-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="ef717-177">Se esse parâmetro não for especificado, esse cmdlet testará todas as regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="ef717-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="ef717-178">Aliases</span><span class="sxs-lookup"><span data-stu-id="ef717-178">Aliases</span></span>                              | <span data-ttu-id="ef717-179">none</span><span class="sxs-lookup"><span data-stu-id="ef717-179">none</span></span>                                 |
| <span data-ttu-id="ef717-180">Necessário?</span><span class="sxs-lookup"><span data-stu-id="ef717-180">Required?</span></span>                            | <span data-ttu-id="ef717-181">false</span><span class="sxs-lookup"><span data-stu-id="ef717-181">false</span></span>                                |
| <span data-ttu-id="ef717-182">Posição?</span><span class="sxs-lookup"><span data-stu-id="ef717-182">Position?</span></span>                            | <span data-ttu-id="ef717-183">chamada</span><span class="sxs-lookup"><span data-stu-id="ef717-183">named</span></span>                                |
| <span data-ttu-id="ef717-184">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="ef717-184">Default Value</span></span>                        | <span data-ttu-id="ef717-185">none</span><span class="sxs-lookup"><span data-stu-id="ef717-185">none</span></span>                                 |
| <span data-ttu-id="ef717-186">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="ef717-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ef717-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="ef717-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="ef717-188">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="ef717-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ef717-189">false</span><span class="sxs-lookup"><span data-stu-id="ef717-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="ef717-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="ef717-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="ef717-191">Especifica o nome do usuário a ser testado.</span><span class="sxs-lookup"><span data-stu-id="ef717-191">Specifies the name of the user to test.</span></span>

|||
|-|-|
| <span data-ttu-id="ef717-192">Aliases</span><span class="sxs-lookup"><span data-stu-id="ef717-192">Aliases</span></span>                              | <span data-ttu-id="ef717-193">none</span><span class="sxs-lookup"><span data-stu-id="ef717-193">none</span></span>                                 |
| <span data-ttu-id="ef717-194">Necessário?</span><span class="sxs-lookup"><span data-stu-id="ef717-194">Required?</span></span>                            | <span data-ttu-id="ef717-195">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="ef717-195">true</span></span>                                 |
| <span data-ttu-id="ef717-196">Posição?</span><span class="sxs-lookup"><span data-stu-id="ef717-196">Position?</span></span>                            | <span data-ttu-id="ef717-197">1</span><span class="sxs-lookup"><span data-stu-id="ef717-197">1</span></span>                                    |
| <span data-ttu-id="ef717-198">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="ef717-198">Default Value</span></span>                        | <span data-ttu-id="ef717-199">none</span><span class="sxs-lookup"><span data-stu-id="ef717-199">none</span></span>                                 |
| <span data-ttu-id="ef717-200">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="ef717-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ef717-201">false</span><span class="sxs-lookup"><span data-stu-id="ef717-201">false</span></span>                                |
| <span data-ttu-id="ef717-202">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="ef717-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ef717-203">false</span><span class="sxs-lookup"><span data-stu-id="ef717-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="ef717-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="ef717-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="ef717-205">Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="ef717-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="ef717-206">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ef717-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="ef717-207">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="ef717-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="ef717-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="ef717-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="ef717-209">Este cmdlet aceita uma matriz de objetos PswaAuthorizationRule como entrada.</span><span class="sxs-lookup"><span data-stu-id="ef717-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="ef717-210">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="ef717-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="ef717-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="ef717-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="ef717-212">Esse cmdlet gera uma matriz de objetos PswaAuthorizationRule como saída.</span><span class="sxs-lookup"><span data-stu-id="ef717-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="ef717-213">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="ef717-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="ef717-214">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="ef717-214">EXAMPLE 1</span></span>

<span data-ttu-id="ef717-215">Este exemplo testa todas as regras de autorização para exibir todas as regras que permitem que o usuário *contoso\\mhanson* se conecte ao computador *srv2* e use uma configuração de sessão do Windows PowerShell chamada *teste*.</span><span class="sxs-lookup"><span data-stu-id="ef717-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="ef717-216">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="ef717-216">EXAMPLE 2</span></span>

<span data-ttu-id="ef717-217">Este exemplo testa todas as regras de autorização para verificar quais regras de autorização se aplicam ao usuário *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="ef717-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="ef717-218">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="ef717-218">Related topics</span></span>

- [<span data-ttu-id="ef717-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ef717-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="ef717-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ef717-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="ef717-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="ef717-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="ef717-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ef717-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)