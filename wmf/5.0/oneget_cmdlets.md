---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 2f05fe96ec792a31fabf3aff0f9e18b40178316c
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893181"
---
# <a name="packagemanagement-cmdlets"></a><span data-ttu-id="95b85-102">Cmdlets do PackageManagement</span><span class="sxs-lookup"><span data-stu-id="95b85-102">PackageManagement Cmdlets</span></span>

<span data-ttu-id="95b85-103">Esse é o núcleo do PackageManagement para dar suporte ao SDII (descoberta, instalação e inventário) de software.</span><span class="sxs-lookup"><span data-stu-id="95b85-103">This is the core of PackageManagement to support software discovery, installation, and inventory (SDII).</span></span> <span data-ttu-id="95b85-104">Experimente os cmdlets para essas operações:</span><span class="sxs-lookup"><span data-stu-id="95b85-104">Try out the cmdlets for these operations:</span></span>

- `Find-Package`
- `Find-PackageProvider`
- `Get-Package`
- `Get-PackageProvider`
- `Get-PackageSource`
- `Import-PackageProvider`
- `Install-Package`
- `Install-PackageProvider`
- `Register-PackageSource`
- `Save-Package`
- `Set-PackageSource`
- `Uninstall-Package`
- `Unregister-PackageSource`

<span data-ttu-id="95b85-105">Como o PackageManagement é um módulo PowerShell, é possível fazer o seguinte para atualizar o próprio PackageManagement:</span><span class="sxs-lookup"><span data-stu-id="95b85-105">As PackageManagement is a PowerShell module, you can do the following to update PackageManagement itself:</span></span>

```powershell
Install-Module PackageManagement –Force
```

<span data-ttu-id="95b85-106">Nesse caso, você terá de entrar novamente na sessão do PowerShell para alternar para a nova versão do PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="95b85-106">In this case, you will have to re-enter PowerShell session to switch to the new version of PackageManagement.</span></span>

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[<span data-ttu-id="95b85-107">Cmdlet Find-Package</span><span class="sxs-lookup"><span data-stu-id="95b85-107">Find-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Find-Package)

<span data-ttu-id="95b85-108">Esse cmdlet permite a descoberta de pacotes de software em origens do pacote disponíveis usando provedores de pacote carregados.</span><span class="sxs-lookup"><span data-stu-id="95b85-108">This cmdlet allows discovery of software packages in available package sources using loaded package providers.</span></span>

```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -ProviderName PowerShellGet -Source as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[<span data-ttu-id="95b85-109">Cmdlet Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="95b85-109">Find-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Find-PackageProvider)

<span data-ttu-id="95b85-110">O cmdlet `Find-PackageProvider` localiza provedores de PackageManagement correspondentes que estão disponíveis nas origens do pacote registrados no PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="95b85-110">The `Find-PackageProvider` cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span> <span data-ttu-id="95b85-111">Esses são os provedores de pacote disponíveis para instalação com o cmdlet `Install-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="95b85-111">These are package providers available for installation with the `Install-PackageProvider` cmdlet.</span></span> <span data-ttu-id="95b85-112">Por padrão, isso inclui os módulos disponíveis na Galeria do PowerShell com as marcas “PackageManagement” e “Provider”.</span><span class="sxs-lookup"><span data-stu-id="95b85-112">By default, this includes modules available in the PowerShell Gallery with the 'PackageManagement' and 'Provider' Tags.</span></span>

<span data-ttu-id="95b85-113">`Find-PackageProvider` também localiza provedores do PackageManagement correspondentes disponíveis no repositório de blob do Azure de PackageManagement, em que podemos usar o provedor de inicializadores do PackageManagement para encontrar e instalá-los.</span><span class="sxs-lookup"><span data-stu-id="95b85-113">`Find-PackageProvider` also finds matching PackageManagement providers that are available in the PackageManagement azure blob store where we use the PackageManagement boostrapper provider for finding and installing them.</span></span>

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[<span data-ttu-id="95b85-114">Cmdlet Get-Package</span><span class="sxs-lookup"><span data-stu-id="95b85-114">Get-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Get-Package)

<span data-ttu-id="95b85-115">Esse cmdlet retorna uma lista de todos os pacotes de software que foram instaladas usando o PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="95b85-115">This cmdlet returns a list of all software packages that have been installed using PackageManagement.</span></span>

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[<span data-ttu-id="95b85-116">Cmdlet Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="95b85-116">Get-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Get-PackageProvider)

