---
ms.date: 09/26/2017
contributor: keithb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Versões de pré-lançamento do módulo
ms.openlocfilehash: e663a42092556ef1c43a7cf236616bf420171af6
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="ff0d1-103">Versões de pré-lançamento do módulo</span><span class="sxs-lookup"><span data-stu-id="ff0d1-103">Prerelease Module Versions</span></span>

<span data-ttu-id="ff0d1-104">Começando com a versão 1.6.0, o PowerShellGet e a Galeria do PowerShell são compatíveis com versões de marcação superiores a 1.0.0 como um pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="ff0d1-105">Antes desse recurso, os itens de pré-lançamento eram limitados a ter uma versão que começasse com 0.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="ff0d1-106">A meta desses recursos é oferecer maior compatibilidade com a convenção de versão [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html), sem perder a compatibilidade com o PowerShell versão 3 e superiores ou com as versões existentes do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="ff0d1-107">Este tópico se concentra nos recursos específicos do módulo.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="ff0d1-108">Os recursos equivalentes para scripts estão no tópico [Versões de pré-lançamento dos scripts](script-prerelease-support.md).</span><span class="sxs-lookup"><span data-stu-id="ff0d1-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="ff0d1-109">Ao usar esses recursos, os editores podem identificar um módulo ou um script como a versão 2.5.0-alpha e, então, lançar uma versão 2.5.0 pronta para produção, que substitui a versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="ff0d1-110">Em um nível alto, os recursos de pré-lançamento do módulo incluem:</span><span class="sxs-lookup"><span data-stu-id="ff0d1-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="ff0d1-111">A adição de uma cadeia de caracteres de pré-lançamento na seção PSData do manifesto do módulo identifica o módulo como uma versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="ff0d1-112">Quando o módulo é publicado na Galeria do PowerShell, esses dados são extraídos do manifesto e usados para identificar os itens de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="ff0d1-113">A aquisição dos itens de pré-lançamento requer a adição do sinalizador -AllowPrerelease aos comandos Find-Module, Install-Module, Update-Module e Save-Module do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Module, Install-Module, Update-Module, and Save-Module.</span></span> <span data-ttu-id="ff0d1-114">Se o sinalizador não for especificado, os itens de pré-lançamento não serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="ff0d1-115">As versões de módulo exibidas pelos comandos Find-Module, Get-InstalledModule e na Galeria do PowerShell serão exibidas como uma única cadeia de caracteres com a cadeia de caracteres de pré-lançamento anexada, como em 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-115">Module versions displayed by Find-Module, Get-InstalledModule, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="ff0d1-116">Os detalhes para os recursos estão incluídos abaixo.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-116">Details for the features are included below.</span></span>

