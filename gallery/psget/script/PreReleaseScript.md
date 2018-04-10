---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: PrereleaseScript
ms.openlocfilehash: 575babd6bc373e99a4e924fafef6e9edeec972d4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="f3c7b-103">Versões de pré-lançamento de Scripts</span><span class="sxs-lookup"><span data-stu-id="f3c7b-103">Prerelease Versions of Scripts</span></span>

<span data-ttu-id="f3c7b-104">Começando com a versão 1.6.0, o PowerShellGet e a Galeria do PowerShell são compatíveis com versões de marcação superiores a 1.0.0 como um pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="f3c7b-105">Antes desse recurso, os itens de pré-lançamento eram limitados a ter uma versão que começasse com 0.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="f3c7b-106">A meta desses recursos é oferecer maior compatibilidade com a convenção de versão [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html), sem perder a compatibilidade com o PowerShell versão 3 e superiores ou com as versões existentes do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span>
<span data-ttu-id="f3c7b-107">Este tópico se concentra os recursos específicos do script.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="f3c7b-108">Os recursos equivalentes para módulos estão no tópico [Versões de pré-lançamento do módulo](../module/PrereleaseModule.md).</span><span class="sxs-lookup"><span data-stu-id="f3c7b-108">The equivalent features for modules are in the [Prerelease Module Versions](../module/PrereleaseModule.md) topic.</span></span> <span data-ttu-id="f3c7b-109">Ao usar esses recursos, os editores podem identificar um script como a versão 2.5.0-alpha e, então, lançar uma versão 2.5.0 pronta para produção que substitui a versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="f3c7b-110">Em um nível alto, os recursos de pré-lançamento do script incluem:</span><span class="sxs-lookup"><span data-stu-id="f3c7b-110">At a high level, the prerelease script features include:</span></span>

* <span data-ttu-id="f3c7b-111">Adição de um sufixo PrereleaseString na cadeia de caracteres de versão no manifesto do script.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span>
<span data-ttu-id="f3c7b-112">Quando os scripts são publicados na Galeria do PowerShell, esses dados são extraídos do manifesto e usados para identificar os itens de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
* <span data-ttu-id="f3c7b-113">A aquisição dos itens de pré-lançamento exige a adição do sinalizador -AllowPrerelease aos comandos Find-Script, Install-Script, Update-Script e Save-Script do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span>
<span data-ttu-id="f3c7b-114">Se o sinalizador não for especificado, os itens de pré-lançamento não serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-114">If the flag is not specified, prerelease items will not be shown.</span></span>
* <span data-ttu-id="f3c7b-115">As versões de script exibidas pelo Find-Script, pelo Get-InstalledScript e na Galeria do PowerShell serão exibidas com o PrereleaseString, como 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="f3c7b-116">Os detalhes para os recursos estão incluídos abaixo.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-116">Details for the features are included below.</span></span>


## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="f3c7b-117">Identificação de uma versão de script como um pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="f3c7b-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="f3c7b-118">O suporte do PowerShellGet para as versões de pré-lançamento é mais simples para os scripts do que para os módulos.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span>
<span data-ttu-id="f3c7b-119">O controle de versão do script é compatível apenas com o PowerShellGet. Portanto, não há nenhum problema de compatibilidade causado ao adicionar a cadeia de caracteres de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span>
<span data-ttu-id="f3c7b-120">Para identificar um script na Galeria do PowerShell como uma versão de pré-lançamento, adicione um sufixo de pré-lançamento a uma cadeia de caracteres de versão formatada adequadamente nos metadados do script.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="f3c7b-121">Uma seção de exemplo de um manifesto de script com uma versão de pré-lançamento seria semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="f3c7b-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>
```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

<span data-ttu-id="f3c7b-122">Para usar um sufixo de pré-lançamento, a cadeia de caracteres de versão deve atender aos seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="f3c7b-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

* <span data-ttu-id="f3c7b-123">Um sufixo de pré-lançamento só poderá ser especificado quando a versão tiver três segmentos para Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="f3c7b-124">Ela é alinhada ao SemVer v1.0.0</span><span class="sxs-lookup"><span data-stu-id="f3c7b-124">This aligns with SemVer v1.0.0</span></span>
* <span data-ttu-id="f3c7b-125">O sufixo de pré-lançamento é uma cadeia de caracteres que começa com um hífen e pode conter ASCII alfanuméricos [0-9A-Za-z-]</span><span class="sxs-lookup"><span data-stu-id="f3c7b-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
* <span data-ttu-id="f3c7b-126">Somente as cadeias de caracteres de pré-lançamento SemVer v1.0.0 são compatíveis no momento, portanto o sufixo de pré-lançamento __não deve__ conter um ponto ou + [. +], que é permitido no SemVer 2.0</span><span class="sxs-lookup"><span data-stu-id="f3c7b-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix __must not__ contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
* <span data-ttu-id="f3c7b-127">Alguns exemplos de cadeias de caracteres PrereleaseString compatíveis são: -alpha, -alpha1, -BETA, -update20171020</span><span class="sxs-lookup"><span data-stu-id="f3c7b-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="f3c7b-128">__Impacto na versão de pré-lançamento sobre a ordem de classificação e nas pastas de instalação__</span><span class="sxs-lookup"><span data-stu-id="f3c7b-128">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="f3c7b-129">A ordem de classificação é alterada ao usar uma versão de pré-lançamento, que é importante ao publicar na Galeria do PowerShell e ao instalar scripts usando comandos do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span>
<span data-ttu-id="f3c7b-130">Se duas versões de scripts com o número de versão existirem, a ordem de classificação será baseada na parte da cadeia de caracteres após o hífen.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="f3c7b-131">Portanto, a versão 2.5.0-alpha é menor que a versão 2.5.0-beta, que é menor que a versão 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span>
<span data-ttu-id="f3c7b-132">Se dois scripts tiverem o mesmo número de versão e somente um tiver um PrereleaseString, o script __sem__ o sufixo de pré-lançamento será considerado como a versão pronta para produção e será classificado como uma versão maior do que a versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-132">If two scripts have the same version number, and only one has a PrereleaseString, the script __without__ the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span>
<span data-ttu-id="f3c7b-133">Por exemplo, ao comparar as versões 2.5.0 e 2.5.0-beta, a versão 2.5.0 será considerada a maior das duas.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="f3c7b-134">Ao publicar na Galeria do PowerShell, por padrão, a versão do script que está sendo publicado deverá ter uma versão maior do que qualquer versão previamente publicada na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>
<span data-ttu-id="f3c7b-135">Um editor pode atualizar a versão 2.5.0-alpha com 2.5.0-beta, ou com 2.5.0 (sem nenhum sufixo de pré-lançamento).</span><span class="sxs-lookup"><span data-stu-id="f3c7b-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="f3c7b-136">Localização e aquisição de itens de pré-lançamento usando os comandos do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f3c7b-136">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="f3c7b-137">Para lidar com os itens de pré-lançamento usando os comandos PowerShellGet Find-Script, Install-Script, Update-Script e Save-Script, é necessário adicionar o sinalizador -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-137">Dealing with prerelease items using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span>
<span data-ttu-id="f3c7b-138">Se -AllowPrerelease for especificado, os itens de pré-lançamento serão incluídos se estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-138">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span>
<span data-ttu-id="f3c7b-139">Se o sinalizador -AllowPrerelease não for especificado, os itens de pré-lançamento não serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-139">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="f3c7b-140">As únicas exceções a isso nos comandos do script PowerShellGet são Get-InstalledScript, e alguns casos com Uninstall-Script.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

* <span data-ttu-id="f3c7b-141">Get-InstalledScript sempre mostrará as informações de pré-lançamento automaticamente na cadeia de caracteres de versão, se estiver presente.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
* <span data-ttu-id="f3c7b-142">Por padrão, o Uninstall-Script desinstalará a versão mais recente de um script se __nenhuma versão__ for especificada.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-142">Uninstall-Script will by default uninstall the most recent version of a script, if __no version__ is specified.</span></span> <span data-ttu-id="f3c7b-143">Esse comportamento não mudou.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-143">That behavior has not changed.</span></span> <span data-ttu-id="f3c7b-144">No entanto, se uma versão de pré-lançamento for especificada usando -RequiredVersion, -AllowPrerelease será necessário.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-144">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="f3c7b-145">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f3c7b-145">Examples</span></span>
```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

<span data-ttu-id="f3c7b-146">Uninstall-Script removerá a versão atual de um script quando -RequiredVersion não for fornecido.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="f3c7b-147">Se -RequiredVersion for especificado e for uma versão de pré-lançamento, -AllowPrerelease deverá ser adicionado ao comando.</span><span class="sxs-lookup"><span data-stu-id="f3c7b-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage


```



## <a name="more-details"></a><span data-ttu-id="f3c7b-148">Mais detalhes</span><span class="sxs-lookup"><span data-stu-id="f3c7b-148">More details</span></span>
### <a name="prerelease-module-versionsmoduleprereleasemodulemd"></a>[<span data-ttu-id="f3c7b-149">Versões de pré-lançamento do módulo</span><span class="sxs-lookup"><span data-stu-id="f3c7b-149">Prerelease Module Versions</span></span>](../module/PrereleaseModule.md)
### <a name="find-scriptpsgetfind-scriptmd"></a>[<span data-ttu-id="f3c7b-150">Find-script</span><span class="sxs-lookup"><span data-stu-id="f3c7b-150">Find-script</span></span>](./psget_find-script.md)
### <a name="install-scriptpsgetinstall-scriptmd"></a>[<span data-ttu-id="f3c7b-151">Install-script</span><span class="sxs-lookup"><span data-stu-id="f3c7b-151">Install-script</span></span>](./psget_install-script.md)
### <a name="save-scriptpsgetsave-scriptmd"></a>[<span data-ttu-id="f3c7b-152">Save-script</span><span class="sxs-lookup"><span data-stu-id="f3c7b-152">Save-script</span></span>](./psget_save-script.md)
### <a name="update-scriptpsgetupdate-scriptmd"></a>[<span data-ttu-id="f3c7b-153">Update-script</span><span class="sxs-lookup"><span data-stu-id="f3c7b-153">Update-script</span></span>](./psget_update-script.md)
### <a name="get-installedscriptpsgetget-installedscriptmd"></a>[<span data-ttu-id="f3c7b-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="f3c7b-154">Get-Installedscript</span></span>](./psget_get-installedscript.md)
### <a name="uninstall-scriptpsgetuninstall-scriptmd"></a>[<span data-ttu-id="f3c7b-155">UnInstall-script</span><span class="sxs-lookup"><span data-stu-id="f3c7b-155">UnInstall-script</span></span>](./psget_uninstall-script.md)