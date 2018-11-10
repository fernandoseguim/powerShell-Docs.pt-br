---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Introdução à Galeria do PowerShell
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225668"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="efdfb-103">Introdução à Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="efdfb-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="efdfb-104">O modo adequado de instalar pacote da Galeria do PowerShell é usar os cmdlets do módulo [PowerShellGet](/powershell/module/powershellget).</span><span class="sxs-lookup"><span data-stu-id="efdfb-104">The proper way to install packages from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="efdfb-105">Não é necessário entrar para baixar itens da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efdfb-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="efdfb-106">É possível baixar o pacote diretamente da Galeria do PowerShell, mas essa não é uma abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="efdfb-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="efdfb-107">Para saber mais detalhes, confira [Download manual do pacote](/powershell/gallery/how-to/working-with-packages/manual-download).</span><span class="sxs-lookup"><span data-stu-id="efdfb-107">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="efdfb-108">Descobrir pacotes da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="efdfb-108">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="efdfb-109">Você pode encontrar pacotes na Galeria do PowerShell, usando o controle **Pesquisar** no site ou navegando pelas páginas de Módulos e Scripts.</span><span class="sxs-lookup"><span data-stu-id="efdfb-109">You can find packages in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="efdfb-110">Você pode também encontrar pacotes da Galeria do PowerShell executando os cmdlets [Find-Module][] e [Find-Script][], dependendo do tipo de item, com `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="efdfb-110">You can also find packages from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="efdfb-111">A filtragem dos resultados da Galeria pode ser feita usando os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="efdfb-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="efdfb-112">Nome</span><span class="sxs-lookup"><span data-stu-id="efdfb-112">Name</span></span>
- <span data-ttu-id="efdfb-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="efdfb-113">AllVersions</span></span>
- <span data-ttu-id="efdfb-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="efdfb-114">MinimumVersion</span></span>
- <span data-ttu-id="efdfb-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="efdfb-115">RequiredVersion</span></span>
- <span data-ttu-id="efdfb-116">Tag</span><span class="sxs-lookup"><span data-stu-id="efdfb-116">Tag</span></span>
- <span data-ttu-id="efdfb-117">Includes</span><span class="sxs-lookup"><span data-stu-id="efdfb-117">Includes</span></span>
- <span data-ttu-id="efdfb-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="efdfb-118">DscResource</span></span>
- <span data-ttu-id="efdfb-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="efdfb-119">RoleCapability</span></span>
- <span data-ttu-id="efdfb-120">Comando</span><span class="sxs-lookup"><span data-stu-id="efdfb-120">Command</span></span>
- <span data-ttu-id="efdfb-121">Filtro</span><span class="sxs-lookup"><span data-stu-id="efdfb-121">Filter</span></span>

