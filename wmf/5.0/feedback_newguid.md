---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a><span data-ttu-id="22909-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="22909-102">New-Guid</span></span>
<span data-ttu-id="22909-103">Geralmente, um script (ou talvez a escrita de um recurso DSC) exige um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="22909-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="22909-104">GUIDs funcionam bem, e é fácil chamar a classe Guid do .NET Framework para gerar um; no entanto, ter um cmdlet faz com que isso seja mais detectável para os usuários finais que não ainda estão familiarizados com a classe do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="22909-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="22909-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="22909-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="22909-106">Guid</span><span class="sxs-lookup"><span data-stu-id="22909-106">Guid</span></span>

----

<span data-ttu-id="22909-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="22909-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>

