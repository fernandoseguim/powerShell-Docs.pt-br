---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: psgallery_pseditions
ms.openlocfilehash: 6634da5c2dadee9c0c6470b3d3e8883e6d02160f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="items-with-compatible-powershell-editions" class="xliff"></a>
# Itens com edições compatíveis do PowerShell
Da versão 5.1 em diante, o PowerShell está disponível nas edições diferentes que denotam diferentes conjuntos de recursos e compatibilidade de plataforma.

- **Desktop Edition:** criada no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows, como Server Core e Área de Trabalho do Windows.
- **Core Edition:** criada no .NET Core e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell executando em edições de superfície reduzida do Windows, como o Nano Server e Windows IoT.

<a id="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions" class="xliff"></a>
## A Galeria do PowerShell extrai metadados de PSEditions com suporte e permite filtrar itens compatíveis para edições específicas do PowerShell

Se um item tiver PSEditions compatíveis especificadas, elas serão listadas como parte das "Edições do PowerShell" na página de exibição de item e nos resultados de itens.
![Página de exibição do item com PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)

<a id="search-for-items-in-the-gallery-ui-which-works-on-powershellcore" class="xliff"></a>
## Pesquise por itens na interface do usuário da Galeria que funcionem no PowerShellCore
Use as marcas: "PSEdition_Desktop" e "PSEdition_Core" para filtrar os itens na Galeria do PowerShell.

<a id="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition" class="xliff"></a>
### Use as marcas: "PSEdition_Core" para pesquisar itens compatíveis com o PowerShell Core Edition.
![Resultados da pesquisa para itens compatíveis com o Core PSEdition](Images/SearchResultsWithPSEditions.PNG)

<a id="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition" class="xliff"></a>
### Use as marcas: "PSEdition_Desktop" para pesquisar itens compatíveis com o PowerShell Desktop Edition.
![Resultados da pesquisa para itens compatíveis com o Desktop PSEdition](Images/SearchResultsWithPSEdition_Desktop.PNG)

<a id="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions" class="xliff"></a>
## Mais detalhes sobre como criar e localizar os itens com as edições compatíveis do PowerShell
<a id="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd" class="xliff"></a>
### [Módulos com PSEditions](../psget/module/modulewithpseditionsupport.md)
<a id="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd" class="xliff"></a>
### [Scripts com PSEditions](../psget/script/scriptwithpseditionsupport.md)

