---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Find-RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a><span data-ttu-id="46c61-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="46c61-103">Find-RoleCapability</span></span>

<span data-ttu-id="46c61-104">Localiza capacidades de função em módulos.</span><span class="sxs-lookup"><span data-stu-id="46c61-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="46c61-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="46c61-105">Description</span></span>
<span data-ttu-id="46c61-106">O cmdlet Find-RoleCapability localiza capacidades de função do PowerShell em módulos.</span><span class="sxs-lookup"><span data-stu-id="46c61-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="46c61-107">Find-RoleCapability faz pesquisas em módulos em repositórios registrados.</span><span class="sxs-lookup"><span data-stu-id="46c61-107">Find-RoleCapability searches modules in registered repositories.</span></span> <span data-ttu-id="46c61-108">Para cada capacidade de função localizada, esse cmdlet retorna um objeto PSGetRoleCapabilityInfo.</span><span class="sxs-lookup"><span data-stu-id="46c61-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="46c61-109">Você pode passar um objeto PSGetRoleCapabilityInfo para o cmdlet Install-Module para instalar o módulo que contém a capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="46c61-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="46c61-110">As capacidades de função do PowerShell definem quais comandos, aplicativos e assim por diante ficam disponíveis para um usuário em um ponto de extremidade do tipo JEA ("Administração Suficiente").</span><span class="sxs-lookup"><span data-stu-id="46c61-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="46c61-111">As capacidades de função são definidas por arquivos com uma extensão .psrc.</span><span class="sxs-lookup"><span data-stu-id="46c61-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="46c61-112">Find-RoleCapability pode filtrar segundo os parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="46c61-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="46c61-113">Esses parâmetros são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="46c61-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="46c61-114">Esses parâmetros de versão são permitidos apenas com o nome exclusivo do módulo, sem curingas.</span><span class="sxs-lookup"><span data-stu-id="46c61-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="46c61-115">Se o parâmetro RequiredVersion não for especificado, Find-RoleCapability retorna a versão mais recente do módulo que for igual ou maior que a versão mínima especificada ou a versão mais recente do módulo se nenhuma versão mínima tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="46c61-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="46c61-116">Se o parâmetro RequiredVersion for especificado, Find-RoleCapability retornará apenas a versão do módulo que corresponde exatamente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="46c61-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="46c61-117">Find-RoleCapability pode filtrar nos metadados do módulo com o parâmetro -Tag</span><span class="sxs-lookup"><span data-stu-id="46c61-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="46c61-118">Find-RoleCapability pode filtrar na linguagem de pesquisa específica do repositório com o parâmetro -Filter.</span><span class="sxs-lookup"><span data-stu-id="46c61-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="46c61-119">Find-RoleCapability pode filtrar módulos de todos ou de alguns dos repositórios registrados.</span><span class="sxs-lookup"><span data-stu-id="46c61-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="46c61-120">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="46c61-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="46c61-121">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="46c61-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="46c61-122">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="46c61-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="46c61-123">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="46c61-123">Example commands</span></span>
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

