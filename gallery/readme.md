---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery,psget
title: A Galeria do PowerShell
ms.openlocfilehash: 9519b8bcca9f43419a33db380c3b852e9bb354ac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="58289-103">A Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="58289-103">The PowerShell Gallery</span></span>

<span data-ttu-id="58289-104">A Galeria do PowerShell é o repositório central de conteúdo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58289-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="58289-105">Você pode encontrar novos comandos do PowerShell ou recursos DSC (Configuração de Estado Desejado) na Galeria.</span><span class="sxs-lookup"><span data-stu-id="58289-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="58289-106">Visão geral do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="58289-106">PowerShellGet Overview</span></span>

<span data-ttu-id="58289-107">O módulo do PowerShellGet contém cmdlets para descoberta, instalação, atualização e publicação dos artefatos do PowerShell como Módulos, Recursos de DSC, Funcionalidades de Função e Scripts da [Galeria do PowerShell](https://www.PowerShellGallery.com) e outros repositórios privados.</span><span class="sxs-lookup"><span data-stu-id="58289-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="58289-108">Introdução à Galeria</span><span class="sxs-lookup"><span data-stu-id="58289-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="58289-109">A instalação de itens da Galeria exige a versão mais recente do módulo PowerShellGet, disponível no Windows 10, no WMF (Windows Management Framework) 5.0 ou no instalador baseado em MSI (para PowerShell 3 e 4).</span><span class="sxs-lookup"><span data-stu-id="58289-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="58289-110">[**Obter o Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span><span class="sxs-lookup"><span data-stu-id="58289-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="58289-111">[**Obter o WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) ou</span><span class="sxs-lookup"><span data-stu-id="58289-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="58289-112">**Obter o instalador MSI**</span><span class="sxs-lookup"><span data-stu-id="58289-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="58289-113">Com o módulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) mais recente, você pode:</span><span class="sxs-lookup"><span data-stu-id="58289-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="58289-114">Pesquisar itens na Galeria com [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) e [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span><span class="sxs-lookup"><span data-stu-id="58289-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="58289-115">Salvar itens da Galeria no sistema com [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) e [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span><span class="sxs-lookup"><span data-stu-id="58289-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="58289-116">Instalar itens da Galeria com [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) e [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span><span class="sxs-lookup"><span data-stu-id="58289-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="58289-117">Carregar itens na Galeria com [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) e [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span><span class="sxs-lookup"><span data-stu-id="58289-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="58289-118">Adicionar um repositório personalizado com [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span><span class="sxs-lookup"><span data-stu-id="58289-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="58289-119">Confira a página [Introdução](psgallery/psgallery_gettingstarted.md) para obter mais informações sobre como usar os comandos PowerShellGet com a Galeria.</span><span class="sxs-lookup"><span data-stu-id="58289-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="58289-120">Também é possível executar *Update-Help -Module PowerShellGet* para instalar a ajuda local para esses comandos.</span><span class="sxs-lookup"><span data-stu-id="58289-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="58289-121">Sistemas operacionais com suporte</span><span class="sxs-lookup"><span data-stu-id="58289-121">Supported Operating Systems</span></span>

<span data-ttu-id="58289-122">O módulo **PowerShellGet** exige o **PowerShell 3.0 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="58289-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="58289-123">Portanto, **PowerShellGet** exige um dos seguintes sistemas operacionais:</span><span class="sxs-lookup"><span data-stu-id="58289-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="58289-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="58289-124">Windows 10</span></span>
- <span data-ttu-id="58289-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="58289-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="58289-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="58289-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="58289-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="58289-127">Windows 7 SP1</span></span>
- <span data-ttu-id="58289-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="58289-128">Windows Server 2016</span></span>
- <span data-ttu-id="58289-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="58289-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="58289-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="58289-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="58289-131">**PowerShellGet** também exige o .NET Framework 4.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="58289-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="58289-132">Você pode instalar o .NET Framework 4.5 ou acima acessando [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="58289-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="58289-133">Tem alguma pergunta?</span><span class="sxs-lookup"><span data-stu-id="58289-133">Got a question?</span></span> <span data-ttu-id="58289-134">Deseja fazer comentários?</span><span class="sxs-lookup"><span data-stu-id="58289-134">Have feedback?</span></span>

<span data-ttu-id="58289-135">Encontre mais informações sobre a Galeria do PowerShell e o PowerShellGet na página [Introdução](psgallery/psgallery_gettingstarted.md).</span><span class="sxs-lookup"><span data-stu-id="58289-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="58289-136">Forneça comentários e relate problemas usando o [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="58289-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>