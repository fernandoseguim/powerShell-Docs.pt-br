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
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 9f3f79a29e0fb7ec5a5111284bb7985548e17749

---

### Considerações sobre a limitação de comandos
Há um ponto importante sobre esta etapa.
É fundamental que todos os recursos expostos por meio de JEA estejam localizados em áreas restritas pelo administrador.
Os usuários não administradores não devem ter a capacidade de modificar os scripts usados por meio de pontos de extremidade JEA.

Falando nisso, é essencial que você não conceda a usuários do JEA a capacidade de substituir configurações do JEA e scripts na lista branca dentro de suas sessões JEA.
Tenha muito cuidado ao expor comandos como `Copy-Item`!




<!--HONumber=Jun16_HO4-->


