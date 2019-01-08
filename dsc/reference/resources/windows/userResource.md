---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso User de DSC
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047089"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="82bce-103">Recurso User de DSC</span><span class="sxs-lookup"><span data-stu-id="82bce-103">DSC User Resource</span></span>

<span data-ttu-id="82bce-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="82bce-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="82bce-105">O recurso **User** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para contas de usuário locais no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="82bce-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="82bce-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82bce-106">Syntax</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="82bce-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="82bce-107">Properties</span></span>

|  <span data-ttu-id="82bce-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="82bce-108">Property</span></span>  |  <span data-ttu-id="82bce-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="82bce-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="82bce-110">UserName</span><span class="sxs-lookup"><span data-stu-id="82bce-110">UserName</span></span>| <span data-ttu-id="82bce-111">Indica o nome da conta para a qual você deseja garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="82bce-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="82bce-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="82bce-112">Description</span></span>| <span data-ttu-id="82bce-113">Indica a descrição que você deseja usar para a conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="82bce-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="82bce-114">Desabilitado</span><span class="sxs-lookup"><span data-stu-id="82bce-114">Disabled</span></span>| <span data-ttu-id="82bce-115">Indica se a conta está habilitada.</span><span class="sxs-lookup"><span data-stu-id="82bce-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="82bce-116">Defina essa propriedade como `$true` para garantir que essa conta esteja desabilitada e defina-a como `$false` para garantir que esteja habilitada.</span><span class="sxs-lookup"><span data-stu-id="82bce-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span>|
| <span data-ttu-id="82bce-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="82bce-117">Ensure</span></span>| <span data-ttu-id="82bce-118">Indica se a conta existe.</span><span class="sxs-lookup"><span data-stu-id="82bce-118">Indicates if the account exists.</span></span> <span data-ttu-id="82bce-119">Defina essa propriedade como "Present" para garantir que a conta exista e defina-o como "Absent" para garantir que a conta não exista.</span><span class="sxs-lookup"><span data-stu-id="82bce-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="82bce-120">FullName</span><span class="sxs-lookup"><span data-stu-id="82bce-120">FullName</span></span>| <span data-ttu-id="82bce-121">Representa uma cadeia de caracteres com o nome completo que você deseja usar para a conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="82bce-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="82bce-122">Senha</span><span class="sxs-lookup"><span data-stu-id="82bce-122">Password</span></span>| <span data-ttu-id="82bce-123">Indica a senha que você deseja usar para essa conta.</span><span class="sxs-lookup"><span data-stu-id="82bce-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="82bce-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="82bce-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="82bce-125">Indica se o usuário pode alterar a senha.</span><span class="sxs-lookup"><span data-stu-id="82bce-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="82bce-126">Defina essa propriedade como `$true` para garantir que o usuário não possa alterar a senha e defina-a como `$false` para permitir que o usuário altere a senha.</span><span class="sxs-lookup"><span data-stu-id="82bce-126">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="82bce-127">O valor padrão é `$false`.</span><span class="sxs-lookup"><span data-stu-id="82bce-127">The default value is `$false`.</span></span>|
| <span data-ttu-id="82bce-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="82bce-128">PasswordChangeRequired</span></span>| <span data-ttu-id="82bce-129">Indica se o usuário deve alterar a senha na próxima entrada.</span><span class="sxs-lookup"><span data-stu-id="82bce-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="82bce-130">Defina essa propriedade como `$true` se o usuário precisar alterar a senha.</span><span class="sxs-lookup"><span data-stu-id="82bce-130">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="82bce-131">O valor padrão é `$true`.</span><span class="sxs-lookup"><span data-stu-id="82bce-131">The default value is `$true`.</span></span>|
| <span data-ttu-id="82bce-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="82bce-132">PasswordNeverExpires</span></span>| <span data-ttu-id="82bce-133">Indica se a senha vai expirar.</span><span class="sxs-lookup"><span data-stu-id="82bce-133">Indicates if the password will expire.</span></span> <span data-ttu-id="82bce-134">Para garantir que a senha para essa conta nunca expire, defina essa propriedade como `$true`; defina-a como `$false` caso a senha vá expirar.</span><span class="sxs-lookup"><span data-stu-id="82bce-134">To ensure that the password for this account will never expire, set this property to `$true`, and set it to `$false` if the password will expire.</span></span> <span data-ttu-id="82bce-135">O valor padrão é `$false`.</span><span class="sxs-lookup"><span data-stu-id="82bce-135">The default value is `$false`.</span></span>|
| <span data-ttu-id="82bce-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="82bce-136">DependsOn</span></span> | <span data-ttu-id="82bce-137">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="82bce-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="82bce-138">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="82bce-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="82bce-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82bce-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```