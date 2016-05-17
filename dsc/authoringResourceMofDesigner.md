---
title:   Usando a ferramenta Designer de Recursos
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Usando a ferramenta Designer de Recursos

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

A ferramenta Designer de Recursos é um conjunto de cmdlets expostos pelo módulo **xDscResourceDesigner** que facilitam a criação de recursos de Configuração de Estado Desejado (DSC) do Windows PowerShell. Os cmdlets nesse recurso ajudam a criar o esquema MOF, o módulo de script e a estrutura de diretórios para seu novo recurso. Para obter mais informações sobre recursos de DSC, consulte [Criar recursos personalizados de configuração de estado desejado do Windows PowerShell](authoringResource.md).
Neste tópico, criaremos um recurso de DSC que gerencia os usuários do Active Directory.
Use o cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) para instalar o módulo **xDscResourceDesigner**.

>**Observação**: **Install-Module** está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0. É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## Criando propriedades de recurso
A primeira coisa que precisamos fazer é decidir sobre as propriedades que serão expostas pelo recuso. Para esse exemplo, definiremos um usuário do Active Directory com as seguintes propriedades.
 
Nome do parâmetro Descrição
* **UserName**: propriedade de chave que identifica um usuário com exclusividade.
* **Ensure**: especifica se a conta do usuário deve ser do tipo Present ou Absent. Esse parâmetro terá apenas dois valores possíveis.
* **DomainCredential**: a senha do domínio para o usuário.
* **Password**: a senha desejada para o usuário permitir que uma configuração altere a senha do usuário, se necessário.

Para criar as propriedades, usamos o cmdlet **novo xDscResourceProperty**. Os seguintes comandos do PowerShell criam as propriedades descritas acima.

```powershell
PS C:\> $UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
PS C:\> $Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
PS C:\> $DomainCredential = New-xDscResourceProperty –Name DomainCredential-Type PSCredential -Attribute Write
PS C:\> $Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## Criar o recurso

Agora que as propriedades do recurso foram criadas, podemos chamar o cmdlet **New-xDscResource** para criar o recurso. O cmdlet **New-xDscResource** utiliza a lista de propriedades como parâmetros. Também usa o caminho no qual o módulo deve ser criado, o nome do novo recurso e o nome do módulo no qual ele está contido. O comando do PowerShell a seguir cria o recurso.

```powershell
PS C:\> New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

O cmdlet **New-xDscResource** cria o esquema MOF, um script de recurso esqueleto, a estrutura de diretório necessária para o novo recurso e um manifesto para o módulo que expõe o novo recurso.

O arquivo do esquema MOF está em **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof** e seu conteúdo é o seguinte.

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
[Key] string UserName;
[Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
[Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
[Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

O script do recurso está em **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Não inclui a lógica real para implementar o recurso, que você mesmo deve adicionar. O conteúdo do script esqueleto é o seguinte.

```powershell
function Get-TargetResource
{
[CmdletBinding()]
[OutputType([System.Collections.Hashtable])]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


<#
$returnValue = @{
UserName = [System.String]
Ensure = [System.String]
DomainAdminCredential = [System.Management.Automation.PSCredential]
Password = [System.Management.Automation.PSCredential]
}

$returnValue
#>
}


function Set-TargetResource
{
[CmdletBinding()]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName,

[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[System.Management.Automation.PSCredential]
$DomainAdminCredential,

[System.Management.Automation.PSCredential]
$Password
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."

#Include this line if the resource requires a system reboot.
#$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName,

[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[System.Management.Automation.PSCredential]
$DomainAdminCredential,

[System.Management.Automation.PSCredential]
$Password
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


<#
$result = [System.Boolean]

$result
#>
}


Export-ModuleMember -Function *-TargetResource
```

## Atualizando o recurso

Se você precisar adicionar ou modificar a lista de parâmetros do recurso, poderá chamar o cmdlet **Update-xDscResource**. O cmdlet atualiza o recurso com uma nova lista de parâmetros. Se você já tiver adicionado lógica no script do recurso, ele permanecerá intacto.

Suponha, por exemplo, que você deseja incluir o horário do último logon para o usuário no nosso recurso. Em vez de reescrever o recurso por completo, é possível chamar **New-xDscResourceProperty** para criar a nova propriedade e, depois, chamar **Update-xDscResource** e adicionar a nova propriedade à sua lista de propriedades.

```powershell
PS C:\> $lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
PS C:\> Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## Testando um esquema de recursos

A ferramenta Designer de Recursos expõe mais um cmdlet que pode ser usado para testar a validade de um esquema MOF escrito manualmente. Chame o cmdlet **Test-xDscSchema**, passando o caminho de um esquema de recursos MOF como parâmetro. O cmdlet mostrará os erros no esquema.

### Consulte Também

#### Conceitos
[Criar recursos personalizados de configuração de estado desejado do Windows PowerShell](authoringResource.md)

#### Outros recursos
[Módulo xDscResourceDesigner](https://powershellgallery.com/packages/xDscResourceDesigner)



<!--HONumber=May16_HO3-->


