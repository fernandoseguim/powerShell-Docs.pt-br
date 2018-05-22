---
ms.date: 06/12/2017
contributor: manikb
keywords: galeria,powershell,cmdlet,psget
title: Módulos com as edições compatíveis do PowerShell
ms.openlocfilehash: fbbfda2f913d54c3e69c0724fea4d977923279c1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="a84c4-103">Módulos com as edições compatíveis do PowerShell</span><span class="sxs-lookup"><span data-stu-id="a84c4-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="a84c4-104">Da versão 5.1 em diante, o PowerShell está disponível nas edições diferentes que denotam diferentes conjuntos de recursos e compatibilidade de plataforma.</span><span class="sxs-lookup"><span data-stu-id="a84c4-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="a84c4-105">**Desktop Edition:** criada no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows, como Server Core e Área de Trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="a84c4-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="a84c4-106">**Core Edition:** criada no .NET Core e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell executando em edições de superfície reduzida do Windows, como o Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="a84c4-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable"></a><span data-ttu-id="a84c4-107">A edição do PowerShell em execução é exibida na propriedade PSEdition de $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="a84c4-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

## <a name="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later"></a><span data-ttu-id="a84c4-108">Os autores de módulo podem declarar seus módulos para serem compatíveis com uma ou mais edições do PowerShell usando a chave de manifesto do módulo CompatiblePSEditions.</span><span class="sxs-lookup"><span data-stu-id="a84c4-108">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="a84c4-109">Essa chave só tem suporte no PowerShell 5.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="a84c4-109">This key is only supported on PowerShell 5.1 or later.</span></span>

<span data-ttu-id="a84c4-110">*OBSERVAÇÃO:* quando um manifesto de módulo for especificado com a chave CompatiblePSEditions, ele não poderá ser importado em versões anteriores do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a84c4-110">*NOTE* Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on lower versions of PowerShell.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
Desktop
Core

$ModuleInfo | Get-Member CompatiblePSEditions

   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}

```

<span data-ttu-id="a84c4-111">Ao obter uma lista de módulos disponíveis, você pode filtrar a lista por edição do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a84c4-111">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop

    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions

Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
Desktop
Core

```

## <a name="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core"></a><span data-ttu-id="a84c4-112">Os autores de módulo podem publicar um único módulo destinado a uma ou ambas as edições do PowerShell (Desktop e Core)</span><span class="sxs-lookup"><span data-stu-id="a84c4-112">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core)</span></span>

<span data-ttu-id="a84c4-113">Um único módulo pode trabalhar em edições de Desktop e Core, nesse módulo, o autor tem que adicionar a lógica necessária em qualquer RootModule ou no manifesto do módulo usando a variável $PSEdition.</span><span class="sxs-lookup"><span data-stu-id="a84c4-113">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span>
<span data-ttu-id="a84c4-114">Os módulos podem ter dois conjuntos de DLLs compilados visando o CoreCLR e FullCLR.</span><span class="sxs-lookup"><span data-stu-id="a84c4-114">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span>
<span data-ttu-id="a84c4-115">Aqui estão as duas opções para empacotar seu módulo com a lógica de carregamento de dlls apropriadas.</span><span class="sxs-lookup"><span data-stu-id="a84c4-115">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="a84c4-116">Opção 1: empacotando um módulo para o direcionamento de várias versões e várias edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="a84c4-116">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

#### <a name="module-folder-contents"></a><span data-ttu-id="a84c4-117">Conteúdo de Pastas do Módulo</span><span class="sxs-lookup"><span data-stu-id="a84c4-117">Module folder contents</span></span>

- <span data-ttu-id="a84c4-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="a84c4-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="a84c4-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="a84c4-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="a84c4-120">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="a84c4-120">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="a84c4-121">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="a84c4-121">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="a84c4-122">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="a84c4-122">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="a84c4-123">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="a84c4-123">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="a84c4-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="a84c4-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="a84c4-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="a84c4-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="a84c4-126">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="a84c4-126">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="a84c4-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="a84c4-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="a84c4-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="a84c4-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="a84c4-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="a84c4-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="a84c4-130">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="a84c4-130">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="a84c4-131">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="a84c4-131">Settings\DSC.psd1</span></span>
- <span data-ttu-id="a84c4-132">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="a84c4-132">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="a84c4-133">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="a84c4-133">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="a84c4-134">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="a84c4-134">Settings\ScriptSecurity.psd1</span></span>

