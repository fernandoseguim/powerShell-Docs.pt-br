---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: psget_get installedscript
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: f809c5c8f5a28c01c67ee4c4453ecca7796838c4

---

# Get-InstalledScript

Obtém os scripts instalados em um computador.

## Descrição

O cmdlet Get-InstalledScript obtém scripts do PowerShell instalados em um computador.

Para cada script instalado, Get-InstalledScript retorna um objeto PSRepositoryItemInfo que pode, opcionalmente, ser redirecionado para Uninstall-Script para desinstalar os scripts instalados.

- Get-InstalledScript pode filtrar os scripts instalados com base em parâmetros de versão e nome.
- Get-InstalledScript pode filtrar segundo os parâmetros de versão: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Esses parâmetros são mutuamente exclusivos, exceto MinmimumVersion e MaximumVersion.
  - Esses parâmetros de versão são permitidos apenas com o nome exclusivo do script, sem curingas.
  - Se o parâmetro RequiredVersion não for especificado, Get-InstalledScript retorna a versão mais recente do script instalado que for igual ou maior que a versão mínima especificada ou a versão mais recente do script se nenhuma versão mínima tiver sido especificada. 
  - Se o parâmetro RequiredVersion for especificado, Get-InstalledScript retorna apenas a versão do script instalado que corresponde exatamente à versão especificada.

## Sintaxe do cmdlet

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## Referência da ajuda online sobre cmdlets

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

## Comandos de exemplo

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




<!--HONumber=Oct16_HO2-->


