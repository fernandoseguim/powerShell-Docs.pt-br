---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Find-Module
ms.openlocfilehash: 03dff4454a31638df564568ef51eec158685c8e9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="find-module"></a>Find-Module
Localiza módulos de uma galeria online que correspondam a critérios especificados.

## <a name="description"></a>Descrição
Find-Module descobre os módulos de repositórios registrados que correspondem aos critérios especificados.
Para cada módulo encontrado, Find-Module retorna um objeto PSRepositoryItemInfo que pode, opcionalmente, ser redirecionado para Install-Module para instalar os módulos.

- Find-Module pode filtrar com base no conteúdo do módulo com os parâmetros -Command, -DscResource, -RoleCapability e -Includes.
- Find-Module pode filtrar segundo os parâmetros de versão: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Esses parâmetros são mutuamente exclusivos, exceto MinmimumVersion e MaximumVersion.
  - Esses parâmetros de versão são permitidos apenas com o nome exclusivo do módulo, sem curingas.
  - Se o parâmetro RequiredVersion não for especificado, Find-Module retorna a versão mais recente do módulo que for igual ou maior que a versão mínima especificada ou a versão mais recente do módulo se nenhuma versão mínima tiver sido especificada.
  - Se o parâmetro RequiredVersion for especificado, Find-Module retorna apenas a versão do módulo que corresponde exatamente à versão especificada.
- Find-Module pode filtrar nos metadados do módulo com o parâmetro -Tag
- Find-Module pode filtrar na linguagem de pesquisa específica do repositório com o parâmetro -Filter.
- Find-Module pode filtrar módulos de todos ou de alguns dos repositórios registrados.

## <a name="cmdlet-syntax"></a>Sintaxe do cmdlet
```powershell
Get-Command -Name Find-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referência da ajuda online sobre cmdlets

[Find-Module](http://go.microsoft.com/fwlink/?LinkID=398574)

## <a name="example-commands"></a>Comandos de exemplo
```powershell
# Find a specific module
Find-Module Azure

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.3.2      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management

# Find multiple modules
Find-Module Azure,AzureRM

# Find modules with wildcards in -Name
Find-Module -Name AzureRM*

# Find all versions of a module
Find-Module -Name PSReadline -AllVersions

# Find a module with -MinimumVersion.
# With MinimumVersion we can find a module whose version is greate than or equal to the specified MinimumVersion value.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12

# Find a module with MaximumVersion
Find-Module -Name PSReadline -MaximumVersion 1.0.0.13

# Find a module with both MinimumVersion and MaximumVersion range.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12 -MaximumVersion 1.0.0.13

# Find a module with exact version
Find-Module -Name AzureRM -RequiredVersion 1.3.2

# Find a module with a specific prerelease version
Find-Module -Name AzureRM -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a module from the specified repository
Find-Module -Name Contoso -Repository MyLocalRepo

# Find available modules from all registered repositories
Find-Module

# Find available modules from few registered repositories
Find-Module -Repository PSGallery,PrivatePSGallery

# Find a module along with its dependencies
Find-Module -Name AzureRM -IncludeDependencies

# Find all modules with Dsc resources
Find-Module -Includes DscResource

# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

# Find all modules with cmdlets
Find-Module -Includes Cmdlet

# Find all modules with functions
Find-Module -Includes Function

# Find all modules with Role Capabilities
Find-Module -Includes RoleCapability

# Find all modules with the specified Role Capability name
Find-Module -RoleCapability RoleCap1
Find-Module -RoleCapability RoleCap2 -Includes RoleCapability

# Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Cmdlet
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Function

# Find modules with -Filter based search. -Filter searches in description and names
Find-Module -Filter Cookbook
Find-Module -Filter RBAC
Find-Module -Filter 'App Domain' -Includes 'DscResource'

# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

# Properties of Find-Module returned object
Find-Module AzureRM.Profile | Format-List * -Force

Name                       : AzureRM.profile
Version                    : 1.0.8
Type                       : Module
Description                : Microsoft Azure PowerShell - Profile credential management cmdlets for Azure Resource
                             Manager
Author                     : Microsoft Corporation
CompanyName                : {elogeel, azure-sdk}
Copyright                  : Microsoft Corporation. All rights reserved.
PublishedDate              : 5/4/2016 9:40:33 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 : https://raw.githubusercontent.com/Azure/azure-powershell/dev/LICENSE.txt
ProjectUri                 : https://github.com/Azure/azure-powershell
IconUri                    :
Tags                       : {PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               : https://github.com/Azure/azure-powershell/blob/dev/ChangeLog.md
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {downloadCount, description, copyright, FileList...}

```