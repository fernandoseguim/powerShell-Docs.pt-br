---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Get-PSRepository
ms.openlocfilehash: 96f87428312c233757aa5fcae405a192aadff385
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="get-psrepository" class="xliff"></a>
# Get-PSRepository

Obtém os repositórios registrados em um computador.

<a id="description" class="xliff"></a>
## Descrição

O cmdlet Get-PSRepository obtém repositórios do módulo do PowerShell que estão registrados para o usuário atual em um computador.

Para cada repositório registrado, Get-PSRepository retorna um objeto PSRepository que pode, opcionalmente, ser redirecionado para Unregister-PSRepository para cancelar o registro de um repositório registrado.

<a id="cmdlet-syntax" class="xliff"></a>
## Sintaxe do cmdlet
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Referência da ajuda online sobre cmdlets

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

<a id="example-commands" class="xliff"></a>
## Comandos de exemplo

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

