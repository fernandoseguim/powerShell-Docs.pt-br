---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Uninstall-Module
ms.openlocfilehash: 90f26e64a8a6bc95faf444b1d3ce82a8e3bbefc1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-module"></a><span data-ttu-id="a335b-103">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="a335b-103">Uninstall-Module</span></span>

<span data-ttu-id="a335b-104">Desinstala um módulo que foi instalado usando cmdlets do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="a335b-104">Uninstalls a module which was installed using PowerShellGet cmdlets.</span></span>

## <a name="description"></a><span data-ttu-id="a335b-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="a335b-105">Description</span></span>

<span data-ttu-id="a335b-106">O cmdlet Uninstall-Module desinstala o módulo especificado do computador local.</span><span class="sxs-lookup"><span data-stu-id="a335b-106">The Uninstall-Module cmdlet uninstalls the specified module from the local computer.</span></span>
<span data-ttu-id="a335b-107">Não será possível desinstalar um módulo se outros módulos tiverem dependência dele.</span><span class="sxs-lookup"><span data-stu-id="a335b-107">You cannot uninstall a module if some other modules have a dependency on it.</span></span>
<span data-ttu-id="a335b-108">O cmdlet Uninstall-Module também valida se o módulo que está sendo desinstalado está em uso ou não.</span><span class="sxs-lookup"><span data-stu-id="a335b-108">The Uninstall-Module cmdlets also validates if the module being uninstalled is in-use or not.</span></span> <span data-ttu-id="a335b-109">Um erro será gerado se o módulo estiver em uso.</span><span class="sxs-lookup"><span data-stu-id="a335b-109">An error will be thrown if the module is in use.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="a335b-110">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="a335b-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Uninstall-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="a335b-111">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="a335b-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="a335b-112">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="a335b-112">Uninstall-Module</span></span>](http://go.microsoft.com/fwlink/?LinkId=526864)


## <a name="example-commands"></a><span data-ttu-id="a335b-113">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="a335b-113">Example commands</span></span>

###  <a name="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget"></a><span data-ttu-id="a335b-114">Execute o cmdlet Uninstall-Module para desinstalar um módulo que foi instalado usando o PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="a335b-114">Run the Uninstall-Module cmdlet to uninstall a module that you installed by using PowerShellGet.</span></span>
<span data-ttu-id="a335b-115">Caso qualquer outro módulo dependa do módulo que deseja excluir, o PowerShellGet gerará um erro.</span><span class="sxs-lookup"><span data-stu-id="a335b-115">If any other module depends on the module that you want to delete, PowerShellGet throws an error.</span></span>
```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

### <a name="uninstalling-a-module-when-some-other-modules-have-a-dependency-on-it"></a><span data-ttu-id="a335b-116">Desinstalando um módulo quando outros módulos têm dependência dele.</span><span class="sxs-lookup"><span data-stu-id="a335b-116">Uninstalling a module when some other modules have a dependency on it.</span></span>

```powershell
Uninstall-Module SnippetPx

PackageManagement\Uninstall-Package : The module 'SnippetPx' of version '1.0.5.18' in module base folder 'C:\ProgramFiles\WindowsPowerShell\Modules\SnippetPx\1.0.5.18' cannot be uninstalled, because one or more other modules 'TypePx' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'SnippetPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.3\PSModule.psm1:1803 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.Pac
   kageManagement.Cmdlets.UninstallPackage
```

### <a name="you-can-override-this-by-specify--force-option-on-uninstall-module-cmdlet"></a><span data-ttu-id="a335b-117">Você pode substituir isso especificando a opção -Force no cmdlet Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="a335b-117">You can override this by specify -Force option on Uninstall-Module cmdlet</span></span>
<span data-ttu-id="a335b-118">**OBSERVAÇÃO:** esta não é uma prática recomendada.</span><span class="sxs-lookup"><span data-stu-id="a335b-118">**NOTE:** This is not a recommended practice.</span></span> <span data-ttu-id="a335b-119">Outros módulos serão interrompidos com esta ação.</span><span class="sxs-lookup"><span data-stu-id="a335b-119">Other modules will break with this action.</span></span>

```powershell
Uninstall-Module SnippetPx -Force
```

### <a name="uninstall-a-module-which-is-already-in-use"></a><span data-ttu-id="a335b-120">Desinstalar um módulo que já está em uso</span><span class="sxs-lookup"><span data-stu-id="a335b-120">Uninstall a module which is already in use</span></span>

```powershell
Get-InstalledModule TypePx,SnippetPx

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experi...
```

### <a name="uninstall-snippetpx-fails-due-to-the-dependent-module"></a><span data-ttu-id="a335b-121">A desinstalação de SnippetPx falha devido ao módulo dependente</span><span class="sxs-lookup"><span data-stu-id="a335b-121">Uninstall SnippetPx fails due to the dependent module</span></span>

```powershell
Uninstall-Module SnippetPx

PackageManagement\Uninstall-Package : The module 'SnippetPx' of version '1.0.5.18' in module base folder 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18' cannot be uninstalled, because one or more other modules 'TypePx'
are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'SnippetPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.Pac
   kageManagement.Cmdlets.UninstallPackage
```

### <a name="uninstall-typepx-then-uninstall-the-snippetpx"></a><span data-ttu-id="a335b-122">Desinstale TypePx e, depois, desinstale SnippetPx</span><span class="sxs-lookup"><span data-stu-id="a335b-122">Uninstall TypePx then uninstall the SnippetPx</span></span>

```powershell
Uninstall-Module TypePx
Uninstall-Module SnippetPx

WARNING: The version '1.0.5.18' of module 'SnippetPx' is currently in use. Retry the operation after closing the
applications.
PackageManagement\Uninstall-Package : Module 'SnippetPx' is in currently in use.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Packag
   e], Exception
    + FullyQualifiedErrorId : ModuleIsInUse,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.Uninstall
   Package
```


### <a name="for-a-module-name-which-is-not-installed-using-powershellget-cmdlets"></a><span data-ttu-id="a335b-123">Para um nome de módulo que não foi instalado usando cmdlets do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a335b-123">For a module name which is not installed using PowerShellGet cmdlets</span></span>

```powershell
Uninstall-Module SnipptPx

PackageManagement\Uninstall-Package : No match was found for the specified search criteria and module names 'SnipptPx'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1914 char:21
+ ...        $null = PackageManagement\Uninstall-Package @PSBoundParameters
+                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package]
   , Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```