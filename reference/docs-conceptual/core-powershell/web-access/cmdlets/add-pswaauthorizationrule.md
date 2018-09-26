---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: fe2b71dcfa870ba3f92484ae3fd3c45b3107a1bc
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523069"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="81596-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="81596-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="81596-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="81596-104">SYNOPSIS</span></span>

<span data-ttu-id="81596-105">Adiciona uma nova regra de autorização ao conjunto de regras de autorização do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="81596-105">Adds a new authorization rule to the Windows PowerShell Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="81596-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81596-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="81596-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="81596-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="81596-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="81596-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="81596-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="81596-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="81596-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="81596-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="81596-111">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="81596-111">DESCRIPTION</span></span>

<span data-ttu-id="81596-112">O cmdlet **Add-PswaAuthorizationRule** adiciona uma nova regra de autorização ao conjunto de regras de autorização do Windows PowerShell(r) Web Access.</span><span class="sxs-lookup"><span data-stu-id="81596-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell(r) Web Access authorization rule set.</span></span>

<span data-ttu-id="81596-113">Você deve especificar os usuários, computadores e pontos de extremidade do Windows PowerShell para essa regra.</span><span class="sxs-lookup"><span data-stu-id="81596-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="81596-114">Você pode especificar usuários e computadores por contas de usuário e nomes de computador individuais ou especificar grupos.</span><span class="sxs-lookup"><span data-stu-id="81596-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="81596-115">Para um computador ingressado em um domínio do Active Directory, o cmdlet usa o SID (identificador de segurança) do computador para criar a regra.</span><span class="sxs-lookup"><span data-stu-id="81596-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span> <span data-ttu-id="81596-116">Isso permite que você use um nome curto, um FQDN (nome de domínio totalmente qualificado) ou um endereço IP para o campo **Nome do Computador** na página de entrada.</span><span class="sxs-lookup"><span data-stu-id="81596-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="81596-117">Para um computador que não ingressou em um domínio do Active Directory, o cmdlet cria a regra usando o nome do computador fornecido pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="81596-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="81596-118">Para conectar-se com êxito a esse computador, o usuário final deve fornecer o nome do computador, exatamente como ele aparece na regra.</span><span class="sxs-lookup"><span data-stu-id="81596-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="81596-119">Se houver vários computadores com o mesmo nome na rede, o nome curto poderá ser resolvido para mais de um computador.</span><span class="sxs-lookup"><span data-stu-id="81596-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="81596-120">Isso poderá causar ambiguidade ao estabelecer uma conexão.</span><span class="sxs-lookup"><span data-stu-id="81596-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="81596-121">Por exemplo, se existir uma regra para o computador do grupo de trabalho chamado "*Server1*" e um novo computador chamado *server1.contoso.com* tiver ingressado na rede, a validação usando as regras de autorização será bem-sucedida e o Windows PowerShell Web Access tentará estabelecer uma conexão com o computador denominado "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="81596-121">For example, if a rule exists for the workgroup computer named "*Server1*" and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named "*Server1*".</span></span> <span data-ttu-id="81596-122">Não há garantia de que a conexão será estabelecida com o computador do grupo de trabalho especificado. Poderia ser feita uma tentativa no grupo de trabalho ou no computador de domínio chamado "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="81596-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="81596-123">Para reduzir a ambiguidade, é recomendável que você use o FQDN do computador de destino sempre que possível para criar uma regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="81596-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="81596-124">As regras de autorização avaliam a credencial de logon principal dos usuários do Windows PowerShell Web Access, não as credenciais alternativas (o segundo conjunto de credenciais encontrado na seção **Configurações opcionais de conexão** da página de entrada).</span><span class="sxs-lookup"><span data-stu-id="81596-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="81596-125">Para obter um exemplo disso, consulte o Exemplo 6.</span><span class="sxs-lookup"><span data-stu-id="81596-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="81596-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81596-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="81596-127">-ComputerGroupName \<String\></span><span class="sxs-lookup"><span data-stu-id="81596-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="81596-128">Especifica o nome de um grupo de computadores no AD DS (Active Directory Domain Services) ou de grupos locais aos quais essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="81596-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="81596-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="81596-129">Aliases</span></span>                     | <span data-ttu-id="81596-130">none</span><span class="sxs-lookup"><span data-stu-id="81596-130">none</span></span>                  |
| <span data-ttu-id="81596-131">Necessário?</span><span class="sxs-lookup"><span data-stu-id="81596-131">Required?</span></span>                   | <span data-ttu-id="81596-132">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="81596-132">true</span></span>                  |
| <span data-ttu-id="81596-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="81596-133">Position?</span></span>                   | <span data-ttu-id="81596-134">chamada</span><span class="sxs-lookup"><span data-stu-id="81596-134">named</span></span>                 |
| <span data-ttu-id="81596-135">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="81596-135">Default Value</span></span>               | <span data-ttu-id="81596-136">none</span><span class="sxs-lookup"><span data-stu-id="81596-136">none</span></span>                  |
| <span data-ttu-id="81596-137">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="81596-137">Accept Pipeline Input?</span></span>      | <span data-ttu-id="81596-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="81596-138">True (ByPropertyName)</span></span> |
| <span data-ttu-id="81596-139">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="81596-139">Accept Wildcard Characters?</span></span> | <span data-ttu-id="81596-140">false</span><span class="sxs-lookup"><span data-stu-id="81596-140">false</span></span>                 |

