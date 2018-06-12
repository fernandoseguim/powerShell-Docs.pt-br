---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Dando o segundo salto na Comunicação Remota do PowerShell
ms.openlocfilehash: 1d24473178bc50321a81ebf1115a20f17078844f
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483008"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="3b90f-103">Dando o segundo salto na Comunicação Remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b90f-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="3b90f-104">O "problema do segundo salto" refere-se a uma situação semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="3b90f-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="3b90f-105">Você está conectado no _ServerA_.</span><span class="sxs-lookup"><span data-stu-id="3b90f-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="3b90f-106">No _ServerA_, você inicia uma sessão remota do PowerShell para se conectar ao _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="3b90f-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="3b90f-107">Um comando executado no _ServerB_ por meio de sua sessão de Conexão Remota do PowerShell tenta acessar um recurso no _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="3b90f-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="3b90f-108">O acesso ao recurso no _ServerC_ é negado, pois as credenciais usadas para criar a sessão de Comunicação Remota do PowerShell não foram passadas do _ServerB_ para o _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="3b90f-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="3b90f-109">Há várias maneiras de resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="3b90f-109">There are several ways to address this problem.</span></span> <span data-ttu-id="3b90f-110">Neste tópico, vamos examinar várias soluções mais comuns para o problema do segundo salto.</span><span class="sxs-lookup"><span data-stu-id="3b90f-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="3b90f-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="3b90f-111">CredSSP</span></span>

