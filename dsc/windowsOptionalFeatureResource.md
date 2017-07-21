---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso do WindowsOptionalFeature DSC
ms.openlocfilehash: 388fbe1bc430098d6680902e0b5643243fbf7f4c
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="3d0b6-103">Recurso do WindowsOptionalFeature DSC</span><span class="sxs-lookup"><span data-stu-id="3d0b6-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="3d0b6-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3d0b6-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3d0b6-105">O recurso **WindowsOptionalFeature** na DSC (Configuração de Estado Desejado) do Windows PowerShell oferece um mecanismo para garantir que os recursos opcionais sejam habilitados em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d0b6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d0b6-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="3d0b6-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3d0b6-107">Properties</span></span>

|  <span data-ttu-id="3d0b6-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="3d0b6-108">Property</span></span>  |  <span data-ttu-id="3d0b6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d0b6-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="3d0b6-110">Nome</span><span class="sxs-lookup"><span data-stu-id="3d0b6-110">Name</span></span>| <span data-ttu-id="3d0b6-111">Indica o nome do recurso que você deseja garantir que esteja habilitado ou desabilitado.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>| 
| <span data-ttu-id="3d0b6-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="3d0b6-112">Ensure</span></span>| <span data-ttu-id="3d0b6-113">Especifica se o recurso está habilitado.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="3d0b6-114">Para garantir que o recurso esteja habilitado, defina essa propriedade para "Habilitado" Para garantir que o recurso esteja desabilitado, defina a propriedade como "Desabilitado".</span><span class="sxs-lookup"><span data-stu-id="3d0b6-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="3d0b6-115">Origem</span><span class="sxs-lookup"><span data-stu-id="3d0b6-115">Source</span></span>| <span data-ttu-id="3d0b6-116">Não foi implementado.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-116">Not implemented.</span></span>|
| <span data-ttu-id="3d0b6-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="3d0b6-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="3d0b6-118">Especifica se o DISM contata o WU (Windows Update) ao procurar os arquivos de origem para habilitar um recurso.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="3d0b6-119">Se $true, DISM não contatará WU.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="3d0b6-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="3d0b6-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="3d0b6-121">Definido como **$true** para remover todos os arquivos associados ao recurso quando estiver desabilitado (isto é, quando **Garantir** estiver definido como "Ausente").</span><span class="sxs-lookup"><span data-stu-id="3d0b6-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="3d0b6-122">LogLevel</span><span class="sxs-lookup"><span data-stu-id="3d0b6-122">LogLevel</span></span>| <span data-ttu-id="3d0b6-123">O nível máximo de saída mostrado nos logs.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="3d0b6-124">Os valores aceitos são: "ErrorsOnly" (somente erros são registrados), "ErrorsAndWarning" (erros e avisos são registrados) e "ErrorsAndWarningAndInformation" (erros, avisos e informações de depuração são registrados).</span><span class="sxs-lookup"><span data-stu-id="3d0b6-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="3d0b6-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="3d0b6-125">LogPath</span></span>| <span data-ttu-id="3d0b6-126">O caminho até um arquivo de log em que você deseja que o provedor de recursos registre a operação.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-126">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="3d0b6-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3d0b6-127">DependsOn</span></span>| <span data-ttu-id="3d0b6-128">Especifica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3d0b6-129">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 



