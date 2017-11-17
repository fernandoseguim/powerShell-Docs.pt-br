---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Get-InstalledScript
ms.openlocfilehash: f35e57cdadd1448bd9032ab007d692003c4cf4a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="get-installedscript"></a><span data-ttu-id="d5876-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="d5876-103">Get-InstalledScript</span></span>

<span data-ttu-id="d5876-104">Obtém os scripts instalados em um computador.</span><span class="sxs-lookup"><span data-stu-id="d5876-104">Gets installed scripts on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="d5876-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5876-105">Description</span></span>

<span data-ttu-id="d5876-106">O cmdlet Get-InstalledScript obtém scripts do PowerShell instalados em um computador.</span><span class="sxs-lookup"><span data-stu-id="d5876-106">The Get-InstalledScript cmdlet gets installed PowerShell scripts on a computer.</span></span>

<span data-ttu-id="d5876-107">Para cada script instalado, Get-InstalledScript retorna um objeto PSRepositoryItemInfo que pode, opcionalmente, ser redirecionado para Uninstall-Script para desinstalar os scripts instalados.</span><span class="sxs-lookup"><span data-stu-id="d5876-107">For each installed script, Get-InstalledScript returns a PSRepositoryItemInfo object which can optionally be piped to Uninstall-Script for uninstalling the installed scripts.</span></span>

- <span data-ttu-id="d5876-108">Get-InstalledScript pode filtrar os scripts instalados com base em parâmetros de versão e nome.</span><span class="sxs-lookup"><span data-stu-id="d5876-108">Get-InstalledScript can filter installed scripts based on name, version parameters.</span></span>
- <span data-ttu-id="d5876-109">Get-InstalledScript pode filtrar segundo os parâmetros de versão: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="d5876-109">Get-InstalledScript can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="d5876-110">Esses parâmetros são mutuamente exclusivos, exceto MinmimumVersion e MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="d5876-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="d5876-111">Esses parâmetros de versão são permitidos apenas com o nome exclusivo do script, sem curingas.</span><span class="sxs-lookup"><span data-stu-id="d5876-111">These version parameters are allowed only with the single script name without any wildcards.</span></span>
  - <span data-ttu-id="d5876-112">Se o parâmetro RequiredVersion não for especificado, Get-InstalledScript retorna a versão mais recente do script instalado que for igual ou maior que a versão mínima especificada ou a versão mais recente do script se nenhuma versão mínima tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="d5876-112">If the RequiredVersion parameter is not specified, Get-InstalledScript returns the latest version of the installed script that is equal to or greater than the minimum version specified or the latest version of the script if no minimum version is specified.</span></span> 
  - <span data-ttu-id="d5876-113">Se o parâmetro RequiredVersion for especificado, Get-InstalledScript retorna apenas a versão do script instalado que corresponde exatamente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="d5876-113">If the RequiredVersion parameter is specified, Get-InstalledScript only returns the version of installed script that exactly matches the specified version.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="d5876-114">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="d5876-114">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="d5876-115">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="d5876-115">Cmdlet online help reference</span></span>

[<span data-ttu-id="d5876-116">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="d5876-116">Get-InstalledScript</span></span>](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a><span data-ttu-id="d5876-117">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="d5876-117">Example commands</span></span>

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```

