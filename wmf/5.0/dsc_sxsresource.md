---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218426"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="8bd9f-102">Suporte ao controle de versão do módulo lado a lado para recursos DSC</span><span class="sxs-lookup"><span data-stu-id="8bd9f-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="8bd9f-103">Os módulos que contêm recursos DSC podem ser instalados lado a lado, e as configurações DSC podem usar uma versão específica do recurso instalado no sistema.</span><span class="sxs-lookup"><span data-stu-id="8bd9f-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="8bd9f-104">Para obter mais informações, veja [Usando recursos com várias versões](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="8bd9f-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="8bd9f-105">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="8bd9f-105">Known issues</span></span>

<span data-ttu-id="8bd9f-106">Nesta versão, os seguintes problemas são problemas conhecidos da instalação lado a lado:</span><span class="sxs-lookup"><span data-stu-id="8bd9f-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="8bd9f-107">Não há suporte para o uso de duas versões diferentes do recurso DSC na mesma configuração.</span><span class="sxs-lookup"><span data-stu-id="8bd9f-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
