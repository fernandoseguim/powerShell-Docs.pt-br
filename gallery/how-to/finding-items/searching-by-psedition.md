---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Itens com edições compatíveis do PowerShell
ms.openlocfilehash: f661c2cd076acb9c11394ba0b752ebd154965ff4
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="items-with-compatible-powershell-editions"></a>Itens com edições compatíveis do PowerShell

Da versão 5.1 em diante, o PowerShell está disponível nas edições diferentes que denotam diferentes conjuntos de recursos e compatibilidade de plataforma.

- **Desktop Edition:** criada no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows, como Server Core e Área de Trabalho do Windows.
- **Core Edition:** criada no .NET Core e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell executando em edições de superfície reduzida do Windows, como o Nano Server e Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>A Galeria do PowerShell extrai metadados de PSEditions com suporte e permite filtrar itens compatíveis para edições específicas do PowerShell

Se um item tiver PSEditions compatíveis especificadas, elas serão listadas como parte das "Edições do PowerShell" na página de exibição de item e nos resultados de itens.

![Página de exibição do item com PSEditions](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Pesquise por itens na interface do usuário da Galeria que funcionem no PowerShellCore

Use as marcas: "PSEdition_Desktop" e "PSEdition_Core" para filtrar os itens na Galeria do PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Use as marcas: "PSEdition_Core" para pesquisar itens compatíveis com o PowerShell Core Edition.

![Resultados da pesquisa para itens compatíveis com o Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Use as marcas: "PSEdition_Desktop" para pesquisar itens compatíveis com o PowerShell Desktop Edition.

![Resultados da pesquisa para itens compatíveis com o Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Mais detalhes sobre como criar e localizar os itens com as edições compatíveis do PowerShell

- [Módulos com PSEditions](../../concepts/module-psedition-support.md)
- [Scripts com PSEditions](../../concepts/script-psedition-support.md)