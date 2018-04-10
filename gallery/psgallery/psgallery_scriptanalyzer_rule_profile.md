---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: psgallery_scriptanalyzer_rule_profile
ms.openlocfilehash: ff575ab56f07312658d111bccd7793b64ac071ea
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a>Perfil de Regra do ScriptAnazlyer para Galeria
Para garantir a qualidade dos itens publicados na Galeria do PowerShell, executamos as regras do [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) para determinar se há quaisquer violações nos scripts enviados.

Você pode encontrar a lista de regras que estão em execução na [página GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) do ScriptAnalyzer.
Se você tiver preocupações sobre as regras que estão sendo executadas, entre em contato com os Administradores de Galeria do PowerShell ou abra um problema do ScriptAnalzyer.

Os resultados do ScriptAnalyzer serão exibidos em cada página de item individual na Galeria no próximo lançamento. Recomendamos que os proprietários de item verifiquem seus itens para se certificar de que não há nenhum erro grave em itens publicados.