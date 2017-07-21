---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Opções de Credenciais nos Dados de Configuração"
ms.openlocfilehash: 7fadce447c418b229a534e92d12bc2131365a37a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="28986-103">Opções de Credenciais nos Dados de Configuração</span><span class="sxs-lookup"><span data-stu-id="28986-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="28986-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="28986-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="28986-105">Senhas de Texto Sem Formatação e Usuários do Domínio</span><span class="sxs-lookup"><span data-stu-id="28986-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="28986-106">As configurações DSC que contêm uma credencial sem criptografia gerarão mensagens de erro sobre senhas de texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="28986-106">DSC configurations containing a credential without encryption will generate an error messages about plain text passwords.</span></span>
<span data-ttu-id="28986-107">Além disso, a DSC gerará um aviso quando usar credenciais de domínio.</span><span class="sxs-lookup"><span data-stu-id="28986-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="28986-108">Para suprimir essas mensagens de erro e aviso, use as palavras-chave de dados de configuração DSC:</span><span class="sxs-lookup"><span data-stu-id="28986-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="28986-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="28986-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="28986-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="28986-110">**PsDscAllowDomainUser**</span></span>

><span data-ttu-id="28986-111">**Observação:** o uso de senhas de texto não criptografado não é seguro.</span><span class="sxs-lookup"><span data-stu-id="28986-111">**Note:** Using plaintext passwords is not secure.</span></span> <span data-ttu-id="28986-112">É recomendável proteger credenciais usando as técnicas discutidas mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="28986-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>

<span data-ttu-id="28986-113">A seguir, um exemplo de passar credenciais de texto sem formatação:</span><span class="sxs-lookup"><span data-stu-id="28986-113">The following is an example of passing plain text credentials:</span></span>

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
        @{
            # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="*"
            PSDscAllowPlainTextPassword = $true
        },
        #however, each node still needs to be explicitly defined for "*" to have meaning
        @{
            NodeName = "TestMachine1"
        },
        #we can also use a property to define node-specific passwords, although this is no more secure
        @{
            NodeName = "TestMachine2";
            UserName = "User2"
            LocalPassword = "ThisIsYetAnotherPlaintextPassword"
        }
        )
}
configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="28986-114">Lidando com Credenciais na DSC</span><span class="sxs-lookup"><span data-stu-id="28986-114">Handling Credentials in DSC</span></span>

