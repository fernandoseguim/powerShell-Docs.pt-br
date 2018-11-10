---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery,psget
title: A Galeria do PowerShell
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225611"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="a2250-103">A Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="a2250-103">The PowerShell Gallery</span></span>

<span data-ttu-id="a2250-104">A Galeria do PowerShell é o repositório central de conteúdo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2250-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="a2250-105">Nela, você pode encontrar módulos úteis do PowerShell que contêm comandos do PowerShell e recursos de DSC (Configuração de Estado Desejado).</span><span class="sxs-lookup"><span data-stu-id="a2250-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="a2250-106">Você também pode encontrar scripts do PowerShell, alguns dos quais podem conter fluxos de trabalho do PowerShell e que descrevem um conjunto de tarefas e fornecem o sequenciamento para essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="a2250-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="a2250-107">Alguns desses pacotes são criados pela Microsoft e outros são criados pela comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2250-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="a2250-108">Visão geral do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a2250-108">PowerShellGet Overview</span></span>

<span data-ttu-id="a2250-109">O módulo do PowerShellGet contém cmdlets para descoberta, instalação, atualização e publicação de pacotes PowerShell que contêm artefatos como Módulos, Recursos de DSC, Funcionalidades de Função e Scripts da [Galeria do PowerShell](https://www.PowerShellGallery.com) e outros repositórios privados.</span><span class="sxs-lookup"><span data-stu-id="a2250-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="a2250-110">Introdução à Galeria</span><span class="sxs-lookup"><span data-stu-id="a2250-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="a2250-111">A instalação de pacotes da Galeria requer a versão mais recente do módulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="a2250-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="a2250-112">Confira [Instalando o PowerShellGet](installing-psget.md) para obter instruções completas.</span><span class="sxs-lookup"><span data-stu-id="a2250-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="a2250-113">Confira a página [Introdução](getting-started.md) para obter mais informações sobre como usar os comandos PowerShellGet com a Galeria.</span><span class="sxs-lookup"><span data-stu-id="a2250-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="a2250-114">Também é possível executar *Update-Help -Module PowerShellGet* para instalar a ajuda local para esses comandos.</span><span class="sxs-lookup"><span data-stu-id="a2250-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="a2250-115">Sistemas operacionais com suporte</span><span class="sxs-lookup"><span data-stu-id="a2250-115">Supported Operating Systems</span></span>

<span data-ttu-id="a2250-116">O módulo **PowerShellGet** exige o **Windows PowerShell 3.0 ou mais recente** ou o **PowerShell Core 6.0 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="a2250-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="a2250-117">Uma versão adequada do **Windows PowerShell** está disponível para esses sistemas operacionais:</span><span class="sxs-lookup"><span data-stu-id="a2250-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="a2250-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="a2250-118">Windows 10</span></span>
- <span data-ttu-id="a2250-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="a2250-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="a2250-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="a2250-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="a2250-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="a2250-121">Windows 7 SP1</span></span>
- <span data-ttu-id="a2250-122">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="a2250-122">Windows Server 2019</span></span>
- <span data-ttu-id="a2250-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="a2250-123">Windows Server 2016</span></span>
- <span data-ttu-id="a2250-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a2250-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="a2250-125">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="a2250-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="a2250-126">O **PowerShellGet** requer o .NET Framework 4.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="a2250-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="a2250-127">Você pode instalar o .NET Framework 4.5 ou acima acessando [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="a2250-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="a2250-128">Como **PowerShell Core** é uma plataforma cruzada, o que significa que funciona no Windows, Linux e MacOS, ele também deixa **PowerShellGet** disponível nesses sistemas.</span><span class="sxs-lookup"><span data-stu-id="a2250-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="a2250-129">Para obter uma lista completa de sistemas compatíveis com **PowerShell Core**, consulte [Instalação do PowerShell](/powershell/scripting/setup/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="a2250-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="a2250-130">Muitos módulos hospedados na galeria darão suporte a sistemas operacionais diferentes e têm outros requisitos.</span><span class="sxs-lookup"><span data-stu-id="a2250-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="a2250-131">Consulte a documentação dos módulos para saber mais.</span><span class="sxs-lookup"><span data-stu-id="a2250-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="a2250-132">Tem alguma pergunta?</span><span class="sxs-lookup"><span data-stu-id="a2250-132">Got a question?</span></span> <span data-ttu-id="a2250-133">Deseja fazer comentários?</span><span class="sxs-lookup"><span data-stu-id="a2250-133">Have feedback?</span></span>

<span data-ttu-id="a2250-134">Encontre mais informações sobre a Galeria do PowerShell e o PowerShellGet na página [Introdução](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="a2250-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="a2250-135">Forneça comentários e relate problemas usando o [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="a2250-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
