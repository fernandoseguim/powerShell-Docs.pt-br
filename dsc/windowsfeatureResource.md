---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso WindowsFeature de DSC
ms.openlocfilehash: 3dd4a9c6f11b0c76054ca3e95796cab8e709a7c6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="18fcf-103">Recurso WindowsFeature de DSC</span><span class="sxs-lookup"><span data-stu-id="18fcf-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="18fcf-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="18fcf-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="18fcf-105">O recurso **WindowsFeature** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para garantir que funções e recursos sejam adicionados ou removidos em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="18fcf-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="18fcf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18fcf-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="18fcf-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="18fcf-107">Properties</span></span>

|  <span data-ttu-id="18fcf-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="18fcf-108">Property</span></span>  |  <span data-ttu-id="18fcf-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="18fcf-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="18fcf-110">Nome</span><span class="sxs-lookup"><span data-stu-id="18fcf-110">Name</span></span>| <span data-ttu-id="18fcf-111">Indica o nome da função ou recurso que você deseja garantir que seja adicionado ou removido.</span><span class="sxs-lookup"><span data-stu-id="18fcf-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="18fcf-112">É igual à propriedade __Name__ do cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature), não o nome de exibição da função ou recurso.</span><span class="sxs-lookup"><span data-stu-id="18fcf-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>| 
| <span data-ttu-id="18fcf-113">Credential</span><span class="sxs-lookup"><span data-stu-id="18fcf-113">Credential</span></span>| <span data-ttu-id="18fcf-114">Indica as credenciais que devem ser usadas para adicionar ou remover a função ou recurso.</span><span class="sxs-lookup"><span data-stu-id="18fcf-114">Indicates the credentials to use to add or remove the role or feature.</span></span>| 
| <span data-ttu-id="18fcf-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="18fcf-115">Ensure</span></span>| <span data-ttu-id="18fcf-116">Indica se a função ou o recurso foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="18fcf-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="18fcf-117">Para garantir que a função ou o recurso seja adicionado, defina essa propriedade como "Present"; para garantir que a função ou o recurso seja removido, defina a propriedade como "Absent".</span><span class="sxs-lookup"><span data-stu-id="18fcf-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>| 
| <span data-ttu-id="18fcf-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="18fcf-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="18fcf-119">Defina essa propriedade como __$true__ para garantir o estado de todos os sub-recursos necessários com o estado do recurso especificado com a propriedade __Name__.</span><span class="sxs-lookup"><span data-stu-id="18fcf-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>| 
| <span data-ttu-id="18fcf-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="18fcf-120">LogPath</span></span>| <span data-ttu-id="18fcf-121">Indica o caminho até um arquivo de log em que você deseja que o provedor de recursos registre a operação.</span><span class="sxs-lookup"><span data-stu-id="18fcf-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="18fcf-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="18fcf-122">DependsOn</span></span>| <span data-ttu-id="18fcf-123">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="18fcf-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="18fcf-124">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="18fcf-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="18fcf-125">Origem</span><span class="sxs-lookup"><span data-stu-id="18fcf-125">Source</span></span>| <span data-ttu-id="18fcf-126">Indica o local do arquivo de origem que deve ser usado para a instalação, se necessário.</span><span class="sxs-lookup"><span data-stu-id="18fcf-126">Indicates the location of the source file to use for installation, if necessary.</span></span>| 

## <a name="example"></a><span data-ttu-id="18fcf-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18fcf-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

