---
title: Como importar os Cmdlets que usam módulos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859142"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="660d6-102">Como importar cmdlets por meio de módulos</span><span class="sxs-lookup"><span data-stu-id="660d6-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="660d6-103">Este tópico descreve como importar os cmdlets para uma sessão do Windows PowerShell usando um módulo binário.</span><span class="sxs-lookup"><span data-stu-id="660d6-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="660d6-104">Os membros de módulos podem incluir cmdlets, provedores, funções, variáveis, aliases e muito mais.</span><span class="sxs-lookup"><span data-stu-id="660d6-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="660d6-105">Snap-ins pode conter apenas os cmdlets e provedores.</span><span class="sxs-lookup"><span data-stu-id="660d6-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="660d6-106">Como carregar os cmdlets usando um módulo</span><span class="sxs-lookup"><span data-stu-id="660d6-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="660d6-107">Crie uma pasta de módulo que tem o mesmo nome que o arquivo do assembly no qual os cmdlets são implementados.</span><span class="sxs-lookup"><span data-stu-id="660d6-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="660d6-108">Neste procedimento, a pasta de módulo é criada no `system32` pasta.</span><span class="sxs-lookup"><span data-stu-id="660d6-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="660d6-109">Certifique-se de que o `PSModulePath` variável de ambiente inclui o caminho para a nova pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="660d6-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="660d6-110">Por padrão, a pasta do sistema já foi adicionada para o `PSModulePath` variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="660d6-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="660d6-111">Copie o assembly de cmdlet para a pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="660d6-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="660d6-112">Execute o seguinte comando para adicionar os cmdlets para a sessão:</span><span class="sxs-lookup"><span data-stu-id="660d6-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="660d6-113">Esse procedimento pode ser usado para testar seus cmdlets.</span><span class="sxs-lookup"><span data-stu-id="660d6-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="660d6-114">Ele adiciona todos os cmdlets no assembly para a sessão.</span><span class="sxs-lookup"><span data-stu-id="660d6-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="660d6-115">Para obter mais informações sobre os módulos, os diferentes tipos de módulos, as diferentes maneiras de carregar módulos e como restringir os elementos de um módulo são exportados, consulte [escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="660d6-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="660d6-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="660d6-116">See Also</span></span>

<span data-ttu-id="660d6-117">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="660d6-117">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="660d6-118">Instalar os módulos</span><span class="sxs-lookup"><span data-stu-id="660d6-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)