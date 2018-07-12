---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a5e55611ac59ff5bfecee59ba2b7d7669d08f840
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893732"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="c8a6f-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c8a6f-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="c8a6f-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="c8a6f-104">SYNOPSIS</span></span>

<span data-ttu-id="c8a6f-105">Adiciona uma nova regra de autorização ao conjunto de regras de autorização do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8a6f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8a6f-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="c8a6f-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="c8a6f-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="c8a6f-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="c8a6f-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="c8a6f-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="c8a6f-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="c8a6f-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="c8a6f-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="c8a6f-111">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c8a6f-111">DESCRIPTION</span></span>

<span data-ttu-id="c8a6f-112">O cmdlet **Add-PswaAuthorizationRule** adiciona uma nova regra de autorização ao conjunto de regras de autorização do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="c8a6f-113">Você deve especificar os usuários, computadores e pontos de extremidade do Windows PowerShell para essa regra.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="c8a6f-114">Você pode especificar usuários e computadores por contas de usuário e nomes de computador individuais ou especificar grupos.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="c8a6f-115">Para um computador ingressado em um domínio do Active Directory, o cmdlet usa o SID (identificador de segurança) do computador para criar a regra.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="c8a6f-116">Isso permite que você use um nome curto, um FQDN (nome de domínio totalmente qualificado) ou um endereço IP para o campo **Nome do Computador** na página de entrada.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="c8a6f-117">Para um computador que não ingressou em um domínio do Active Directory, o cmdlet cria a regra usando o nome do computador fornecido pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="c8a6f-118">Para conectar-se com êxito a esse computador, o usuário final deve fornecer o nome do computador, exatamente como ele aparece na regra.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="c8a6f-119">Se houver vários computadores com o mesmo nome na rede, o nome curto poderá ser resolvido para mais de um computador.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="c8a6f-120">Isso poderá causar ambiguidade ao estabelecer uma conexão.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="c8a6f-121">Por exemplo, se existir uma regra para o computador do grupo de trabalho chamado "*Server1*" e um novo computador chamado *server1.contoso.com* tiver ingressado na rede, a validação usando as regras de autorização será bem-sucedida e o Windows PowerShell Web Access tentará estabelecer uma conexão com o computador denominado "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="c8a6f-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="c8a6f-122">Não há garantia de que a conexão será estabelecida com o computador do grupo de trabalho especificado. Poderia ser feita uma tentativa no grupo de trabalho ou no computador de domínio chamado "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="c8a6f-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="c8a6f-123">Para reduzir a ambiguidade, é recomendável que você use o FQDN do computador de destino sempre que possível para criar uma regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="c8a6f-124">As regras de autorização avaliam a credencial de logon principal dos usuários do Windows PowerShell Web Access, não as credenciais alternativas (o segundo conjunto de credenciais encontrado na seção **Configurações opcionais de conexão** da página de entrada).</span><span class="sxs-lookup"><span data-stu-id="c8a6f-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="c8a6f-125">Para obter um exemplo disso, consulte o Exemplo 6.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="c8a6f-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8a6f-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="c8a6f-127">-ComputerGroupName \<String\></span><span class="sxs-lookup"><span data-stu-id="c8a6f-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="c8a6f-128">Especifica o nome de um grupo de computadores no AD DS (Active Directory Domain Services) ou de grupos locais aos quais essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="c8a6f-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="c8a6f-129">Aliases</span></span>                              | <span data-ttu-id="c8a6f-130">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-130">none</span></span>                                 |
| <span data-ttu-id="c8a6f-131">Necessário?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-131">Required?</span></span>                            | <span data-ttu-id="c8a6f-132">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="c8a6f-132">true</span></span>                                 |
| <span data-ttu-id="c8a6f-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-133">Position?</span></span>                            | <span data-ttu-id="c8a6f-134">chamada</span><span class="sxs-lookup"><span data-stu-id="c8a6f-134">named</span></span>                                |
| <span data-ttu-id="c8a6f-135">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c8a6f-135">Default Value</span></span>                        | <span data-ttu-id="c8a6f-136">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-136">none</span></span>                                 |
| <span data-ttu-id="c8a6f-137">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c8a6f-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c8a6f-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="c8a6f-139">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c8a6f-140">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-140">false</span></span>                                |

### <a name="-computername-string"></a><span data-ttu-id="c8a6f-141">-ComputerName \<String\></span><span class="sxs-lookup"><span data-stu-id="c8a6f-141">-ComputerName \<String\></span></span>

