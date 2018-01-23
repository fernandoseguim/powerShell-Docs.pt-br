---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
description: "Oferece um mecanismo para gerenciar grupos locais no nó de destino."
title: Recurso de GroupSet DSC
ms.openlocfilehash: 158cb28747c5fe1987eb62b2cc0f6d6f6fb14332
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="aa3c8-104">Recurso de GroupSet DSC</span><span class="sxs-lookup"><span data-stu-id="aa3c8-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="aa3c8-105">Aplica-se a: Windows Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="aa3c8-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="aa3c8-106">O recurso **GroupSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell oferece um mecanismo para gerenciar grupos locais no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="aa3c8-107">Esse recurso é um [recurso composto](authoringResourceComposite.md) que chama o [Recurso de grupo](groupResource.md) para cada grupo especificado no parâmetro `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="aa3c8-108">Use esse recurso quando desejar adicionar e/ou remover a mesma lista de membros para mais de um grupo, remova mais de um grupo ou adicionar mais de um grupo com a mesma lista de membros.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

##<a name="syntax"></a><span data-ttu-id="aa3c8-109">Sintaxe##</span><span class="sxs-lookup"><span data-stu-id="aa3c8-109">Syntax##</span></span>
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

## <a name="properties"></a><span data-ttu-id="aa3c8-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="aa3c8-110">Properties</span></span>

|  <span data-ttu-id="aa3c8-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="aa3c8-111">Property</span></span>  |  <span data-ttu-id="aa3c8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa3c8-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="aa3c8-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="aa3c8-113">GroupName</span></span>| <span data-ttu-id="aa3c8-114">Os nomes dos grupos para os quais você deseja garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-114">The names of the groups for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="aa3c8-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="aa3c8-115">MembersToExclude</span></span>| <span data-ttu-id="aa3c8-116">Use essa propriedade para remover membros da associação existente dos grupos.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="aa3c8-117">O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="aa3c8-118">Se você definir essa propriedade em uma configuração, não use a propriedade **Membros**.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="aa3c8-119">Isso vai gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-119">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="aa3c8-120">Credential</span><span class="sxs-lookup"><span data-stu-id="aa3c8-120">Credential</span></span>| <span data-ttu-id="aa3c8-121">As credenciais necessárias para acessar recursos remotos.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="aa3c8-122">**Observação**: essa conta deve ter as permissões apropriadas do Active Directory para adicionar todas as contas não locais ao grupo; caso contrário, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="aa3c8-123">Ensure</span><span class="sxs-lookup"><span data-stu-id="aa3c8-123">Ensure</span></span>| <span data-ttu-id="aa3c8-124">Indica se os grupos existem.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="aa3c8-125">Defina essa propriedade como "Ausente" para garantir que os grupos não existam.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="aa3c8-126">Configurá-la como "Present" (o valor padrão) garante que os grupos existam.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>| 
| <span data-ttu-id="aa3c8-127">Membros</span><span class="sxs-lookup"><span data-stu-id="aa3c8-127">Members</span></span>| <span data-ttu-id="aa3c8-128">Use essa propriedade para substituir a associação ao grupo pelos membros especificados.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="aa3c8-129">O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="aa3c8-130">Se você definir essa propriedade em uma configuração, não use a propriedade **MembersToExclude** ou **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="aa3c8-131">Isso vai gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-131">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="aa3c8-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="aa3c8-132">MembersToInclude</span></span>| <span data-ttu-id="aa3c8-133">Use essa propriedade para adicionar membros à associação existente do grupo.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="aa3c8-134">O valor dessa propriedade é uma matriz de cadeias de caracteres do formulário *Domínio*\\*NomeDoUsuário*.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="aa3c8-135">Se você definir essa propriedade em uma configuração, não use a propriedade **Membros**.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="aa3c8-136">Isso vai gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-136">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="aa3c8-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aa3c8-137">DependsOn</span></span> | <span data-ttu-id="aa3c8-138">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aa3c8-139">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="aa3c8-140">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="aa3c8-140">Example 1</span></span>

<span data-ttu-id="aa3c8-141">O exemplo a seguir mostra como garantir que dois grupos chamados "myGroup" e "myOtherGroup" estejam presentes.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span> 

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

><span data-ttu-id="aa3c8-142">**Observação:** este exemplo usa as credenciais de texto sem formatação para manter a simplicidade.</span><span class="sxs-lookup"><span data-stu-id="aa3c8-142">**Note:** This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="aa3c8-143">Para obter informações sobre como criptografar credenciais no arquivo MOF de configuração, consulte [Protegendo o Arquivo MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="aa3c8-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>