### <a name="-computername-string"></a><span data-ttu-id="81596-141">-ComputerName \<String\></span><span class="sxs-lookup"><span data-stu-id="81596-141">-ComputerName \<String\></span></span>

<span data-ttu-id="81596-142">Especifica o nome do computador ao qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="81596-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="81596-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="81596-143">Aliases</span></span>                     | <span data-ttu-id="81596-144">none</span><span class="sxs-lookup"><span data-stu-id="81596-144">none</span></span>                  |
| <span data-ttu-id="81596-145">Necessário?</span><span class="sxs-lookup"><span data-stu-id="81596-145">Required?</span></span>                   | <span data-ttu-id="81596-146">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="81596-146">true</span></span>                  |
| <span data-ttu-id="81596-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="81596-147">Position?</span></span>                   | <span data-ttu-id="81596-148">chamada</span><span class="sxs-lookup"><span data-stu-id="81596-148">named</span></span>                 |
| <span data-ttu-id="81596-149">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="81596-149">Default Value</span></span>               | <span data-ttu-id="81596-150">none</span><span class="sxs-lookup"><span data-stu-id="81596-150">none</span></span>                  |
| <span data-ttu-id="81596-151">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="81596-151">Accept Pipeline Input?</span></span>      | <span data-ttu-id="81596-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="81596-152">True (ByPropertyName)</span></span> |
| <span data-ttu-id="81596-153">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="81596-153">Accept Wildcard Characters?</span></span> | <span data-ttu-id="81596-154">false</span><span class="sxs-lookup"><span data-stu-id="81596-154">false</span></span>                 |

### <a name="-configurationname-string"></a><span data-ttu-id="81596-155">-ConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="81596-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="81596-156">Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como runspace, ao qual essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="81596-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="81596-157">Aliases</span><span class="sxs-lookup"><span data-stu-id="81596-157">Aliases</span></span>                     | <span data-ttu-id="81596-158">none</span><span class="sxs-lookup"><span data-stu-id="81596-158">none</span></span>                  |
| <span data-ttu-id="81596-159">Necessário?</span><span class="sxs-lookup"><span data-stu-id="81596-159">Required?</span></span>                   | <span data-ttu-id="81596-160">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="81596-160">true</span></span>                  |
| <span data-ttu-id="81596-161">Posição?</span><span class="sxs-lookup"><span data-stu-id="81596-161">Position?</span></span>                   | <span data-ttu-id="81596-162">chamada</span><span class="sxs-lookup"><span data-stu-id="81596-162">named</span></span>                 |
| <span data-ttu-id="81596-163">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="81596-163">Default Value</span></span>               | <span data-ttu-id="81596-164">none</span><span class="sxs-lookup"><span data-stu-id="81596-164">none</span></span>                  |
| <span data-ttu-id="81596-165">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="81596-165">Accept Pipeline Input?</span></span>      | <span data-ttu-id="81596-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="81596-166">True (ByPropertyName)</span></span> |
| <span data-ttu-id="81596-167">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="81596-167">Accept Wildcard Characters?</span></span> | <span data-ttu-id="81596-168">false</span><span class="sxs-lookup"><span data-stu-id="81596-168">false</span></span>                 |

