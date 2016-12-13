---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: PackageManagement_cmdlets
ms.technology: powershell
ms.openlocfilehash: 954097f6f3516eb627902c126a70203818ef84db
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="packagemanagement-cmdlets"></a>Cmdlets do PackageManagement
Esse é o núcleo do PackageManagement para dar suporte ao SDII (descoberta, instalação e inventário) de software. Experimente os cmdlets para essas operações:
-   Find-Package
-   Find-PackageProvider
-   Get-Package
-   Get-PackageProvider
-   Get-PackageSource
-   Import-PackageProvider
-   Install-Package
-   Install-PackageProvider
-   Register-PackageSource
-   Save-Package
-   Set-PackageSource
-   Uninstall-Package
-   Unregister-PackageSource

Como o PackageManagement é um módulo PowerShell, é possível fazer o seguinte para atualizar o próprio PackageManagement:
```powershell
PS C:\> Install-Module PackageManagement –Force
```
Nesse caso, você terá de entrar novamente na sessão do PowerShell para alternar para a nova versão do PackageManagement.

## <a name="find-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890709aspx"></a>[Cmdlet Find-Package](https://technet.microsoft.com/en-us/library/dn890709.aspx)
Esse cmdlet permite a descoberta de pacotes de software em origens do pacote disponíveis usando provedores de pacote carregados.
```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -Provider PowerShellGet -Source PSGallery

# Find a package from a provider that is not yet installed
# This will bootstrap NuGet provider and then search for jquery package using NuGet
# with <http://www.nuget.org/api/v2/> as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676544aspx"></a>[Cmdlet Find-PackageProvider](https://technet.microsoft.com/en-us/library/mt676544.aspx)
O cmdlet Find-PackageProvider localiza provedores de PackageManagement correspondentes que estão disponíveis nas origens do pacote registrados no PowerShellGet. Esses são os provedores de pacote disponíveis para instalação com o cmdlet Install-PackageProvider. Por padrão, isso inclui os módulos disponíveis na Galeria do PowerShell com as marcas “PackageManagement” e “Provider”. 

Find-PackageProvider também localiza provedores do PackageManagement correspondentes disponíveis no repositório de blob do Azure de PackageManagement, em que podemos usar o provedor de inicializadores do PackageManagement para encontrar e instalá-los.
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"

#For machines without internet, you can download the nuget provider first, put it to you file share and then use the following to install the nuget provider (TP5 or later).

Find-PackageProvider -Source  C:\sharedfolder\Providers\
Install-PackageProvider -Source C:\sharedfolder\Providers\ -Name nuget -force
    
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890704aspx"></a>[Cmdlet Get-Package](https://technet.microsoft.com/en-us/library/dn890704.aspx)
Esse cmdlet retorna uma lista de todos os pacotes de software que foram instaladas usando o PackageManagement.
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[Cmdlet Get-PackageProvider](https://technet.microsoft.com/en-us/library/dn890703.aspx)
Provedores de pacote carregados e que estão prontos para ser usados no computador local podem ser inventariados usando o cmdlet.
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[Cmdlet Get-PackageSource](https://technet.microsoft.com/en-us/library/dn890705.aspx)
Esse cmdlet obtém uma lista de origens do pacote registrados para um provedor de pacote.
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[Cmdlet Import-PackageProvider](https://technet.microsoft.com/en-us/library/mt676545.aspx)
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

As of the Windows Server Technical Preview(TP5), Install-PackageProvider does install as well as import the provider. Hence after you run find-packageprovider and install-packageprovider, the provider should be ready to use 
```

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[ Cmdlet Install-Package](https://technet.microsoft.com/en-us/library/dn890711.aspx)

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

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[Cmdlet Install-PackageProvider](https://technet.microsoft.com/en-us/library/mt676543.aspx)
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

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[Cmdlet Register-PackageSource](https://technet.microsoft.com/en-us/library/dn890701.aspx)
Esse cmdlet adiciona uma origem do pacote para um provedor de pacote especificado.
Cada provedor do PackageManagement pode ter uma ou várias origens de software, ou repositórios. O PackageManagement fornece cmdlets do PowerShell para adicionar/remover/consultar a origem. Por exemplo, é possível registrar uma origem do pacote para o provedor do NuGet:
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[Cmdlet Save-Package](https://technet.microsoft.com/en-us/library/dn890708.aspx)
Esse cmdlet salva os pacotes no computador local sem instalá-los.
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[Cmdlet Set-PackageSource](https://technet.microsoft.com/en-us/library/dn890710.aspx)
Esse cmdlet altera as informações sobre uma origem do pacote existente. 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[Cmdlet Uninstall-Package](https://technet.microsoft.com/en-us/library/dn890702.aspx)
Esse cmdlet desinstala pacotes instalados no computador local.
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[Cmdlet Unregister-PackageSource](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```

