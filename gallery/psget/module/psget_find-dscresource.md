---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Find-DscResource
ms.openlocfilehash: 522a44e25c57a7dd75a098a1f34e53e74d96f4a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="find-dscresource"></a><span data-ttu-id="eac82-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="eac82-103">Find-DscResource</span></span>

<span data-ttu-id="eac82-104">Localiza Recursos de DSC nos módulos.</span><span class="sxs-lookup"><span data-stu-id="eac82-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="eac82-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="eac82-105">Description</span></span>

<span data-ttu-id="eac82-106">O cmdlet Find-DscResource localiza recursos de [DSC (Configuração de Estado Desejado)](https://msdn.microsoft.com/PowerShell/dsc/overview) contidos em módulos que correspondam aos critérios especificados dos repositórios registrados.</span><span class="sxs-lookup"><span data-stu-id="eac82-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="eac82-107">Para cada módulo que localiza, o cmdlet Find-DscResource retorna um objeto PSGetDscResourceInfo que você pode redirecionar para Install-Module para instalar os módulos que contêm os recursos que esse cmdlet retorna.</span><span class="sxs-lookup"><span data-stu-id="eac82-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="eac82-108">A DSC é uma nova plataforma de gerenciamento do Windows PowerShell que permite implantar e gerenciar dados de configuração para serviços de software e gerenciar o ambiente no qual esses serviços são executados.</span><span class="sxs-lookup"><span data-stu-id="eac82-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="eac82-109">Os Recursos de Configuração de Estado Desejado (DSC) fornecem os blocos de construção para uma configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="eac82-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="eac82-110">Um recurso expõe propriedades que podem ser configuradas (esquema) e contém as funções de script do PowerShell que o Gerenciador de Configurações Local (LCM) chama de "realizar".</span><span class="sxs-lookup"><span data-stu-id="eac82-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="eac82-111">Um recurso pode modelar algo tão genérico quanto um arquivo ou tão específico quanto uma configuração de servidor do IIS.</span><span class="sxs-lookup"><span data-stu-id="eac82-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="eac82-112">Grupos de recursos semelhantes são combinados em um Módulo de DSC, que organiza todos os arquivos necessários em uma estrutura que é portátil e inclui metadados para identificar como os recursos devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="eac82-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="eac82-113">Find-DscResource pode filtrar segundo os parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="eac82-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="eac82-114">Esses parâmetros são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="eac82-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="eac82-115">Esses parâmetros de versão são permitidos apenas com o nome exclusivo do módulo, sem curingas.</span><span class="sxs-lookup"><span data-stu-id="eac82-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="eac82-116">Se o parâmetro RequiredVersion não for especificado, Find-DscResource retorna a versão mais recente do módulo que for igual ou maior que a versão mínima especificada ou a versão mais recente do módulo se nenhuma versão mínima tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="eac82-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="eac82-117">Se o parâmetro RequiredVersion for especificado, Find-DscResource retornará apenas a versão do módulo que corresponde exatamente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="eac82-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="eac82-118">Find-DscResource pode filtrar nos metadados do módulo com o parâmetro -Tag</span><span class="sxs-lookup"><span data-stu-id="eac82-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="eac82-119">Find-DscResource pode filtrar na linguagem de pesquisa específica do repositório com o parâmetro -Filter.</span><span class="sxs-lookup"><span data-stu-id="eac82-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="eac82-120">Find-DscResource pode filtrar módulos de todos ou de alguns dos repositórios registrados.</span><span class="sxs-lookup"><span data-stu-id="eac82-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="eac82-121">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="eac82-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="eac82-122">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="eac82-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="eac82-123">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="eac82-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="eac82-124">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="eac82-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```