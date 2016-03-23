# Opções de Credenciais nos Dados de Configuração
>Aplica-se a: Windows PowerShell 5.0

## Senhas de Texto Sem Formatação e Usuários do Domínio

As configurações DSC que contêm uma credencial sem criptografia gerarão mensagens de erro sobre senhas de texto sem formatação.
Além disso, a DSC gerará um aviso quando usar credenciais de domínio.
Para suprimir essas mensagens de erro e aviso, use as palavras-chave de dados de configuração DSC:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

## Lidando com Credenciais na DSC

Os recursos de configuração DSC são executados como `Local System` por padrão.
Contudo, alguns recursos precisam de uma credencial, como quando o recurso `Package` precisa instalar um software em uma conta de usuário específica.

Recursos anteriores usaram um nome de propriedade `Credential` embutido em código para lidar com isso.
O WMF 5.0 adicionou uma propriedade `PsDscRunAsCredential` automática para todos os recursos.
Recursos mais recentes e recursos personalizados podem usar essa propriedade automática em vez de criar sua própria propriedade para credenciais.

*Observe que o design de alguns recursos consiste em usar diversas credenciais por um motivo específico e eles terão suas próprias propriedades de credencial.*

Para encontrar as propriedades de credencial disponíveis em um recurso, use `Get-DscResource -Name ResourceName -Syntax` ou o Intellisense no ISE (`CTRL+SPACE`).

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

Esse exemplo usa um recurso [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) do módulo interno de recurso de DSC `PSDesiredStateConfiguration`.
Pode criar grupos locais e adicionar ou remover membros.
Ele aceita a propriedade `Credential` e a propriedade `PsDscRunAsCredential` automática.
No entanto, o recurso usa apenas a propriedade `Credential`.
Leia mais sobre `PsDscRunAsCredential` nas [Notas de Versão do WMF](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_runas).

## Exemplo: a propriedade de credencial do recurso Group

A DSC é executada em `Local System`; portanto, já tem permissões para alterar os usuários locais e grupos.
Se o membro adicionado for uma conta local, nenhuma credencial será necessária.
Se o recurso `Group` adicionar uma conta de domínio ao grupo local, uma credencial será necessária.

Não são permitidas consultas anônimas ao Active Directory.
A propriedade `Credential` do recurso `Group` é a conta de domínio usada para consultar o Active Directory.
Em geral, pode ser uma conta de usuário genérica, porque, por padrão, os usuários podem *ler* a maioria dos objetos no Active Directory.

## Exemplo de Configuração

O exemplo de código a seguir usa DSC para preencher um grupo local com um usuário de domínio:

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
1.  Um erro explica que senhas de texto sem formatação não são recomendadas
2.  Um aviso alerta para não usar uma credencial de domínio

## PsDscAllowPlainTextPassword

A primeira mensagem de erro tem uma URL com a documentação.
Esse link explica como criptografar senhas usando uma estrutura [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) e um certificado.
Para obter mais informações sobre certificados e DSC, [leia esta postagem](http://aka.ms/certs4dsc).

Para forçar uma senha de texto sem formatação, o recurso requer a palavra-chave `PsDscAllowPlainTextPassword` na seção de dados de configuração, conforme segue:

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

*Observe que `NodeName` não pode ser igual a um asterisco; um nome de nó específico é obrigatório.*

**O Microsoft avisa para evitar senhas de texto sem formatação devido ao risco de segurança significativo.**

## Credenciais de Domínio

Executar o script de configuração de exemplo novamente (com ou sem criptografia) ainda gera um aviso de que o uso de uma conta de domínio para uma credencial não é recomendado.
O uso de uma conta local elimina a possível exposição das credenciais de domínio que podem ser usadas em outros servidores.

**Ao usar credenciais com recursos de DSC, prefira uma conta local a uma conta de domínio, quando possível.**

Se houver um '\' ou um '@' na propriedade `Username` da credencial, a DSC vai tratá-la como uma conta de domínio.
Há uma exceção para "localhost", "127.0.0.1" e "::1" na parte do domínio do nome de usuário.

## PSDscAllowDomainUser

No exemplo do recurso `Group` da DSC acima, a consulta de um domínio do Active Directory *exige* uma conta de domínio.
Nesse caso, adicione a propriedade `PSDscAllowDomainUser` ao bloco `ConfigurationData` conforme segue:

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

Agora o script de configuração vai gerar o arquivo MOF sem erros ou avisos.
<!--HONumber=Feb16_HO4-->