<span data-ttu-id="95b85-117">Provedores de pacote carregados e que estão prontos para ser usados no computador local podem ser inventariados usando o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95b85-117">Package providers that are loaded and ready to be used on the local machine can be inventoried by using the cmdlet.</span></span>

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[<span data-ttu-id="95b85-118">Cmdlet Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="95b85-118">Get-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Get-PackageSource)

<span data-ttu-id="95b85-119">Esse cmdlet obtém uma lista de origens do pacote registrados para um provedor de pacote.</span><span class="sxs-lookup"><span data-stu-id="95b85-119">This cmdlet gets a list of package sources that are registered for a package provider.</span></span>

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[<span data-ttu-id="95b85-120">Cmdlet Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="95b85-120">Import-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Import-PackageProvider)

<span data-ttu-id="95b85-121">Esse cmdlet adiciona provedores do pacote do Gerenciamento de Pacotes à sessão atual.</span><span class="sxs-lookup"><span data-stu-id="95b85-121">This cmdlet adds Package Management package providers to the current session.</span></span>

```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

## <a name="-install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[<span data-ttu-id="95b85-122"> Cmdlet Install-Package</span><span class="sxs-lookup"><span data-stu-id="95b85-122"> Install-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Install-Package)

<span data-ttu-id="95b85-123">Esse cmdlet permite a instalação de pacotes de software em origens do pacote disponíveis usando provedores de pacote carregados.</span><span class="sxs-lookup"><span data-stu-id="95b85-123">This cmdlet allows installation of software packages in available package sources using loaded package providers.</span></span>

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[<span data-ttu-id="95b85-124">Cmdlet Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="95b85-124">Install-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Install-PackageProvider)

<span data-ttu-id="95b85-125">Este cmdlet instala um ou mais provedores de pacote do Gerenciamento de Pacotes.</span><span class="sxs-lookup"><span data-stu-id="95b85-125">This cmdlet installs one or more Package Management package providers.</span></span>

```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[<span data-ttu-id="95b85-126">Cmdlet Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="95b85-126">Register-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Register-PackageSource)

<span data-ttu-id="95b85-127">Esse cmdlet adiciona uma origem do pacote para um provedor de pacote especificado.</span><span class="sxs-lookup"><span data-stu-id="95b85-127">This cmdlet adds a package source for a specified package provider.</span></span>
<span data-ttu-id="95b85-128">Cada provedor do PackageManagement pode ter uma ou várias origens de software, ou repositórios.</span><span class="sxs-lookup"><span data-stu-id="95b85-128">Each PackageManagement provider may have one or multiple software sources, or repositories.</span></span> <span data-ttu-id="95b85-129">O PackageManagement fornece cmdlets do PowerShell para adicionar/remover/consultar a origem.</span><span class="sxs-lookup"><span data-stu-id="95b85-129">PackageManagement provides PowerShell cmdlets to add/remove/query the source.</span></span> <span data-ttu-id="95b85-130">Por exemplo, é possível registrar uma origem do pacote para o provedor do NuGet:</span><span class="sxs-lookup"><span data-stu-id="95b85-130">For example, you can register a package source for the NuGet provider:</span></span>

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[<span data-ttu-id="95b85-131">Cmdlet Save-Package</span><span class="sxs-lookup"><span data-stu-id="95b85-131">Save-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Save-Package)

<span data-ttu-id="95b85-132">Esse cmdlet salva os pacotes no computador local sem instalá-los.</span><span class="sxs-lookup"><span data-stu-id="95b85-132">This cmdlet saves packages to the local computer without installing them.</span></span>

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[<span data-ttu-id="95b85-133">Cmdlet Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="95b85-133">Set-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Set-PackageSource)

<span data-ttu-id="95b85-134">Esse cmdlet altera as informações sobre uma origem do pacote existente.</span><span class="sxs-lookup"><span data-stu-id="95b85-134">This cmdlet changes information about an existing package source.</span></span>

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[<span data-ttu-id="95b85-135">Cmdlet Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="95b85-135">Uninstall-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Uninstall-Package)

<span data-ttu-id="95b85-136">Esse cmdlet desinstala pacotes instalados no computador local.</span><span class="sxs-lookup"><span data-stu-id="95b85-136">This cmdlet uninstalls packages installed on the local computer.</span></span>

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[<span data-ttu-id="95b85-137">Cmdlet Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="95b85-137">Unregister-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```