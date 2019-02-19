---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Opções de Credenciais nos Dados de Configuração
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2019
ms.locfileid: "55675885"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="9a4e9-103">Opções de Credenciais nos Dados de Configuração</span><span class="sxs-lookup"><span data-stu-id="9a4e9-103">Credentials Options in Configuration Data</span></span>

><span data-ttu-id="9a4e9-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9a4e9-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="9a4e9-105">Senhas de Texto Sem Formatação e Usuários do Domínio</span><span class="sxs-lookup"><span data-stu-id="9a4e9-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="9a4e9-106">As configurações DSC com uma credencial sem criptografia gerarão mensagens de erro sobre senhas de texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="9a4e9-107">Além disso, a DSC gerará um aviso quando usar credenciais de domínio.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="9a4e9-108">Para suprimir essas mensagens de erro e aviso, use as palavras-chave de dados de configuração DSC:</span><span class="sxs-lookup"><span data-stu-id="9a4e9-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="9a4e9-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="9a4e9-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="9a4e9-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="9a4e9-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="9a4e9-111">Armazenar/transmitir senhas de texto sem formatação não criptografadas não é seguro.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="9a4e9-112">É recomendável proteger credenciais usando as técnicas discutidas mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="9a4e9-113">O serviço de DSC de Automação do Azure permite que gerenciar centralmente as credenciais a serem compiladas em configurações e armazenadas com segurança.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="9a4e9-114">Para obter informações, consulte: [Compilando configurações de DSC / Ativos de credencial](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="9a4e9-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="9a4e9-115">Lidando com Credenciais na DSC</span><span class="sxs-lookup"><span data-stu-id="9a4e9-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="9a4e9-116">Os recursos de configuração DSC são executados como `Local System` por padrão.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-116">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="9a4e9-117">Contudo, alguns recursos precisam de uma credencial, como quando o recurso `Package` precisa instalar um software em uma conta de usuário específica.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="9a4e9-118">Recursos anteriores usaram um nome de propriedade `Credential` embutido em código para lidar com isso.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="9a4e9-119">O WMF 5.0 adicionou uma propriedade `PsDscRunAsCredential` automática para todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="9a4e9-120">Para obter informações sobre como usar o `PsDscRunAsCredential`, confira [Executar DSC com as credenciais do usuário](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="9a4e9-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="9a4e9-121">Recursos mais recentes e recursos personalizados podem usar essa propriedade automática em vez de criar sua própria propriedade para credenciais.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="9a4e9-122">O design de alguns recursos consiste em usar diversas credenciais por um motivo específico e eles terão suas próprias propriedades de credencial.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="9a4e9-123">Para encontrar as propriedades de credencial disponíveis em um recurso, use `Get-DscResource -Name ResourceName -Syntax` ou o Intellisense no ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="9a4e9-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
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

<span data-ttu-id="9a4e9-124">Esse exemplo usa um recurso [Group](../resources/resources.md) do módulo interno de recurso de DSC `PSDesiredStateConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="9a4e9-125">Pode criar grupos locais e adicionar ou remover membros.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-125">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="9a4e9-126">Ele aceita a propriedade `Credential` e a propriedade `PsDscRunAsCredential` automática.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="9a4e9-127">No entanto, o recurso usa apenas a propriedade `Credential`.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="9a4e9-128">Para saber mais sobre a propriedade `PsDscRunAsCredential`, veja [Execução do DSC com as credenciais do usuário](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="9a4e9-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="9a4e9-129">Exemplo: a propriedade de credencial do recurso Group</span><span class="sxs-lookup"><span data-stu-id="9a4e9-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="9a4e9-130">A DSC é executada em `Local System`; portanto, já tem permissões para alterar os usuários locais e grupos.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="9a4e9-131">Se o membro adicionado for uma conta local, nenhuma credencial será necessária.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-131">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="9a4e9-132">Se o recurso `Group` adicionar uma conta de domínio ao grupo local, uma credencial será necessária.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="9a4e9-133">Não são permitidas consultas anônimas ao Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-133">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="9a4e9-134">A propriedade `Credential` do recurso `Group` é a conta de domínio usada para consultar o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="9a4e9-135">Em geral, pode ser uma conta de usuário genérica, porque, por padrão, os usuários podem *ler* a maioria dos objetos no Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="9a4e9-136">Exemplo de Configuração</span><span class="sxs-lookup"><span data-stu-id="9a4e9-136">Example Configuration</span></span>

<span data-ttu-id="9a4e9-137">O exemplo de código a seguir usa DSC para preencher um grupo local com um usuário de domínio:</span><span class="sxs-lookup"><span data-stu-id="9a4e9-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

```powershell
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

<span data-ttu-id="9a4e9-138">Esse código gera uma mensagem de erro e uma de aviso:</span><span class="sxs-lookup"><span data-stu-id="9a4e9-138">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

<span data-ttu-id="9a4e9-139">Esse exemplo tem dois problemas:</span><span class="sxs-lookup"><span data-stu-id="9a4e9-139">This example has two issues:</span></span>

1. <span data-ttu-id="9a4e9-140">Um erro explica que senhas de texto sem formatação não são recomendadas</span><span class="sxs-lookup"><span data-stu-id="9a4e9-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="9a4e9-141">Um aviso alerta para não usar uma credencial de domínio</span><span class="sxs-lookup"><span data-stu-id="9a4e9-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="9a4e9-142">Os sinalizadores **PSDSCAllowPlainTextPassword** e **PSDSCAllowDomainUser** suprimir o erro e aviso informando o usuário sobre o risco envolvido.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="9a4e9-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="9a4e9-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="9a4e9-144">A primeira mensagem de erro tem uma URL com a documentação.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="9a4e9-145">Esse link explica como criptografar senhas usando uma estrutura [ConfigurationData](./configData.md) e um certificado.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="9a4e9-146">Para obter mais informações sobre certificados e DSC, [leia esta postagem](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="9a4e9-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="9a4e9-147">Para forçar uma senha de texto sem formatação, o recurso requer a palavra-chave `PsDscAllowPlainTextPassword` na seção de dados de configuração, conforme segue:</span><span class="sxs-lookup"><span data-stu-id="9a4e9-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
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

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a><span data-ttu-id="9a4e9-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="9a4e9-148">localhost.mof</span></span>

<span data-ttu-id="9a4e9-149">O **PSDSCAllowPlainTextPassword** sinalizador requer que o usuário confirme o risco de armazenar senhas em texto sem formatação em um arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="9a4e9-150">No arquivo MOF gerado, mesmo que um **PSCredential** objeto que contém uma **SecureString** tiver sido usado, as senhas ainda aparecem como texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="9a4e9-151">Isso é o único momento em que as credenciais são expostas.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="9a4e9-152">Obtendo acesso a este dá do arquivo MOF qualquer pessoa acesse a conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="9a4e9-153">Credenciais em trânsito e em repouso</span><span class="sxs-lookup"><span data-stu-id="9a4e9-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="9a4e9-154">O **PSDscAllowPlainTextPassword** sinalizador permite a compilação de arquivos MOF que contêm as senhas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span>
  <span data-ttu-id="9a4e9-155">Tome precauções ao armazenar os arquivos MOF que contém senhas de texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="9a4e9-156">Quando o arquivo MOF é entregue a um nó no **enviar por Push** modo, o WinRM criptografa a comunicação para proteger a senha de texto não criptografado, a menos que você substituir o padrão com o **AllowUnencrypted** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="9a4e9-157">Criptografar o MOF com um certificado protege o arquivo MOF em repouso, antes que ela foi aplicada a um nó.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="9a4e9-158">Na **Pull** modo, você pode configurar o servidor de pull do Windows para usar HTTPS para criptografar o tráfego usando o protocolo especificado no servidor de informações da Internet.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="9a4e9-159">Para obter mais informações, consulte os artigos [Configurando um cliente de pull de DSC](../pull-server/pullclient.md) e [arquivos MOF protegendo com certificados](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="9a4e9-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="9a4e9-160">No [configuração de estado de automação do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) serviço Pull tráfego sempre será criptografado.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-160">In the [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="9a4e9-161">No nó, os arquivos MOF são criptografados em repouso a partir do PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="9a4e9-162">No PowerShell 4.0 MOF arquivos não são criptografados em repouso, a menos que eles são criptografados com um certificado quando enviada por push ou extraídos para o nó.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="9a4e9-163">**A Microsoft avisa para evitar senhas de texto sem formatação devido ao risco de segurança significativo.**</span><span class="sxs-lookup"><span data-stu-id="9a4e9-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="9a4e9-164">Credenciais de Domínio</span><span class="sxs-lookup"><span data-stu-id="9a4e9-164">Domain Credentials</span></span>

<span data-ttu-id="9a4e9-165">Executar o script de configuração de exemplo novamente (com ou sem criptografia) ainda gera um aviso de que o uso de uma conta de domínio para uma credencial não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="9a4e9-166">O uso de uma conta local elimina a possível exposição das credenciais de domínio que podem ser usadas em outros servidores.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="9a4e9-167">**Ao usar credenciais com recursos de DSC, prefira uma conta local a uma conta de domínio, quando possível.**</span><span class="sxs-lookup"><span data-stu-id="9a4e9-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="9a4e9-168">Se houver um "\\" ou um "\@", na propriedade `Username` da credencial, a DSC vai tratá-la como uma conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="9a4e9-169">Há uma exceção para "localhost", "127.0.0.1" e "::1" na parte do domínio do nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="9a4e9-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="9a4e9-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="9a4e9-171">No exemplo do recurso `Group` da DSC acima, a consulta de um domínio do Active Directory *exige* uma conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="9a4e9-172">Nesse caso, adicione a propriedade `PSDscAllowDomainUser` ao bloco `ConfigurationData` conforme segue:</span><span class="sxs-lookup"><span data-stu-id="9a4e9-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

<span data-ttu-id="9a4e9-173">Agora o script de configuração vai gerar o arquivo MOF sem erros ou avisos.</span><span class="sxs-lookup"><span data-stu-id="9a4e9-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
