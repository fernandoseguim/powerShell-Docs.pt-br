---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Pacotes com edições compatíveis do PowerShell
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003637"
---
# <a name="packages-with-compatible-powershell-editions"></a><span data-ttu-id="9f561-103">Pacotes com edições compatíveis do PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f561-103">Packages with compatible PowerShell Editions</span></span>

<span data-ttu-id="9f561-104">Da versão 5.1 em diante, o PowerShell está disponível nas edições diferentes que denotam diferentes conjuntos de recursos e compatibilidade de plataforma.</span><span class="sxs-lookup"><span data-stu-id="9f561-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="9f561-105">**Desktop Edition:** criada no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows, como Server Core e Área de Trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="9f561-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="9f561-106">**Core Edition:** criada no .NET Core e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell executando em edições de superfície reduzida do Windows, como o Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="9f561-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="9f561-107">A Galeria do PowerShell extrai metadados de PSEditions com suporte e permite filtrar pacotes compatíveis para edições específicas do PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f561-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="9f561-108">Se um pacote tiver PSEditions compatíveis especificadas, elas serão listadas como parte das "Edições do PowerShell" na página de exibição de pacote e nos resultados de pacotes.</span><span class="sxs-lookup"><span data-stu-id="9f561-108">If a package has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>

![Página de exibição do item com PSEditions](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="9f561-110">Pesquise por pacotes na interface do usuário da Galeria que funcionem no PowerShellCore</span><span class="sxs-lookup"><span data-stu-id="9f561-110">Search for packages in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="9f561-111">Use as marcas: "PSEdition_Desktop" e "PSEdition_Core" para filtrar os pacotes na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9f561-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="9f561-112">Use as marcas: "PSEdition_Core" para pesquisar itens compatíveis com o PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="9f561-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Resultados da pesquisa para itens compatíveis com o Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="9f561-114">Use as marcas: "PSEdition_Desktop" para pesquisar itens compatíveis com o PowerShell Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="9f561-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Resultados da pesquisa para itens compatíveis com o Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="9f561-116">Mais detalhes sobre como criar e localizar os pacotes com as edições compatíveis do PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f561-116">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="9f561-117">Módulos com PSEditions</span><span class="sxs-lookup"><span data-stu-id="9f561-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="9f561-118">Scripts com PSEditions</span><span class="sxs-lookup"><span data-stu-id="9f561-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
