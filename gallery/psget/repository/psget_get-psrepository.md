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
# <a name="get-psrepository"></a><span data-ttu-id="a3d4c-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a3d4c-103">Get-PSRepository</span></span>

<span data-ttu-id="a3d4c-104">Obtém os repositórios registrados em um computador.</span><span class="sxs-lookup"><span data-stu-id="a3d4c-104">Gets the registered repositories on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="a3d4c-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3d4c-105">Description</span></span>

<span data-ttu-id="a3d4c-106">O cmdlet Get-PSRepository obtém repositórios do módulo do PowerShell que estão registrados para o usuário atual em um computador.</span><span class="sxs-lookup"><span data-stu-id="a3d4c-106">The Get-PSRepository cmdlet gets PowerShell module repositories that are registered for the current user on a computer.</span></span>

<span data-ttu-id="a3d4c-107">Para cada repositório registrado, Get-PSRepository retorna um objeto PSRepository que pode, opcionalmente, ser redirecionado para Unregister-PSRepository para cancelar o registro de um repositório registrado.</span><span class="sxs-lookup"><span data-stu-id="a3d4c-107">For each registered repository, Get-PSRepository returns a PSRepository object which can optionally be piped to Unregister-PSRepository for unregistering a registered repository.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="a3d4c-108">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3d4c-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="a3d4c-109">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="a3d4c-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="a3d4c-110">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a3d4c-110">Get-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517127)

## <a name="example-commands"></a><span data-ttu-id="a3d4c-111">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="a3d4c-111">Example commands</span></span>

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