---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: galeria,powershell,cmdlet,psgallery
title: Pacotes com as edições do PowerShell ou do sistema operacional compatível
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747697"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="36d78-103">Pacotes com as edições do PowerShell ou em sistemas operacionais compatíveis</span><span class="sxs-lookup"><span data-stu-id="36d78-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="36d78-104">Da versão 5.1 em diante, o PowerShell está disponível em edições diferentes que denotam diversos conjuntos de recursos e compatibilidade de plataforma.</span><span class="sxs-lookup"><span data-stu-id="36d78-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="36d78-105">Pesquisar por edição do PowerShell</span><span class="sxs-lookup"><span data-stu-id="36d78-105">Searching by PowerShell Edition</span></span> 
<span data-ttu-id="36d78-106">As duas edições do Powershell são:</span><span class="sxs-lookup"><span data-stu-id="36d78-106">The two editions of Powershell are:</span></span>
- <span data-ttu-id="36d78-107">Desktop Edition Baseado no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows como núcleo de servidor e área de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="36d78-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="36d78-108">**Core Edition:** Baseada no .NET Core e fornece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de volume reduzido do Windows, como o Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="36d78-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="36d78-109">Galeria do PowerShell lhe permite filtrar os pacotes compatíveis para edições específicas do PowerShell</span><span class="sxs-lookup"><span data-stu-id="36d78-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="36d78-110">Se um pacote tem compatível PSEditions especificado, eles são listados como parte das edições do PowerShell na página de exibição do pacote e também nos resultados de pacotes.</span><span class="sxs-lookup"><span data-stu-id="36d78-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="36d78-111">Você também pode procurar pacotes compatíveis usando o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36d78-111">You can also search for compatible packages using PowerShell.</span></span>

![Página de exibição do item com PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="36d78-113">Procurar pacotes na Galeria de interface do usuário que funcionam no PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="36d78-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="36d78-114">Use as marcas: "PSEdition_Desktop" e "PSEdition_Core" para filtrar os pacotes na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36d78-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="36d78-115">Use as marcas: "PSEdition_Core" para pesquisar itens compatíveis com o PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="36d78-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Resultados da pesquisa para itens compatíveis com o Core PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="36d78-117">Use as marcas: "PSEdition_Desktop" para pesquisar itens compatíveis com o PowerShell Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="36d78-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Resultados da pesquisa para itens compatíveis com o Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="36d78-119">Procurar pacotes encontrar as edições compatíveis usando o PowerShell</span><span class="sxs-lookup"><span data-stu-id="36d78-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="36d78-120">Você pode especificar marcas para filtrar para a edição do PowerShell e o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="36d78-120">You can specify tags to filter for the PowerShell edition and OS.</span></span> <span data-ttu-id="36d78-121">Você usa o `Find-Package` cmdlet especificando o `-Tag` parâmetro para especificar a edição (e o sistema operacional) destinados.</span><span class="sxs-lookup"><span data-stu-id="36d78-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="36d78-122">Assim:</span><span class="sxs-lookup"><span data-stu-id="36d78-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="36d78-123">Pesquisar pelo sistema operacional</span><span class="sxs-lookup"><span data-stu-id="36d78-123">Searching by Operating System</span></span> 

<span data-ttu-id="36d78-124">Uma vez que o PowerShell Core está disponível para Windows, Linux e MacOS, pacotes na galeria podem ser projetados para qualquer combinação desses sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="36d78-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="36d78-125">Na Galeria de interface do usuário, use as seguintes marcas searchs encontrar pacotes marcados pelo sistema operacional:</span><span class="sxs-lookup"><span data-stu-id="36d78-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="36d78-126">Marcações: “Windows”</span><span class="sxs-lookup"><span data-stu-id="36d78-126">Tags: "Windows"</span></span>
- <span data-ttu-id="36d78-127">Marcações: “Linux”</span><span class="sxs-lookup"><span data-stu-id="36d78-127">Tags: "Linux"</span></span>
- <span data-ttu-id="36d78-128">Marcações: “MacOS”</span><span class="sxs-lookup"><span data-stu-id="36d78-128">Tags: "MacOS"</span></span> 

<span data-ttu-id="36d78-129">Você pode especificar essas marcas em `Find-Module` (e outros cmdlets no módulo do PowerShellGet), semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="36d78-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="36d78-130">Pesquisando vários compatibilidades</span><span class="sxs-lookup"><span data-stu-id="36d78-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="36d78-131">Você pode procurar por um pacote que tem vários compatibilidades usando a sintaxe:</span><span class="sxs-lookup"><span data-stu-id="36d78-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span> 

<span data-ttu-id="36d78-132">Marcas "Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="36d78-132">Tags: "Compatibility1" "Compatibility2"</span></span> 

<span data-ttu-id="36d78-133">Por exemplo, se você estiver procurando por um pacote com o PowerShell Core compatibilidade que é executado em computadores meu Windows e Linux, use as marcas de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="36d78-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="36d78-134">Marcas "PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="36d78-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span> 

<span data-ttu-id="36d78-135">Para pesquisar usando o PowerShell, você pode usar o `Find-Module` (e outros cmdlets no módulo do PowerShellGet), semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="36d78-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="36d78-136">Mais detalhes sobre como criar e localizar os pacotes com as edições compatíveis do PowerShell</span><span class="sxs-lookup"><span data-stu-id="36d78-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="36d78-137">Módulos com PSEditions</span><span class="sxs-lookup"><span data-stu-id="36d78-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="36d78-138">Scripts com PSEditions</span><span class="sxs-lookup"><span data-stu-id="36d78-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
