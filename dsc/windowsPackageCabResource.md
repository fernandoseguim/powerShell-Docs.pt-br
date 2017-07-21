---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso de DSC WindowsPackageCab
ms.openlocfilehash: 9b1bf3cb95abcbe46976ae0fd328280a3a8d7f28
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="52894-103">Recurso de DSC WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="52894-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="52894-104">Aplica-se a: Windows PowerShell 5.1 e posterior</span><span class="sxs-lookup"><span data-stu-id="52894-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="52894-105">O **WindowsPackageCab** no DSC (Desired State Configuration) do Windows PowerShell fornece um mecanismo para instalar ou desinstalar pacotes de gabinete (.cab) do Windows em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="52894-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="52894-106">O nó de destino deve ter o módulo PowerShell do DISM instalado.</span><span class="sxs-lookup"><span data-stu-id="52894-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="52894-107">Para obter informações, consulte [Usar DISM no Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="52894-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span> 


## <a name="syntax"></a><span data-ttu-id="52894-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52894-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="52894-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="52894-109">Properties</span></span>

|  <span data-ttu-id="52894-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="52894-110">Property</span></span>  |  <span data-ttu-id="52894-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="52894-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="52894-112">Nome</span><span class="sxs-lookup"><span data-stu-id="52894-112">Name</span></span>| <span data-ttu-id="52894-113">Indica o nome do pacote para o qual você deseja garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="52894-113">Indicates the name of the package for you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="52894-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="52894-114">Ensure</span></span>| <span data-ttu-id="52894-115">Indica se o pacote foi instalado.</span><span class="sxs-lookup"><span data-stu-id="52894-115">Indicates if the package is installed.</span></span> <span data-ttu-id="52894-116">Defina esta propriedade como "Absent" para garantir que o pacote não seja instalado (ou desinstalar o pacote, se ele estiver instalado).</span><span class="sxs-lookup"><span data-stu-id="52894-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="52894-117">Defina-a como "Present" (o valor padrão) para garantir que o pacote seja instalado.</span><span class="sxs-lookup"><span data-stu-id="52894-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="52894-118">Caminho</span><span class="sxs-lookup"><span data-stu-id="52894-118">Path</span></span>| <span data-ttu-id="52894-119">Indica o caminho em que o pacote reside.</span><span class="sxs-lookup"><span data-stu-id="52894-119">Indicates the path where the package resides.</span></span>| 
| <span data-ttu-id="52894-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="52894-120">LogPath</span></span>| <span data-ttu-id="52894-121">Indica o caminho completo em que você deseja que o provedor salve um arquivo de log para instalar ou desinstalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="52894-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>| 
| <span data-ttu-id="52894-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="52894-122">DependsOn</span></span> | <span data-ttu-id="52894-123">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="52894-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="52894-124">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`\`.</span><span class="sxs-lookup"><span data-stu-id="52894-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example"></a><span data-ttu-id="52894-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52894-125">Example</span></span>

<span data-ttu-id="52894-126">A configuração de exemplo a seguir usa parâmetros de entrada e garante que o arquivo .cab especificado pelo parâmetro `$Name` esteja instalado.</span><span class="sxs-lookup"><span data-stu-id="52894-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```

