---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso nxArchive de DSC para Linux
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="b5e90-103">Recurso nxArchive de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="b5e90-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="b5e90-104">O recurso **nxArchive** na Configuração de Estado Desejado (DSC) do PowerShell fornece um mecanismo para descompactar arquivos mortos (.tar, .zip) em um caminho específico em um nó do Linux.</span><span class="sxs-lookup"><span data-stu-id="b5e90-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5e90-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5e90-105">Syntax</span></span>

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="b5e90-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b5e90-106">Properties</span></span>

|  <span data-ttu-id="b5e90-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b5e90-107">Property</span></span> |  <span data-ttu-id="b5e90-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5e90-108">Description</span></span> |
|---|---|
| <span data-ttu-id="b5e90-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="b5e90-109">SourcePath</span></span>| <span data-ttu-id="b5e90-110">Especifica o caminho de origem do arquivo morto.</span><span class="sxs-lookup"><span data-stu-id="b5e90-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="b5e90-111">Deve ser um arquivo .tar, .zip ou .tar.gz.</span><span class="sxs-lookup"><span data-stu-id="b5e90-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="b5e90-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="b5e90-112">DestinationPath</span></span>| <span data-ttu-id="b5e90-113">Especifica o local onde você deseja garantir que o conteúdo do arquivo seja extraído.</span><span class="sxs-lookup"><span data-stu-id="b5e90-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="b5e90-114">Soma de verificação</span><span class="sxs-lookup"><span data-stu-id="b5e90-114">Checksum</span></span>| <span data-ttu-id="b5e90-115">Define o tipo que deve ser usado ao determinar se o arquivo de origem foi atualizado.</span><span class="sxs-lookup"><span data-stu-id="b5e90-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="b5e90-116">Os valores são: "ctime", "mtime" ou "md5".</span><span class="sxs-lookup"><span data-stu-id="b5e90-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="b5e90-117">O valor padrão é "md5".</span><span class="sxs-lookup"><span data-stu-id="b5e90-117">The default value is "md5".</span></span>|
| <span data-ttu-id="b5e90-118">Force</span><span class="sxs-lookup"><span data-stu-id="b5e90-118">Force</span></span>| <span data-ttu-id="b5e90-119">Determinadas operações de arquivo (como substituição de um arquivo ou exclusão de um diretório que não esteja vazio) resultarão em erro.</span><span class="sxs-lookup"><span data-stu-id="b5e90-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="b5e90-120">O uso da propriedade **Force** substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="b5e90-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="b5e90-121">O valor padrão é **$false**.</span><span class="sxs-lookup"><span data-stu-id="b5e90-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="b5e90-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b5e90-122">DependsOn</span></span> | <span data-ttu-id="b5e90-123">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="b5e90-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b5e90-124">Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b5e90-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="b5e90-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="b5e90-125">Ensure</span></span>| <span data-ttu-id="b5e90-126">Determina se é necessário verificar se o conteúdo do arquivo existe em **Destination**.</span><span class="sxs-lookup"><span data-stu-id="b5e90-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="b5e90-127">Defina essa propriedade como "Present" para garantir que o conteúdo exista.</span><span class="sxs-lookup"><span data-stu-id="b5e90-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="b5e90-128">Defina-a como "Absent" para garantir que não exista.</span><span class="sxs-lookup"><span data-stu-id="b5e90-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="b5e90-129">O valor padrão é "Present".</span><span class="sxs-lookup"><span data-stu-id="b5e90-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="b5e90-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5e90-130">Example</span></span>

<span data-ttu-id="b5e90-131">O exemplo a seguir mostra como usar o recurso **nxArchive** para garantir que o conteúdo de um arquivo morto chamado `website.tar` exista e seja extraído em um destino específico.</span><span class="sxs-lookup"><span data-stu-id="b5e90-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```