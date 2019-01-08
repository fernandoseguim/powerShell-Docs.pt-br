---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso do WindowsOptionalFeatureSet DSC
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047013"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="25a5e-103">Recurso do WindowsOptionalFeatureSet DSC</span><span class="sxs-lookup"><span data-stu-id="25a5e-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="25a5e-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="25a5e-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="25a5e-105">O recurso **WindowsOptionalFeatureSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell oferece um mecanismo para garantir que os recursos opcionais sejam habilitados em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="25a5e-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="25a5e-106">Esse recurso é um [recurso composto](../../../resources/authoringResourceComposite.md) que chama o [recurso WindowsOptionalFeature](windowsOptionalFeatureResource.md) para cada recurso especificado na propriedade `Name`.</span><span class="sxs-lookup"><span data-stu-id="25a5e-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="25a5e-107">Use esse recurso quando desejar configurar vários recursos opcionais do Windows para o mesmo estado.</span><span class="sxs-lookup"><span data-stu-id="25a5e-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="25a5e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25a5e-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="25a5e-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="25a5e-109">Properties</span></span>

|  <span data-ttu-id="25a5e-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="25a5e-110">Property</span></span>  |  <span data-ttu-id="25a5e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="25a5e-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="25a5e-112">Nome</span><span class="sxs-lookup"><span data-stu-id="25a5e-112">Name</span></span>| <span data-ttu-id="25a5e-113">Indica o nome dos recursos que você deseja garantir que estejam habilitados ou desabilitados.</span><span class="sxs-lookup"><span data-stu-id="25a5e-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="25a5e-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="25a5e-114">Ensure</span></span>| <span data-ttu-id="25a5e-115">Especifica se os recursos estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="25a5e-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="25a5e-116">Para garantir que os recursos estejam habilitados, defina essa propriedade para "Habilitado" Para garantir que os recursos estejam desabilitados, defina a propriedade como "Desabilitado".</span><span class="sxs-lookup"><span data-stu-id="25a5e-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="25a5e-117">Origem</span><span class="sxs-lookup"><span data-stu-id="25a5e-117">Source</span></span>| <span data-ttu-id="25a5e-118">Não foi implementado.</span><span class="sxs-lookup"><span data-stu-id="25a5e-118">Not implemented.</span></span>|
| <span data-ttu-id="25a5e-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="25a5e-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="25a5e-120">Especifica se o DISM contata o WU (Windows Update) ao procurar os arquivos de origem para habilitar recursos.</span><span class="sxs-lookup"><span data-stu-id="25a5e-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="25a5e-121">Se $true, DISM não contatará WU.</span><span class="sxs-lookup"><span data-stu-id="25a5e-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="25a5e-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="25a5e-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="25a5e-123">Definido como **$true** para remover todos os arquivos associados ao recurso quando eles são desabilitados (ou seja, quando **Garantir** está definido como "Ausente").</span><span class="sxs-lookup"><span data-stu-id="25a5e-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="25a5e-124">LogLevel</span><span class="sxs-lookup"><span data-stu-id="25a5e-124">LogLevel</span></span>| <span data-ttu-id="25a5e-125">O nível máximo de saída mostrado nos logs.</span><span class="sxs-lookup"><span data-stu-id="25a5e-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="25a5e-126">Os valores aceitos são: "ErrorsOnly" (somente erros são registrados), "ErrorsAndWarning" (erros e avisos são registrados) e "ErrorsAndWarningAndInformation" (erros, avisos e informações de depuração são registrados).</span><span class="sxs-lookup"><span data-stu-id="25a5e-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="25a5e-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="25a5e-127">LogPath</span></span>| <span data-ttu-id="25a5e-128">O caminho até um arquivo de log em que você deseja que o provedor de recursos registre a operação.</span><span class="sxs-lookup"><span data-stu-id="25a5e-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="25a5e-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="25a5e-129">DependsOn</span></span>| <span data-ttu-id="25a5e-130">Especifica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="25a5e-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="25a5e-131">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="25a5e-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
