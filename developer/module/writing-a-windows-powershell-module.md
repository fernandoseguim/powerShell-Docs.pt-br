---
title: Escrevendo um módulo do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857932"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="d59b1-102">Escrever um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d59b1-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="d59b1-103">Este documento foi escrito para administradores, desenvolvedores de script e os desenvolvedores de cmdlet que precisam empacotar e distribuir seus cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d59b1-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="d59b1-104">Usando módulos do Windows PowerShell, você pode empacotar e distribuir suas soluções do Windows PowerShell sem usar uma linguagem compilada.</span><span class="sxs-lookup"><span data-stu-id="d59b1-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="d59b1-105">Módulos do Windows PowerShell permitem que você a partição, organizam e abstraem o código do Windows PowerShell em unidades independentes e reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="d59b1-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="d59b1-106">Com essas unidades reutilizáveis, você pode compartilhar facilmente seus módulos diretamente com outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="d59b1-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="d59b1-107">Se você for um desenvolvedor de script, você também pode reempacotar os módulos de terceiros para criar aplicativos personalizados baseados em script.</span><span class="sxs-lookup"><span data-stu-id="d59b1-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="d59b1-108">Soluções de script pronta para produção que usam componentes reutilizáveis e redistribuíveis, com o benefício adicional de permitindo que você empacote e abstrair os vários componentes para habilitar a módulos, semelhantes aos módulos em outras linguagens de script como Perl e Python, Crie soluções personalizadas.</span><span class="sxs-lookup"><span data-stu-id="d59b1-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="d59b1-109">Em sua forma mais básica, Windows PowerShell tratará qualquer código de script do Windows PowerShell válido salvo em um arquivo. psm1 como um módulo.</span><span class="sxs-lookup"><span data-stu-id="d59b1-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="d59b1-110">PowerShell tratará automaticamente qualquer assembly do cmdlet binário como um módulo.</span><span class="sxs-lookup"><span data-stu-id="d59b1-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="d59b1-111">No entanto, você também pode usar um módulo (ou mais especificamente, um manifesto de módulo) para agrupar uma solução inteira.</span><span class="sxs-lookup"><span data-stu-id="d59b1-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="d59b1-112">Os cenários a seguir descrevem os usos comuns para módulos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d59b1-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="d59b1-113">Bibliotecas</span><span class="sxs-lookup"><span data-stu-id="d59b1-113">Libraries</span></span>

<span data-ttu-id="d59b1-114">Módulos podem ser usados para empacotar e distribuir as bibliotecas coesas de funções que executam tarefas comuns.</span><span class="sxs-lookup"><span data-stu-id="d59b1-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="d59b1-115">Normalmente, os nomes dessas funções compartilham um ou mais substantivos que refletem a tarefa comum que elas são usadas.</span><span class="sxs-lookup"><span data-stu-id="d59b1-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="d59b1-116">Essas funções também podem ser semelhantes a classes do .NET Framework em que eles podem ter membros públicos e privados.</span><span class="sxs-lookup"><span data-stu-id="d59b1-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="d59b1-117">Por exemplo, uma biblioteca pode conter um conjunto de funções para transferências de arquivos.</span><span class="sxs-lookup"><span data-stu-id="d59b1-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="d59b1-118">Nesse caso, o substantivo refletindo a tarefa comum pode ser "arquivo".</span><span class="sxs-lookup"><span data-stu-id="d59b1-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="d59b1-119">Configuração</span><span class="sxs-lookup"><span data-stu-id="d59b1-119">Configuration</span></span>

<span data-ttu-id="d59b1-120">Módulos podem ser usados para personalizar seu ambiente com a adição de variáveis, provedores, funções e cmdlets específicos.</span><span class="sxs-lookup"><span data-stu-id="d59b1-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="d59b1-121">Desenvolvimento de código compilado e distribuição</span><span class="sxs-lookup"><span data-stu-id="d59b1-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="d59b1-122">Os desenvolvedores de cmdlet e o provedor podem usar módulos para testar e distribuir seu código compilado sem a necessidade de criar snap-ins. Eles podem importar o assembly que contém o código compilado como um módulo (um módulo binário) sem a necessidade de criar e registrar o snap-ins.</span><span class="sxs-lookup"><span data-stu-id="d59b1-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="d59b1-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d59b1-123">See Also</span></span>

[<span data-ttu-id="d59b1-124">Noções básicas sobre um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d59b1-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="d59b1-125">Como escrever um módulo de Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d59b1-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="d59b1-126">Como escrever um módulo binário do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d59b1-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="d59b1-127">Como escrever um manifesto de módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d59b1-127">How to Write a PowerShell Module Manifest</span></span>](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[<span data-ttu-id="d59b1-128">Modificando o caminho de instalação do PSModulePath</span><span class="sxs-lookup"><span data-stu-id="d59b1-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="d59b1-129">Importando um módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d59b1-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="d59b1-130">Instalando um módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d59b1-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
