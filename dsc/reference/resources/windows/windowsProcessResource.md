---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso WindowsProcess de DSC
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047032"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="de4cb-103">Recurso WindowsProcess de DSC</span><span class="sxs-lookup"><span data-stu-id="de4cb-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="de4cb-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="de4cb-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="de4cb-105">O recurso **WindowsProcess** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para configurar processos em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="de4cb-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="de4cb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de4cb-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="de4cb-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="de4cb-107">Properties</span></span>

| <span data-ttu-id="de4cb-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="de4cb-108">Property</span></span> | <span data-ttu-id="de4cb-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="de4cb-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="de4cb-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="de4cb-110">Arguments</span></span>| <span data-ttu-id="de4cb-111">Indica uma cadeia de caracteres de argumentos para passar para o processo no estado em que se encontra.</span><span class="sxs-lookup"><span data-stu-id="de4cb-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="de4cb-112">Se você precisar passar vários argumentos, coloque todos nessa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="de4cb-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="de4cb-113">Caminho</span><span class="sxs-lookup"><span data-stu-id="de4cb-113">Path</span></span>| <span data-ttu-id="de4cb-114">O caminho para o executável do processo.</span><span class="sxs-lookup"><span data-stu-id="de4cb-114">The path to the process executable.</span></span> <span data-ttu-id="de4cb-115">Se esse for o nome do arquivo do executável (não o caminho totalmente qualificado), o recurso DSC pesquisará a variável de ambiente **caminho** (`$env:Path`) para localizar o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="de4cb-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="de4cb-116">Se o valor dessa propriedade for um caminho totalmente qualificado, o DSC não usará a variável de ambiente **Caminho** para encontrar o arquivo e emitirá um erro se o caminho não existir.</span><span class="sxs-lookup"><span data-stu-id="de4cb-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="de4cb-117">Caminhos relativos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="de4cb-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="de4cb-118">Credential</span><span class="sxs-lookup"><span data-stu-id="de4cb-118">Credential</span></span>| <span data-ttu-id="de4cb-119">Indica as credenciais para iniciar o processo.</span><span class="sxs-lookup"><span data-stu-id="de4cb-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="de4cb-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="de4cb-120">Ensure</span></span>| <span data-ttu-id="de4cb-121">Indica se o processo existe.</span><span class="sxs-lookup"><span data-stu-id="de4cb-121">Indicates if the process exists.</span></span> <span data-ttu-id="de4cb-122">Defina essa propriedade como "Present" para garantir que o processo exista.</span><span class="sxs-lookup"><span data-stu-id="de4cb-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="de4cb-123">Caso contrário, defina-a como "Absent".</span><span class="sxs-lookup"><span data-stu-id="de4cb-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="de4cb-124">O padrão é "Present".</span><span class="sxs-lookup"><span data-stu-id="de4cb-124">The default is "Present".</span></span>|
| <span data-ttu-id="de4cb-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="de4cb-125">DependsOn</span></span> | <span data-ttu-id="de4cb-126">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="de4cb-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="de4cb-127">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="de4cb-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
| <span data-ttu-id="de4cb-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="de4cb-128">StandardErrorPath</span></span>| <span data-ttu-id="de4cb-129">Indica o caminho do diretório para escrever o erro padrão.</span><span class="sxs-lookup"><span data-stu-id="de4cb-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="de4cb-130">Qualquer arquivo existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="de4cb-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="de4cb-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="de4cb-131">StandardInputPath</span></span>| <span data-ttu-id="de4cb-132">Indica o local de entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="de4cb-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="de4cb-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="de4cb-133">StandardOutputPath</span></span>| <span data-ttu-id="de4cb-134">Indica o local para escrever a saída padrão.</span><span class="sxs-lookup"><span data-stu-id="de4cb-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="de4cb-135">Qualquer arquivo existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="de4cb-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="de4cb-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="de4cb-136">WorkingDirectory</span></span>| <span data-ttu-id="de4cb-137">Indica o local que será usado como diretório de trabalho atual para o processo.</span><span class="sxs-lookup"><span data-stu-id="de4cb-137">Indicates the location that will be used as the current working directory for the process.</span></span>|