<span data-ttu-id="3b90f-112">Você pode usar o [CredSSP (Credential Security Support Provider)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="3b90f-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="3b90f-113">O CredSSP armazena em cache as credenciais no servidor remoto (_ServerB_), portanto, usá-lo abre para ataques de roubo de credenciais.</span><span class="sxs-lookup"><span data-stu-id="3b90f-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="3b90f-114">Se o computador remoto estiver comprometido, o invasor terá acesso às credenciais do usuário.</span><span class="sxs-lookup"><span data-stu-id="3b90f-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="3b90f-115">O CredSSP é desabilitado por padrão nos computadores cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="3b90f-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="3b90f-116">Você só deve habilitar o CredSSP nos ambientes mais confiáveis.</span><span class="sxs-lookup"><span data-stu-id="3b90f-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="3b90f-117">Por exemplo, um administrador de domínio que se conecta a um controlador de domínio porque o controlador de domínio é altamente confiável.</span><span class="sxs-lookup"><span data-stu-id="3b90f-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="3b90f-118">Para saber mais sobre questões de segurança ao usar o CredSSP para comunicação remota do PowerShell, consulte [Accidental Sabotage: Beware of CredSSP (Sabotagem acidental: cuidado com o CredSSP)](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="3b90f-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="3b90f-119">Para obter mais informações sobre ataques de roubo de credenciais, consulte [Mitigando ataques PtH (Pass-the-Hash) e outro roubo de credenciais](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="3b90f-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="3b90f-120">Para obter um exemplo de como habilitar e usar o CredSSP para a Comunicação Remota do PowerShell, consulte [Usando o CredSSP para resolver o problema do segundo salto](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="3b90f-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="3b90f-121">Vantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-121">Pros</span></span>

- <span data-ttu-id="3b90f-122">Ele funciona para todos os servidores com o Windows Server 2008 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="3b90f-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="3b90f-123">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-123">Cons</span></span>

- <span data-ttu-id="3b90f-124">Tem vulnerabilidades de segurança.</span><span class="sxs-lookup"><span data-stu-id="3b90f-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="3b90f-125">Requer a configuração de funções de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="3b90f-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="3b90f-126">Delegação Kerberos (irrestrita)</span><span class="sxs-lookup"><span data-stu-id="3b90f-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="3b90f-127">Você pode também pode usar a delegação Kerberos irrestrita para realizar o segundo salto.</span><span class="sxs-lookup"><span data-stu-id="3b90f-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="3b90f-128">No entanto, esse método não fornece controle de onde as credenciais delegadas são usadas.</span><span class="sxs-lookup"><span data-stu-id="3b90f-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="3b90f-129">**Observação:** As contas do Active Directory que têm a propriedade **Conta sensível à segurança não pode ser delegada** definida, não podem ser delegadas.</span><span class="sxs-lookup"><span data-stu-id="3b90f-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="3b90f-130">Para obter mais informações, consulte [Foco de Segurança: analisando 'Conta sensível à segurança não pode ser delegada' para Contas Privilegiadas](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Configurações e Ferramentas da Autenticação Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="3b90f-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="3b90f-131">Vantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-131">Pros</span></span>

- <span data-ttu-id="3b90f-132">Não exige nenhuma codificação especial.</span><span class="sxs-lookup"><span data-stu-id="3b90f-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="3b90f-133">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-133">Cons</span></span>

- <span data-ttu-id="3b90f-134">Não oferece suporte ao segundo salto para o WinRM.</span><span class="sxs-lookup"><span data-stu-id="3b90f-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="3b90f-135">Não fornece controle sobre onde as credenciais são usadas, criando uma vulnerabilidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="3b90f-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="3b90f-136">Delegação restrita de Kerberos</span><span class="sxs-lookup"><span data-stu-id="3b90f-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="3b90f-137">Você pode usar a delegação restrita herdada (não baseada em recursos) para realizar o segundo salto.</span><span class="sxs-lookup"><span data-stu-id="3b90f-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span>

><span data-ttu-id="3b90f-138">**Observação:** As contas do Active Directory que têm a propriedade **Conta sensível à segurança não pode ser delegada** definida, não podem ser delegadas.</span><span class="sxs-lookup"><span data-stu-id="3b90f-138">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="3b90f-139">Para obter mais informações, consulte [Foco de Segurança: analisando 'Conta sensível à segurança não pode ser delegada' para Contas Privilegiadas](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Configurações e Ferramentas da Autenticação Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="3b90f-139">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="3b90f-140">Vantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-140">Pros</span></span>

- <span data-ttu-id="3b90f-141">Não exige nenhuma codificação especial</span><span class="sxs-lookup"><span data-stu-id="3b90f-141">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="3b90f-142">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-142">Cons</span></span>

- <span data-ttu-id="3b90f-143">Não oferece suporte ao segundo salto para o WinRM.</span><span class="sxs-lookup"><span data-stu-id="3b90f-143">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="3b90f-144">Deve ser configurada no objeto do Active Directory do servidor remoto (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="3b90f-144">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="3b90f-145">Limitado a um domínio.</span><span class="sxs-lookup"><span data-stu-id="3b90f-145">Limited to one domain.</span></span> <span data-ttu-id="3b90f-146">Não pode cruzar domínios ou florestas.</span><span class="sxs-lookup"><span data-stu-id="3b90f-146">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="3b90f-147">Requer direitos para atualizar objetos e SPNs (Nomes de Entidade de Serviço).</span><span class="sxs-lookup"><span data-stu-id="3b90f-147">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="3b90f-148">Delegação restrita de Kerberos com base em recursos</span><span class="sxs-lookup"><span data-stu-id="3b90f-148">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="3b90f-149">A utilização da delegação restrita de Kerberos baseada em recursos (introduzida no Windows Server 2012) permite que seja configurada a delegação de credencial no objeto do servidor no qual os recursos residem.</span><span class="sxs-lookup"><span data-stu-id="3b90f-149">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="3b90f-150">No cenário de segundo salto descrito acima, você configura o _ServerC_ para especificar de onde ele aceitará as credenciais delegadas.</span><span class="sxs-lookup"><span data-stu-id="3b90f-150">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="3b90f-151">**Observação:** As contas do Active Directory que têm a propriedade **Conta sensível à segurança não pode ser delegada** definida, não podem ser delegadas.</span><span class="sxs-lookup"><span data-stu-id="3b90f-151">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="3b90f-152">Para obter mais informações, consulte [Foco de Segurança: analisando 'Conta sensível à segurança não pode ser delegada' para Contas Privilegiadas](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Configurações e Ferramentas da Autenticação Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="3b90f-152">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="3b90f-153">Vantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-153">Pros</span></span>

- <span data-ttu-id="3b90f-154">As credenciais não são armazenadas.</span><span class="sxs-lookup"><span data-stu-id="3b90f-154">Credentials are not stored.</span></span>
- <span data-ttu-id="3b90f-155">É relativamente fácil de configurar usando cmdlets do PowerShell – não é necessária nenhuma codificação especial.</span><span class="sxs-lookup"><span data-stu-id="3b90f-155">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="3b90f-156">Não é necessário acesso de domínio especial.</span><span class="sxs-lookup"><span data-stu-id="3b90f-156">No special domain access is required.</span></span>
- <span data-ttu-id="3b90f-157">Funciona entre domínios e florestas.</span><span class="sxs-lookup"><span data-stu-id="3b90f-157">Works across domains and forests.</span></span>
- <span data-ttu-id="3b90f-158">Código do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3b90f-158">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="3b90f-159">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-159">Cons</span></span>

- <span data-ttu-id="3b90f-160">Requer o Windows Server 2012 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="3b90f-160">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="3b90f-161">Não oferece suporte ao segundo salto para o WinRM.</span><span class="sxs-lookup"><span data-stu-id="3b90f-161">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="3b90f-162">Requer direitos para atualizar objetos e SPNs (Nomes de Entidade de Serviço).</span><span class="sxs-lookup"><span data-stu-id="3b90f-162">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="3b90f-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b90f-163">Example</span></span>

<span data-ttu-id="3b90f-164">Vejamos um exemplo do PowerShell que configura a delegação restrita baseada em recursos no _ServerC_ para permitir credenciais delegadas de um _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="3b90f-164">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="3b90f-165">Este exemplo pressupõe que todos os servidores estão executando o Windows Server 2012 ou posterior, e que há pelo menos um controlador de domínio do Windows Server 2012 em cada domínio aos quais os servidores pertencem.</span><span class="sxs-lookup"><span data-stu-id="3b90f-165">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="3b90f-166">Antes de configurar a delegação restrita, você deve adicionar o recurso `RSAT-AD-PowerShell` para instalar o módulo Active Directory PowerShell e, em seguida, importar esse módulo na sua sessão:</span><span class="sxs-lookup"><span data-stu-id="3b90f-166">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="3b90f-167">Vários cmdlets disponíveis agora têm um parâmetro **PrincipalsAllowedToDelegateToAccount**:</span><span class="sxs-lookup"><span data-stu-id="3b90f-167">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="3b90f-168">O parâmetro **PrincipalsAllowedToDelegateToAccount** define o atributo de objeto do Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, que contém uma lista de controle de acesso (ACL) que especifica as contas que têm permissão para delegar credenciais para a conta associada (no nosso exemplo, será a conta do computador para _Servidor_).</span><span class="sxs-lookup"><span data-stu-id="3b90f-168">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="3b90f-169">Agora vamos configurar as variáveis que usaremos para representar os servidores:</span><span class="sxs-lookup"><span data-stu-id="3b90f-169">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="3b90f-170">O WinRM (e, portanto, comunicação remota do PowerShell) é executado como a conta de computador por padrão.</span><span class="sxs-lookup"><span data-stu-id="3b90f-170">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="3b90f-171">Você pode ver isso examinando a propriedade **StartName** do serviço `winrm`:</span><span class="sxs-lookup"><span data-stu-id="3b90f-171">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="3b90f-172">Para que o _ServerC_ permita a delegação de uma sessão de comunicação remota do PowerShell no _ServerB_, vamos conceder acesso ao definir o parâmetro **PrincipalsAllowedToDelegateToAccount** no _ServerC_ para o objeto de computador do _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="3b90f-172">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="3b90f-173">O Kerberos [KDC (Centro de distribuição de chaves)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) armazena em cache as tentativas de acesso negado (cache negativo) por 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="3b90f-173">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="3b90f-174">Se _ServerB_ tentou acessar anteriormente o _ServerC_, será necessário limpar o cache no _ServerB_ invocando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3b90f-174">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="3b90f-175">Você também pode reiniciar o computador ou aguardar pelo menos 15 minutos para limpar o cache.</span><span class="sxs-lookup"><span data-stu-id="3b90f-175">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="3b90f-176">Depois de limpar o cache, é possível executar com êxito o código do _ServerA_ por meio do _ServerB_ no _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="3b90f-176">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

<span data-ttu-id="3b90f-177">Neste exemplo, a variável `$using` é usada para tornar a variável `$ServerC` visível ao _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="3b90f-177">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="3b90f-178">Para obter mais informações sobre a variável `$using`, consulte [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="3b90f-178">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="3b90f-179">Para permitir que vários servidores deleguem credenciais ao _ServerC_, defina o valor do parâmetro **PrincipalsAllowedToDelegateToAccount** no _ServerC_ em uma matriz:</span><span class="sxs-lookup"><span data-stu-id="3b90f-179">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="3b90f-180">Se você quiser realizar o segundo salto entre domínios, adicione o FQDN (nome de domínio totalmente qualificado) do controlador de domínio do domínio ao qual o _ServerB_ pertence:</span><span class="sxs-lookup"><span data-stu-id="3b90f-180">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="3b90f-181">Para remover a capacidade de delegar credenciais para o ServerC, defina o valor do parâmetro **PrincipalsAllowedToDelegateToAccount** no _ServerC_ como `$null`:</span><span class="sxs-lookup"><span data-stu-id="3b90f-181">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="3b90f-182">Informações sobre delegação restrita de Kerberos baseada em recursos</span><span class="sxs-lookup"><span data-stu-id="3b90f-182">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="3b90f-183">Novidades na Autenticação Kerberos</span><span class="sxs-lookup"><span data-stu-id="3b90f-183">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="3b90f-184">Como o Windows Server 2012 Ameniza a Dificuldade da Delegação Restrita de Kerberos, Parte 1</span><span class="sxs-lookup"><span data-stu-id="3b90f-184">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="3b90f-185">Como o Windows Server 2012 Ameniza a Dificuldade da Delegação Restrita de Kerberos, Parte 2</span><span class="sxs-lookup"><span data-stu-id="3b90f-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="3b90f-186">Noções básicas sobre a Delegação Restrita de Kerberos para Implantações de Proxy de Aplicativo do Azure Active Directory com a Autenticação Integrada do Windows</span><span class="sxs-lookup"><span data-stu-id="3b90f-186">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](http://aka.ms/kcdpaper)
- <span data-ttu-id="3b90f-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="3b90f-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="3b90f-188">[[MS-SFU]: Extensões do protocolo Kerberos: serviço para usuário e Protocolo de Delegação Restrita 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="3b90f-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="3b90f-189">Delegação Restrita de Kerberos Baseada em Recursos</span><span class="sxs-lookup"><span data-stu-id="3b90f-189">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="3b90f-190">Administração remota sem a delegação restrita usando PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="3b90f-190">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="3b90f-191">PSSessionConfiguration usando RunAs</span><span class="sxs-lookup"><span data-stu-id="3b90f-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="3b90f-192">Você pode criar uma configuração de sessão no _ServerB_ e definir o parâmetro **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="3b90f-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="3b90f-193">Para obter informações sobre como usar PSSessionConfiguration e RunAs para resolver o problema do segundo salto, consulte [Outra solução para a comunicação remota de saltos múltiplos do PowerShell](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="3b90f-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="3b90f-194">Vantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-194">Pros</span></span>

- <span data-ttu-id="3b90f-195">Funciona com qualquer servidor com o WMF 3.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="3b90f-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="3b90f-196">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-196">Cons</span></span>

- <span data-ttu-id="3b90f-197">Requer a configuração de **PSSessionConfiguration** e de **RunAs** em cada servidor intermediário (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="3b90f-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="3b90f-198">Requer manutenção de senha ao usar uma conta **RunAs** de domínio</span><span class="sxs-lookup"><span data-stu-id="3b90f-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="3b90f-199">JEA (Administração Just Enough)</span><span class="sxs-lookup"><span data-stu-id="3b90f-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="3b90f-200">O JEA permite restringir os comandos que um administrador pode executar durante uma sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3b90f-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="3b90f-201">Pode ser usado para resolver o problema do segundo salto.</span><span class="sxs-lookup"><span data-stu-id="3b90f-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="3b90f-202">Para obter informações sobre o JEA, consulte [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="3b90f-202">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="3b90f-203">Vantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-203">Pros</span></span>

- <span data-ttu-id="3b90f-204">Não necessita manutenção de senha ao usar uma conta virtual.</span><span class="sxs-lookup"><span data-stu-id="3b90f-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="3b90f-205">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-205">Cons</span></span>

- <span data-ttu-id="3b90f-206">Requer o WMF 5.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="3b90f-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="3b90f-207">Requer a configuração em cada servidor intermediário (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="3b90f-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="3b90f-208">Passar credenciais dentro de um bloco de script Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="3b90f-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="3b90f-209">É possível passar credenciais dentro do parâmetro **ScriptBlock** de uma chamada do cmdlet [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="3b90f-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="3b90f-210">Vantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-210">Pros</span></span>

- <span data-ttu-id="3b90f-211">Não requer configuração especial do servidor.</span><span class="sxs-lookup"><span data-stu-id="3b90f-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="3b90f-212">Funciona em qualquer servidor que executa o WMF 2.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="3b90f-212">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="3b90f-213">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="3b90f-213">Cons</span></span>

- <span data-ttu-id="3b90f-214">Requer uma técnica de código complicada.</span><span class="sxs-lookup"><span data-stu-id="3b90f-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="3b90f-215">Se estiver executando o WMF 2.0, necessita de uma sintaxe diferente para passar argumentos para uma sessão remota.</span><span class="sxs-lookup"><span data-stu-id="3b90f-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="3b90f-216">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b90f-216">Example</span></span>

<span data-ttu-id="3b90f-217">O exemplo a seguir mostra como passar credenciais em um bloco de script **Invoke-Command**:</span><span class="sxs-lookup"><span data-stu-id="3b90f-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="3b90f-218">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b90f-218">See also</span></span>

[<span data-ttu-id="3b90f-219">Considerações de segurança de comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b90f-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)