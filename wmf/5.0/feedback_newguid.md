---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675704"
---
# <a name="new-guid"></a><span data-ttu-id="9484a-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="9484a-102">New-Guid</span></span>
<span data-ttu-id="9484a-103">Geralmente, um script (ou talvez a escrita de um recurso DSC) exige um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="9484a-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="9484a-104">GUIDs funcionam bem, e é fácil chamar a classe Guid do .NET Framework para gerar um; no entanto, ter um cmdlet faz com que isso seja mais detectável para os usuários finais que não ainda estão familiarizados com a classe do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9484a-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="9484a-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="9484a-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="9484a-106">Guid</span><span class="sxs-lookup"><span data-stu-id="9484a-106">Guid</span></span>

----

<span data-ttu-id="9484a-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="9484a-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
