---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Introdução à Galeria do PowerShell
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="ececc-103">Introdução à Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ececc-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="ececc-104">Baixar itens da Galeria do PowerShell para o seu sistema requer o módulo [PowerShellGet](/powershell/module/powershellget).</span><span class="sxs-lookup"><span data-stu-id="ececc-104">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="ececc-105">Você pode encontrar o módulo PowerShellGet em qualquer um dos recursos indicados a seguir.</span><span class="sxs-lookup"><span data-stu-id="ececc-105">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="ececc-106">Não é necessário entrar para baixar itens da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ececc-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="ececc-107">Descobrindo itens da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ececc-107">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="ececc-108">Você pode encontrar itens na Galeria do PowerShell usando o controle **Pesquisar** no site ou navegando pelas páginas de Módulos e Scripts.</span><span class="sxs-lookup"><span data-stu-id="ececc-108">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="ececc-109">Você pode também encontrar itens da Galeria do PowerShell executando os cmdlets [Find-Module][] e [Find-Script][], dependendo do tipo de item, com `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="ececc-109">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="ececc-110">A filtragem dos resultados da Galeria pode ser feita usando os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="ececc-110">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="ececc-111">Nome</span><span class="sxs-lookup"><span data-stu-id="ececc-111">Name</span></span>
- <span data-ttu-id="ececc-112">AllVersions</span><span class="sxs-lookup"><span data-stu-id="ececc-112">AllVersions</span></span>
- <span data-ttu-id="ececc-113">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="ececc-113">MinimumVersion</span></span>
- <span data-ttu-id="ececc-114">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ececc-114">RequiredVersion</span></span>
- <span data-ttu-id="ececc-115">Tag</span><span class="sxs-lookup"><span data-stu-id="ececc-115">Tag</span></span>
- <span data-ttu-id="ececc-116">Includes</span><span class="sxs-lookup"><span data-stu-id="ececc-116">Includes</span></span>
- <span data-ttu-id="ececc-117">DscResource</span><span class="sxs-lookup"><span data-stu-id="ececc-117">DscResource</span></span>
- <span data-ttu-id="ececc-118">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="ececc-118">RoleCapability</span></span>
- <span data-ttu-id="ececc-119">Comando</span><span class="sxs-lookup"><span data-stu-id="ececc-119">Command</span></span>
- <span data-ttu-id="ececc-120">Filtro</span><span class="sxs-lookup"><span data-stu-id="ececc-120">Filter</span></span>

<span data-ttu-id="ececc-121">Caso tenha interesse apenas em descobrir recursos de DSC específicos na Galeria, execute o cmdlet [Find-DscResource].</span><span class="sxs-lookup"><span data-stu-id="ececc-121">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="ececc-122">Find-DscResource retorna dados em recursos de DSC contidos na Galeria.</span><span class="sxs-lookup"><span data-stu-id="ececc-122">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="ececc-123">Como os recursos de DSC sempre são fornecidos como parte de um módulo, você ainda precisa executar [Install-Module][] para instalar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="ececc-123">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="ececc-124">Aprendendo sobre itens na Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ececc-124">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="ececc-125">Depois de identificar um item no qual tem interesse, talvez você queira aprender mais sobre ele.</span><span class="sxs-lookup"><span data-stu-id="ececc-125">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="ececc-126">Você pode fazer isso examinando a página específica do item na Galeria.</span><span class="sxs-lookup"><span data-stu-id="ececc-126">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="ececc-127">Nessa página, você poderá ver todos os metadados carregados com o item.</span><span class="sxs-lookup"><span data-stu-id="ececc-127">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="ececc-128">Esses metadados do item são fornecidos pelo autor do item e não são verificados pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ececc-128">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="ececc-129">O Proprietário do item está intimamente ligado à conta da Galeria usada para publicar o item e é mais confiável do que o campo Autor.</span><span class="sxs-lookup"><span data-stu-id="ececc-129">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="ececc-130">Se você descobrir que um item que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do item.</span><span class="sxs-lookup"><span data-stu-id="ececc-130">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="ececc-131">Se estiver executando [Find-Module][] ou [Find-Script][], você poderá exibir esses dados no objeto PSGetModuleInfo retornado.</span><span class="sxs-lookup"><span data-stu-id="ececc-131">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="ececc-132">Por exemplo, executar `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` retorna dados sobre o módulo PSReadLine na Galeria.</span><span class="sxs-lookup"><span data-stu-id="ececc-132">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="ececc-133">Baixando itens da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ececc-133">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="ececc-134">Recomendamos o processo a seguir para baixar itens da Galeria do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ececc-134">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="ececc-135">Inspecionar</span><span class="sxs-lookup"><span data-stu-id="ececc-135">Inspect</span></span>

