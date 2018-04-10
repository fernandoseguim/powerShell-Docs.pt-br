---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Get-PSRepository
ms.openlocfilehash: 97279a8ed0087c835fb924991484959cd7237016
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
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