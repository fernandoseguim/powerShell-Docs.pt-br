---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225667"
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="e77f6-102">Entregar um documento de configuração sem aplicação</span><span class="sxs-lookup"><span data-stu-id="e77f6-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="e77f6-103">O cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) faz uma cópia de um arquivo MOF de configuração e a cola em um nó de destino, mas não aplica a configuração.</span><span class="sxs-lookup"><span data-stu-id="e77f6-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="e77f6-104">Essa configuração é aplicada durante a próxima passagem de consistência ou ao executar o cmdlet [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).</span><span class="sxs-lookup"><span data-stu-id="e77f6-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>
