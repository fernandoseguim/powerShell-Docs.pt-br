---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Considerações sobre a limitação de comandos"
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="considerations-when-limiting-commands"></a>Considerações sobre a limitação de comandos
Há um ponto importante sobre esta etapa.
É fundamental que todos os recursos expostos por meio de JEA estejam localizados em áreas restritas pelo administrador.
Os usuários não administradores não devem ter a capacidade de modificar os scripts usados por meio de pontos de extremidade JEA.

Falando nisso, é essencial que você não conceda a usuários do JEA a capacidade de substituir configurações do JEA e scripts na lista de permissões dentro de suas sessões JEA.
Tenha muito cuidado ao expor comandos como `Copy-Item`!

