# Recurso Group de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso Group na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar grupos locais no nó de destino.

##Sintaxe##
```
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
}
```

## Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| GroupName| Indica o nome do grupo para o qual você deseja garantir um estado específico.| 
| Credential| Indica as credenciais necessárias para acessar recursos remotos. **Observação**: essa conta deve ter as permissões apropriadas do Active Directory para adicionar todas as contas não locais ao grupo; caso contrário, ocorrerá um erro.
| Descrição| Indica a descrição do grupo.| 
| Ensure| Indica se o grupo existe. Defina essa propriedade como "Absent" para garantir que o grupo não exista. Ao defini-la como "Present" (o valor padrão), você garante que o grupo exista.| 
| Membros| Indica que você deseja garantir que esses membros formem o grupo.| 
| MembersToExclude| Indica os usuários que você deseja garantir que não sejam membros desse grupo.| 
| MembersToInclude| Indica os usuários que você deseja garantir que sejam membros do grupo.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"``.| 

## Exemplo

O exemplo a seguir mostra como garantir que um grupo chamado TestGroup esteja ausente. 

```powershell
Group GroupExample
{
    # This will remove TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
<!--HONumber=Feb16_HO4-->