### <a name="-credential--pscredential"></a><span data-ttu-id="81596-169">-Credential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="81596-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="81596-170">Especifica um objeto **PSCredential** para uma conta de usuário que você deseja usar para alterar as regras de autorização do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="81596-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="81596-171">Se você não adicionar esse parâmetro, o cmdlet usará a conta do usuário conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="81596-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="81596-172">Para obter um objeto **PSCredential**, que é necessário para adicionar regras de autorização remotamente, execute o cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).</span><span class="sxs-lookup"><span data-stu-id="81596-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="81596-173">Aliases</span><span class="sxs-lookup"><span data-stu-id="81596-173">Aliases</span></span>                     | <span data-ttu-id="81596-174">none</span><span class="sxs-lookup"><span data-stu-id="81596-174">none</span></span>  |
| <span data-ttu-id="81596-175">Necessário?</span><span class="sxs-lookup"><span data-stu-id="81596-175">Required?</span></span>                   | <span data-ttu-id="81596-176">false</span><span class="sxs-lookup"><span data-stu-id="81596-176">false</span></span> |
| <span data-ttu-id="81596-177">Posição?</span><span class="sxs-lookup"><span data-stu-id="81596-177">Position?</span></span>                   | <span data-ttu-id="81596-178">chamada</span><span class="sxs-lookup"><span data-stu-id="81596-178">named</span></span> |
| <span data-ttu-id="81596-179">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="81596-179">Default Value</span></span>               | <span data-ttu-id="81596-180">none</span><span class="sxs-lookup"><span data-stu-id="81596-180">none</span></span>  |
| <span data-ttu-id="81596-181">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="81596-181">Accept Pipeline Input?</span></span>      | <span data-ttu-id="81596-182">false</span><span class="sxs-lookup"><span data-stu-id="81596-182">false</span></span> |
| <span data-ttu-id="81596-183">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="81596-183">Accept Wildcard Characters?</span></span> | <span data-ttu-id="81596-184">false</span><span class="sxs-lookup"><span data-stu-id="81596-184">false</span></span> |

### <a name="-force"></a><span data-ttu-id="81596-185">-Force</span><span class="sxs-lookup"><span data-stu-id="81596-185">-Force</span></span>

<span data-ttu-id="81596-186">Força o comando a ser executado sem solicitar a confirmação do usuário.</span><span class="sxs-lookup"><span data-stu-id="81596-186">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="81596-187">Além disso, ele também solicita confirmação quando você insere um nome do computador curto ou simples (como um nome que não seja um nome de domínio ou não seja totalmente qualificado).</span><span class="sxs-lookup"><span data-stu-id="81596-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="81596-188">A confirmação é solicitada por motivos de segurança, de modo que você apenas possa usar o nome simples para adicionar um computador se o computador estiver em um grupo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="81596-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="81596-189">Aliases</span><span class="sxs-lookup"><span data-stu-id="81596-189">Aliases</span></span>                              | <span data-ttu-id="81596-190">none</span><span class="sxs-lookup"><span data-stu-id="81596-190">none</span></span>                                 |
| <span data-ttu-id="81596-191">Necessário?</span><span class="sxs-lookup"><span data-stu-id="81596-191">Required?</span></span>                            | <span data-ttu-id="81596-192">false</span><span class="sxs-lookup"><span data-stu-id="81596-192">false</span></span>                                |
| <span data-ttu-id="81596-193">Posição?</span><span class="sxs-lookup"><span data-stu-id="81596-193">Position?</span></span>                            | <span data-ttu-id="81596-194">chamada</span><span class="sxs-lookup"><span data-stu-id="81596-194">named</span></span>                                |
| <span data-ttu-id="81596-195">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="81596-195">Default Value</span></span>                        | <span data-ttu-id="81596-196">none</span><span class="sxs-lookup"><span data-stu-id="81596-196">none</span></span>                                 |
| <span data-ttu-id="81596-197">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="81596-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="81596-198">false</span><span class="sxs-lookup"><span data-stu-id="81596-198">false</span></span>                                |
| <span data-ttu-id="81596-199">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="81596-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="81596-200">false</span><span class="sxs-lookup"><span data-stu-id="81596-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="81596-201">-RuleName \<String\></span><span class="sxs-lookup"><span data-stu-id="81596-201">-RuleName \<String\></span></span>

