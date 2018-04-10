---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: psgallery_items_tab
ms.openlocfilehash: 5058253678a4f996b080e43820fee06b35b681f4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="items-tab"></a><span data-ttu-id="8eeee-103">Guia Itens</span><span class="sxs-lookup"><span data-stu-id="8eeee-103">Items Tab</span></span>

<span data-ttu-id="8eeee-104">A [guia Itens](https://www.powershellgallery.com/items) exibe todos os itens disponíveis na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8eeee-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="8eeee-105">Há várias maneiras de filtrar, classificar e pesquisar os itens.</span><span class="sxs-lookup"><span data-stu-id="8eeee-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="8eeee-106">Para ver mais detalhes sobre um item específico, clique no item.</span><span class="sxs-lookup"><span data-stu-id="8eeee-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="8eeee-107">Filtrar Por</span><span class="sxs-lookup"><span data-stu-id="8eeee-107">Filter By</span></span>

<span data-ttu-id="8eeee-108">O menu suspenso em "Filtrar Por" permite aos usuários filtrar os resultados por:</span><span class="sxs-lookup"><span data-stu-id="8eeee-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
* <span data-ttu-id="8eeee-109">Incluir pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="8eeee-109">Include Prerelease</span></span>
* <span data-ttu-id="8eeee-110">Apenas estável</span><span class="sxs-lookup"><span data-stu-id="8eeee-110">Stable Only</span></span>

<span data-ttu-id="8eeee-111">Para saber mais sobre itens de "pré-lançamento" e "estáveis", confira o artigo [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Controle de versão de pré-lançamento adicionado ao PowerShellGet e à Galeria do PowerShell), no blog da equipe do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8eeee-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="8eeee-112">Com as caixas de seleção no menu suspenso, os usuários podem filtrar os resultados por:</span><span class="sxs-lookup"><span data-stu-id="8eeee-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
* <span data-ttu-id="8eeee-113">Tipos de item</span><span class="sxs-lookup"><span data-stu-id="8eeee-113">Item Types</span></span>
  - <span data-ttu-id="8eeee-114">Módulo</span><span class="sxs-lookup"><span data-stu-id="8eeee-114">Module</span></span>
  - <span data-ttu-id="8eeee-115">script</span><span class="sxs-lookup"><span data-stu-id="8eeee-115">Script</span></span>
* <span data-ttu-id="8eeee-116">Categorias</span><span class="sxs-lookup"><span data-stu-id="8eeee-116">Categories</span></span>
  - <span data-ttu-id="8eeee-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8eeee-117">Cmdlet</span></span>
  - <span data-ttu-id="8eeee-118">Recurso de DSC</span><span class="sxs-lookup"><span data-stu-id="8eeee-118">DSC Resource</span></span>
  - <span data-ttu-id="8eeee-119">Função</span><span class="sxs-lookup"><span data-stu-id="8eeee-119">Function</span></span>
  - <span data-ttu-id="8eeee-120">Capacidade da função</span><span class="sxs-lookup"><span data-stu-id="8eeee-120">Role Capability</span></span>
  - <span data-ttu-id="8eeee-121">Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="8eeee-121">Workflow</span></span>

<span data-ttu-id="8eeee-122">Para ver somente módulos na Galeria do PowerShell, marque a opção Módulo nos Tipos de item.</span><span class="sxs-lookup"><span data-stu-id="8eeee-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="8eeee-123">Da mesma forma, para ver somente scripts na Galeria do PowerShell, marque a opção Script nos Tipos de item.</span><span class="sxs-lookup"><span data-stu-id="8eeee-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="8eeee-124">Os filtros são inclusivos.</span><span class="sxs-lookup"><span data-stu-id="8eeee-124">Filters are inclusive.</span></span>
> <span data-ttu-id="8eeee-125">Exemplo: um item que contém cmdlets e funções será exibido se Cmdlet ou Função (ou ambos) estiverem marcados.</span><span class="sxs-lookup"><span data-stu-id="8eeee-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="8eeee-126">Se nenhum dos dois for selecionado, o item não será exibido.</span><span class="sxs-lookup"><span data-stu-id="8eeee-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="8eeee-127">De forma semelhante, se todas as categorias forem selecionadas, apenas itens que contêm uma dessas categorias serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="8eeee-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="8eeee-128">**Itens que não pertencem a nenhuma dessas categorias não serão exibidos.**</span><span class="sxs-lookup"><span data-stu-id="8eeee-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="8eeee-129">Classificar Por</span><span class="sxs-lookup"><span data-stu-id="8eeee-129">Sort By</span></span>

<span data-ttu-id="8eeee-130">O menu suspenso Classificar Por permite aos usuários classificar os resultados por:</span><span class="sxs-lookup"><span data-stu-id="8eeee-130">The Sort By drop-down allows users to sort the results by:</span></span>
* <span data-ttu-id="8eeee-131">Popularidade – a popularidade é determinada pela Contagem de Downloads</span><span class="sxs-lookup"><span data-stu-id="8eeee-131">Popularity - Popularity is determined by Download Count</span></span>
* <span data-ttu-id="8eeee-132">A a Z – em ordem alfabética por nome do item</span><span class="sxs-lookup"><span data-stu-id="8eeee-132">A-Z - Alphabetically by item name</span></span>
* <span data-ttu-id="8eeee-133">Recentes – os itens aparecem na ordem da data de publicação</span><span class="sxs-lookup"><span data-stu-id="8eeee-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="8eeee-134">Caixa de Pesquisa</span><span class="sxs-lookup"><span data-stu-id="8eeee-134">Search Box</span></span>

<span data-ttu-id="8eeee-135">A Caixa de Pesquisa permite que os usuários pesquisem itens por palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="8eeee-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="8eeee-136">Para saber mais, confira [Sintaxe de Pesquisa da Galeria](psgallery_search_syntax.md).</span><span class="sxs-lookup"><span data-stu-id="8eeee-136">For more information, see [Gallery Search Syntax](psgallery_search_syntax.md).</span></span>