<span data-ttu-id="ff0d1-117">Essas alterações não afetam o suporte de versão do módulo que é criado no PowerShell, e são compatíveis com o PowerShell 3.0, 4.0 e 5.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="ff0d1-118">Identificação de uma versão de módulo como uma versão de pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="ff0d1-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="ff0d1-119">O suporte para as versões de pré-lançamento do PowerShellGet exige o uso de dois campos no manifesto de módulo:</span><span class="sxs-lookup"><span data-stu-id="ff0d1-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="ff0d1-120">O ModuleVersion incluído no manifesto de módulo deverá ser uma versão de três partes se uma versão de pré-lançamento for usada, e deverá estar em conformidade com o controle de versão existente do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="ff0d1-121">O formato da versão seria A.B.C, em que A, B e C são todos os números inteiros.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="ff0d1-122">A cadeia de caracteres de pré-lançamento é especificada no manifesto de módulo, na seção PSData de PrivateData.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="ff0d1-123">A seguir estão os requisitos detalhados na cadeia de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="ff0d1-124">Uma seção de exemplo de um manifesto de módulo que define um módulo como uma versão de pré-lançamento seria semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="ff0d1-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="ff0d1-125">Os requisitos detalhados para a cadeia de caracteres de pré-lançamento são:</span><span class="sxs-lookup"><span data-stu-id="ff0d1-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="ff0d1-126">A cadeia de caracteres de pré-lançamento só poderá ser especificada quando o ModuleVersion tiver três segmentos para Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="ff0d1-127">Ela é alinhada ao SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="ff0d1-128">Um hífen é o delimitador entre o número de build e a cadeia de caracteres de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="ff0d1-129">Um hífen pode ser incluído na cadeia de pré-lançamento apenas como o primeiro caractere.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="ff0d1-130">A cadeia de caracteres de pré-lançamento pode conter somente ASCII alfanuméricos [0-9A-Za-z-].</span><span class="sxs-lookup"><span data-stu-id="ff0d1-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="ff0d1-131">Uma prática recomendada é iniciar a cadeia de caracteres de pré-lançamento com um caractere alfabético, pois será mais fácil de identificar que se trata de uma versão de pré-lançamento ao examinar uma lista de itens.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of items.</span></span>
- <span data-ttu-id="ff0d1-132">Somente as cadeias de caracteres SemVer v1.0.0 são compatíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="ff0d1-133">A cadeia de caracteres de pré-lançamento __não deve__ conter um ponto ou + [.+], que é permitido no SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-133">Prerelease string __must not__ contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="ff0d1-134">Alguns exemplos de cadeias de caracteres de pré-lançamento compatíveis são: -alpha, -alpha1, -BETA, -update20171020</span><span class="sxs-lookup"><span data-stu-id="ff0d1-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="ff0d1-135">__Impacto na versão de pré-lançamento sobre a ordem de classificação e nas pastas de instalação__</span><span class="sxs-lookup"><span data-stu-id="ff0d1-135">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="ff0d1-136">A ordem de classificação é alterada ao usar uma versão de pré-lançamento, que é importante ao publicar na Galeria do PowerShell e ao instalar módulos usando comandos do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="ff0d1-137">Se a cadeia de caracteres de pré-lançamento for especificada para dois módulos, a ordem de classificação será baseada na parte da cadeia de caracteres após o hífen.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="ff0d1-138">Portanto, a versão 2.5.0-alpha é menor que a versão 2.5.0-beta, que é menor que a versão 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="ff0d1-139">Se dois módulos tiverem o mesmo ModuleVersion e somente um tiver uma cadeia de caracteres de pré-lançamento, o módulo sem a cadeia de caracteres de pré-lançamento será considerado como a versão pronta para produção e será classificado como uma versão maior do que a versão de pré-lançamento (que inclui a cadeia de caracteres de pré-lançamento).</span><span class="sxs-lookup"><span data-stu-id="ff0d1-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="ff0d1-140">Por exemplo, ao comparar as versões 2.5.0 e 2.5.0-beta, a versão 2.5.0 será considerada a maior das duas.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="ff0d1-141">Ao publicar na Galeria do PowerShell, por padrão a versão do módulo que está sendo publicado deverá ter uma versão maior do que qualquer versão previamente publicada na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="ff0d1-142">Localização e aquisição de itens de pré-lançamento usando os comandos do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="ff0d1-142">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="ff0d1-143">Para lidar com os itens de pré-lançamento usando os comandos PowerShellGet Find-Module, Install-Module, Update-Module e Save-Module, é necessário adicionar o sinalizador -AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-143">Dealing with prerelease items using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="ff0d1-144">Se -AllowPrerelease for especificado, os itens de pré-lançamento serão incluídos se estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-144">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="ff0d1-145">Se o sinalizador -AllowPrerelease não for especificado, os itens de pré-lançamento não serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-145">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="ff0d1-146">As únicas exceções a isso nos comandos do módulo PowerShellGet são Get-InstalledModule e alguns casos com Uninstall-Module.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="ff0d1-147">Get-InstalledModule sempre mostrará as informações de pré-lançamento automaticamente na cadeia de caracteres de versão para os módulos.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="ff0d1-148">Por padrão, o Uninstall-Module desinstalará a versão mais recente de um módulo se __nenhuma versão__ for especificada.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="ff0d1-149">Esse comportamento não mudou.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-149">That behavior has not changed.</span></span> <span data-ttu-id="ff0d1-150">No entanto, se uma versão de pré-lançamento for especificada usando -RequiredVersion, -AllowPrerelease será necessário.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="ff0d1-151">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ff0d1-151">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="ff0d1-152">Não há compatibilidade para a instalação lado a lado das versões de um módulo que diferem apenas devido à versão de pré-lançamento especificada.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-152">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="ff0d1-153">Ao instalar um módulo usando o PowerShellGet, versões diferentes do mesmo módulo serão instaladas lado a lado com a criação de um nome de pasta usando o ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-153">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="ff0d1-154">O ModuleVersion, sem a cadeia de caracteres de pré-lançamento, é usado para o nome da pasta.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-154">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="ff0d1-155">Se um usuário instalar MyModule versão 2.5.0-alpha, ele será instalado na pasta MyModule\2.5.0.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-155">If a user installs MyModule version 2.5.0-alpha, it will be installed to the MyModule\2.5.0 folder.</span></span> <span data-ttu-id="ff0d1-156">Se o usuário instalar a versão 2.5.0-beta, ela __substituirá__ o conteúdo da pasta MyModule\2.5.0.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-156">If the user then installs 2.5.0-beta, the 2.5.0-beta version will __over-write__ the contents of the folder MyModule\2.5.0.</span></span> <span data-ttu-id="ff0d1-157">Uma vantagem dessa abordagem é que não é necessário desinstalar a versão de pré-lançamento depois de instalar a versão pronta para produção.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-157">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="ff0d1-158">O exemplo a seguir mostra o que esperar:</span><span class="sxs-lookup"><span data-stu-id="ff0d1-158">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="ff0d1-159">O Uninstall-Module removerá a versão mais recente de um módulo quando -RequiredVersion não for fornecido.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-159">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="ff0d1-160">Se -RequiredVersion for especificado e for uma versão de pré-lançamento, -AllowPrerelease deverá ser adicionado ao comando.</span><span class="sxs-lookup"><span data-stu-id="ff0d1-160">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```

## <a name="more-details"></a><span data-ttu-id="ff0d1-161">Mais detalhes</span><span class="sxs-lookup"><span data-stu-id="ff0d1-161">More details</span></span>

- [<span data-ttu-id="ff0d1-162">Versões de pré-lançamento do Script</span><span class="sxs-lookup"><span data-stu-id="ff0d1-162">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="ff0d1-163">Find-Module</span><span class="sxs-lookup"><span data-stu-id="ff0d1-163">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="ff0d1-164">Install-Module</span><span class="sxs-lookup"><span data-stu-id="ff0d1-164">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="ff0d1-165">Save-Module</span><span class="sxs-lookup"><span data-stu-id="ff0d1-165">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="ff0d1-166">Update-Module</span><span class="sxs-lookup"><span data-stu-id="ff0d1-166">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="ff0d1-167">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="ff0d1-167">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="ff0d1-168">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="ff0d1-168">UnInstall-Module</span></span>](/powershell/gallery/psget/module/psget_uninstall-module)