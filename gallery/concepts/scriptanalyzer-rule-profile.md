---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Perfil de regra do ScriptAnalyzer para a Galeria
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059584"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="ad441-103">Perfil de regra do ScriptAnalyzer para a Galeria</span><span class="sxs-lookup"><span data-stu-id="ad441-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="ad441-104">Para garantir a qualidade dos pacotes publicados na Galeria do PowerShell, executamos as regras do [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) para determinar se há violações nos scripts enviados.</span><span class="sxs-lookup"><span data-stu-id="ad441-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="ad441-105">Você pode encontrar a lista de regras que estão em execução na [página GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) do ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="ad441-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="ad441-106">Se tiver preocupações com relação às regras que estamos executando, entre em contato com os Administradores da Galeria do PowerShell ou abra um problema do ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="ad441-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="ad441-107">Os resultados do ScriptAnalyzer serão exibidos em cada página de pacote individual na Galeria no próximo lançamento.</span><span class="sxs-lookup"><span data-stu-id="ad441-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="ad441-108">Recomendamos que os proprietários de pacote verifiquem seus pacotes para se certificar de que não haja nenhum erro grave nos pacotes publicados.</span><span class="sxs-lookup"><span data-stu-id="ad441-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
