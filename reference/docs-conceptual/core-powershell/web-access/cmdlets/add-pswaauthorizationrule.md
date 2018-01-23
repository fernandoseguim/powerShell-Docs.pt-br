---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell, cmdlet
ms.date: 2016-12-12
title: add pswaauthorizationrule
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 196797215a678e6f674592dc6b289816aced3c01
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="9a4a6-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9a4a6-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="9a4a6-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="9a4a6-104">SYNOPSIS</span></span>

<span data-ttu-id="9a4a6-105">Adiciona uma nova regra de autorização ao conjunto de regras de autorização do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a4a6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a4a6-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="9a4a6-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="9a4a6-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="9a4a6-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="9a4a6-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="9a4a6-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="9a4a6-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="9a4a6-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="9a4a6-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="9a4a6-111">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="9a4a6-111">DESCRIPTION</span></span>

<span data-ttu-id="9a4a6-112">O cmdlet **Add-PswaAuthorizationRule** adiciona uma nova regra de autorização ao conjunto de regras de autorização do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="9a4a6-113">Você deve especificar os usuários, computadores e pontos de extremidade do Windows PowerShell para essa regra.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="9a4a6-114">Você pode especificar usuários e computadores por contas de usuário e nomes de computador individuais ou especificar grupos.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="9a4a6-115">Para um computador ingressado em um domínio do Active Directory, o cmdlet usa o SID (identificador de segurança) do computador para criar a regra.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="9a4a6-116">Isso permite que você use um nome curto, um FQDN (nome de domínio totalmente qualificado) ou um endereço IP para o campo **Nome do Computador** na página de entrada.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="9a4a6-117">Para um computador que não ingressou em um domínio do Active Directory, o cmdlet cria a regra usando o nome do computador fornecido pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="9a4a6-118">Para conectar-se com êxito a esse computador, o usuário final deve fornecer o nome do computador, exatamente como ele aparece na regra.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="9a4a6-119">Se houver vários computadores com o mesmo nome na rede, o nome curto poderá ser resolvido para mais de um computador.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="9a4a6-120">Isso poderá causar ambiguidade ao estabelecer uma conexão.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="9a4a6-121">Por exemplo, se existir uma regra para o computador do grupo de trabalho chamado "*Server1*" e um novo computador chamado *server1.contoso.com* tiver ingressado na rede, a validação usando as regras de autorização será bem-sucedida e o Windows PowerShell Web Access tentará estabelecer uma conexão com o computador denominado "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="9a4a6-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="9a4a6-122">Não há garantia de que a conexão será estabelecida com o computador do grupo de trabalho especificado. Poderia ser feita uma tentativa no grupo de trabalho ou no computador de domínio chamado "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="9a4a6-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="9a4a6-123">Para reduzir a ambiguidade, é recomendável que você use o FQDN do computador de destino sempre que possível para criar uma regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="9a4a6-124">As regras de autorização avaliam a credencial de logon principal dos usuários do Windows PowerShell Web Access, não as credenciais alternativas (o segundo conjunto de credenciais encontrado na seção **Configurações opcionais de conexão** da página de entrada).</span><span class="sxs-lookup"><span data-stu-id="9a4a6-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="9a4a6-125">Para obter um exemplo disso, consulte o Exemplo 6.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="9a4a6-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a4a6-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="9a4a6-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9a4a6-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="9a4a6-128">Especifica o nome de um grupo de computadores no AD DS (Active Directory Domain Services) ou de grupos locais aos quais essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="9a4a6-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="9a4a6-129">Aliases</span></span>                              | <span data-ttu-id="9a4a6-130">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-130">none</span></span>                                 |
| <span data-ttu-id="9a4a6-131">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-131">Required?</span></span>                            | <span data-ttu-id="9a4a6-132">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="9a4a6-132">true</span></span>                                 |
| <span data-ttu-id="9a4a6-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-133">Position?</span></span>                            | <span data-ttu-id="9a4a6-134">chamada</span><span class="sxs-lookup"><span data-stu-id="9a4a6-134">named</span></span>                                |
| <span data-ttu-id="9a4a6-135">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9a4a6-135">Default Value</span></span>                        | <span data-ttu-id="9a4a6-136">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-136">none</span></span>                                 |
| <span data-ttu-id="9a4a6-137">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a4a6-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="9a4a6-139">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a4a6-140">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="9a4a6-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9a4a6-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="9a4a6-142">Especifica o nome do computador ao qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="9a4a6-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="9a4a6-143">Aliases</span></span>                              | <span data-ttu-id="9a4a6-144">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-144">none</span></span>                                 |
| <span data-ttu-id="9a4a6-145">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-145">Required?</span></span>                            | <span data-ttu-id="9a4a6-146">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="9a4a6-146">true</span></span>                                 |
| <span data-ttu-id="9a4a6-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-147">Position?</span></span>                            | <span data-ttu-id="9a4a6-148">chamada</span><span class="sxs-lookup"><span data-stu-id="9a4a6-148">named</span></span>                                |
| <span data-ttu-id="9a4a6-149">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9a4a6-149">Default Value</span></span>                        | <span data-ttu-id="9a4a6-150">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-150">none</span></span>                                 |
| <span data-ttu-id="9a4a6-151">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a4a6-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="9a4a6-153">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a4a6-154">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="9a4a6-155">-ConfigurationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9a4a6-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="9a4a6-156">Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como runspace, ao qual essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="9a4a6-157">Aliases</span><span class="sxs-lookup"><span data-stu-id="9a4a6-157">Aliases</span></span>                              | <span data-ttu-id="9a4a6-158">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-158">none</span></span>                                 |
| <span data-ttu-id="9a4a6-159">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-159">Required?</span></span>                            | <span data-ttu-id="9a4a6-160">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="9a4a6-160">true</span></span>                                 |
| <span data-ttu-id="9a4a6-161">Posição?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-161">Position?</span></span>                            | <span data-ttu-id="9a4a6-162">chamada</span><span class="sxs-lookup"><span data-stu-id="9a4a6-162">named</span></span>                                |
| <span data-ttu-id="9a4a6-163">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9a4a6-163">Default Value</span></span>                        | <span data-ttu-id="9a4a6-164">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-164">none</span></span>                                 |
| <span data-ttu-id="9a4a6-165">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a4a6-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="9a4a6-167">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a4a6-168">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="9a4a6-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="9a4a6-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="9a4a6-170">Especifica um objeto **PSCredential** para uma conta de usuário que você deseja usar para alterar as regras de autorização do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="9a4a6-171">Se você não adicionar esse parâmetro, o cmdlet usará a conta do usuário conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="9a4a6-172">Para obter um objeto **PSCredential**, que é necessário para adicionar regras de autorização remotamente, execute o cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).</span><span class="sxs-lookup"><span data-stu-id="9a4a6-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="9a4a6-173">Aliases</span><span class="sxs-lookup"><span data-stu-id="9a4a6-173">Aliases</span></span>                              | <span data-ttu-id="9a4a6-174">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-174">none</span></span>                                 |
| <span data-ttu-id="9a4a6-175">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-175">Required?</span></span>                            | <span data-ttu-id="9a4a6-176">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-176">false</span></span>                                |
| <span data-ttu-id="9a4a6-177">Posição?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-177">Position?</span></span>                            | <span data-ttu-id="9a4a6-178">chamada</span><span class="sxs-lookup"><span data-stu-id="9a4a6-178">named</span></span>                                |
| <span data-ttu-id="9a4a6-179">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9a4a6-179">Default Value</span></span>                        | <span data-ttu-id="9a4a6-180">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-180">none</span></span>                                 |
| <span data-ttu-id="9a4a6-181">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a4a6-182">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-182">false</span></span>                                |
| <span data-ttu-id="9a4a6-183">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a4a6-184">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="9a4a6-185">-Force</span><span class="sxs-lookup"><span data-stu-id="9a4a6-185">-Force</span></span>

