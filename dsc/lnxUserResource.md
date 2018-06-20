---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso nxUser de DSC para Linux
ms.openlocfilehash: ca77bcd1f23a78ddb9e2ac988e4aadfec504bbbe
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218919"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="a102c-103">Recurso nxUser de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="a102c-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="a102c-104">O recurso **nxUser** na Configuração de Estado Desejado (DSC) do PowerShell fornece um mecanismo para gerenciar usuários locais em um nó do Linux.</span><span class="sxs-lookup"><span data-stu-id="a102c-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a102c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a102c-105">Syntax</span></span>

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="a102c-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a102c-106">Properties</span></span>

|  <span data-ttu-id="a102c-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a102c-107">Property</span></span> |  <span data-ttu-id="a102c-108">Indica o nome da conta para a qual você deseja garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="a102c-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="a102c-109">UserName</span><span class="sxs-lookup"><span data-stu-id="a102c-109">UserName</span></span>| <span data-ttu-id="a102c-110">Especifica o local onde você deseja garantir o estado de um arquivo ou diretório.</span><span class="sxs-lookup"><span data-stu-id="a102c-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="a102c-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="a102c-111">Ensure</span></span>| <span data-ttu-id="a102c-112">Especifica se a conta existe.</span><span class="sxs-lookup"><span data-stu-id="a102c-112">Specifies whether the account exists.</span></span> <span data-ttu-id="a102c-113">Defina essa propriedade como "Present" para garantir que a conta exista e defina-o como "Absent" para garantir que a conta não exista.</span><span class="sxs-lookup"><span data-stu-id="a102c-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="a102c-114">FullName</span><span class="sxs-lookup"><span data-stu-id="a102c-114">FullName</span></span>| <span data-ttu-id="a102c-115">Uma cadeia de caracteres que contém o nome completo que deve ser usado para a conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="a102c-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="a102c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a102c-116">Description</span></span>| <span data-ttu-id="a102c-117">A descrição da conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="a102c-117">The description for the user account.</span></span>|
| <span data-ttu-id="a102c-118">Senha</span><span class="sxs-lookup"><span data-stu-id="a102c-118">Password</span></span>| <span data-ttu-id="a102c-119">O hash da senha de usuário no formato apropriado para o computador Linux.</span><span class="sxs-lookup"><span data-stu-id="a102c-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="a102c-120">Normalmente, é um hash SHA-256 ou SHA-512 com valor de sal.</span><span class="sxs-lookup"><span data-stu-id="a102c-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="a102c-121">No Debian e no Ubuntu Linux, esse valor pode ser gerado com o comando mkpasswd.</span><span class="sxs-lookup"><span data-stu-id="a102c-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="a102c-122">Para outras distribuições de Linux, o método de criptografia da biblioteca de Criptografia do Python pode ser usado para gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="a102c-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="a102c-123">Desabilitado</span><span class="sxs-lookup"><span data-stu-id="a102c-123">Disabled</span></span>| <span data-ttu-id="a102c-124">Indica se a conta está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a102c-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="a102c-125">Defina essa propriedade como **$true** para garantir que essa conta esteja desabilitada e defina-a como **$false** para garantir que esteja habilitada.</span><span class="sxs-lookup"><span data-stu-id="a102c-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="a102c-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="a102c-126">PasswordChangeRequired</span></span>| <span data-ttu-id="a102c-127">Indica se o usuário pode alterar a senha.</span><span class="sxs-lookup"><span data-stu-id="a102c-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="a102c-128">Defina essa propriedade como **$true** para garantir que o usuário não possa alterar a senha e defina-a como **$false** para permitir que o usuário altere a senha.</span><span class="sxs-lookup"><span data-stu-id="a102c-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="a102c-129">O valor padrão é **$false**.</span><span class="sxs-lookup"><span data-stu-id="a102c-129">The default value is **$false**.</span></span> <span data-ttu-id="a102c-130">Essa propriedade é avaliada apenas se a conta de usuário não existia anteriormente e está sendo criada.</span><span class="sxs-lookup"><span data-stu-id="a102c-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="a102c-131">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="a102c-131">HomeDirectory</span></span>| <span data-ttu-id="a102c-132">O diretório inicial do usuário.</span><span class="sxs-lookup"><span data-stu-id="a102c-132">The home directory for the user.</span></span>|
| <span data-ttu-id="a102c-133">GroupID</span><span class="sxs-lookup"><span data-stu-id="a102c-133">GroupID</span></span>| <span data-ttu-id="a102c-134">A ID primária de grupo do usuário.</span><span class="sxs-lookup"><span data-stu-id="a102c-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="a102c-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a102c-135">DependsOn</span></span> | <span data-ttu-id="a102c-136">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="a102c-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a102c-137">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for "ResourceName" e seu tipo for "ResourceType", a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a102c-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="a102c-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a102c-138">Example</span></span>

<span data-ttu-id="a102c-139">O exemplo a seguir garante que o usuário "monuser" exista e seja membro do grupo "DBusers".</span><span class="sxs-lookup"><span data-stu-id="a102c-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```