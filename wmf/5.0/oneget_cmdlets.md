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
# <a name="packagemanagement-cmdlets"></a>Cmdlets do PackageManagement

Esse é o núcleo do PackageManagement para dar suporte ao SDII (descoberta, instalação e inventário) de software. Experimente os cmdlets para essas operações:

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

Como o PackageManagement é um módulo PowerShell, é possível fazer o seguinte para atualizar o próprio PackageManagement:

```powershell
Install-Module PackageManagement –Force
```

Nesse caso, você terá de entrar novamente na sessão do PowerShell para alternar para a nova versão do PackageManagement.

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[Cmdlet Find-Package](/powershell/module/PackageManagement/Find-Package)

Esse cmdlet permite a descoberta de pacotes de software em origens do pacote disponíveis usando provedores de pacote carregados.

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

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[Cmdlet Find-PackageProvider](/powershell/module/PackageManagement/Find-PackageProvider)

O cmdlet `Find-PackageProvider` localiza provedores de PackageManagement correspondentes que estão disponíveis nas origens do pacote registrados no PowerShellGet. Esses são os provedores de pacote disponíveis para instalação com o cmdlet `Install-PackageProvider`. Por padrão, isso inclui os módulos disponíveis na Galeria do PowerShell com as marcas “PackageManagement” e “Provider”.

`Find-PackageProvider` também localiza provedores do PackageManagement correspondentes disponíveis no repositório de blob do Azure de PackageManagement, em que podemos usar o provedor de inicializadores do PackageManagement para encontrar e instalá-los.

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[Cmdlet Get-Package](/powershell/module/PackageManagement/Get-Package)

Esse cmdlet retorna uma lista de todos os pacotes de software que foram instaladas usando o PackageManagement.

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[Cmdlet Get-PackageProvider](/powershell/module/PackageManagement/Get-PackageProvider)

Provedores de pacote carregados e que estão prontos para ser usados no computador local podem ser inventariados usando o cmdlet.

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[Cmdlet Get-PackageSource](/powershell/module/PackageManagement/Get-PackageSource)

Esse cmdlet obtém uma lista de origens do pacote registrados para um provedor de pacote.

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[Cmdlet Import-PackageProvider](/powershell/module/PackageManagement/Import-PackageProvider)

Esse cmdlet adiciona provedores do pacote do Gerenciamento de Pacotes à sessão atual.

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

## <a name="-install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[ Cmdlet Install-Package](/powershell/module/PackageManagement/Install-Package)

Esse cmdlet permite a instalação de pacotes de software em origens do pacote disponíveis usando provedores de pacote carregados.

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[Cmdlet Install-PackageProvider](/powershell/module/PackageManagement/Install-PackageProvider)

Este cmdlet instala um ou mais provedores de pacote do Gerenciamento de Pacotes.

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

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[Cmdlet Register-PackageSource](/powershell/module/PackageManagement/Register-PackageSource)

Esse cmdlet adiciona uma origem do pacote para um provedor de pacote especificado.
Cada provedor do PackageManagement pode ter uma ou várias origens de software, ou repositórios. O PackageManagement fornece cmdlets do PowerShell para adicionar/remover/consultar a origem. Por exemplo, é possível registrar uma origem do pacote para o provedor do NuGet:

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[Cmdlet Save-Package](/powershell/module/PackageManagement/Save-Package)

Esse cmdlet salva os pacotes no computador local sem instalá-los.

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[Cmdlet Set-PackageSource](/powershell/module/PackageManagement/Set-PackageSource)

Esse cmdlet altera as informações sobre uma origem do pacote existente.

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[Cmdlet Uninstall-Package](/powershell/module/PackageManagement/Uninstall-Package)

Esse cmdlet desinstala pacotes instalados no computador local.

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[Cmdlet Unregister-PackageSource](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```