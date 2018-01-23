---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Opções de Credenciais nos Dados de Configuração"
ms.openlocfilehash: 15cdb29127d9774c58e1d6518bbba56273e7defd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="credentials-options-in-configuration-data"></a>Opções de Credenciais nos Dados de Configuração
>Aplica-se a: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Senhas de Texto Sem Formatação e Usuários do Domínio

As configurações DSC com uma credencial sem criptografia gerarão mensagens de erro sobre senhas de texto sem formatação.
Além disso, a DSC gerará um aviso quando usar credenciais de domínio.
Para suprimir essas mensagens de erro e aviso, use as palavras-chave de dados de configuração DSC:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

> [!NOTE]
> Armazenar/transmitir senhas de texto sem formatação não criptografadas não é seguro. É recomendável proteger credenciais usando as técnicas discutidas mais adiante neste tópico.
> O serviço de DSC de Automação do Azure permite que gerenciar centralmente as credenciais a serem compiladas em configurações e armazenadas com segurança.
> Para obter informações, consulte: [Compilando configurações de DSC / Ativos de credencial](/azure/automation/automation-dsc-compile#credential-assets)

A seguir, um exemplo de passar credenciais de texto sem formatação:

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

## <a name="handling-credentials-in-dsc"></a>Lidando com Credenciais na DSC

Os recursos de configuração DSC são executados como `Local System` por padrão.
Contudo, alguns recursos precisam de uma credencial, como quando o recurso `Package` precisa instalar um software em uma conta de usuário específica.

Recursos anteriores usaram um nome de propriedade `Credential` embutido em código para lidar com isso.
O WMF 5.0 adicionou uma propriedade `PsDscRunAsCredential` automática para todos os recursos.
Para obter informações sobre como usar o `PsDscRunAsCredential`, confira [Executar DSC com as credenciais do usuário](runAsUser.md).
Recursos mais recentes e recursos personalizados podem usar essa propriedade automática em vez de criar sua própria propriedade para credenciais.

> [!NOTE]
> O design de alguns recursos consiste em usar diversas credenciais por um motivo específico e eles terão suas próprias propriedades de credencial.

Para encontrar as propriedades de credencial disponíveis em um recurso, use `Get-DscResource -Name ResourceName -Syntax` ou o Intellisense no ISE (`CTRL+SPACE`).

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

Esse exemplo usa um recurso [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) do módulo interno de recurso de DSC `PSDesiredStateConfiguration`.
Pode criar grupos locais e adicionar ou remover membros.
Ele aceita a propriedade `Credential` e a propriedade `PsDscRunAsCredential` automática.
No entanto, o recurso usa apenas a propriedade `Credential`.

Para saber mais sobre a propriedade `PsDscRunAsCredential`, veja [Execução do DSC com as credenciais do usuário](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Exemplo: a propriedade de credencial do recurso Group

A DSC é executada em `Local System`; portanto, já tem permissões para alterar os usuários locais e grupos.
Se o membro adicionado for uma conta local, nenhuma credencial será necessária.
Se o recurso `Group` adicionar uma conta de domínio ao grupo local, uma credencial será necessária.

Não são permitidas consultas anônimas ao Active Directory.
A propriedade `Credential` do recurso `Group` é a conta de domínio usada para consultar o Active Directory.
Em geral, pode ser uma conta de usuário genérica, porque, por padrão, os usuários podem *ler* a maioria dos objetos no Active Directory.

## <a name="example-configuration"></a>Exemplo de Configuração

O exemplo de código a seguir usa DSC para preencher um grupo local com um usuário de domínio:

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

Esse código gera uma mensagem de erro e uma de aviso:

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

Esse exemplo tem dois problemas:
1. Um erro explica que senhas de texto sem formatação não são recomendadas
2. Um aviso alerta para não usar uma credencial de domínio

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

A primeira mensagem de erro tem uma URL com a documentação.
Esse link explica como criptografar senhas usando uma estrutura [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) e um certificado.
Para obter mais informações sobre certificados e DSC, [leia esta postagem](http://aka.ms/certs4dsc).

Para forçar uma senha de texto sem formatação, o recurso requer a palavra-chave `PsDscAllowPlainTextPassword` na seção de dados de configuração, conforme segue:

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

> [!NOTE]
> `NodeName` não pode ser um asterisco; um nome do nó específico é obrigatório.

**A Microsoft avisa para evitar senhas de texto sem formatação devido ao risco de segurança significativo.**

Uma exceção seria ao usar o serviço de DSC de Automação do Azure, pois os dados sempre são armazenados criptografados (em trânsito, em repouso no serviço e em repouso no nó).

## <a name="domain-credentials"></a>Credenciais de Domínio

Executar o script de configuração de exemplo novamente (com ou sem criptografia) ainda gera um aviso de que o uso de uma conta de domínio para uma credencial não é recomendado.
O uso de uma conta local elimina a possível exposição das credenciais de domínio que podem ser usadas em outros servidores.

**Ao usar credenciais com recursos de DSC, prefira uma conta local a uma conta de domínio, quando possível.**

Se houver um '\'' ou um '@' na propriedade `Username` da credencial, a DSC vai tratá-la como uma conta de domínio.
Há uma exceção para "localhost", "127.0.0.1" e "::1" na parte do domínio do nome de usuário.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

No exemplo do recurso `Group` da DSC acima, a consulta de um domínio do Active Directory *exige* uma conta de domínio.
Nesse caso, adicione a propriedade `PSDscAllowDomainUser` ao bloco `ConfigurationData` conforme segue:

```powershell
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

Agora o script de configuração vai gerar o arquivo MOF sem erros ou avisos.