<span data-ttu-id="9a4a6-186">Força o comando a ser executado sem solicitar confirmação do usuário.\\</span><span class="sxs-lookup"><span data-stu-id="9a4a6-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="9a4a6-187">Além disso, ele também solicita confirmação quando você insere um nome do computador curto ou simples (como um nome que não seja um nome de domínio ou não seja totalmente qualificado).</span><span class="sxs-lookup"><span data-stu-id="9a4a6-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="9a4a6-188">A confirmação é solicitada por motivos de segurança, de modo que você apenas possa usar o nome simples para adicionar um computador se o computador estiver em um grupo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="9a4a6-189">Aliases</span><span class="sxs-lookup"><span data-stu-id="9a4a6-189">Aliases</span></span>                              | <span data-ttu-id="9a4a6-190">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-190">none</span></span>                                 |
| <span data-ttu-id="9a4a6-191">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-191">Required?</span></span>                            | <span data-ttu-id="9a4a6-192">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-192">false</span></span>                                |
| <span data-ttu-id="9a4a6-193">Posição?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-193">Position?</span></span>                            | <span data-ttu-id="9a4a6-194">chamada</span><span class="sxs-lookup"><span data-stu-id="9a4a6-194">named</span></span>                                |
| <span data-ttu-id="9a4a6-195">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9a4a6-195">Default Value</span></span>                        | <span data-ttu-id="9a4a6-196">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-196">none</span></span>                                 |
| <span data-ttu-id="9a4a6-197">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a4a6-198">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-198">false</span></span>                                |
| <span data-ttu-id="9a4a6-199">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a4a6-200">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="9a4a6-201">-RuleName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9a4a6-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="9a4a6-202">Especifica o nome amigável dessa regra.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="9a4a6-203">Aliases</span><span class="sxs-lookup"><span data-stu-id="9a4a6-203">Aliases</span></span>                              | <span data-ttu-id="9a4a6-204">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-204">none</span></span>                                 |
| <span data-ttu-id="9a4a6-205">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-205">Required?</span></span>                            | <span data-ttu-id="9a4a6-206">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-206">false</span></span>                                |
| <span data-ttu-id="9a4a6-207">Posição?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-207">Position?</span></span>                            | <span data-ttu-id="9a4a6-208">chamada</span><span class="sxs-lookup"><span data-stu-id="9a4a6-208">named</span></span>                                |
| <span data-ttu-id="9a4a6-209">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9a4a6-209">Default Value</span></span>                        | <span data-ttu-id="9a4a6-210">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-210">none</span></span>                                 |
| <span data-ttu-id="9a4a6-211">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a4a6-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="9a4a6-213">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a4a6-214">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="9a4a6-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="9a4a6-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="9a4a6-216">Especifica o nome de um ou mais grupos de usuários no AD DS ou grupos locais aos quais essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="9a4a6-217">Aliases</span><span class="sxs-lookup"><span data-stu-id="9a4a6-217">Aliases</span></span>                              | <span data-ttu-id="9a4a6-218">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-218">none</span></span>                                 |
| <span data-ttu-id="9a4a6-219">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-219">Required?</span></span>                            | <span data-ttu-id="9a4a6-220">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="9a4a6-220">true</span></span>                                 |
| <span data-ttu-id="9a4a6-221">Posição?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-221">Position?</span></span>                            | <span data-ttu-id="9a4a6-222">chamada</span><span class="sxs-lookup"><span data-stu-id="9a4a6-222">named</span></span>                                |
| <span data-ttu-id="9a4a6-223">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9a4a6-223">Default Value</span></span>                        | <span data-ttu-id="9a4a6-224">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-224">none</span></span>                                 |
| <span data-ttu-id="9a4a6-225">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a4a6-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="9a4a6-227">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a4a6-228">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="9a4a6-229">-UserName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="9a4a6-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="9a4a6-230">Especifica um ou mais usuários aos quais essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="9a4a6-231">O nome de usuário pode ser uma conta de usuário local no computador do gateway ou um usuário no AD DS.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="9a4a6-232">O formato é `domain\user` ou `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="9a4a6-233">Aliases</span><span class="sxs-lookup"><span data-stu-id="9a4a6-233">Aliases</span></span>                              | <span data-ttu-id="9a4a6-234">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-234">none</span></span>                                 |
| <span data-ttu-id="9a4a6-235">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-235">Required?</span></span>                            | <span data-ttu-id="9a4a6-236">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="9a4a6-236">true</span></span>                                 |
| <span data-ttu-id="9a4a6-237">Posição?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-237">Position?</span></span>                            | <span data-ttu-id="9a4a6-238">1</span><span class="sxs-lookup"><span data-stu-id="9a4a6-238">1</span></span>                                    |
| <span data-ttu-id="9a4a6-239">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9a4a6-239">Default Value</span></span>                        | <span data-ttu-id="9a4a6-240">none</span><span class="sxs-lookup"><span data-stu-id="9a4a6-240">none</span></span>                                 |
| <span data-ttu-id="9a4a6-241">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a4a6-242">Verdadeiro (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="9a4a6-243">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9a4a6-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a4a6-244">false</span><span class="sxs-lookup"><span data-stu-id="9a4a6-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="9a4a6-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="9a4a6-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="9a4a6-246">Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="9a4a6-247">Para obter mais informações, consulte [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="9a4a6-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="9a4a6-248">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="9a4a6-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="9a4a6-249">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9a4a6-249">String</span></span>

<span data-ttu-id="9a4a6-250">Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="9a4a6-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="9a4a6-251">String\[\]</span></span>

<span data-ttu-id="9a4a6-252">Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="9a4a6-253">Saídas</span><span class="sxs-lookup"><span data-stu-id="9a4a6-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="9a4a6-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9a4a6-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="9a4a6-255">Este cmdlet retorna o objeto de regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="9a4a6-256">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="9a4a6-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="9a4a6-257">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="9a4a6-257">EXAMPLE 1</span></span>

<span data-ttu-id="9a4a6-258">Este exemplo concede acesso à configuração de sessão *PSWAEndpoint*, um runspace restrito no *srv2* para os usuários no grupo *SMAdmins*.\\</span><span class="sxs-lookup"><span data-stu-id="9a4a6-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="9a4a6-259">**Observação**: o nome do computador deve ser um FQDN (nome de domínio totalmente qualificado).</span><span class="sxs-lookup"><span data-stu-id="9a4a6-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="9a4a6-260">Os administradores definem uma configuração de sessão restrita ou um runspace, que é um intervalo limitado de cmdlets e tarefas que os usuários finais podem executar.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="9a4a6-261">A definição de um runspace restrito pode evitar que usuários acessem outros computadores que não estejam no runspace permitido do Windows PowerShell®, oferecendo assim uma conexão mais segura.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="9a4a6-262">Para obter mais informações sobre as configurações de sessão, consulte [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) ou [Instalar e usar o Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="9a4a6-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="9a4a6-263">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="9a4a6-263">EXAMPLE 2</span></span>

<span data-ttu-id="9a4a6-264">Este exemplo concede acesso à configuração de sessão padrão do Windows PowerShell, `Microsoft.PowerShell`, no *srv2* para os usuários chamados contoso\\user1, contoso\\user2 e contoso\\user3.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="9a4a6-265">Esse cmdlet cria três regras (uma por pessoa).</span><span class="sxs-lookup"><span data-stu-id="9a4a6-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="9a4a6-266">EXEMPLO 3</span><span class="sxs-lookup"><span data-stu-id="9a4a6-266">EXAMPLE 3</span></span>

<span data-ttu-id="9a4a6-267">Este exemplo ilustra como inserir valores de nome de usuário por meio do pipeline.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="9a4a6-268">EXEMPLO 4</span><span class="sxs-lookup"><span data-stu-id="9a4a6-268">EXAMPLE 4</span></span>

<span data-ttu-id="9a4a6-269">Este exemplo ilustra como todos os parâmetros obtêm os valores do pipeline pelo nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject | 
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | 
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | 
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="9a4a6-270">EXEMPLO 5</span><span class="sxs-lookup"><span data-stu-id="9a4a6-270">EXAMPLE 5</span></span>

<span data-ttu-id="9a4a6-271">Este exemplo adiciona uma regra para permitir que o usuário local chamado *PswaServer\\ChrisLocal* acesse um servidor chamado *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="9a4a6-272">Este exemplo ilustra um cenário em que o gateway está em um grupo de trabalho e o computador de destino está em um domínio.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="9a4a6-273">A regra de autorização aplica-se aos usuários locais no gateway.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="9a4a6-274">Na página de logon do Windows PowerShell Web Access, para autenticar-se com êxito, o usuário deve fornecer um segundo conjunto de credenciais na área **Configurações opcionais de conexão**.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="9a4a6-275">O servidor de gateway usa o conjunto adicional de credenciais para autenticar o usuário no computador de destino, um servidor chamado *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="9a4a6-276">EXEMPLO 6</span><span class="sxs-lookup"><span data-stu-id="9a4a6-276">EXAMPLE 6</span></span>

<span data-ttu-id="9a4a6-277">Este exemplo permite que todos os usuários acessem todos os pontos de extremidade em todos os computadores.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="9a4a6-278">Essa opção basicamente desativa as regras de autorização.\\</span><span class="sxs-lookup"><span data-stu-id="9a4a6-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="9a4a6-279">**Observação**: o uso do caractere curinga `*` não é recomendado para implantações que exigem um alto nível de segurança e só deve ser considerado para ambientes de teste ou usado em implantações nas quais a segurança possa ser reduzida.</span><span class="sxs-lookup"><span data-stu-id="9a4a6-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="9a4a6-280">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="9a4a6-280">See Also</span></span>

- <span data-ttu-id="9a4a6-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="9a4a6-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="9a4a6-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="9a4a6-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="9a4a6-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="9a4a6-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="9a4a6-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="9a4a6-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="9a4a6-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="9a4a6-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="9a4a6-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)
