---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso Package de DSC
ms.openlocfilehash: 16f7f1b8fa7b84bcfdeb09fdc46db9c93113e70c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188523"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="87c8a-103">Recurso Package de DSC</span><span class="sxs-lookup"><span data-stu-id="87c8a-103">DSC Package Resource</span></span>

> <span data-ttu-id="87c8a-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="87c8a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="87c8a-105">O recurso **Package** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para instalar ou desinstalar pacotes, tais como os pacotes do Windows Installer e setup.exe, em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="87c8a-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="87c8a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87c8a-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="87c8a-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="87c8a-107">Properties</span></span>
|  <span data-ttu-id="87c8a-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="87c8a-108">Property</span></span>  |  <span data-ttu-id="87c8a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="87c8a-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="87c8a-110">Nome</span><span class="sxs-lookup"><span data-stu-id="87c8a-110">Name</span></span>| <span data-ttu-id="87c8a-111">Indica o nome do pacote para o qual você deseja garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="87c8a-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="87c8a-112">Caminho</span><span class="sxs-lookup"><span data-stu-id="87c8a-112">Path</span></span>| <span data-ttu-id="87c8a-113">Indica o caminho em que o pacote reside.</span><span class="sxs-lookup"><span data-stu-id="87c8a-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="87c8a-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="87c8a-114">ProductId</span></span>| <span data-ttu-id="87c8a-115">Indica a ID do produto que identifica o pacote com exclusividade.</span><span class="sxs-lookup"><span data-stu-id="87c8a-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="87c8a-116">Argumentos</span><span class="sxs-lookup"><span data-stu-id="87c8a-116">Arguments</span></span>| <span data-ttu-id="87c8a-117">Lista uma cadeia de caracteres de argumentos que será passada para o pacote exatamente conforme fornecido.</span><span class="sxs-lookup"><span data-stu-id="87c8a-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="87c8a-118">Credential</span><span class="sxs-lookup"><span data-stu-id="87c8a-118">Credential</span></span>| <span data-ttu-id="87c8a-119">Fornece acesso ao pacote em uma fonte remota.</span><span class="sxs-lookup"><span data-stu-id="87c8a-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="87c8a-120">Essa propriedade não é usada para instalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="87c8a-120">This property is not used to install the package.</span></span> <span data-ttu-id="87c8a-121">O pacote é sempre instalado no sistema local.</span><span class="sxs-lookup"><span data-stu-id="87c8a-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="87c8a-122">Ensure</span><span class="sxs-lookup"><span data-stu-id="87c8a-122">Ensure</span></span>| <span data-ttu-id="87c8a-123">Indica se o pacote foi instalado.</span><span class="sxs-lookup"><span data-stu-id="87c8a-123">Indicates if the package is installed.</span></span> <span data-ttu-id="87c8a-124">Defina esta propriedade como "Absent" para garantir que o pacote não seja instalado (ou desinstalar o pacote, se ele estiver instalado).</span><span class="sxs-lookup"><span data-stu-id="87c8a-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="87c8a-125">Defina-a como "Present" (o valor padrão) para garantir que o pacote seja instalado.</span><span class="sxs-lookup"><span data-stu-id="87c8a-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="87c8a-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="87c8a-126">LogPath</span></span>| <span data-ttu-id="87c8a-127">Indica o caminho completo em que você deseja que o provedor salve um arquivo de log para instalar ou desinstalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="87c8a-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="87c8a-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="87c8a-128">DependsOn</span></span> | <span data-ttu-id="87c8a-129">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="87c8a-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="87c8a-130">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="87c8a-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|
| <span data-ttu-id="87c8a-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="87c8a-131">ReturnCode</span></span>| <span data-ttu-id="87c8a-132">Indica o código de retorno esperado.</span><span class="sxs-lookup"><span data-stu-id="87c8a-132">Indicates the expected return code.</span></span> <span data-ttu-id="87c8a-133">Se o código de retorno real não corresponder ao valor esperado fornecido aqui, a configuração gerará um erro.</span><span class="sxs-lookup"><span data-stu-id="87c8a-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="87c8a-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87c8a-134">Example</span></span>

<span data-ttu-id="87c8a-135">Este exemplo executa o instalador .msi que está localizado no caminho especificado e tem a ID do produto especificado.</span><span class="sxs-lookup"><span data-stu-id="87c8a-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```