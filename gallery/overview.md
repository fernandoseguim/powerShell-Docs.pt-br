---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery,psget
title: A Galeria do PowerShell
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482923"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="f1db6-103">A Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1db6-103">The PowerShell Gallery</span></span>

<span data-ttu-id="f1db6-104">A Galeria do PowerShell é o repositório central de conteúdo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1db6-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="f1db6-105">Nela, você pode encontrar módulos úteis do PowerShell que contêm comandos do PowerShell e recursos de DSC (Configuração de Estado Desejado).</span><span class="sxs-lookup"><span data-stu-id="f1db6-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="f1db6-106">Você também pode encontrar scripts do PowerShell, alguns dos quais podem conter fluxos de trabalho do PowerShell e que descrevem um conjunto de tarefas e fornecem o sequenciamento para essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="f1db6-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="f1db6-107">Alguns desses itens são criados pela Microsoft e outros são criados pela comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1db6-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="f1db6-108">Visão geral do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f1db6-108">PowerShellGet Overview</span></span>

<span data-ttu-id="f1db6-109">O módulo do PowerShellGet contém cmdlets para descoberta, instalação, atualização e publicação dos artefatos do PowerShell como Módulos, Recursos de DSC, Funcionalidades de Função e Scripts da [Galeria do PowerShell](https://www.PowerShellGallery.com) e outros repositórios privados.</span><span class="sxs-lookup"><span data-stu-id="f1db6-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="f1db6-110">Introdução à Galeria</span><span class="sxs-lookup"><span data-stu-id="f1db6-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="f1db6-111">A instalação de itens da Galeria requer a versão mais recente do módulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="f1db6-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="f1db6-112">Confira [Instalando o PowerShellGet](installing-psget.md) para obter instruções completas.</span><span class="sxs-lookup"><span data-stu-id="f1db6-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="f1db6-113">Confira a página [Introdução](getting-started.md) para obter mais informações sobre como usar os comandos PowerShellGet com a Galeria.</span><span class="sxs-lookup"><span data-stu-id="f1db6-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="f1db6-114">Também é possível executar *Update-Help -Module PowerShellGet* para instalar a ajuda local para esses comandos.</span><span class="sxs-lookup"><span data-stu-id="f1db6-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="f1db6-115">Sistemas operacionais com suporte</span><span class="sxs-lookup"><span data-stu-id="f1db6-115">Supported Operating Systems</span></span>

<span data-ttu-id="f1db6-116">O módulo **PowerShellGet** exige o **Windows PowerShell 3.0 ou mais recente** ou o **PowerShell Core 6.0 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="f1db6-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="f1db6-117">Uma versão adequada do **Windows PowerShell** está disponível para esses sistemas operacionais:</span><span class="sxs-lookup"><span data-stu-id="f1db6-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="f1db6-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="f1db6-118">Windows 10</span></span>
- <span data-ttu-id="f1db6-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="f1db6-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="f1db6-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="f1db6-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="f1db6-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="f1db6-121">Windows 7 SP1</span></span>
- <span data-ttu-id="f1db6-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="f1db6-122">Windows Server 2016</span></span>
- <span data-ttu-id="f1db6-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f1db6-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="f1db6-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="f1db6-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="f1db6-125">O **PowerShellGet** também requer o .NET Framework 4.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="f1db6-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="f1db6-126">Você pode instalar o .NET Framework 4.5 ou acima acessando [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="f1db6-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="f1db6-127">O **PowerShell Core** oferece suporte a vários sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="f1db6-127">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="f1db6-128">Confira [este artigo](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) para obter uma lista completa.</span><span class="sxs-lookup"><span data-stu-id="f1db6-128">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="f1db6-129">Muitos módulos hospedados na galeria darão suporte a sistemas operacionais diferentes e têm outros requisitos.</span><span class="sxs-lookup"><span data-stu-id="f1db6-129">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="f1db6-130">Consulte a documentação dos módulos para saber mais.</span><span class="sxs-lookup"><span data-stu-id="f1db6-130">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="f1db6-131">Tem alguma pergunta?</span><span class="sxs-lookup"><span data-stu-id="f1db6-131">Got a question?</span></span> <span data-ttu-id="f1db6-132">Deseja fazer comentários?</span><span class="sxs-lookup"><span data-stu-id="f1db6-132">Have feedback?</span></span>

<span data-ttu-id="f1db6-133">Encontre mais informações sobre a Galeria do PowerShell e o PowerShellGet na página [Introdução](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="f1db6-133">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="f1db6-134">Forneça comentários e relate problemas usando o [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="f1db6-134">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
