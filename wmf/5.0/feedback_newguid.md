---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225582"
---
# <a name="new-guid"></a><span data-ttu-id="a094f-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="a094f-102">New-Guid</span></span>
<span data-ttu-id="a094f-103">Geralmente, um script (ou talvez a escrita de um recurso DSC) exige um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="a094f-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="a094f-104">GUIDs funcionam bem, e é fácil chamar a classe Guid do .NET Framework para gerar um; no entanto, ter um cmdlet faz com que isso seja mais detectável para os usuários finais que não ainda estão familiarizados com a classe do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a094f-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="a094f-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="a094f-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="a094f-106">Guid</span><span class="sxs-lookup"><span data-stu-id="a094f-106">Guid</span></span>

----

<span data-ttu-id="a094f-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="a094f-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
