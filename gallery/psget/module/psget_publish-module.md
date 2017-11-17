---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Publish-Module
ms.openlocfilehash: 53fca3d6756ebf698023152ce5b58b45eb0ef757
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="publish-module"></a><span data-ttu-id="3e4b4-103">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="3e4b4-103">Publish-Module</span></span>

<span data-ttu-id="3e4b4-104">Publica um módulo especificado do computador local em uma galeria online.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-104">Publishes a specified module from the local computer to an online gallery.</span></span>

## <a name="description"></a><span data-ttu-id="3e4b4-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e4b4-105">Description</span></span>

<span data-ttu-id="3e4b4-106">O cmdlet **Publish-Module** publica um módulo em uma galeria online baseada em NuGet usando uma chave de API, armazenada como parte do perfil do usuário na galeria.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-106">The **Publish-Module** cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="3e4b4-107">Você pode especificar o módulo a ser publicado usando o nome do módulo ou o caminho para a pasta que contém o módulo.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-107">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="3e4b4-108">Quando você especifica um módulo pelo nome, **Publish-Module** publica o primeiro módulo que seria encontrado executando `Get-Module -ListAvailable <Name>`.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-108">When you specify a module by name, **Publish-Module** publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="3e4b4-109">Se você especificar uma versão mínima de um módulo a ser publicado, **Publish-Module** publica o primeiro módulo com uma versão que seja maior ou igual à versão mínima que você especificou.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-109">If you specify a minimum version of a module to publish, **Publish-Module** publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="3e4b4-110">A publicação de um módulo requer metadados que são exibidos na página da galeria para o módulo.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-110">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="3e4b4-111">Os metadados necessários incluem o nome, a versão, a descrição e o autor do módulo.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-111">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="3e4b4-112">Embora a maioria dos metadados sejam obtidos do manifesto do módulo, alguns deles devem ser especificado nos parâmetros de **Publish-Module**, como *Tag, ReleaseNote, IconUri, ProjectUri* e *LicenseUri*, porque esses parâmetros correspondem a campos em uma galeria baseada em NuGet.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-112">Although most metadata is taken from the module manifest, some metadata must be specified in **Publish-Module** parameters, such as *Tag, ReleaseNote, IconUri, ProjectUri,* and *LicenseUri*, because these parameters match fields in a NuGet-based gallery.</span></span>

<span data-ttu-id="3e4b4-113">O parâmetro RequiredVersion permite que você especifique a versão exata de um módulo a ser publicado.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-113">The RequiredVersion parameter allows you to specify the exact version of a module to be published.</span></span>
<span data-ttu-id="3e4b4-114">O parâmetro Path também dá suporte ao caminho base do módulo com a pasta de versão.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-114">The Path parameter also supports the module base path with the version folder.</span></span>
<span data-ttu-id="3e4b4-115">O parâmetro de opção Force no cmdlet Publish-Module inicializa o NuGet.exe sem avisar.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-115">The Force switch parameter on Publish-Module cmdlet bootstraps the NuGet.exe without prompting.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="3e4b4-116">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e4b4-116">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Publish-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="3e4b4-117">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="3e4b4-117">Cmdlet online help reference</span></span>

[<span data-ttu-id="3e4b4-118">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="3e4b4-118">Publish-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398575)

## <a name="example-commands"></a><span data-ttu-id="3e4b4-119">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="3e4b4-119">Example commands</span></span>

```powershell
ContosoServer module with different versions to be published.
PS C:\\windows\\system32> Get-Module -Name ContosoServer -ListAvailable
Directory: C:\\Program Files\\WindowsPowerShell\\Modules
ModuleType Version Name ExportedCommands
---------- ------- ---- ----------------
Manifest 2.8 ContosoServer Get-ContosoServer
Manifest 2.0 ContosoServer Get-ContosoServer
Manifest 1.5 ContosoServer Get-ContosoServer
Manifest 1.0 ContosoServer Get-ContosoServer
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.0 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.5 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Path "C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0" -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
_------ ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
2.0 ContosoServer LocalRepo ContosoServer module
```

## <a name="publishing-a-module-with-dependencies"></a><span data-ttu-id="3e4b4-120">Publicando um módulo com dependências</span><span class="sxs-lookup"><span data-stu-id="3e4b4-120">Publishing a module with dependencies</span></span>

### <a name="create-a-module-with-dependencies-and-version-range-specified-in-requiredmodules-property-of-its-module-manifest"></a><span data-ttu-id="3e4b4-121">Crie um módulo com dependências e um intervalo de versão que são especificados na propriedade RequiredModules do manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-121">Create a module with dependencies and version range specified in RequiredModules property of its module manifest.</span></span>

<span data-ttu-id="3e4b4-122">**Observação:**</span><span class="sxs-lookup"><span data-stu-id="3e4b4-122">**Note:**</span></span>
  - <span data-ttu-id="3e4b4-123">\* tem suporte apenas em MaximumVersion e também deve estar no final da cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-123">\* is supported only in MaximumVersion and also it should be at the end of version string.</span></span> 
  - <span data-ttu-id="3e4b4-124">\* é substituído por 999999999 no objeto de versão.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-124">\* is replaced with 999999999 in the version object.</span></span>

