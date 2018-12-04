---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Introdução à Galeria do PowerShell
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: 1082b13115c5c5be4b76574ba55307b3e567983f
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52576882"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="5e2a5-103">Introdução à Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e2a5-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="5e2a5-104">A Galeria do PowerShell é um repositório de pacote que contém scripts, módulos e recursos de DSC, você pode baixar e aproveitar.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-104">The PowerShell Gallery is a package repository containing scripts, modules, and DSC resources you can download and leverage.</span></span> <span data-ttu-id="5e2a5-105">Usar os cmdlets na [PowerShellGet](/powershell/module/powershellget) module para instalar os pacotes da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-105">You use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module to install packages from the PowerShell Gallery.</span></span> <span data-ttu-id="5e2a5-106">Não é necessário entrar para baixar itens da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="5e2a5-107">É possível baixar o pacote diretamente da Galeria do PowerShell, mas essa não é uma abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-107">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="5e2a5-108">Para saber mais detalhes, confira [Download manual do pacote](/powershell/gallery/how-to/working-with-packages/manual-download).</span><span class="sxs-lookup"><span data-stu-id="5e2a5-108">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="5e2a5-109">Descobrir pacotes da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e2a5-109">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="5e2a5-110">Pacotes podem ser encontrados na Galeria do PowerShell usando o **pesquisa** controle na Galeria do PowerShell [página inicial](https://www.powershellgallery.com), ou navegando por meio de módulos e Scripts da [página pacotes ](https://www.powershellgallery.com/packages).</span><span class="sxs-lookup"><span data-stu-id="5e2a5-110">You can find packages in the PowerShell Gallery by using the **Search** control on the PowerShell Gallery's [home page](https://www.powershellgallery.com), or by browsing through the Modules and Scripts from the [Packages page](https://www.powershellgallery.com/packages).</span></span> <span data-ttu-id="5e2a5-111">Você também pode encontrar os pacotes da Galeria do PowerShell executando o [Find-Module][], [Find-DscResource], e [Find-Script][] cmdlets, dependendo do tipo de pacote com `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-111">You can also find packages from the PowerShell Gallery by running the [Find-Module][], [Find-DscResource], and [Find-Script][] cmdlets, depending on the package type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="5e2a5-112">Você pode filtrar os resultados da galeria usando os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="5e2a5-112">You can filter results from the Gallery by using the following parameters:</span></span>

- <span data-ttu-id="5e2a5-113">Nome</span><span class="sxs-lookup"><span data-stu-id="5e2a5-113">Name</span></span>
- <span data-ttu-id="5e2a5-114">AllVersions</span><span class="sxs-lookup"><span data-stu-id="5e2a5-114">AllVersions</span></span>
- <span data-ttu-id="5e2a5-115">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="5e2a5-115">MinimumVersion</span></span>
- <span data-ttu-id="5e2a5-116">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5e2a5-116">RequiredVersion</span></span>
- <span data-ttu-id="5e2a5-117">Tag</span><span class="sxs-lookup"><span data-stu-id="5e2a5-117">Tag</span></span>
- <span data-ttu-id="5e2a5-118">Includes</span><span class="sxs-lookup"><span data-stu-id="5e2a5-118">Includes</span></span>
- <span data-ttu-id="5e2a5-119">DscResource</span><span class="sxs-lookup"><span data-stu-id="5e2a5-119">DscResource</span></span>
- <span data-ttu-id="5e2a5-120">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="5e2a5-120">RoleCapability</span></span>
- <span data-ttu-id="5e2a5-121">Comando</span><span class="sxs-lookup"><span data-stu-id="5e2a5-121">Command</span></span>
- <span data-ttu-id="5e2a5-122">Filtro</span><span class="sxs-lookup"><span data-stu-id="5e2a5-122">Filter</span></span>

