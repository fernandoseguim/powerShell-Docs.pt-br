---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: Sintaxe de pesquisa da Galeria
ms.openlocfilehash: 4c0e357957ef970826ee90868db78ac07a14c804
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="5378e-103">Sintaxe de pesquisa da Galeria</span><span class="sxs-lookup"><span data-stu-id="5378e-103">Gallery Search Syntax</span></span>

<span data-ttu-id="5378e-104">A Galeria do PowerShell oferece uma caixa de pesquisa de texto em que você pode usar palavras, frases e expressões de palavra-chave para refinar os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="5378e-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="5378e-105">Pesquisa com palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5378e-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="5378e-106">A pesquisa fará seu melhor esforço para encontrar documentos relevantes contendo as três palavras-chave e retornar os documentos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="5378e-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="5378e-107">Pesquisa usando frases e palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5378e-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="5378e-108">Inserir uma frase entre aspas ("") altera a pesquisa para procurar pela frase específica, em vez de palavras-chave separadas.</span><span class="sxs-lookup"><span data-stu-id="5378e-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="5378e-109">Documentos correspondentes normalmente devem conter exatamente a frase "azure sql", incluindo variações nas maiúsculas e minúsculas, como "Azure SQL" e geralmente também contêm a palavra “deployment".</span><span class="sxs-lookup"><span data-stu-id="5378e-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="5378e-110">Filtrando pelos campos</span><span class="sxs-lookup"><span data-stu-id="5378e-110">Filtering on fields</span></span>

<span data-ttu-id="5378e-111">Você pode pesquisar pela ID de um item específico (ou "Id" ou "id") ou por alguns outros campos prefixando os termos de pesquisa com o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="5378e-111">You can search for a specific item ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="5378e-112">Atualmente, os campos pesquisáveis são "Id", "Version", "Tags", "Author", "Owner", "Functions", "Cmdlets", "DscResources" e "PowerShellVersion".</span><span class="sxs-lookup"><span data-stu-id="5378e-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="5378e-113">[Qual é a diferença entre o título e a ID?</span><span class="sxs-lookup"><span data-stu-id="5378e-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="5378e-114">ID é o nome que você usa no console.</span><span class="sxs-lookup"><span data-stu-id="5378e-114">ID is the name you use in the console.</span></span> <span data-ttu-id="5378e-115">O título é mostrado na parte superior da página do item nos resultados da pesquisa.]</span><span class="sxs-lookup"><span data-stu-id="5378e-115">Title is what is shown at the top of the item page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="5378e-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5378e-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="5378e-117">localiza itens com "PSReadline" ou "AzureRM.Profile" no campo de ID, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5378e-117">finds items with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="5378e-118">é outra maneira de localizar itens com "AzureRM.Profile" no campo de ID.</span><span class="sxs-lookup"><span data-stu-id="5378e-118">is another way to find items with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="5378e-119">O filtro "Id" é correspondente a uma subcadeia, de modo que se pesquisar pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="5378e-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="5378e-120">Você obterá resultados como "AzureRM.Profile" e "Azure.Storage".</span><span class="sxs-lookup"><span data-stu-id="5378e-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="5378e-121">Você também pode pesquisar por várias palavras-chave em um único campo.</span><span class="sxs-lookup"><span data-stu-id="5378e-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="5378e-122">Ou misturar e combinar os campos.</span><span class="sxs-lookup"><span data-stu-id="5378e-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="5378e-123">E você pode fazer pesquisas por frase:</span><span class="sxs-lookup"><span data-stu-id="5378e-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="5378e-124">Para pesquisar todos os itens com a marca DSC.</span><span class="sxs-lookup"><span data-stu-id="5378e-124">To search all items with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="5378e-125">Para pesquisar todos os itens com a função especificada.</span><span class="sxs-lookup"><span data-stu-id="5378e-125">To search all items with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="5378e-126">Para pesquisar todos os itens com o cmdlet especificado.</span><span class="sxs-lookup"><span data-stu-id="5378e-126">To search all items with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="5378e-127">Para pesquisar todos os itens com o nome do Recurso de DCS especificado.</span><span class="sxs-lookup"><span data-stu-id="5378e-127">To search all items with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="5378e-128">Para pesquisar todos os itens com o PowerShellVersion especificado</span><span class="sxs-lookup"><span data-stu-id="5378e-128">To search all items with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="5378e-129">Por fim, se você usar um campo para o qual não há suporte, como "commands", vamos ignorá-lo e pesquisar em todos os campos.</span><span class="sxs-lookup"><span data-stu-id="5378e-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="5378e-130">Sendo assim, a seguinte consulta</span><span class="sxs-lookup"><span data-stu-id="5378e-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="5378e-131">É interpretada exatamente como esta consulta:</span><span class="sxs-lookup"><span data-stu-id="5378e-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage