---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso ProcessSet da DSC
ms.openlocfilehash: ec1d6a04b5debc22fe2f3b4a4396c385514a3b0c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="99a18-103">Recurso WindowsProcess de DSC</span><span class="sxs-lookup"><span data-stu-id="99a18-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="99a18-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="99a18-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="99a18-105">O recurso **ProcessSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell fornece um mecanismo para configurar processos em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="99a18-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="99a18-106">Esse recurso é um [recurso composto](authoringResourceComposite.md) que chama o [Recurso do WindowsProcess](windowsProcessResource.md) para cada grupo especificado no parâmetro `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="99a18-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="99a18-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99a18-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]   
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="99a18-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="99a18-108">Properties</span></span>
|  <span data-ttu-id="99a18-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="99a18-109">Property</span></span>  |  <span data-ttu-id="99a18-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="99a18-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="99a18-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="99a18-111">Arguments</span></span>| <span data-ttu-id="99a18-112">Uma cadeia de caracteres que contém os argumentos a serem passados ao processo no estado em que se encontram.</span><span class="sxs-lookup"><span data-stu-id="99a18-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="99a18-113">Se você precisar passar vários argumentos, coloque todos nessa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="99a18-113">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="99a18-114">Caminho</span><span class="sxs-lookup"><span data-stu-id="99a18-114">Path</span></span>| <span data-ttu-id="99a18-115">Os caminhos para os executáveis do processo.</span><span class="sxs-lookup"><span data-stu-id="99a18-115">The paths to the process executables.</span></span> <span data-ttu-id="99a18-116">Se esses forem os nomes dos arquivos executáveis (caminhos não totalmente qualificados), o recurso DSC pesquisará a variável de ambiente **Path** (`$env:Path`) para localizar os arquivos.</span><span class="sxs-lookup"><span data-stu-id="99a18-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="99a18-117">Se os valores dessa propriedade forem caminhos totalmente qualificados, a DSC não usará a variável de ambiente **Path** para localizar os arquivos e gerará um erro se qualquer um dos caminhos não existir.</span><span class="sxs-lookup"><span data-stu-id="99a18-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="99a18-118">Caminhos relativos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="99a18-118">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="99a18-119">Credential</span><span class="sxs-lookup"><span data-stu-id="99a18-119">Credential</span></span>| <span data-ttu-id="99a18-120">Indica as credenciais para iniciar o processo.</span><span class="sxs-lookup"><span data-stu-id="99a18-120">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="99a18-121">Ensure</span><span class="sxs-lookup"><span data-stu-id="99a18-121">Ensure</span></span>| <span data-ttu-id="99a18-122">Especifica se os processos existem.</span><span class="sxs-lookup"><span data-stu-id="99a18-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="99a18-123">Defina essa propriedade como "Present" para garantir que o processo exista.</span><span class="sxs-lookup"><span data-stu-id="99a18-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="99a18-124">Caso contrário, defina-a como "Absent".</span><span class="sxs-lookup"><span data-stu-id="99a18-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="99a18-125">O padrão é "Present".</span><span class="sxs-lookup"><span data-stu-id="99a18-125">The default is "Present".</span></span>| 
| <span data-ttu-id="99a18-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="99a18-126">StandardErrorPath</span></span>| <span data-ttu-id="99a18-127">O caminho para o qual os processos gravam o erro padrão.</span><span class="sxs-lookup"><span data-stu-id="99a18-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="99a18-128">Qualquer arquivo existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="99a18-128">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="99a18-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="99a18-129">StandardInputPath</span></span>| <span data-ttu-id="99a18-130">O fluxo do qual o processo recebe entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="99a18-130">The stream from which the process receives standard input.</span></span>| 
| <span data-ttu-id="99a18-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="99a18-131">StandardOutputPath</span></span>| <span data-ttu-id="99a18-132">O caminho do arquivo para o qual os processos gravam a saída padrão.</span><span class="sxs-lookup"><span data-stu-id="99a18-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="99a18-133">Qualquer arquivo existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="99a18-133">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="99a18-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="99a18-134">WorkingDirectory</span></span>| <span data-ttu-id="99a18-135">O local usado como diretório de trabalho atual para os processos.</span><span class="sxs-lookup"><span data-stu-id="99a18-135">The location used as the current working directory for the processes.</span></span>| 
| <span data-ttu-id="99a18-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="99a18-136">DependsOn</span></span> | <span data-ttu-id="99a18-137">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="99a18-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="99a18-138">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **_ResourceType**, a sintaxe para usar essa propriedade será \`DependsOn = "[ResourceType]ResourceName"\`\` .</span><span class="sxs-lookup"><span data-stu-id="99a18-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>| 