<span data-ttu-id="81596-202">Especifica o nome amigável dessa regra.</span><span class="sxs-lookup"><span data-stu-id="81596-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="81596-203">Aliases</span><span class="sxs-lookup"><span data-stu-id="81596-203">Aliases</span></span>                              | <span data-ttu-id="81596-204">none</span><span class="sxs-lookup"><span data-stu-id="81596-204">none</span></span>                                 |
| <span data-ttu-id="81596-205">Necessário?</span><span class="sxs-lookup"><span data-stu-id="81596-205">Required?</span></span>                            | <span data-ttu-id="81596-206">false</span><span class="sxs-lookup"><span data-stu-id="81596-206">false</span></span>                                |
| <span data-ttu-id="81596-207">Posição?</span><span class="sxs-lookup"><span data-stu-id="81596-207">Position?</span></span>                            | <span data-ttu-id="81596-208">chamada</span><span class="sxs-lookup"><span data-stu-id="81596-208">named</span></span>                                |
| <span data-ttu-id="81596-209">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="81596-209">Default Value</span></span>                        | <span data-ttu-id="81596-210">none</span><span class="sxs-lookup"><span data-stu-id="81596-210">none</span></span>                                 |
| <span data-ttu-id="81596-211">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="81596-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="81596-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="81596-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="81596-213">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="81596-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="81596-214">false</span><span class="sxs-lookup"><span data-stu-id="81596-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="81596-215">-UserGroupName \<String\[\]\></span><span class="sxs-lookup"><span data-stu-id="81596-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="81596-216">Especifica o nome de um ou mais grupos de usuários no AD DS ou grupos locais aos quais essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="81596-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="81596-217">Aliases</span><span class="sxs-lookup"><span data-stu-id="81596-217">Aliases</span></span>                              | <span data-ttu-id="81596-218">none</span><span class="sxs-lookup"><span data-stu-id="81596-218">none</span></span>                                 |
| <span data-ttu-id="81596-219">Necessário?</span><span class="sxs-lookup"><span data-stu-id="81596-219">Required?</span></span>                            | <span data-ttu-id="81596-220">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="81596-220">true</span></span>                                 |
| <span data-ttu-id="81596-221">Posição?</span><span class="sxs-lookup"><span data-stu-id="81596-221">Position?</span></span>                            | <span data-ttu-id="81596-222">chamada</span><span class="sxs-lookup"><span data-stu-id="81596-222">named</span></span>                                |
| <span data-ttu-id="81596-223">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="81596-223">Default Value</span></span>                        | <span data-ttu-id="81596-224">none</span><span class="sxs-lookup"><span data-stu-id="81596-224">none</span></span>                                 |
| <span data-ttu-id="81596-225">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="81596-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="81596-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="81596-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="81596-227">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="81596-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="81596-228">false</span><span class="sxs-lookup"><span data-stu-id="81596-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="81596-229">-UserName \<String\[\]\></span><span class="sxs-lookup"><span data-stu-id="81596-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="81596-230">Especifica um ou mais usuários aos quais essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="81596-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="81596-231">O nome de usuário pode ser uma conta de usuário local no computador do gateway ou um usuário no AD DS.</span><span class="sxs-lookup"><span data-stu-id="81596-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span> <span data-ttu-id="81596-232">O formato é `domain\user` ou `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="81596-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="81596-233">Aliases</span><span class="sxs-lookup"><span data-stu-id="81596-233">Aliases</span></span>                              | <span data-ttu-id="81596-234">none</span><span class="sxs-lookup"><span data-stu-id="81596-234">none</span></span>                                 |
| <span data-ttu-id="81596-235">Necessário?</span><span class="sxs-lookup"><span data-stu-id="81596-235">Required?</span></span>                            | <span data-ttu-id="81596-236">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="81596-236">true</span></span>                                 |
| <span data-ttu-id="81596-237">Posição?</span><span class="sxs-lookup"><span data-stu-id="81596-237">Position?</span></span>                            | <span data-ttu-id="81596-238">1</span><span class="sxs-lookup"><span data-stu-id="81596-238">1</span></span>                                    |
| <span data-ttu-id="81596-239">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="81596-239">Default Value</span></span>                        | <span data-ttu-id="81596-240">none</span><span class="sxs-lookup"><span data-stu-id="81596-240">none</span></span>                                 |
| <span data-ttu-id="81596-241">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="81596-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="81596-242">Verdadeiro (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="81596-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="81596-243">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="81596-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="81596-244">false</span><span class="sxs-lookup"><span data-stu-id="81596-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="81596-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="81596-245">\<CommonParameters\></span></span>

<span data-ttu-id="81596-246">Esse cmdlet oferece suporte aos parâmetros comuns:</span><span class="sxs-lookup"><span data-stu-id="81596-246">This cmdlet supports the common parameters:</span></span>

<span data-ttu-id="81596-247">-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="81596-247">-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="81596-248">Para obter mais informações, consulte [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="81596-248">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="81596-249">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="81596-249">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="81596-250">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="81596-250">String</span></span>

<span data-ttu-id="81596-251">Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.</span><span class="sxs-lookup"><span data-stu-id="81596-251">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="81596-252">String\[\]</span><span class="sxs-lookup"><span data-stu-id="81596-252">String\[\]</span></span>

<span data-ttu-id="81596-253">Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.</span><span class="sxs-lookup"><span data-stu-id="81596-253">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="81596-254">Saídas</span><span class="sxs-lookup"><span data-stu-id="81596-254">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="81596-255">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="81596-255">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="81596-256">Este cmdlet retorna o objeto de regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="81596-256">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="81596-257">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="81596-257">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="81596-258">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="81596-258">EXAMPLE 1</span></span>

<span data-ttu-id="81596-259">Este exemplo concede acesso à configuração de sessão _PSWAEndpoint_, um runspace restrito no _srv2_ para os usuários no grupo _SMAdmins_.</span><span class="sxs-lookup"><span data-stu-id="81596-259">This example grants access to the session configuration _PSWAEndpoint_, a restricted runspace, on _srv2_ for users in the _SMAdmins_ group.</span></span>

> [!NOTE]
> <span data-ttu-id="81596-260">O nome do computador deve ser um FQDN (nome de domínio totalmente qualificado).</span><span class="sxs-lookup"><span data-stu-id="81596-260">The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="81596-261">Os administradores definem uma configuração de sessão restrita ou um runspace, que é um intervalo limitado de cmdlets e tarefas que os usuários finais podem executar.</span><span class="sxs-lookup"><span data-stu-id="81596-261">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="81596-262">A definição de um runspace restrito pode evitar que usuários acessem outros computadores que não estejam no runspace permitido do Windows PowerShell(r), oferecendo assim uma conexão mais segura.</span><span class="sxs-lookup"><span data-stu-id="81596-262">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell(r) runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="81596-263">Para saber mais sobre as configurações de sessão, confira [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) ou [Instalar e usar o Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="81596-263">For more information on session configurations, see [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) or [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```powershell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="81596-264">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="81596-264">EXAMPLE 2</span></span>