<span data-ttu-id="5e2a5-123">Caso tenha interesse apenas em descobrir recursos de DSC específicos na Galeria, execute o cmdlet [Find-DscResource].</span><span class="sxs-lookup"><span data-stu-id="5e2a5-123">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="5e2a5-124">Find-DscResource retorna dados em recursos de DSC contidos na Galeria.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-124">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="5e2a5-125">Como os recursos de DSC sempre são fornecidos como parte de um módulo, você ainda precisa executar [Install-Module][] para instalar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-125">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="5e2a5-126">Aprender sobre itens na Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e2a5-126">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="5e2a5-127">Depois de identificar um pacote no qual tem interesse, talvez você queira aprender mais sobre ele.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-127">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="5e2a5-128">Você pode fazer isso examinando a página específica do pacote na Galeria.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-128">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="5e2a5-129">Nessa página, você poderá ver todos os metadados carregados com o pacote.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-129">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="5e2a5-130">Esses metadados do pacote são fornecidos pelo autor dele e não são verificados pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-130">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="5e2a5-131">O Proprietário do pacote está intimamente ligado à conta da Galeria usada para publicar o pacote e é mais confiável do que o campo Autor.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-131">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="5e2a5-132">Se você descobrir que um pacote que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do pacote.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-132">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="5e2a5-133">Se estiver executando [Find-Module][] ou [Find-Script][], você poderá exibir esses dados no objeto PSGetModuleInfo retornado.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-133">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="5e2a5-134">Por exemplo, executar `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="5e2a5-134">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="5e2a5-135">retorna dados sobre o módulo PSReadLine na Galeria.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-135">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="5e2a5-136">Baixar pacotes da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e2a5-136">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="5e2a5-137">Recomendamos o processo a seguir para baixar pacotes da Galeria do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5e2a5-137">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="5e2a5-138">Inspecionar</span><span class="sxs-lookup"><span data-stu-id="5e2a5-138">Inspect</span></span>

<span data-ttu-id="5e2a5-139">Para baixar um pacote da Galeria para inspeção, execute o cmdlet [Save-Module][] ou [Save-Script][], dependendo do tipo de pacote.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-139">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="5e2a5-140">Isso permite que você salve o pacote localmente sem instalá-lo e inspecione o conteúdo do pacote.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-140">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="5e2a5-141">Lembre-se de excluir o pacote salvo manualmente.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-141">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="5e2a5-142">Alguns desses pacotes são criados pela Microsoft e outros são criados pela comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-142">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="5e2a5-143">A Microsoft recomenda que você examine o conteúdo e o código dos pacotes nesta galeria antes da instalação.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-143">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="5e2a5-144">Se você descobrir que um pacote que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do pacote.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-144">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="5e2a5-145">Instalar</span><span class="sxs-lookup"><span data-stu-id="5e2a5-145">Install</span></span>

<span data-ttu-id="5e2a5-146">Para instalar um pacote da Galeria para uso, execute o cmdlet [Install-Module][] ou [Install-Script][], dependendo do tipo de pacote.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-146">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="5e2a5-147">[Install-Module][] instala o módulo em `$env:ProgramFiles\WindowsPowerShell\Modules` por padrão.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-147">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="5e2a5-148">Isso requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-148">This requires an administrator account.</span></span> <span data-ttu-id="5e2a5-149">Se você adicionar o parâmetro `-Scope CurrentUser`, o módulo será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-149">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="5e2a5-150">[Install-Script][] instala o script em `$env:ProgramFiles\WindowsPowerShell\Scripts` por padrão.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-150">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="5e2a5-151">Isso requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-151">This requires an administrator account.</span></span> <span data-ttu-id="5e2a5-152">Se você adicionar o parâmetro `-Scope CurrentUser`, o script será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-152">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="5e2a5-153">Por padrão, [Install-Module][] e [Install-Script][] instalam a versão mais recente de um pacote.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-153">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="5e2a5-154">Para instalar uma versão mais antiga do pacote, adicione o parâmetro `-RequiredVersion`.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-154">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="5e2a5-155">Implantar</span><span class="sxs-lookup"><span data-stu-id="5e2a5-155">Deploy</span></span>

<span data-ttu-id="5e2a5-156">Para implantar um pacote da Galeria do PowerShell para automação do Azure, clique em **automação do Azure**, em seguida, clique em **implantar na automação do Azure** na página de detalhes do pacote.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-156">To deploy a package from the PowerShell Gallery to Azure Automation, click **Azure Automation**, then click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="5e2a5-157">Você será redirecionado para o Portal de gerenciamento em que você entrar usando suas credenciais de conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-157">You are redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="5e2a5-158">Observe que a implantação de pacotes com dependências implanta todas as dependências à automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-158">Note that deploying packages with dependencies deploys all the dependencies to Azure Automation.</span></span> <span data-ttu-id="5e2a5-159">O botão "Implantar na Automação do Azure" pode ser desabilitado adicionando a marca **AzureAutomationNotSupported** aos metadados do pacote.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-159">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="5e2a5-160">Para saber mais sobre a Automação do Azure, confira a documentação da [Automação do Azure](/azure/automation).</span><span class="sxs-lookup"><span data-stu-id="5e2a5-160">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="5e2a5-161">Atualizar pacotes da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e2a5-161">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="5e2a5-162">Para atualizar pacotes instalados usando a Galeria do PowerShell, execute o cmdlet [Update-Module][] ou [Update-Script][].</span><span class="sxs-lookup"><span data-stu-id="5e2a5-162">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="5e2a5-163">Quando executado sem parâmetros adicionais, [] de [Update-Module] tenta atualizar todos os módulos instalados, executando [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="5e2a5-163">When run without any additional parameters, [Update-Module][] attempts to update all modules installed by running [Install-Module][].</span></span> <span data-ttu-id="5e2a5-164">Para atualizar os módulos seletivamente, adicione o parâmetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-164">To selectively update modules, add the `-Name` parameter.</span></span> 

<span data-ttu-id="5e2a5-165">Da mesma forma, quando executado sem parâmetros adicionais, [] de [Update-Script] também tenta atualizar todos os scripts instalados executando [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="5e2a5-165">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update all scripts installed by running [Install-Script][].</span></span> <span data-ttu-id="5e2a5-166">Para atualizar os scripts seletivamente, adicione o parâmetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-166">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="5e2a5-167">Listar pacotes que você instalou da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e2a5-167">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="5e2a5-168">Para descobrir quais módulos você instalou da Galeria do PowerShell, execute o cmdlet [Get-InstalledModule][].</span><span class="sxs-lookup"><span data-stu-id="5e2a5-168">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="5e2a5-169">Esse comando lista todos os módulos no seu sistema que foram instalados diretamente da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-169">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="5e2a5-170">De forma semelhante, para descobrir quais scripts você instalou da Galeria do PowerShell, execute o cmdlet [Get-InstalledScript][].</span><span class="sxs-lookup"><span data-stu-id="5e2a5-170">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="5e2a5-171">Esse comando lista todos os scripts no seu sistema que foram instalados diretamente da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e2a5-171">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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