<span data-ttu-id="c8a6f-142">Especifica o nome do computador ao qual esta regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="c8a6f-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="c8a6f-143">Aliases</span></span>                              | <span data-ttu-id="c8a6f-144">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-144">none</span></span>                                 |
| <span data-ttu-id="c8a6f-145">Necessário?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-145">Required?</span></span>                            | <span data-ttu-id="c8a6f-146">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="c8a6f-146">true</span></span>                                 |
| <span data-ttu-id="c8a6f-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-147">Position?</span></span>                            | <span data-ttu-id="c8a6f-148">chamada</span><span class="sxs-lookup"><span data-stu-id="c8a6f-148">named</span></span>                                |
| <span data-ttu-id="c8a6f-149">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c8a6f-149">Default Value</span></span>                        | <span data-ttu-id="c8a6f-150">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-150">none</span></span>                                 |
| <span data-ttu-id="c8a6f-151">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c8a6f-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c8a6f-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="c8a6f-153">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c8a6f-154">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-154">false</span></span>                                |

### <a name="-configurationname-string"></a><span data-ttu-id="c8a6f-155">-ConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="c8a6f-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="c8a6f-156">Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como runspace, ao qual essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="c8a6f-157">Aliases</span><span class="sxs-lookup"><span data-stu-id="c8a6f-157">Aliases</span></span>                              | <span data-ttu-id="c8a6f-158">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-158">none</span></span>                                 |
| <span data-ttu-id="c8a6f-159">Necessário?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-159">Required?</span></span>                            | <span data-ttu-id="c8a6f-160">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="c8a6f-160">true</span></span>                                 |
| <span data-ttu-id="c8a6f-161">Posição?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-161">Position?</span></span>                            | <span data-ttu-id="c8a6f-162">chamada</span><span class="sxs-lookup"><span data-stu-id="c8a6f-162">named</span></span>                                |
| <span data-ttu-id="c8a6f-163">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c8a6f-163">Default Value</span></span>                        | <span data-ttu-id="c8a6f-164">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-164">none</span></span>                                 |
| <span data-ttu-id="c8a6f-165">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c8a6f-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c8a6f-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="c8a6f-167">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c8a6f-168">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-168">false</span></span>                                |

### <a name="-credential--pscredential"></a><span data-ttu-id="c8a6f-169">-Credential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="c8a6f-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="c8a6f-170">Especifica um objeto **PSCredential** para uma conta de usuário que você deseja usar para alterar as regras de autorização do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="c8a6f-171">Se você não adicionar esse parâmetro, o cmdlet usará a conta do usuário conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="c8a6f-172">Para obter um objeto **PSCredential**, que é necessário para adicionar regras de autorização remotamente, execute o cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).</span><span class="sxs-lookup"><span data-stu-id="c8a6f-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="c8a6f-173">Aliases</span><span class="sxs-lookup"><span data-stu-id="c8a6f-173">Aliases</span></span>                              | <span data-ttu-id="c8a6f-174">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-174">none</span></span>                                 |
| <span data-ttu-id="c8a6f-175">Necessário?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-175">Required?</span></span>                            | <span data-ttu-id="c8a6f-176">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-176">false</span></span>                                |
| <span data-ttu-id="c8a6f-177">Posição?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-177">Position?</span></span>                            | <span data-ttu-id="c8a6f-178">chamada</span><span class="sxs-lookup"><span data-stu-id="c8a6f-178">named</span></span>                                |
| <span data-ttu-id="c8a6f-179">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c8a6f-179">Default Value</span></span>                        | <span data-ttu-id="c8a6f-180">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-180">none</span></span>                                 |
| <span data-ttu-id="c8a6f-181">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c8a6f-182">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-182">false</span></span>                                |
| <span data-ttu-id="c8a6f-183">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c8a6f-184">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="c8a6f-185">-Force</span><span class="sxs-lookup"><span data-stu-id="c8a6f-185">-Force</span></span>

<span data-ttu-id="c8a6f-186">Força o comando a ser executado sem solicitar confirmação do usuário.\\</span><span class="sxs-lookup"><span data-stu-id="c8a6f-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="c8a6f-187">Além disso, ele também solicita confirmação quando você insere um nome do computador curto ou simples (como um nome que não seja um nome de domínio ou não seja totalmente qualificado).</span><span class="sxs-lookup"><span data-stu-id="c8a6f-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="c8a6f-188">A confirmação é solicitada por motivos de segurança, de modo que você apenas possa usar o nome simples para adicionar um computador se o computador estiver em um grupo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="c8a6f-189">Aliases</span><span class="sxs-lookup"><span data-stu-id="c8a6f-189">Aliases</span></span>                              | <span data-ttu-id="c8a6f-190">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-190">none</span></span>                                 |
| <span data-ttu-id="c8a6f-191">Necessário?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-191">Required?</span></span>                            | <span data-ttu-id="c8a6f-192">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-192">false</span></span>                                |
| <span data-ttu-id="c8a6f-193">Posição?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-193">Position?</span></span>                            | <span data-ttu-id="c8a6f-194">chamada</span><span class="sxs-lookup"><span data-stu-id="c8a6f-194">named</span></span>                                |
| <span data-ttu-id="c8a6f-195">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c8a6f-195">Default Value</span></span>                        | <span data-ttu-id="c8a6f-196">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-196">none</span></span>                                 |
| <span data-ttu-id="c8a6f-197">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c8a6f-198">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-198">false</span></span>                                |
| <span data-ttu-id="c8a6f-199">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c8a6f-200">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="c8a6f-201">-RuleName \<String\></span><span class="sxs-lookup"><span data-stu-id="c8a6f-201">-RuleName \<String\></span></span>