```powershell
PS C:\windows\system32> $requiredModules = @( @{ModuleName = 'RequiredModule1'; ModuleVersion = '0.1'; MaximumVersion = '1.9'; }, @{ModuleName = 'RequiredModule2'; MaximumVersion = '1.*'; })

PS C:\windows\system32> cd C:\MyModules\ModuleWithDependencies

PS C:\MyModules\ModuleWithDependencies> New-ModuleManifest -Path .\ModuleWithDependencies.psd1 -ModuleVersion 1.0 -RequiredModules $requiredModules -Description 'ModuleWithDependencies demo module'
```

### <a name="publish-modulewithdependencies-module-with-dependencies-to-the-repository"></a><span data-ttu-id="3e4b4-125">Publique o módulo ModuleWithDependencies com dependências no repositório.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-125">Publish ModuleWithDependencies module with dependencies to the repository.</span></span>

```powershell
PS C:\MyModules\ModuleWithDependencies> Publish-Module -Path C:\MyModules\ModuleWithDependencies -Repository LocalRepo
```

### <a name="find-modulewithdependencies-module-with-its-dependencies-by-specifying--includedependencies"></a><span data-ttu-id="3e4b4-126">Encontre o módulo ModuleWithDependencies com suas dependências especificando -IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="3e4b4-126">Find ModuleWithDependencies module with its dependencies by specifying -IncludeDependencies</span></span>

```powershell
PS C:\MyModules\ModuleWithDependencies> Find-Module -Name ModuleWithDependencies -Repository LocalRepo -IncludeDependencies

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="install-the-modulewithdependencies-module-with-dependencies"></a><span data-ttu-id="3e4b4-127">Instale o módulo ModuleWithDependencies com dependências.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-127">Install the ModuleWithDependencies module with dependencies.</span></span>
<span data-ttu-id="3e4b4-128">Observe que os intervalos de versão são considerados durante a instalação de dependências.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-128">Note that version ranges are honored during the dependency installation.</span></span>

```powershell
PS C:\windows\system32> Get-InstalledModule
PS C:\windows\system32>
PS C:\windows\system32> Install-Module -Name ModuleWithDependencies -Repository LocalRepo
PS C:\windows\system32>
PS C:\windows\system32> Get-InstalledModule

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="contents-of-modulewithdependencies2-module-manifest-file"></a><span data-ttu-id="3e4b4-129">Conteúdo do arquivo de manifesto do módulo ModuleWithDependencies2</span><span class="sxs-lookup"><span data-stu-id="3e4b4-129">Contents of ModuleWithDependencies2 module manifest file</span></span>

```powershell
@{
# Version number of this module.
ModuleVersion = '2.0'
# ID used to uniquely identify this module
GUID = '0eae34da-99dd-4608-8d28-c614fe7b0841'
# Author of this module
Author = 'manikb'
# Company or vendor of this module
CompanyName = 'Unknown'
# Copyright statement for this module
Copyright = '(c) 2015 manikb. All rights reserved.'
# Description of the functionality provided by this module
Description = 'ModuleWithDependencies2 module'
# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @('RequiredModule1',
@{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'RequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'RequiredModule4'; ModuleVersion = '1.1'; MaximumVersion = '2.0'; },
@{ModuleName = 'RequiredModule5'; MaximumVersion = '1.5'; })
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @('NestedRequiredModule1',
@{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'NestedRequiredModule4'; ModuleVersion = '0.7'; MaximumVersion = '2.4'; },
@{ModuleName = 'NestedRequiredModule5'; MaximumVersion = '1.6'; },'ModuleWithDependencies2.psm1')
# Functions to export from this module
FunctionsToExport = '\*'
# Cmdlets to export from this module
CmdletsToExport = '\*'
# Variables to export from this module
VariablesToExport = '\*'
# Aliases to export from this module
AliasesToExport = '\*'
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
      # Tags applied to this module. These help with module discovery in online galleries.
      Tags = 'Tag1', 'Tag2', 'Tag-ModuleWithDependencies2-2.0'
      # A URL to the license for this module.
      LicenseUri = 'http://modulewithdependencies2.com/license'
      # A URL to the main website for this project.
      ProjectUri = 'http://modulewithdependencies2.com/'
      # A URL to an icon representing this module.
      IconUri = 'http://modulewithdependencies2.com/icon'
      # ReleaseNotes of this module
      ReleaseNotes = 'ModuleWithDependencies2 release notes'
    } # End of PSData hashtable
} # End of PrivateData hashtable
}
```


### <a name="external-dependencies"></a><span data-ttu-id="3e4b4-130">Dependências externas</span><span class="sxs-lookup"><span data-stu-id="3e4b4-130">External dependencies</span></span>
<span data-ttu-id="3e4b4-131">Algumas dependências de módulo podem ser gerenciadas externamente. Nesse caso, elas devem ser adicionadas à entrada ExternalModuleDependencies na seção PSData do manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-131">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>

<span data-ttu-id="3e4b4-132">Se "SnippetPx" não estiver disponível no repositório, o erro abaixo será gerado.</span><span class="sxs-lookup"><span data-stu-id="3e4b4-132">If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
```powershell
Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
```

