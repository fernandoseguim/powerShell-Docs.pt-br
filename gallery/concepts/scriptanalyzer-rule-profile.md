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
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Perfil de regra do ScriptAnalyzer para a Galeria

Para garantir a qualidade dos pacotes publicados na Galeria do PowerShell, executamos as regras do [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) para determinar se há violações nos scripts enviados.

Você pode encontrar a lista de regras que estão em execução na [página GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) do ScriptAnalyzer.
Se tiver preocupações com relação às regras que estamos executando, entre em contato com os Administradores da Galeria do PowerShell ou abra um problema do ScriptAnalyzer.

Os resultados do ScriptAnalyzer serão exibidos em cada página de pacote individual na Galeria no próximo lançamento. Recomendamos que os proprietários de pacote verifiquem seus pacotes para se certificar de que não haja nenhum erro grave nos pacotes publicados.