<span data-ttu-id="28986-115">Os recursos de configuração DSC são executados como `Local System` por padrão.</span><span class="sxs-lookup"><span data-stu-id="28986-115">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="28986-116">Contudo, alguns recursos precisam de uma credencial, como quando o recurso `Package` precisa instalar um software em uma conta de usuário específica.</span><span class="sxs-lookup"><span data-stu-id="28986-116">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="28986-117">Recursos anteriores usaram um nome de propriedade `Credential` embutido em código para lidar com isso.</span><span class="sxs-lookup"><span data-stu-id="28986-117">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="28986-118">O WMF 5.0 adicionou uma propriedade `PsDscRunAsCredential` automática para todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="28986-118">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="28986-119">Para obter informações sobre como usar o `PsDscRunAsCredential`, confira [Executar DSC com as credenciais do usuário](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="28986-119">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="28986-120">Recursos mais recentes e recursos personalizados podem usar essa propriedade automática em vez de criar sua própria propriedade para credenciais.</span><span class="sxs-lookup"><span data-stu-id="28986-120">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

<span data-ttu-id="28986-121">*Observe que o design de alguns recursos consiste em usar diversas credenciais por um motivo específico e eles terão suas próprias propriedades de credencial.*</span><span class="sxs-lookup"><span data-stu-id="28986-121">*Note that the design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.*</span></span>

<span data-ttu-id="28986-122">Para encontrar as propriedades de credencial disponíveis em um recurso, use `Get-DscResource -Name ResourceName -Syntax` ou o Intellisense no ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="28986-122">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```PowerShell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="28986-123">Esse exemplo usa um recurso [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) do módulo interno de recurso de DSC `PSDesiredStateConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="28986-123">This example uses a [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="28986-124">Pode criar grupos locais e adicionar ou remover membros.</span><span class="sxs-lookup"><span data-stu-id="28986-124">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="28986-125">Ele aceita a propriedade `Credential` e a propriedade `PsDscRunAsCredential` automática.</span><span class="sxs-lookup"><span data-stu-id="28986-125">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="28986-126">No entanto, o recurso usa apenas a propriedade `Credential`.</span><span class="sxs-lookup"><span data-stu-id="28986-126">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="28986-127">Para saber mais sobre a propriedade `PsDscRunAsCredential`, veja [Execução do DSC com as credenciais do usuário](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="28986-127">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="28986-128">Exemplo: a propriedade de credencial do recurso Group</span><span class="sxs-lookup"><span data-stu-id="28986-128">Example: The Group resource Credential property</span></span>

<span data-ttu-id="28986-129">A DSC é executada em `Local System`; portanto, já tem permissões para alterar os usuários locais e grupos.</span><span class="sxs-lookup"><span data-stu-id="28986-129">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="28986-130">Se o membro adicionado for uma conta local, nenhuma credencial será necessária.</span><span class="sxs-lookup"><span data-stu-id="28986-130">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="28986-131">Se o recurso `Group` adicionar uma conta de domínio ao grupo local, uma credencial será necessária.</span><span class="sxs-lookup"><span data-stu-id="28986-131">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="28986-132">Não são permitidas consultas anônimas ao Active Directory.</span><span class="sxs-lookup"><span data-stu-id="28986-132">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="28986-133">A propriedade `Credential` do recurso `Group` é a conta de domínio usada para consultar o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="28986-133">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="28986-134">Em geral, pode ser uma conta de usuário genérica, porque, por padrão, os usuários podem *ler* a maioria dos objetos no Active Directory.</span><span class="sxs-lookup"><span data-stu-id="28986-134">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="28986-135">Exemplo de Configuração</span><span class="sxs-lookup"><span data-stu-id="28986-135">Example Configuration</span></span>

<span data-ttu-id="28986-136">O exemplo de código a seguir usa DSC para preencher um grupo local com um usuário de domínio:</span><span class="sxs-lookup"><span data-stu-id="28986-136">The following example code uses DSC to populate a local group with a domain user:</span></span>

```PowerShell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

<span data-ttu-id="28986-137">Esse código gera uma mensagem de erro e uma de aviso:</span><span class="sxs-lookup"><span data-stu-id="28986-137">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

<span data-ttu-id="28986-138">Esse exemplo tem dois problemas:</span><span class="sxs-lookup"><span data-stu-id="28986-138">This example has two issues:</span></span>
1.  <span data-ttu-id="28986-139">Um erro explica que senhas de texto sem formatação não são recomendadas</span><span class="sxs-lookup"><span data-stu-id="28986-139">An error explains that plain text passwords are not recommended</span></span>
2.  <span data-ttu-id="28986-140">Um aviso alerta para não usar uma credencial de domínio</span><span class="sxs-lookup"><span data-stu-id="28986-140">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="28986-141">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="28986-141">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="28986-142">A primeira mensagem de erro tem uma URL com a documentação.</span><span class="sxs-lookup"><span data-stu-id="28986-142">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="28986-143">Esse link explica como criptografar senhas usando uma estrutura [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) e um certificado.</span><span class="sxs-lookup"><span data-stu-id="28986-143">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="28986-144">Para obter mais informações sobre certificados e DSC, [leia esta postagem](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="28986-144">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="28986-145">Para forçar uma senha de texto sem formatação, o recurso requer a palavra-chave `PsDscAllowPlainTextPassword` na seção de dados de configuração, conforme segue:</span><span class="sxs-lookup"><span data-stu-id="28986-145">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

```PowerShell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

<span data-ttu-id="28986-146">*Observe que `NodeName` não pode ser igual a um asterisco; um nome de nó específico é obrigatório.*</span><span class="sxs-lookup"><span data-stu-id="28986-146">*Note that `NodeName` cannot equal asterisk, a specific node name is mandatory.*</span></span>

<span data-ttu-id="28986-147">**A Microsoft avisa para evitar senhas de texto sem formatação devido ao risco de segurança significativo.**</span><span class="sxs-lookup"><span data-stu-id="28986-147">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="28986-148">Credenciais de Domínio</span><span class="sxs-lookup"><span data-stu-id="28986-148">Domain Credentials</span></span>

<span data-ttu-id="28986-149">Executar o script de configuração de exemplo novamente (com ou sem criptografia) ainda gera um aviso de que o uso de uma conta de domínio para uma credencial não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="28986-149">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="28986-150">O uso de uma conta local elimina a possível exposição das credenciais de domínio que podem ser usadas em outros servidores.</span><span class="sxs-lookup"><span data-stu-id="28986-150">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="28986-151">**Ao usar credenciais com recursos de DSC, prefira uma conta local a uma conta de domínio, quando possível.**</span><span class="sxs-lookup"><span data-stu-id="28986-151">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="28986-152">Se houver um '\'' ou um '@' na propriedade `Username` da credencial, a DSC vai tratá-la como uma conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="28986-152">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="28986-153">Há uma exceção para "localhost", "127.0.0.1" e "::1" na parte do domínio do nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="28986-153">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="28986-154">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="28986-154">PSDscAllowDomainUser</span></span>

<span data-ttu-id="28986-155">No exemplo do recurso `Group` da DSC acima, a consulta de um domínio do Active Directory *exige* uma conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="28986-155">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="28986-156">Nesse caso, adicione a propriedade `PSDscAllowDomainUser` ao bloco `ConfigurationData` conforme segue:</span><span class="sxs-lookup"><span data-stu-id="28986-156">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```PowerShell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

<span data-ttu-id="28986-157">Agora o script de configuração vai gerar o arquivo MOF sem erros ou avisos.</span><span class="sxs-lookup"><span data-stu-id="28986-157">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>

