---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="02038-102">Recursos DSC baseados em classe</span><span class="sxs-lookup"><span data-stu-id="02038-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="02038-103">Definindo recursos DSC com classes</span><span class="sxs-lookup"><span data-stu-id="02038-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="02038-104">Com base nos comentários, tornamos a criação de recursos DSC baseados em classe mais simples e mais fácil de entender.</span><span class="sxs-lookup"><span data-stu-id="02038-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="02038-105">As principais diferenças entre um recurso DSC baseado em classe e um provedor de recursos DSC de cmdlet são:</span><span class="sxs-lookup"><span data-stu-id="02038-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="02038-106">Um arquivo MOF para o esquema não é necessário.</span><span class="sxs-lookup"><span data-stu-id="02038-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="02038-107">Uma subpasta **DSCResource** na pasta do módulo não é necessária.</span><span class="sxs-lookup"><span data-stu-id="02038-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="02038-108">Um arquivo de módulo do PowerShell pode conter várias classes de recursos DSC.</span><span class="sxs-lookup"><span data-stu-id="02038-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="02038-109">Para obter mais informações, veja [Escrevendo um recurso personalizado de DSC com classes do PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="02038-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

