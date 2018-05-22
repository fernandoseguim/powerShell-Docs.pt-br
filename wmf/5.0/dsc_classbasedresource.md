---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="3d196-102">Recursos DSC baseados em classe</span><span class="sxs-lookup"><span data-stu-id="3d196-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="3d196-103">Definindo recursos DSC com classes</span><span class="sxs-lookup"><span data-stu-id="3d196-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="3d196-104">Com base nos comentários, tornamos a criação de recursos DSC baseados em classe mais simples e mais fácil de entender.</span><span class="sxs-lookup"><span data-stu-id="3d196-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="3d196-105">As principais diferenças entre um recurso DSC baseado em classe e um provedor de recursos DSC de cmdlet são:</span><span class="sxs-lookup"><span data-stu-id="3d196-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="3d196-106">Um arquivo MOF para o esquema não é necessário.</span><span class="sxs-lookup"><span data-stu-id="3d196-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="3d196-107">Uma subpasta **DSCResource** na pasta do módulo não é necessária.</span><span class="sxs-lookup"><span data-stu-id="3d196-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="3d196-108">Um arquivo de módulo do PowerShell pode conter várias classes de recursos DSC.</span><span class="sxs-lookup"><span data-stu-id="3d196-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="3d196-109">Para obter mais informações, veja [Escrevendo um recurso personalizado de DSC com classes do PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="3d196-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
