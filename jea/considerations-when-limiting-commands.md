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
ms.translationtype: HT
ms.contentlocale: pt-BR
---
### <a name="considerations-when-limiting-commands"></a><span data-ttu-id="e73e2-103">Considerações sobre a limitação de comandos</span><span class="sxs-lookup"><span data-stu-id="e73e2-103">Considerations When Limiting Commands</span></span>
<span data-ttu-id="e73e2-104">Há um ponto importante sobre esta etapa.</span><span class="sxs-lookup"><span data-stu-id="e73e2-104">There is one important point to make about this step.</span></span>
<span data-ttu-id="e73e2-105">É fundamental que todos os recursos expostos por meio de JEA estejam localizados em áreas restritas pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="e73e2-105">It is critical that all capabilities exposed through JEA are located in administrator-restricted areas.</span></span>
<span data-ttu-id="e73e2-106">Os usuários não administradores não devem ter a capacidade de modificar os scripts usados por meio de pontos de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="e73e2-106">Non-administrator users should not have the capability to modify the scripts used through JEA endpoints.</span></span>

<span data-ttu-id="e73e2-107">Falando nisso, é essencial que você não conceda a usuários do JEA a capacidade de substituir configurações do JEA e scripts na lista de permissões dentro de suas sessões JEA.</span><span class="sxs-lookup"><span data-stu-id="e73e2-107">On a related note, it is critical that you do not give JEA users the ability to overwrite JEA configurations and whitelisted scripts within their JEA sessions.</span></span>
<span data-ttu-id="e73e2-108">Tenha muito cuidado ao expor comandos como `Copy-Item`!</span><span class="sxs-lookup"><span data-stu-id="e73e2-108">Be extremely careful when exposing commands like `Copy-Item`!</span></span>