<span data-ttu-id="ececc-136">Para baixar um item da Galeria para inspeção, execute o cmdlet [Save-Module][] ou [Save-Script][], dependendo do tipo de item.</span><span class="sxs-lookup"><span data-stu-id="ececc-136">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="ececc-137">Isso permite que você salve o item localmente sem instalá-lo e inspecione o conteúdo do item.</span><span class="sxs-lookup"><span data-stu-id="ececc-137">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="ececc-138">Lembre-se de excluir o item salvo manualmente.</span><span class="sxs-lookup"><span data-stu-id="ececc-138">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="ececc-139">Alguns desses itens são criados pela Microsoft e outros são criados pela comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ececc-139">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="ececc-140">A Microsoft recomenda que você examine o conteúdo e o código dos itens nesta galeria antes da instalação.</span><span class="sxs-lookup"><span data-stu-id="ececc-140">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="ececc-141">Se você descobrir que um item que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do item.</span><span class="sxs-lookup"><span data-stu-id="ececc-141">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="ececc-142">Instalar</span><span class="sxs-lookup"><span data-stu-id="ececc-142">Install</span></span>

<span data-ttu-id="ececc-143">Para instalar um item da Galeria para uso, execute o cmdlet [Install-Module][] ou [Install-Script][], dependendo do tipo de item.</span><span class="sxs-lookup"><span data-stu-id="ececc-143">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="ececc-144">[Install-Module][] instala o módulo em `$env:ProgramFiles\WindowsPowerShell\Modules` por padrão.</span><span class="sxs-lookup"><span data-stu-id="ececc-144">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="ececc-145">Isso requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="ececc-145">This requires an administrator account.</span></span> <span data-ttu-id="ececc-146">Se você adicionar o parâmetro `-Scope CurrentUser`, o módulo será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="ececc-146">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="ececc-147">[Install-Script][] instala o script em `$env:ProgramFiles\WindowsPowerShell\Scripts` por padrão.</span><span class="sxs-lookup"><span data-stu-id="ececc-147">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="ececc-148">Isso requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="ececc-148">This requires an administrator account.</span></span> <span data-ttu-id="ececc-149">Se você adicionar o parâmetro `-Scope CurrentUser`, o script será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.</span><span class="sxs-lookup"><span data-stu-id="ececc-149">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="ececc-150">Por padrão, [Install-Module][] e [Install-Script][] instalam a versão mais recente de um item.</span><span class="sxs-lookup"><span data-stu-id="ececc-150">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="ececc-151">Para instalar uma versão mais antiga do item, adicione o parâmetro `-RequiredVersion`.</span><span class="sxs-lookup"><span data-stu-id="ececc-151">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="ececc-152">Implantar</span><span class="sxs-lookup"><span data-stu-id="ececc-152">Deploy</span></span>

<span data-ttu-id="ececc-153">Para implantar um item da Galeria do PowerShell na Automação do Azure, clique em **Implantar na Automação do Azure** na página de detalhes do item.</span><span class="sxs-lookup"><span data-stu-id="ececc-153">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="ececc-154">Você será redirecionado ao Portal de Gerenciamento do Azure, em que você entra usando as credenciais de sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="ececc-154">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="ececc-155">Observe que implantar itens com dependências implantará todas as dependências na Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="ececc-155">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="ececc-156">O botão Implantar na Automação do Azure pode ser desabilitado adicionando a marca **AzureAutomationNotSupported** aos metadados do item.</span><span class="sxs-lookup"><span data-stu-id="ececc-156">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="ececc-157">Para saber mais sobre a Automação do Azure, confira a documentação da [Automação do Azure](/azure/automation).</span><span class="sxs-lookup"><span data-stu-id="ececc-157">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="ececc-158">Atualizando itens da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ececc-158">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="ececc-159">Para atualizar itens instalados usando a Galeria do PowerShell, execute o cmdlet [Update-Module][] ou [Update-Script][].</span><span class="sxs-lookup"><span data-stu-id="ececc-159">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="ececc-160">Quando executado sem parâmetros adicionais, [Update-Module][] tenta atualizar cada módulo instalado executando [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="ececc-160">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="ececc-161">Para atualizar os módulos seletivamente, adicione o parâmetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="ececc-161">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="ececc-162">Da mesma forma, quando executado sem parâmetros adicionais, [Update-Script][] também tenta atualizar cada script instalado executando [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="ececc-162">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="ececc-163">Para atualizar os scripts seletivamente, adicione o parâmetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="ececc-163">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="ececc-164">Listar itens que você instalou da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ececc-164">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="ececc-165">Para descobrir quais módulos você instalou da Galeria do PowerShell, execute o cmdlet [Get-InstalledModule][].</span><span class="sxs-lookup"><span data-stu-id="ececc-165">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="ececc-166">Esse comando lista todos os módulos no seu sistema que foram instalados diretamente da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ececc-166">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="ececc-167">De forma semelhante, para descobrir quais scripts você instalou da Galeria do PowerShell, execute o cmdlet [Get-InstalledScript][].</span><span class="sxs-lookup"><span data-stu-id="ececc-167">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="ececc-168">Esse comando lista todos os scripts no seu sistema que foram instalados diretamente da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ececc-168">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script