#### <a name="contents-of-psscriptanalyzerpsd1-file"></a><span data-ttu-id="a84c4-135">Conteúdo do arquivo PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="a84c4-135">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

#### <a name="contents-of-psscriptanalyzerpsm1-file"></a><span data-ttu-id="a84c4-136">Conteúdo do arquivo PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="a84c4-136">Contents of PSScriptAnalyzer.psm1 file</span></span>

<span data-ttu-id="a84c4-137">Abaixo, a lógica carrega os assemblies necessários, dependendo da edição atual ou da versão.</span><span class="sxs-lookup"><span data-stu-id="a84c4-137">Below logic loads the required assemblies depending on the current edition or version.</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0') {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}

```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="a84c4-138">Opção 2: usar a variável $PSEdition no arquivo PSD1 para carregar as DLLs apropriadas e módulos aninhados/exigidos</span><span class="sxs-lookup"><span data-stu-id="a84c4-138">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="a84c4-139">No PS 5.1 ou mais recente, a variável global $PSEdition é permitida no arquivo de manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="a84c4-139">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span>
<span data-ttu-id="a84c4-140">Usando essa variável, autor de módulo pode especificar os valores condicionais no arquivo de manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="a84c4-140">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="a84c4-141">A variável de $PSEdition pode ser referenciada no modo de linguagem restrita ou em uma seção de dados.</span><span class="sxs-lookup"><span data-stu-id="a84c4-141">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

<span data-ttu-id="a84c4-142">*OBSERVAÇÃO:* quando um manifesto de módulo for especificado com a chave CompatiblePSEditions ou usar a variável $PSEdition, ele não poderá ser importado em versões anteriores do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a84c4-142">*NOTE* Once a module manifest is specified with the CompatiblePSEditions key or uses $PSEdition variable, it can not be imported on lower versions of PowerShell.</span></span>


#### <a name="sample-module-manifest-file-with-compatiblepseditions-key"></a><span data-ttu-id="a84c4-143">Arquivo de manifesto de módulo de exemplo com chave CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="a84c4-143">Sample module manifest file with CompatiblePSEditions key</span></span>

```powershell
@{
# - - -

# Script module or binary module file associated with this manifest.
RootModule = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrRM.dll'
}
else # Desktop
{
'clr\MyFullClrRM.dll'
}

# Supported PSEditions
CompatiblePSEditions = 'Desktop', 'Core'

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrNM1.dll',
'coreclr\MyCoreClrNM2.dll'
}
else # Desktop
{
'clr\MyFullClrNM1.dll',
'clr\MyFullClrNM2.dll'
}

# -- - -
}
```

#### <a name="module-contents"></a><span data-ttu-id="a84c4-144">Conteúdos do módulo</span><span class="sxs-lookup"><span data-stu-id="a84c4-144">Module contents</span></span>

```powershell

PS C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions> dir -Recurse

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/5/2016   1:37 PM                clr
d-----         7/5/2016   1:36 PM                coreclr
-a----         7/5/2016   1:34 PM           4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyFullClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrRM.dl
```

## <a name="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditioncore"></a><span data-ttu-id="a84c4-145">Os usuários da Galeria do PowerShell podem encontrar a lista de módulos com suporte em uma edição do PowerShell específica usando as marcas PSEdition_Desktop e PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="a84c4-145">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="a84c4-146">Módulos sem as marcas PSEdition_Desktop e PSEdition_Core funcionam corretamente em edições do PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="a84c4-146">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core

```


## <a name="more-details"></a><span data-ttu-id="a84c4-147">Mais detalhes</span><span class="sxs-lookup"><span data-stu-id="a84c4-147">More details</span></span>

- [<span data-ttu-id="a84c4-148">Scripts com PSEditions</span><span class="sxs-lookup"><span data-stu-id="a84c4-148">Scripts with PSEditions</span></span>](script-psedition-support.md)
- [<span data-ttu-id="a84c4-149">Suporte do PSEditions na PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="a84c4-149">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)
- <span data-ttu-id="a84c4-150">[Atualizar manifesto do módulo] (/powershell/module/powershellget/update-modulemanifest)</span><span class="sxs-lookup"><span data-stu-id="a84c4-150">[Update module manifest] (/powershell/module/powershellget/update-modulemanifest)</span></span>