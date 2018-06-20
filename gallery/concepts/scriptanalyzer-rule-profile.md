---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Perfil de regra do ScriptAnalyzer para a Galeria
ms.openlocfilehash: 54100f7a530cbc769e4a0e2dbff18dbc5de88fa6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225735"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Perfil de regra do ScriptAnalyzer para a Galeria

Para garantir a qualidade dos itens publicados na Galeria do PowerShell, executamos as regras do [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) para determinar se há quaisquer violações nos scripts enviados.

Você pode encontrar a lista de regras que estão em execução na [página GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) do ScriptAnalyzer.
Se você tiver preocupações sobre as regras que estão sendo executadas, entre em contato com os Administradores de Galeria do PowerShell ou abra um problema do ScriptAnalzyer.

Os resultados do ScriptAnalyzer serão exibidos em cada página de item individual na Galeria no próximo lançamento. Recomendamos que os proprietários de item verifiquem seus itens para se certificar de que não há nenhum erro grave em itens publicados.