<span data-ttu-id="81596-265">Este exemplo concede acesso à configuração de sessão padrão do Windows PowerShell, `Microsoft.PowerShell`, no *srv2* para os usuários chamados `contoso\user1`, `contoso\user2` e `contoso\user3`.</span><span class="sxs-lookup"><span data-stu-id="81596-265">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="81596-266">Esse cmdlet cria três regras (uma por pessoa).</span><span class="sxs-lookup"><span data-stu-id="81596-266">This cmdlet creates three rules (1 per person).</span></span>

```powershell
Add-PswaAuthorizationRule -UserName contoso\user1, contoso\user2, contoso\user3 -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="81596-267">EXEMPLO 3</span><span class="sxs-lookup"><span data-stu-id="81596-267">EXAMPLE 3</span></span>

<span data-ttu-id="81596-268">Este exemplo ilustra como inserir valores de nome de usuário por meio do pipeline.</span><span class="sxs-lookup"><span data-stu-id="81596-268">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="81596-269">EXEMPLO 4</span><span class="sxs-lookup"><span data-stu-id="81596-269">EXAMPLE 4</span></span>

<span data-ttu-id="81596-270">Este exemplo ilustra como todos os parâmetros obtêm os valores do pipeline pelo nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="81596-270">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````powershell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" -PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="81596-271">EXEMPLO 5</span><span class="sxs-lookup"><span data-stu-id="81596-271">EXAMPLE 5</span></span>

<span data-ttu-id="81596-272">Este exemplo adiciona uma regra para permitir que o usuário local chamado `PswaServer\ChrisLocal` acesse um servidor chamado **srv1.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="81596-272">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="81596-273">Este exemplo ilustra um cenário em que o gateway está em um grupo de trabalho e o computador de destino está em um domínio.</span><span class="sxs-lookup"><span data-stu-id="81596-273">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="81596-274">A regra de autorização aplica-se aos usuários locais no gateway.</span><span class="sxs-lookup"><span data-stu-id="81596-274">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="81596-275">Na página de logon do Windows PowerShell Web Access, para autenticar-se com êxito, o usuário deve fornecer um segundo conjunto de credenciais na área **Configurações opcionais de conexão**.</span><span class="sxs-lookup"><span data-stu-id="81596-275">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="81596-276">O servidor de gateway usa o conjunto adicional de credenciais para autenticar o usuário no computador de destino, um servidor chamado *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="81596-276">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule -UserName PswaServer\ChrisLocal -ComputerName srv1.contoso.com -ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="81596-277">EXEMPLO 6</span><span class="sxs-lookup"><span data-stu-id="81596-277">EXAMPLE 6</span></span>

<span data-ttu-id="81596-278">Este exemplo permite que todos os usuários acessem todos os pontos de extremidade em todos os computadores.</span><span class="sxs-lookup"><span data-stu-id="81596-278">This example allows all users access to all endpoints on all computers.</span></span> <span data-ttu-id="81596-279">Essa opção basicamente desativa as regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="81596-279">This essentially turns off authorization rules.</span></span>

> [!NOTE]
> <span data-ttu-id="81596-280">O uso do caractere curinga `*` não é recomendado para implantações que exigem um alto nível de segurança e só deve ser considerado para ambientes de teste ou usado em implantações nas quais a segurança possa ser reduzida.</span><span class="sxs-lookup"><span data-stu-id="81596-280">Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````powershell
Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="81596-281">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="81596-281">See Also</span></span>

<span data-ttu-id="81596-282">[Get-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="81596-282">[Get-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="81596-283">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="81596-283">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="81596-284">[Test-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="81596-284">[Test-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="81596-285">[Install-PswaWebApplication](https://technet.microsoft.com/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="81596-285">[Install-PswaWebApplication](https://technet.microsoft.com/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="81596-286">Add-Member</span><span class="sxs-lookup"><span data-stu-id="81596-286">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="81596-287">New-Object</span><span class="sxs-lookup"><span data-stu-id="81596-287">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="81596-288">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="81596-288">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)
