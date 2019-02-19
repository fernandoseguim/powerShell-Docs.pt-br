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
# <a name="credentials-options-in-configuration-data"></a>Opções de Credenciais nos Dados de Configuração

>Aplica-se a: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Senhas de Texto Sem Formatação e Usuários do Domínio

As configurações DSC com uma credencial sem criptografia gerarão mensagens de erro sobre senhas de texto sem formatação.
Além disso, a DSC gerará um aviso quando usar credenciais de domínio.
Para suprimir essas mensagens de erro e aviso, use as palavras-chave de dados de configuração DSC:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Armazenar/transmitir senhas de texto sem formatação não criptografadas não é seguro. É recomendável proteger credenciais usando as técnicas discutidas mais adiante neste tópico.
> O serviço de DSC de Automação do Azure permite que gerenciar centralmente as credenciais a serem compiladas em configurações e armazenadas com segurança.
> Para obter informações, consulte: [Compilando configurações de DSC / Ativos de credencial](/azure/automation/automation-dsc-compile#credential-assets)

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

Esse exemplo usa um recurso [Group](../resources/resources.md) do módulo interno de recurso de DSC `PSDesiredStateConfiguration`.
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

Esse exemplo tem dois problemas:

1. Um erro explica que senhas de texto sem formatação não são recomendadas
2. Um aviso alerta para não usar uma credencial de domínio

Os sinalizadores **PSDSCAllowPlainTextPassword** e **PSDSCAllowDomainUser** suprimir o erro e aviso informando o usuário sobre o risco envolvido.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

A primeira mensagem de erro tem uma URL com a documentação.
Esse link explica como criptografar senhas usando uma estrutura [ConfigurationData](./configData.md) e um certificado.
Para obter mais informações sobre certificados e DSC, [leia esta postagem](http://aka.ms/certs4dsc).

Para forçar uma senha de texto sem formatação, o recurso requer a palavra-chave `PsDscAllowPlainTextPassword` na seção de dados de configuração, conforme segue:

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

### <a name="localhostmof"></a>localhost.mof

O **PSDSCAllowPlainTextPassword** sinalizador requer que o usuário confirme o risco de armazenar senhas em texto sem formatação em um arquivo MOF. No arquivo MOF gerado, mesmo que um **PSCredential** objeto que contém uma **SecureString** tiver sido usado, as senhas ainda aparecem como texto sem formatação. Isso é o único momento em que as credenciais são expostas. Obtendo acesso a este dá do arquivo MOF qualquer pessoa acesse a conta de administrador.

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

### <a name="credentials-in-transit-and-at-rest"></a>Credenciais em trânsito e em repouso

- O **PSDscAllowPlainTextPassword** sinalizador permite a compilação de arquivos MOF que contêm as senhas em texto não criptografado.
  Tome precauções ao armazenar os arquivos MOF que contém senhas de texto não criptografado.
- Quando o arquivo MOF é entregue a um nó no **enviar por Push** modo, o WinRM criptografa a comunicação para proteger a senha de texto não criptografado, a menos que você substituir o padrão com o **AllowUnencrypted** parâmetro.
  - Criptografar o MOF com um certificado protege o arquivo MOF em repouso, antes que ela foi aplicada a um nó.
- Na **Pull** modo, você pode configurar o servidor de pull do Windows para usar HTTPS para criptografar o tráfego usando o protocolo especificado no servidor de informações da Internet. Para obter mais informações, consulte os artigos [Configurando um cliente de pull de DSC](../pull-server/pullclient.md) e [arquivos MOF protegendo com certificados](../pull-server/secureMOF.md).
  - No [configuração de estado de automação do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) serviço Pull tráfego sempre será criptografado.
- No nó, os arquivos MOF são criptografados em repouso a partir do PowerShell 5.0.
  - No PowerShell 4.0 MOF arquivos não são criptografados em repouso, a menos que eles são criptografados com um certificado quando enviada por push ou extraídos para o nó.

**A Microsoft avisa para evitar senhas de texto sem formatação devido ao risco de segurança significativo.**

## <a name="domain-credentials"></a>Credenciais de Domínio

Executar o script de configuração de exemplo novamente (com ou sem criptografia) ainda gera um aviso de que o uso de uma conta de domínio para uma credencial não é recomendado.
O uso de uma conta local elimina a possível exposição das credenciais de domínio que podem ser usadas em outros servidores.

**Ao usar credenciais com recursos de DSC, prefira uma conta local a uma conta de domínio, quando possível.**

Se houver um "\\" ou um "\@", na propriedade `Username` da credencial, a DSC vai tratá-la como uma conta de domínio.
Há uma exceção para "localhost", "127.0.0.1" e "::1" na parte do domínio do nome de usuário.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

No exemplo do recurso `Group` da DSC acima, a consulta de um domínio do Active Directory *exige* uma conta de domínio.
Nesse caso, adicione a propriedade `PSDscAllowDomainUser` ao bloco `ConfigurationData` conforme segue:

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

Agora o script de configuração vai gerar o arquivo MOF sem erros ou avisos.
