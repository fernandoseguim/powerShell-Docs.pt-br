---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso Group de DSC
ms.openlocfilehash: 6fb6c5f9593687d7204ff31fddd9bca978ed2707
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-group-resource"></a><span data-ttu-id="5f1de-103">Recurso Group de DSC</span><span class="sxs-lookup"><span data-stu-id="5f1de-103">DSC Group Resource</span></span>

> <span data-ttu-id="5f1de-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5f1de-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5f1de-105">O recurso Group na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar grupos locais no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="5f1de-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f1de-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f1de-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="5f1de-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5f1de-107">Properties</span></span>

|  <span data-ttu-id="5f1de-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5f1de-108">Property</span></span>  |  <span data-ttu-id="5f1de-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f1de-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="5f1de-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="5f1de-110">GroupName</span></span>| <span data-ttu-id="5f1de-111">O nome do grupo para o qual você deseja garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="5f1de-111">The name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="5f1de-112">Credential</span><span class="sxs-lookup"><span data-stu-id="5f1de-112">Credential</span></span>| <span data-ttu-id="5f1de-113">As credenciais necessárias para acessar recursos remotos.</span><span class="sxs-lookup"><span data-stu-id="5f1de-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="5f1de-114">**Observação**: essa conta deve ter as permissões apropriadas do Active Directory para adicionar todas as contas não locais ao grupo; caso contrário, ocorrerá um erro quando a configuração for executada no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="5f1de-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>  
| <span data-ttu-id="5f1de-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f1de-115">Description</span></span>| <span data-ttu-id="5f1de-116">A descrição do grupo.</span><span class="sxs-lookup"><span data-stu-id="5f1de-116">The description of the group.</span></span>| 
| <span data-ttu-id="5f1de-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="5f1de-117">Ensure</span></span>| <span data-ttu-id="5f1de-118">Indica se o grupo existe.</span><span class="sxs-lookup"><span data-stu-id="5f1de-118">Indicates if the group exists.</span></span> <span data-ttu-id="5f1de-119">Defina essa propriedade como "Absent" para garantir que o grupo não exista.</span><span class="sxs-lookup"><span data-stu-id="5f1de-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="5f1de-120">Ao defini-la como "Present" (o valor padrão), você garante que o grupo exista.</span><span class="sxs-lookup"><span data-stu-id="5f1de-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>| 
| <span data-ttu-id="5f1de-121">Membros</span><span class="sxs-lookup"><span data-stu-id="5f1de-121">Members</span></span>| <span data-ttu-id="5f1de-122">Use essa propriedade para substituir a associação ao grupo pelos membros especificados.</span><span class="sxs-lookup"><span data-stu-id="5f1de-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="5f1de-123">O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*.</span><span class="sxs-lookup"><span data-stu-id="5f1de-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="5f1de-124">Se você definir essa propriedade em uma configuração, não use a propriedade **MembersToExclude** ou **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="5f1de-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="5f1de-125">Isso gerará um erro.</span><span class="sxs-lookup"><span data-stu-id="5f1de-125">Doing so generates an error.</span></span>| 
| <span data-ttu-id="5f1de-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="5f1de-126">MembersToExclude</span></span>| <span data-ttu-id="5f1de-127">Use essa propriedade para remover membros da associação existente do grupo.</span><span class="sxs-lookup"><span data-stu-id="5f1de-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="5f1de-128">O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*.</span><span class="sxs-lookup"><span data-stu-id="5f1de-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="5f1de-129">Se você definir essa propriedade em uma configuração, não use a propriedade **Membros**.</span><span class="sxs-lookup"><span data-stu-id="5f1de-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="5f1de-130">Isso gerará um erro.</span><span class="sxs-lookup"><span data-stu-id="5f1de-130">Doing so generates an error.</span></span>| 
| <span data-ttu-id="5f1de-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="5f1de-131">MembersToInclude</span></span>| <span data-ttu-id="5f1de-132">Use essa propriedade para adicionar membros à associação existente do grupo.</span><span class="sxs-lookup"><span data-stu-id="5f1de-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="5f1de-133">O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*.</span><span class="sxs-lookup"><span data-stu-id="5f1de-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="5f1de-134">Se você definir essa propriedade em uma configuração, não use a propriedade **Membros**.</span><span class="sxs-lookup"><span data-stu-id="5f1de-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="5f1de-135">Isso vai gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="5f1de-135">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="5f1de-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5f1de-136">DependsOn</span></span> | <span data-ttu-id="5f1de-137">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="5f1de-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5f1de-138">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`\`.</span><span class="sxs-lookup"><span data-stu-id="5f1de-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="5f1de-139">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="5f1de-139">Example 1</span></span>

<span data-ttu-id="5f1de-140">O exemplo a seguir mostra como garantir que um grupo chamado "TestGroup" esteja ausente.</span><span class="sxs-lookup"><span data-stu-id="5f1de-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span> 

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## <a name="example-2"></a><span data-ttu-id="5f1de-141">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="5f1de-141">Example 2</span></span>
<span data-ttu-id="5f1de-142">O exemplo a seguir mostra como adicionar um usuário do Active Directory ao grupo de administradores locais como parte de um build de laboratório com vários computadores, em que você já está usando um PSCredential para a conta de Administrador Local.</span><span class="sxs-lookup"><span data-stu-id="5f1de-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span> <span data-ttu-id="5f1de-143">Como isso também é usado para a conta de administrador do domínio (após a promoção do domínio), precisamos converter esse PSCredential existente em uma credencial de domínio amigável para adicionar um usuário de domínio ao grupo de Administradores Locais no servidor membro.</span><span class="sxs-lookup"><span data-stu-id="5f1de-143">As this is also used for the Domain Admin Account (after Domain promotion) we then need to convert this existing PSCredential to a Domain Friendly credential to enable us to add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

## <a name="example-3"></a><span data-ttu-id="5f1de-144">Exemplo 3</span><span class="sxs-lookup"><span data-stu-id="5f1de-144">Example 3</span></span>
<span data-ttu-id="5f1de-145">O exemplo a seguir mostra como verificar se um grupo local, TigerTeamAdmins, no servidor TigerTeamSource.Contoso.Com, não contém uma conta de domínio específico, Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="5f1de-145">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>  

```powershell

Configuration SecureTigerTeamSrouce 
{
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'
  
  Node TigerTeamSource.Contoso.Com {
  Group TigerTeamAdmins
    {
       GroupName        = 'TigerTeamAdmins'   
       Ensure           = 'Absent'             
       MembersToInclude = "Contoso\JerryG"
    }
  }
}
```

