---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 7eaa4dfb68bc299ad31bce81af96b6a760c4fcc5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="d1ee8-102">Criando tipos personalizados usando classes do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1ee8-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="d1ee8-103">Melhoramos a linguagem do PowerShell para definir classes e outros tipos definidos pelo usuário usando uma sintaxe formal e semântica que são semelhantes a outras linguagens de programação orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="d1ee8-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="d1ee8-104">O objetivo é permitir que desenvolvedores e profissionais de TI adotem o PowerShell para uma grande variedade de casos de uso, simplificar o desenvolvimento de artefatos do PowerShell (como recursos DSC) e acelerar a cobertura de superfícies de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="d1ee8-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="d1ee8-105">Cenários com suporte nesta versão</span><span class="sxs-lookup"><span data-stu-id="d1ee8-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="d1ee8-106">Definir recursos DSC e os tipos associados usando a linguagem do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1ee8-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="d1ee8-107">Definir tipos personalizados no PowerShell usando constructos de programação orientada a objeto conhecidos, como classes, propriedades, métodos, etc.</span><span class="sxs-lookup"><span data-stu-id="d1ee8-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="d1ee8-108">Suporte à herança com classe no PowerShell e no recurso DSC de classe base</span><span class="sxs-lookup"><span data-stu-id="d1ee8-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="d1ee8-109">Depurar tipos usando a linguagem do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1ee8-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="d1ee8-110">Gerar e manipular exceções usando mecanismos formais e no nível certo</span><span class="sxs-lookup"><span data-stu-id="d1ee8-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>