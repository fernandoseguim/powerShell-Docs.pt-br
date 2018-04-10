---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Find-Command
ms.openlocfilehash: 26ddf4824816db245131a0fc95b7d2a88bef8f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="find-command"></a><span data-ttu-id="fdf9b-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="fdf9b-103">Find-Command</span></span>

<span data-ttu-id="fdf9b-104">Localiza comandos do PowerShell em módulos.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="fdf9b-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdf9b-105">Description</span></span>
<span data-ttu-id="fdf9b-106">O cmdlet Find-Command localiza comandos do PowerShell, como cmdlets, aliases, funções e fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="fdf9b-107">Find-Command faz pesquisas em módulos em repositórios registrados.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="fdf9b-108">Para cada comando que localiza, esse cmdlet retorna um objeto PSGetCommandInfo.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="fdf9b-109">Você pode passar um objeto PSGetCommandInfo para o cmdlet Install-Module para instalar o módulo que contém o comando.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="fdf9b-110">Find-Command pode filtrar segundo os parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="fdf9b-111">Esses parâmetros são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="fdf9b-112">Esses parâmetros de versão são permitidos apenas com o nome exclusivo do módulo, sem curingas.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="fdf9b-113">Se o parâmetro RequiredVersion não for especificado, Find-Command retorna a versão mais recente do módulo que for igual ou maior que a versão mínima especificada ou a versão mais recente do módulo se nenhuma versão mínima tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="fdf9b-114">Se o parâmetro RequiredVersion for especificado, Find-Command retornará apenas a versão do módulo que corresponde exatamente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="fdf9b-115">Find-Command pode filtrar os metadados do módulo com o parâmetro -Tag</span><span class="sxs-lookup"><span data-stu-id="fdf9b-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="fdf9b-116">Find-Command pode filtrar a linguagem de pesquisa específica do repositório com o parâmetro -Filter.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="fdf9b-117">Find-Command pode filtrar módulos de todos ou de alguns dos repositórios registrados.</span><span class="sxs-lookup"><span data-stu-id="fdf9b-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="fdf9b-118">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="fdf9b-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="fdf9b-119">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="fdf9b-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="fdf9b-120">Find-Command</span><span class="sxs-lookup"><span data-stu-id="fdf9b-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="fdf9b-121">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="fdf9b-121">Example commands</span></span>
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```