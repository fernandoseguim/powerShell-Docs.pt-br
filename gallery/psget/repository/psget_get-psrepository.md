---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: psget_get psrepository
ms.technology: powershell
ms.openlocfilehash: b1d5172232f0c2916382b6c35093a238f6b2cb4d
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="get-psrepository"></a>Get-PSRepository

Obtém os repositórios registrados em um computador.

## <a name="description"></a>Descrição

O cmdlet Get-PSRepository obtém repositórios do módulo do PowerShell que estão registrados para o usuário atual em um computador.

Para cada repositório registrado, Get-PSRepository retorna um objeto PSRepository que pode, opcionalmente, ser redirecionado para Unregister-PSRepository para cancelar o registro de um repositório registrado.

## <a name="cmdlet-syntax"></a>Sintaxe do cmdlet
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referência da ajuda online sobre cmdlets

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

## <a name="example-commands"></a>Comandos de exemplo

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```