<span data-ttu-id="c8a6f-202">Especifica o nome amigável dessa regra.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="c8a6f-203">Aliases</span><span class="sxs-lookup"><span data-stu-id="c8a6f-203">Aliases</span></span>                              | <span data-ttu-id="c8a6f-204">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-204">none</span></span>                                 |
| <span data-ttu-id="c8a6f-205">Necessário?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-205">Required?</span></span>                            | <span data-ttu-id="c8a6f-206">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-206">false</span></span>                                |
| <span data-ttu-id="c8a6f-207">Posição?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-207">Position?</span></span>                            | <span data-ttu-id="c8a6f-208">chamada</span><span class="sxs-lookup"><span data-stu-id="c8a6f-208">named</span></span>                                |
| <span data-ttu-id="c8a6f-209">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c8a6f-209">Default Value</span></span>                        | <span data-ttu-id="c8a6f-210">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-210">none</span></span>                                 |
| <span data-ttu-id="c8a6f-211">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c8a6f-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c8a6f-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="c8a6f-213">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c8a6f-214">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="c8a6f-215">-UserGroupName \<String\[\]\></span><span class="sxs-lookup"><span data-stu-id="c8a6f-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="c8a6f-216">Especifica o nome de um ou mais grupos de usuários no AD DS ou grupos locais aos quais essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="c8a6f-217">Aliases</span><span class="sxs-lookup"><span data-stu-id="c8a6f-217">Aliases</span></span>                              | <span data-ttu-id="c8a6f-218">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-218">none</span></span>                                 |
| <span data-ttu-id="c8a6f-219">Necessário?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-219">Required?</span></span>                            | <span data-ttu-id="c8a6f-220">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="c8a6f-220">true</span></span>                                 |
| <span data-ttu-id="c8a6f-221">Posição?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-221">Position?</span></span>                            | <span data-ttu-id="c8a6f-222">chamada</span><span class="sxs-lookup"><span data-stu-id="c8a6f-222">named</span></span>                                |
| <span data-ttu-id="c8a6f-223">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c8a6f-223">Default Value</span></span>                        | <span data-ttu-id="c8a6f-224">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-224">none</span></span>                                 |
| <span data-ttu-id="c8a6f-225">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c8a6f-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c8a6f-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="c8a6f-227">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c8a6f-228">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="c8a6f-229">-UserName \<String\[\]\></span><span class="sxs-lookup"><span data-stu-id="c8a6f-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="c8a6f-230">Especifica um ou mais usuários aos quais essa regra concede acesso.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="c8a6f-231">O nome de usuário pode ser uma conta de usuário local no computador do gateway ou um usuário no AD DS.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="c8a6f-232">O formato é `domain\user` ou `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="c8a6f-233">Aliases</span><span class="sxs-lookup"><span data-stu-id="c8a6f-233">Aliases</span></span>                              | <span data-ttu-id="c8a6f-234">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-234">none</span></span>                                 |
| <span data-ttu-id="c8a6f-235">Necessário?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-235">Required?</span></span>                            | <span data-ttu-id="c8a6f-236">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="c8a6f-236">true</span></span>                                 |
| <span data-ttu-id="c8a6f-237">Posição?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-237">Position?</span></span>                            | <span data-ttu-id="c8a6f-238">1</span><span class="sxs-lookup"><span data-stu-id="c8a6f-238">1</span></span>                                    |
| <span data-ttu-id="c8a6f-239">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c8a6f-239">Default Value</span></span>                        | <span data-ttu-id="c8a6f-240">none</span><span class="sxs-lookup"><span data-stu-id="c8a6f-240">none</span></span>                                 |
| <span data-ttu-id="c8a6f-241">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c8a6f-242">Verdadeiro (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c8a6f-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="c8a6f-243">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="c8a6f-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c8a6f-244">false</span><span class="sxs-lookup"><span data-stu-id="c8a6f-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="c8a6f-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="c8a6f-245">\<CommonParameters\></span></span>

<span data-ttu-id="c8a6f-246">Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="c8a6f-247">Para obter mais informações, consulte [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="c8a6f-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="c8a6f-248">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="c8a6f-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="c8a6f-249">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c8a6f-249">String</span></span>

<span data-ttu-id="c8a6f-250">Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="c8a6f-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="c8a6f-251">String\[\]</span></span>

<span data-ttu-id="c8a6f-252">Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="c8a6f-253">Saídas</span><span class="sxs-lookup"><span data-stu-id="c8a6f-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="c8a6f-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c8a6f-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="c8a6f-255">Este cmdlet retorna o objeto de regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="c8a6f-256">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="c8a6f-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="c8a6f-257">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="c8a6f-257">EXAMPLE 1</span></span>

<span data-ttu-id="c8a6f-258">Este exemplo concede acesso à configuração de sessão *PSWAEndpoint*, um runspace restrito no *srv2* para os usuários no grupo *SMAdmins*.\\</span><span class="sxs-lookup"><span data-stu-id="c8a6f-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="c8a6f-259">**Observação**: o nome do computador deve ser um FQDN (nome de domínio totalmente qualificado).</span><span class="sxs-lookup"><span data-stu-id="c8a6f-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="c8a6f-260">Os administradores definem uma configuração de sessão restrita ou um runspace, que é um intervalo limitado de cmdlets e tarefas que os usuários finais podem executar.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="c8a6f-261">A definição de um runspace restrito pode evitar que usuários acessem outros computadores que não estejam no runspace permitido do Windows PowerShell®, oferecendo assim uma conexão mais segura.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="c8a6f-262">Para obter mais informações sobre as configurações de sessão, consulte [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) ou [Instalar e usar o Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="c8a6f-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="c8a6f-263">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="c8a6f-263">EXAMPLE 2</span></span>

<span data-ttu-id="c8a6f-264">Este exemplo concede acesso à configuração de sessão padrão do Windows PowerShell, `Microsoft.PowerShell`, no *srv2* para os usuários chamados `contoso\user1`, `contoso\user2` e `contoso\user3`.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="c8a6f-265">Esse cmdlet cria três regras (uma por pessoa).</span><span class="sxs-lookup"><span data-stu-id="c8a6f-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="c8a6f-266">EXEMPLO 3</span><span class="sxs-lookup"><span data-stu-id="c8a6f-266">EXAMPLE 3</span></span>

<span data-ttu-id="c8a6f-267">Este exemplo ilustra como inserir valores de nome de usuário por meio do pipeline.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-267">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="c8a6f-268">EXEMPLO 4</span><span class="sxs-lookup"><span data-stu-id="c8a6f-268">EXAMPLE 4</span></span>

<span data-ttu-id="c8a6f-269">Este exemplo ilustra como todos os parâmetros obtêm os valores do pipeline pelo nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="c8a6f-270">EXEMPLO 5</span><span class="sxs-lookup"><span data-stu-id="c8a6f-270">EXAMPLE 5</span></span>

<span data-ttu-id="c8a6f-271">Este exemplo adiciona uma regra para permitir que o usuário local chamado `PswaServer\ChrisLocal` acesse um servidor chamado **srv1.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-271">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="c8a6f-272">Este exemplo ilustra um cenário em que o gateway está em um grupo de trabalho e o computador de destino está em um domínio.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="c8a6f-273">A regra de autorização aplica-se aos usuários locais no gateway.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="c8a6f-274">Na página de logon do Windows PowerShell Web Access, para autenticar-se com êxito, o usuário deve fornecer um segundo conjunto de credenciais na área **Configurações opcionais de conexão**.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="c8a6f-275">O servidor de gateway usa o conjunto adicional de credenciais para autenticar o usuário no computador de destino, um servidor chamado *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="c8a6f-276">EXEMPLO 6</span><span class="sxs-lookup"><span data-stu-id="c8a6f-276">EXAMPLE 6</span></span>

<span data-ttu-id="c8a6f-277">Este exemplo permite que todos os usuários acessem todos os pontos de extremidade em todos os computadores.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="c8a6f-278">Essa opção basicamente desativa as regras de autorização.\\</span><span class="sxs-lookup"><span data-stu-id="c8a6f-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="c8a6f-279">**Observação**: o uso do caractere curinga `*` não é recomendado para implantações que exigem um alto nível de segurança e só deve ser considerado para ambientes de teste ou usado em implantações nas quais a segurança possa ser reduzida.</span><span class="sxs-lookup"><span data-stu-id="c8a6f-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="c8a6f-280">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c8a6f-280">See Also</span></span>

<span data-ttu-id="c8a6f-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="c8a6f-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="c8a6f-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="c8a6f-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="c8a6f-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="c8a6f-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="c8a6f-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="c8a6f-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="c8a6f-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="c8a6f-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="c8a6f-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="c8a6f-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="c8a6f-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="c8a6f-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)