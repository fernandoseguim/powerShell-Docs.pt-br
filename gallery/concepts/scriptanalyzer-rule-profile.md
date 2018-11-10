---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Perfil de regra do ScriptAnalyzer para a Galeria
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002489"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="2ccad-103">Perfil de regra do ScriptAnalyzer para a Galeria</span><span class="sxs-lookup"><span data-stu-id="2ccad-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="2ccad-104">Para garantir a qualidade dos pacotes publicados na Galeria do PowerShell, executamos as regras do [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) para determinar se há violações nos scripts enviados.</span><span class="sxs-lookup"><span data-stu-id="2ccad-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="2ccad-105">Você pode encontrar a lista de regras que estão em execução na [página GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) do ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="2ccad-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="2ccad-106">Se você tiver preocupações sobre as regras que estão sendo executadas, entre em contato com os Administradores de Galeria do PowerShell ou abra um problema do ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="2ccad-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="2ccad-107">Os resultados do ScriptAnalyzer serão exibidos em cada página de pacote individual na Galeria no próximo lançamento.</span><span class="sxs-lookup"><span data-stu-id="2ccad-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="2ccad-108">Recomendamos que os proprietários de pacote verifiquem seus pacotes para se certificar de que não haja nenhum erro grave nos pacotes publicados.</span><span class="sxs-lookup"><span data-stu-id="2ccad-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
