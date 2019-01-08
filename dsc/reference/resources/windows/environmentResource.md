---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso Environment de DSC
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047011"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="27cad-103">Recurso Environment de DSC</span><span class="sxs-lookup"><span data-stu-id="27cad-103">DSC Environment Resource</span></span>

> <span data-ttu-id="27cad-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="27cad-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="27cad-105">O recurso __Environment__ na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar as variáveis de ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="27cad-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="27cad-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27cad-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="27cad-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="27cad-107">Properties</span></span>

|  <span data-ttu-id="27cad-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="27cad-108">Property</span></span>  |  <span data-ttu-id="27cad-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="27cad-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="27cad-110">Nome</span><span class="sxs-lookup"><span data-stu-id="27cad-110">Name</span></span>| <span data-ttu-id="27cad-111">Indica o nome da variável de ambiente para a qual você deseja garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="27cad-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="27cad-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="27cad-112">Ensure</span></span>| <span data-ttu-id="27cad-113">Indica se existe uma variável.</span><span class="sxs-lookup"><span data-stu-id="27cad-113">Indicates if a variable exists.</span></span> <span data-ttu-id="27cad-114">Defina essa propriedade como __Present__ para criar a variável de ambiente caso ela não exista ou para garantir que seu valor corresponda ao que é fornecido por meio da propriedade __Value__ se a variável já existir.</span><span class="sxs-lookup"><span data-stu-id="27cad-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="27cad-115">Defina-a como __Absent__ para excluir a variável se ela existir.</span><span class="sxs-lookup"><span data-stu-id="27cad-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="27cad-116">Caminho</span><span class="sxs-lookup"><span data-stu-id="27cad-116">Path</span></span>| <span data-ttu-id="27cad-117">Define a variável de ambiente que está sendo configurada.</span><span class="sxs-lookup"><span data-stu-id="27cad-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="27cad-118">Defina essa propriedade como __$true__ se a variável for a variável __Path__; caso contrário, defina-a como __$false__.</span><span class="sxs-lookup"><span data-stu-id="27cad-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="27cad-119">O padrão é __$false__.</span><span class="sxs-lookup"><span data-stu-id="27cad-119">The default is __$false__.</span></span> <span data-ttu-id="27cad-120">Se a variável que estiver sendo configurada for a variável __Path__, o valor fornecido por meio da propriedade __Value__ será acrescentado ao valor existente.</span><span class="sxs-lookup"><span data-stu-id="27cad-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="27cad-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="27cad-121">DependsOn</span></span> | <span data-ttu-id="27cad-122">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="27cad-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="27cad-123">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="27cad-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="27cad-124">Valor</span><span class="sxs-lookup"><span data-stu-id="27cad-124">Value</span></span>| <span data-ttu-id="27cad-125">O valor que será atribuído à variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="27cad-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="27cad-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27cad-126">Example</span></span>

<span data-ttu-id="27cad-127">O exemplo a seguir assegura que __TestEnvironmentVariable__ esteja presente e tenha o valor __TestValue__.</span><span class="sxs-lookup"><span data-stu-id="27cad-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="27cad-128">Se não estiver presente, será criado.</span><span class="sxs-lookup"><span data-stu-id="27cad-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```