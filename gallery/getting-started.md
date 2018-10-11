---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Introdução à Galeria do PowerShell
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523004"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="f8692-103">Introdução à Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8692-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="f8692-104">O modo adequado de instalar itens da Galeria do PowerShell é usar os cmdlets do módulo [PowerShellGet](/powershell/module/powershellget).</span><span class="sxs-lookup"><span data-stu-id="f8692-104">The proper way to install items from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="f8692-105">Não é necessário entrar para baixar itens da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f8692-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="f8692-106">É possível baixar o pacote diretamente da Galeria do PowerShell, mas essa não é uma abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="f8692-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span> <span data-ttu-id="f8692-107">Para saber mais detalhes, confira [Download manual do pacote](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span><span class="sxs-lookup"><span data-stu-id="f8692-107">For more details, see [Manual Package Download](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span></span>  


## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="f8692-108">Descobrindo itens da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8692-108">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="f8692-109">Você pode encontrar itens na Galeria do PowerShell usando o controle **Pesquisar** no site ou navegando pelas páginas de Módulos e Scripts.</span><span class="sxs-lookup"><span data-stu-id="f8692-109">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="f8692-110">Você pode também encontrar itens da Galeria do PowerShell executando os cmdlets [Find-Module][] e [Find-Script][], dependendo do tipo de item, com `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="f8692-110">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="f8692-111">A filtragem dos resultados da Galeria pode ser feita usando os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="f8692-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="f8692-112">Nome</span><span class="sxs-lookup"><span data-stu-id="f8692-112">Name</span></span>
- <span data-ttu-id="f8692-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="f8692-113">AllVersions</span></span>
- <span data-ttu-id="f8692-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f8692-114">MinimumVersion</span></span>
- <span data-ttu-id="f8692-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f8692-115">RequiredVersion</span></span>
- <span data-ttu-id="f8692-116">Tag</span><span class="sxs-lookup"><span data-stu-id="f8692-116">Tag</span></span>
- <span data-ttu-id="f8692-117">Includes</span><span class="sxs-lookup"><span data-stu-id="f8692-117">Includes</span></span>
- <span data-ttu-id="f8692-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="f8692-118">DscResource</span></span>
- <span data-ttu-id="f8692-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="f8692-119">RoleCapability</span></span>
- <span data-ttu-id="f8692-120">Comando</span><span class="sxs-lookup"><span data-stu-id="f8692-120">Command</span></span>
- <span data-ttu-id="f8692-121">Filtro</span><span class="sxs-lookup"><span data-stu-id="f8692-121">Filter</span></span>

<span data-ttu-id="f8692-122">Caso tenha interesse apenas em descobrir recursos de DSC específicos na Galeria, execute o cmdlet [Find-DscResource].</span><span class="sxs-lookup"><span data-stu-id="f8692-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="f8692-123">Find-DscResource retorna dados em recursos de DSC contidos na Galeria.</span><span class="sxs-lookup"><span data-stu-id="f8692-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="f8692-124">Como os recursos de DSC sempre são fornecidos como parte de um módulo, você ainda precisa executar [Install-Module][] para instalar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="f8692-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="f8692-125">Aprendendo sobre itens na Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8692-125">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="f8692-126">Depois de identificar um item no qual tem interesse, talvez você queira aprender mais sobre ele.</span><span class="sxs-lookup"><span data-stu-id="f8692-126">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="f8692-127">Você pode fazer isso examinando a página específica do item na Galeria.</span><span class="sxs-lookup"><span data-stu-id="f8692-127">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="f8692-128">Nessa página, você poderá ver todos os metadados carregados com o item.</span><span class="sxs-lookup"><span data-stu-id="f8692-128">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="f8692-129">Esses metadados do item são fornecidos pelo autor do item e não são verificados pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f8692-129">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="f8692-130">O Proprietário do item está intimamente ligado à conta da Galeria usada para publicar o item e é mais confiável do que o campo Autor.</span><span class="sxs-lookup"><span data-stu-id="f8692-130">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="f8692-131">Se você descobrir que um item que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do item.</span><span class="sxs-lookup"><span data-stu-id="f8692-131">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="f8692-132">Se estiver executando [Find-Module][] ou [Find-Script][], você poderá exibir esses dados no objeto PSGetModuleInfo retornado.</span><span class="sxs-lookup"><span data-stu-id="f8692-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="f8692-133">Por exemplo, executar `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="f8692-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="f8692-134">retorna dados sobre o módulo PSReadLine na Galeria.</span><span class="sxs-lookup"><span data-stu-id="f8692-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="f8692-135">Baixando itens da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8692-135">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="f8692-136">Recomendamos o processo a seguir para baixar itens da Galeria do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f8692-136">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="f8692-137">Inspecionar</span><span class="sxs-lookup"><span data-stu-id="f8692-137">Inspect</span></span>

<span data-ttu-id="f8692-138">Para baixar um item da Galeria para inspeção, execute o cmdlet [Save-Module][] ou [Save-Script][], dependendo do tipo de item.</span><span class="sxs-lookup"><span data-stu-id="f8692-138">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="f8692-139">Isso permite que você salve o item localmente sem instalá-lo e inspecione o conteúdo do item.</span><span class="sxs-lookup"><span data-stu-id="f8692-139">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="f8692-140">Lembre-se de excluir o item salvo manualmente.</span><span class="sxs-lookup"><span data-stu-id="f8692-140">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="f8692-141">Alguns desses itens são criados pela Microsoft e outros são criados pela comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f8692-141">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="f8692-142">A Microsoft recomenda que você examine o conteúdo e o código dos itens nesta galeria antes da instalação.</span><span class="sxs-lookup"><span data-stu-id="f8692-142">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="f8692-143">Se você descobrir que um item que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do item.</span><span class="sxs-lookup"><span data-stu-id="f8692-143">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="f8692-144">Instalar</span><span class="sxs-lookup"><span data-stu-id="f8692-144">Install</span></span>

<span data-ttu-id="f8692-145">Para instalar um item da Galeria para uso, execute o cmdlet [Install-Module][] ou [Install-Script][], dependendo do tipo de item.</span><span class="sxs-lookup"><span data-stu-id="f8692-145">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="f8692-146">[Install-Module][] instala o módulo em `$env:ProgramFiles\WindowsPowerShell\Modules` por padrão.</span><span class="sxs-lookup"><span data-stu-id="f8692-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="f8692-147">Isso requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="f8692-147">This requires an administrator account.</span></span> <span data-ttu-id="f8692-148">Se você adicionar o parâmetro `-Scope CurrentUser`, o módulo será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="f8692-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="f8692-149">[Install-Script][] instala o script em `$env:ProgramFiles\WindowsPowerShell\Scripts` por padrão.</span><span class="sxs-lookup"><span data-stu-id="f8692-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="f8692-150">Isso requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="f8692-150">This requires an administrator account.</span></span> <span data-ttu-id="f8692-151">Se você adicionar o parâmetro `-Scope CurrentUser`, o script será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.</span><span class="sxs-lookup"><span data-stu-id="f8692-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="f8692-152">Por padrão, [Install-Module][] e [Install-Script][] instalam a versão mais recente de um item.</span><span class="sxs-lookup"><span data-stu-id="f8692-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="f8692-153">Para instalar uma versão mais antiga do item, adicione o parâmetro `-RequiredVersion`.</span><span class="sxs-lookup"><span data-stu-id="f8692-153">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="f8692-154">Implantar</span><span class="sxs-lookup"><span data-stu-id="f8692-154">Deploy</span></span>

<span data-ttu-id="f8692-155">Para implantar um item da Galeria do PowerShell na Automação do Azure, clique em **Implantar na Automação do Azure** na página de detalhes do item.</span><span class="sxs-lookup"><span data-stu-id="f8692-155">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="f8692-156">Você será redirecionado ao Portal de Gerenciamento do Azure, em que você entra usando as credenciais de sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="f8692-156">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="f8692-157">Observe que implantar itens com dependências implantará todas as dependências na Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="f8692-157">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="f8692-158">O botão Implantar na Automação do Azure pode ser desabilitado adicionando a marca **AzureAutomationNotSupported** aos metadados do item.</span><span class="sxs-lookup"><span data-stu-id="f8692-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="f8692-159">Para saber mais sobre a Automação do Azure, confira a documentação da [Automação do Azure](/azure/automation).</span><span class="sxs-lookup"><span data-stu-id="f8692-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="f8692-160">Atualizando itens da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8692-160">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="f8692-161">Para atualizar itens instalados usando a Galeria do PowerShell, execute o cmdlet [Update-Module][] ou [Update-Script][].</span><span class="sxs-lookup"><span data-stu-id="f8692-161">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="f8692-162">Quando executado sem parâmetros adicionais, [Update-Module][] tenta atualizar cada módulo instalado executando [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="f8692-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="f8692-163">Para atualizar os módulos seletivamente, adicione o parâmetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="f8692-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="f8692-164">Da mesma forma, quando executado sem parâmetros adicionais, [Update-Script][] também tenta atualizar cada script instalado executando [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="f8692-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="f8692-165">Para atualizar os scripts seletivamente, adicione o parâmetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="f8692-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="f8692-166">Listar itens que você instalou da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8692-166">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="f8692-167">Para descobrir quais módulos você instalou da Galeria do PowerShell, execute o cmdlet [Get-InstalledModule][].</span><span class="sxs-lookup"><span data-stu-id="f8692-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="f8692-168">Esse comando lista todos os módulos no seu sistema que foram instalados diretamente da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f8692-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="f8692-169">De forma semelhante, para descobrir quais scripts você instalou da Galeria do PowerShell, execute o cmdlet [Get-InstalledScript][].</span><span class="sxs-lookup"><span data-stu-id="f8692-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="f8692-170">Esse comando lista todos os scripts no seu sistema que foram instalados diretamente da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f8692-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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