<span data-ttu-id="efdfb-122">Caso tenha interesse apenas em descobrir recursos de DSC específicos na Galeria, execute o cmdlet [Find-DscResource].</span><span class="sxs-lookup"><span data-stu-id="efdfb-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="efdfb-123">Find-DscResource retorna dados em recursos de DSC contidos na Galeria.</span><span class="sxs-lookup"><span data-stu-id="efdfb-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="efdfb-124">Como os recursos de DSC sempre são fornecidos como parte de um módulo, você ainda precisa executar [Install-Module][] para instalar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="efdfb-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="efdfb-125">Aprender sobre itens na Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="efdfb-125">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="efdfb-126">Depois de identificar um pacote no qual tem interesse, talvez você queira aprender mais sobre ele.</span><span class="sxs-lookup"><span data-stu-id="efdfb-126">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="efdfb-127">Você pode fazer isso examinando a página específica do pacote na Galeria.</span><span class="sxs-lookup"><span data-stu-id="efdfb-127">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="efdfb-128">Nessa página, você poderá ver todos os metadados carregados com o pacote.</span><span class="sxs-lookup"><span data-stu-id="efdfb-128">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="efdfb-129">Esses metadados do pacote são fornecidos pelo autor dele e não são verificados pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="efdfb-129">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="efdfb-130">O Proprietário do pacote está intimamente ligado à conta da Galeria usada para publicar o pacote e é mais confiável do que o campo Autor.</span><span class="sxs-lookup"><span data-stu-id="efdfb-130">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="efdfb-131">Se você descobrir que um pacote que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do pacote.</span><span class="sxs-lookup"><span data-stu-id="efdfb-131">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="efdfb-132">Se estiver executando [Find-Module][] ou [Find-Script][], você poderá exibir esses dados no objeto PSGetModuleInfo retornado.</span><span class="sxs-lookup"><span data-stu-id="efdfb-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="efdfb-133">Por exemplo, executar `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="efdfb-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="efdfb-134">retorna dados sobre o módulo PSReadLine na Galeria.</span><span class="sxs-lookup"><span data-stu-id="efdfb-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="efdfb-135">Baixar pacotes da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="efdfb-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="efdfb-136">Recomendamos o processo a seguir para baixar pacotes da Galeria do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="efdfb-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="efdfb-137">Inspecionar</span><span class="sxs-lookup"><span data-stu-id="efdfb-137">Inspect</span></span>

<span data-ttu-id="efdfb-138">Para baixar um pacote da Galeria para inspeção, execute o cmdlet [Save-Module][] ou [Save-Script][], dependendo do tipo de pacote.</span><span class="sxs-lookup"><span data-stu-id="efdfb-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="efdfb-139">Isso permite que você salve o pacote localmente sem instalá-lo e inspecione o conteúdo do pacote.</span><span class="sxs-lookup"><span data-stu-id="efdfb-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="efdfb-140">Lembre-se de excluir o pacote salvo manualmente.</span><span class="sxs-lookup"><span data-stu-id="efdfb-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="efdfb-141">Alguns desses pacotes são criados pela Microsoft e outros são criados pela comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efdfb-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="efdfb-142">A Microsoft recomenda que você examine o conteúdo e o código dos pacotes nesta galeria antes da instalação.</span><span class="sxs-lookup"><span data-stu-id="efdfb-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="efdfb-143">Se você descobrir que um pacote que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do pacote.</span><span class="sxs-lookup"><span data-stu-id="efdfb-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="efdfb-144">Instalar</span><span class="sxs-lookup"><span data-stu-id="efdfb-144">Install</span></span>

<span data-ttu-id="efdfb-145">Para instalar um pacote da Galeria para uso, execute o cmdlet [Install-Module][] ou [Install-Script][], dependendo do tipo de pacote.</span><span class="sxs-lookup"><span data-stu-id="efdfb-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="efdfb-146">[Install-Module][] instala o módulo em `$env:ProgramFiles\WindowsPowerShell\Modules` por padrão.</span><span class="sxs-lookup"><span data-stu-id="efdfb-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="efdfb-147">Isso requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="efdfb-147">This requires an administrator account.</span></span> <span data-ttu-id="efdfb-148">Se você adicionar o parâmetro `-Scope CurrentUser`, o módulo será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="efdfb-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="efdfb-149">[Install-Script][] instala o script em `$env:ProgramFiles\WindowsPowerShell\Scripts` por padrão.</span><span class="sxs-lookup"><span data-stu-id="efdfb-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="efdfb-150">Isso requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="efdfb-150">This requires an administrator account.</span></span> <span data-ttu-id="efdfb-151">Se você adicionar o parâmetro `-Scope CurrentUser`, o script será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.</span><span class="sxs-lookup"><span data-stu-id="efdfb-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="efdfb-152">Por padrão, [Install-Module][] e [Install-Script][] instalam a versão mais recente de um pacote.</span><span class="sxs-lookup"><span data-stu-id="efdfb-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="efdfb-153">Para instalar uma versão mais antiga do pacote, adicione o parâmetro `-RequiredVersion`.</span><span class="sxs-lookup"><span data-stu-id="efdfb-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="efdfb-154">Implantar</span><span class="sxs-lookup"><span data-stu-id="efdfb-154">Deploy</span></span>

<span data-ttu-id="efdfb-155">Para implantar um pacote da Galeria do PowerShell na Automação do Azure, clique em **Implantar na Automação do Azure** na página de detalhes do pacote.</span><span class="sxs-lookup"><span data-stu-id="efdfb-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="efdfb-156">Você será redirecionado ao Portal de Gerenciamento do Azure, em que você entra usando as credenciais de sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="efdfb-156">You will be redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="efdfb-157">Implantar pacotes com dependências implantará todas as dependências na Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="efdfb-157">Note that deploying packages with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="efdfb-158">O botão "Implantar na Automação do Azure" pode ser desabilitado adicionando a marca **AzureAutomationNotSupported** aos metadados do pacote.</span><span class="sxs-lookup"><span data-stu-id="efdfb-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="efdfb-159">Para saber mais sobre a Automação do Azure, confira a documentação da [Automação do Azure](/azure/automation).</span><span class="sxs-lookup"><span data-stu-id="efdfb-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="efdfb-160">Atualizar pacotes da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="efdfb-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="efdfb-161">Para atualizar pacotes instalados usando a Galeria do PowerShell, execute o cmdlet [Update-Module][] ou [Update-Script][].</span><span class="sxs-lookup"><span data-stu-id="efdfb-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="efdfb-162">Quando executado sem parâmetros adicionais, [Update-Module][] tenta atualizar cada módulo instalado executando [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="efdfb-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="efdfb-163">Para atualizar os módulos seletivamente, adicione o parâmetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="efdfb-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="efdfb-164">Da mesma forma, quando executado sem parâmetros adicionais, [Update-Script][] também tenta atualizar cada script instalado executando [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="efdfb-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="efdfb-165">Para atualizar os scripts seletivamente, adicione o parâmetro `-Name`.</span><span class="sxs-lookup"><span data-stu-id="efdfb-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="efdfb-166">Listar pacotes que você instalou da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="efdfb-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="efdfb-167">Para descobrir quais módulos você instalou da Galeria do PowerShell, execute o cmdlet [Get-InstalledModule][].</span><span class="sxs-lookup"><span data-stu-id="efdfb-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="efdfb-168">Esse comando lista todos os módulos no seu sistema que foram instalados diretamente da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efdfb-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="efdfb-169">De forma semelhante, para descobrir quais scripts você instalou da Galeria do PowerShell, execute o cmdlet [Get-InstalledScript][].</span><span class="sxs-lookup"><span data-stu-id="efdfb-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="efdfb-170">Esse comando lista todos os scripts no seu sistema que foram instalados diretamente da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efdfb-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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
