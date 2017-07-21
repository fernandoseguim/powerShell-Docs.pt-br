---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery,psget
title: A Galeria do PowerShell
ms.openlocfilehash: 3e324f15b251822163c3ea9b6655767419a5ac4e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="f62ee-103">A Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f62ee-103">The PowerShell Gallery</span></span>

<span data-ttu-id="f62ee-104">A Galeria do PowerShell é o repositório central de conteúdo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f62ee-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="f62ee-105">Você pode encontrar novos comandos do PowerShell ou recursos DSC (Configuração de Estado Desejado) na Galeria.</span><span class="sxs-lookup"><span data-stu-id="f62ee-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="f62ee-106">Visão geral do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f62ee-106">PowerShellGet Overview</span></span>

<span data-ttu-id="f62ee-107">O módulo do PowerShellGet contém cmdlets para descoberta, instalação, atualização e publicação dos artefatos do PowerShell como Módulos, Recursos DSC, Funcionalidades de Função e Scripts de https://www.PowerShellGallery.com e outros repositórios privados.</span><span class="sxs-lookup"><span data-stu-id="f62ee-107">PowerShellGet module contains cmdlets for discovering, installing, updating and publishing the PowerShell artifacts like Modules, DSC Resources, Role Capabilities and Scripts from the https://www.PowerShellGallery.com and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="f62ee-108">Introdução à Galeria</span><span class="sxs-lookup"><span data-stu-id="f62ee-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="f62ee-109">A instalação de itens da Galeria exige a versão mais recente do módulo PowerShellGet, disponível no Windows 10, no WMF (Windows Management Framework) 5.0 ou no instalador baseado em MSI (para PowerShell 3 e 4).</span><span class="sxs-lookup"><span data-stu-id="f62ee-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="f62ee-110">[**Obter o Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span><span class="sxs-lookup"><span data-stu-id="f62ee-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="f62ee-111">[**Obter o WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) ou</span><span class="sxs-lookup"><span data-stu-id="f62ee-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="f62ee-112">**Obter o instalador MSI**</span><span class="sxs-lookup"><span data-stu-id="f62ee-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="f62ee-113">Com o módulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) mais recente, você pode:</span><span class="sxs-lookup"><span data-stu-id="f62ee-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="f62ee-114">Pesquisar por itens na Galeria com [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="f62ee-114">Search through items in the Gallery with [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="f62ee-115">Salvar itens da Galeria em seu sistema com [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="f62ee-115">Save items to your system from the Gallery with [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="f62ee-116">Instalar itens da Galeria com [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="f62ee-116">Install items from the Gallery with [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="f62ee-117">Carregar itens na Galeria com [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="f62ee-117">Upload items to the Gallery with [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) and [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>
-   <span data-ttu-id="f62ee-118">Adicionar seu próprio repositório personalizado com [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="f62ee-118">Add your own custom repository with [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)</span></span>

<span data-ttu-id="f62ee-119">Confira a página [Introdução](psgallery/psgallery_gettingstarted.md) para obter mais informações sobre como usar os comandos PowerShellGet com a Galeria.</span><span class="sxs-lookup"><span data-stu-id="f62ee-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="f62ee-120">Também é possível executar *Update-Help -Module PowerShellGet* para instalar a ajuda local para esses comandos.</span><span class="sxs-lookup"><span data-stu-id="f62ee-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="f62ee-121">Sistemas operacionais com suporte</span><span class="sxs-lookup"><span data-stu-id="f62ee-121">Supported Operating Systems</span></span>

<span data-ttu-id="f62ee-122">O módulo **PowerShellGet** exige o **PowerShell 3.0 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="f62ee-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="f62ee-123">Portanto, **PowerShellGet** exige um dos seguintes sistemas operacionais:</span><span class="sxs-lookup"><span data-stu-id="f62ee-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="f62ee-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="f62ee-124">Windows 10</span></span>
- <span data-ttu-id="f62ee-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="f62ee-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="f62ee-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="f62ee-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="f62ee-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="f62ee-127">Windows 7 SP1</span></span>
- <span data-ttu-id="f62ee-128">Windows Server 2016 TP5</span><span class="sxs-lookup"><span data-stu-id="f62ee-128">Windows Server 2016 TP5</span></span>
- <span data-ttu-id="f62ee-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f62ee-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="f62ee-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="f62ee-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="f62ee-131">**PowerShellGet** também exige o .NET Framework 4.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="f62ee-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="f62ee-132">Você pode instalar o .NET Framework 4.5 ou acima acessando [aqui](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="f62ee-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="f62ee-133">Tem alguma pergunta?</span><span class="sxs-lookup"><span data-stu-id="f62ee-133">Got a question?</span></span> <span data-ttu-id="f62ee-134">Deseja fazer comentários?</span><span class="sxs-lookup"><span data-stu-id="f62ee-134">Have feedback?</span></span>

<span data-ttu-id="f62ee-135">Encontre mais informações sobre a Galeria do PowerShell e o PowerShellGet na página [Introdução](psgallery/psgallery_gettingstarted.md).</span><span class="sxs-lookup"><span data-stu-id="f62ee-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="f62ee-136">Forneça comentários e relate problemas usando o [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="f62ee-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

