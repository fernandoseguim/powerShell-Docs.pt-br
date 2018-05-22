---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
description: Oferece um mecanismo para gerenciar grupos locais no nó de destino.
title: Recurso de GroupSet DSC
ms.openlocfilehash: 3d6fdcaef6053964d3fb3b709a5263d291a7c840
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-groupset-resource"></a>Recurso de GroupSet DSC

> Aplica-se a: Windows Windows PowerShell 5.0

O recurso **GroupSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell oferece um mecanismo para gerenciar grupos locais no nó de destino. Esse recurso é um [recurso composto](authoringResourceComposite.md) que chama o [Recurso de grupo](groupResource.md) para cada grupo especificado no parâmetro `GroupName`.

Use esse recurso quando desejar adicionar e/ou remover a mesma lista de membros para mais de um grupo, remova mais de um grupo ou adicionar mais de um grupo com a mesma lista de membros.

##<a name="syntax"></a>Sintaxe##
```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| GroupName| Os nomes dos grupos para os quais você deseja garantir um estado específico.|
| MembersToExclude| Use essa propriedade para remover membros da associação existente dos grupos. O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*. Se você definir essa propriedade em uma configuração, não use a propriedade **Membros**. Isso vai gerar um erro.|
| Credential| As credenciais necessárias para acessar recursos remotos. **Observação**: essa conta deve ter as permissões apropriadas do Active Directory para adicionar todas as contas não locais ao grupo; caso contrário, ocorrerá um erro.
| Ensure| Indica se os grupos existem. Defina essa propriedade como "Ausente" para garantir que os grupos não existam. Configurá-la como "Present" (o valor padrão) garante que os grupos existam.|
| Membros| Use essa propriedade para substituir a associação ao grupo pelos membros especificados. O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*. Se você definir essa propriedade em uma configuração, não use a propriedade **MembersToExclude** ou **MembersToInclude**. Isso vai gerar um erro.|
| MembersToInclude| Use essa propriedade para adicionar membros à associação existente do grupo. O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*. Se você definir essa propriedade em uma configuração, não use a propriedade **Membros**. Isso vai gerar um erro.|
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"``.|

## <a name="example-1"></a>Exemplo 1

O exemplo a seguir mostra como garantir que dois grupos chamados "myGroup" e "myOtherGroup" estejam presentes.

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}


GroupSetTest -ConfigurationData $cd
```

>**Observação:** este exemplo usa as credenciais de texto sem formatação para manter a simplicidade. Para obter informações sobre como criptografar credenciais no arquivo MOF de configuração, consulte [Protegendo o Arquivo MOF](secureMOF.md).