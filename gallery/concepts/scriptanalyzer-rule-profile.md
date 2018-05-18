---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: Perfil de regra do ScriptAnalyzer para a Galeria
ms.openlocfilehash: 22b95f0901fe95d5ad79df0e23e675ab52313fee
ms.sourcegitcommit: f8a37df92db22b9368469fb07378399b2ab90cea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2018
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="2a301-103">Perfil de regra do ScriptAnalyzer para a Galeria</span><span class="sxs-lookup"><span data-stu-id="2a301-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="2a301-104">Para garantir a qualidade dos itens publicados na Galeria do PowerShell, executamos as regras do [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) para determinar se há quaisquer violações nos scripts enviados.</span><span class="sxs-lookup"><span data-stu-id="2a301-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="2a301-105">Você pode encontrar a lista de regras que estão em execução na [página GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) do ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="2a301-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="2a301-106">Se você tiver preocupações sobre as regras que estão sendo executadas, entre em contato com os Administradores de Galeria do PowerShell ou abra um problema do ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="2a301-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="2a301-107">Os resultados do ScriptAnalyzer serão exibidos em cada página de item individual na Galeria no próximo lançamento.</span><span class="sxs-lookup"><span data-stu-id="2a301-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="2a301-108">Recomendamos que os proprietários de item verifiquem seus itens para se certificar de que não há nenhum erro grave em itens publicados.</span><span class="sxs-lookup"><span data-stu-id="2a301-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>
