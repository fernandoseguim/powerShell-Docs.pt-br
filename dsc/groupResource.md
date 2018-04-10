---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Recurso Group de DSC
ms.openlocfilehash: 6a4732439bb45e36fa9201975f12194442611002
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-group-resource"></a>Recurso Group de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso Group na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar grupos locais no nó de destino.

## <a name="syntax"></a>Sintaxe

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| GroupName| O nome do grupo para o qual você deseja garantir um estado específico.|
| Credential| As credenciais necessárias para acessar recursos remotos. **Observação**: essa conta deve ter as permissões apropriadas do Active Directory para adicionar todas as contas não locais ao grupo; caso contrário, ocorrerá um erro quando a configuração for executada no nó de destino.
| Descrição| A descrição do grupo.|
| Ensure| Indica se o grupo existe. Defina essa propriedade como "Absent" para garantir que o grupo não exista. Ao defini-la como "Present" (o valor padrão), você garante que o grupo exista.|
| Membros| Use essa propriedade para substituir a associação ao grupo pelos membros especificados. O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*. Se você definir essa propriedade em uma configuração, não use a propriedade **MembersToExclude** ou **MembersToInclude**. Isso gerará um erro.|
| MembersToExclude| Use essa propriedade para remover membros da associação existente do grupo. O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*. Se você definir essa propriedade em uma configuração, não use a propriedade **Membros**. Isso gerará um erro.|
| MembersToInclude| Use essa propriedade para adicionar membros à associação existente do grupo. O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*. Se você definir essa propriedade em uma configuração, não use a propriedade **Membros**. Isso vai gerar um erro.|
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"``.|

## <a name="example-1"></a>Exemplo 1

O exemplo a seguir mostra como garantir que um grupo chamado "TestGroup" esteja ausente.

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a>Exemplo 2

O exemplo a seguir mostra como adicionar um usuário do Active Directory ao grupo de administradores locais como parte de um build de laboratório com vários computadores, em que você já está usando um PSCredential para a conta de Administrador Local.
Como isso também é usado para a conta de administrador do domínio (após a promoção do domínio), devemos converter essa PSCredential existente em uma credencial de domínio amigável.
Em seguida, podemos adicionar um usuário do domínio ao grupo de administradores local no servidor membro.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a>Exemplo 3

O exemplo a seguir mostra como verificar se um grupo local, TigerTeamAdmins, no servidor TigerTeamSource.Contoso.Com, não contém uma conta de domínio específico, Contoso\JerryG.

```powershell
Configuration SecureTigerTeamSrouce {
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

  Node TigerTeamSource.Contoso.Com {
    Group TigerTeamAdmins {
       GroupName        = 'TigerTeamAdmins'
       Ensure           = 'Present'
       MembersToExclude = "Contoso\JerryG"
    }
  }
}
```