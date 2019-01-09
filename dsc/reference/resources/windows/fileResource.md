---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recursos File de DSC
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047066"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="90b4a-103">Recursos File de DSC</span><span class="sxs-lookup"><span data-stu-id="90b4a-103">DSC File Resource</span></span>

> <span data-ttu-id="90b4a-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="90b4a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="90b4a-105">O recurso File na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar arquivos e pastas no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="90b4a-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="90b4a-106">**Observação:** Se a propriedade **MatchSource** estiver definida como **$false** (que é o valor padrão), o conteúdo a ser copiado será armazenado em cache na primeira vez que a configuração for aplicada.</span><span class="sxs-lookup"><span data-stu-id="90b4a-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="90b4a-107">Os aplicativos subsequentes da configuração não verificarão arquivos e/ou pastas atualizados no caminho especificado pelo **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="90b4a-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="90b4a-108">Se você quiser verificar se há atualizações para os arquivos e/ou pastas em **SourcePath** toda vez que a configuração for aplicada, defina **MatchSource** como **$true**.</span><span class="sxs-lookup"><span data-stu-id="90b4a-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="90b4a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90b4a-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="90b4a-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="90b4a-110">Properties</span></span>

|  <span data-ttu-id="90b4a-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="90b4a-111">Property</span></span>  |  <span data-ttu-id="90b4a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="90b4a-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="90b4a-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="90b4a-113">DestinationPath</span></span>| <span data-ttu-id="90b4a-114">Indica o local onde você deseja garantir o estado de um arquivo ou diretório.</span><span class="sxs-lookup"><span data-stu-id="90b4a-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="90b4a-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="90b4a-115">Attributes</span></span>| <span data-ttu-id="90b4a-116">Especifica o estado desejado dos atributos para o arquivo ou diretório de destino.</span><span class="sxs-lookup"><span data-stu-id="90b4a-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="90b4a-117">Soma de verificação</span><span class="sxs-lookup"><span data-stu-id="90b4a-117">Checksum</span></span>| <span data-ttu-id="90b4a-118">Indica o tipo de soma de verificação que deve ser usado para determinar se dois arquivos são iguais.</span><span class="sxs-lookup"><span data-stu-id="90b4a-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="90b4a-119">Se __Checksum__ não for especificado, somente o nome de arquivo ou diretório será usado para comparação.</span><span class="sxs-lookup"><span data-stu-id="90b4a-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="90b4a-120">Os valores válidos incluem: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="90b4a-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="90b4a-121">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="90b4a-121">Contents</span></span>| <span data-ttu-id="90b4a-122">Especifica o conteúdo de um arquivo, como uma cadeia de caracteres específica.</span><span class="sxs-lookup"><span data-stu-id="90b4a-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="90b4a-123">Credential</span><span class="sxs-lookup"><span data-stu-id="90b4a-123">Credential</span></span>| <span data-ttu-id="90b4a-124">Indicará as credenciais necessárias para acessar recursos, como arquivos de origem, se tal acesso for necessário.</span><span class="sxs-lookup"><span data-stu-id="90b4a-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="90b4a-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="90b4a-125">Ensure</span></span>| <span data-ttu-id="90b4a-126">Indica se o arquivo ou diretório existe.</span><span class="sxs-lookup"><span data-stu-id="90b4a-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="90b4a-127">Defina essa propriedade como "Absent" para garantir que o arquivo ou diretório não exista.</span><span class="sxs-lookup"><span data-stu-id="90b4a-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="90b4a-128">Defina-a como "Present" para garantir que o arquivo ou diretório exista.</span><span class="sxs-lookup"><span data-stu-id="90b4a-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="90b4a-129">O padrão é "Present".</span><span class="sxs-lookup"><span data-stu-id="90b4a-129">The default is "Present".</span></span>|
| <span data-ttu-id="90b4a-130">Force</span><span class="sxs-lookup"><span data-stu-id="90b4a-130">Force</span></span>| <span data-ttu-id="90b4a-131">Determinadas operações de arquivo (como substituição de um arquivo ou exclusão de um diretório que não esteja vazio) resultarão em erro.</span><span class="sxs-lookup"><span data-stu-id="90b4a-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="90b4a-132">O uso da propriedade Force substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="90b4a-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="90b4a-133">O valor padrão é __$false__.</span><span class="sxs-lookup"><span data-stu-id="90b4a-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="90b4a-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="90b4a-134">Recurse</span></span>| <span data-ttu-id="90b4a-135">Indica se subdiretórios são incluídos.</span><span class="sxs-lookup"><span data-stu-id="90b4a-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="90b4a-136">Defina essa propriedade como __$true__ para indicar que você deseja que subdiretórios sejam incluídos.</span><span class="sxs-lookup"><span data-stu-id="90b4a-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="90b4a-137">O padrão é __$false__.</span><span class="sxs-lookup"><span data-stu-id="90b4a-137">The default is __$false__.</span></span> <span data-ttu-id="90b4a-138">**Observação**: Essa propriedade é válida somente quando a propriedade Type é definida como Directory.</span><span class="sxs-lookup"><span data-stu-id="90b4a-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="90b4a-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="90b4a-139">DependsOn</span></span> | <span data-ttu-id="90b4a-140">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="90b4a-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="90b4a-141">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="90b4a-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="90b4a-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="90b4a-142">SourcePath</span></span>| <span data-ttu-id="90b4a-143">Indica o caminho do qual o recurso de arquivo ou pasta deve ser copiado.</span><span class="sxs-lookup"><span data-stu-id="90b4a-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="90b4a-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="90b4a-144">Type</span></span>| <span data-ttu-id="90b4a-145">Indica se o recurso que está sendo configurado é um diretório ou um arquivo.</span><span class="sxs-lookup"><span data-stu-id="90b4a-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="90b4a-146">Defina essa propriedade como "Directory" para indicar que o recurso é um diretório.</span><span class="sxs-lookup"><span data-stu-id="90b4a-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="90b4a-147">Defina-a como "File" para indicar que o recurso é um arquivo.</span><span class="sxs-lookup"><span data-stu-id="90b4a-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="90b4a-148">O valor padrão é “File”.</span><span class="sxs-lookup"><span data-stu-id="90b4a-148">The default value is “File”.</span></span>|
| <span data-ttu-id="90b4a-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="90b4a-149">MatchSource</span></span>| <span data-ttu-id="90b4a-150">Se definida como o valor padrão de __$false__, em seguida, todos os arquivos de origem (digamos, arquivos A, B e C) serão adicionados ao destino na primeira vez em que a configuração for aplicada.</span><span class="sxs-lookup"><span data-stu-id="90b4a-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="90b4a-151">Se for adicionado um novo arquivo (D) à origem, ele não será adicionado ao destino, mesmo quando a configuração for reaplicada posteriormente.</span><span class="sxs-lookup"><span data-stu-id="90b4a-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="90b4a-152">Se o valor for __$true__, em seguida, cada vez que a configuração for aplicada, os novos arquivos subsequentemente encontrados na origem (como arquivo D, neste exemplo) serão adicionados ao destino.</span><span class="sxs-lookup"><span data-stu-id="90b4a-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="90b4a-153">O valor padrão é **$false**.</span><span class="sxs-lookup"><span data-stu-id="90b4a-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="90b4a-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90b4a-154">Example</span></span>

<span data-ttu-id="90b4a-155">O exemplo a seguir mostra como usar o recurso Files para garantir que um diretório com o caminho `C:\Users\Public\Documents\DSCDemo\DemoSource` em um computador de origem (como o servidor de “pull”) também esteja presente (juntamente com todos os subdiretórios) no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="90b4a-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="90b4a-156">Também escreve uma mensagem de confirmação no log quando for concluído e inclui uma declaração para garantir que a operação de verificação de arquivos seja executada antes da operação de registro em log.</span><span class="sxs-lookup"><span data-stu-id="90b4a-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```