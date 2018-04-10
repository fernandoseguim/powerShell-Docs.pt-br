---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Update-ModuleManifest
ms.openlocfilehash: 45f40f753af17e82c83dbf57dea13749ba626503
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="update-modulemanifest"></a><span data-ttu-id="40e70-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="40e70-103">Update-ModuleManifest</span></span>
<span data-ttu-id="40e70-104">Atualiza um arquivo de manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="40e70-104">Updates a module manifest file.</span></span>

## <a name="description"></a><span data-ttu-id="40e70-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="40e70-105">Description</span></span>

<span data-ttu-id="40e70-106">O cmdlet Update-ModuleManifest atualiza um arquivo de manifesto do módulo (.psd1).</span><span class="sxs-lookup"><span data-stu-id="40e70-106">The Update-ModuleManifest cmdlet updates a module manifest (.psd1) file.</span></span>

### <a name="notes"></a><span data-ttu-id="40e70-107">Observações</span><span class="sxs-lookup"><span data-stu-id="40e70-107">Notes</span></span>
    - <span data-ttu-id="40e70-108">DscResourcesToExport tem suporte somente na versão mais recente do PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="40e70-108">DscResourcesToExport is only supported on the latest PowerShell version 5.0.</span></span> <span data-ttu-id="40e70-109">Nós não poderemos atualizar o campo se você estiver executando em versões anteriores do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40e70-109">We won’t be able to update the field if you are running on lower versions of PowerShell.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="40e70-110">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="40e70-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-ModuleManifest -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="40e70-111">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="40e70-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="40e70-112">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="40e70-112">Update-ModuleManifest</span></span>](http://go.microsoft.com/fwlink/?LinkId=619311)

## <a name="example-commands"></a><span data-ttu-id="40e70-113">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="40e70-113">Example commands</span></span>

<span data-ttu-id="40e70-114">Esse novo cmdlet é usado para ajudar a atualizar o arquivo de manifesto com valores de propriedade de entrada.</span><span class="sxs-lookup"><span data-stu-id="40e70-114">This new cmdlet is used to help update manifest file with input property values.</span></span> <span data-ttu-id="40e70-115">Ele usa todos os parâmetros usados por New-ModuleManifest.</span><span class="sxs-lookup"><span data-stu-id="40e70-115">It takes all parameters that New-ModuleManifest does.</span></span>

<span data-ttu-id="40e70-116">Percebemos que muitos autores de módulos gostariam de especificar “\*” em valores exportados como FunctionsToExport, CmdletsToExport, etc. Durante a publicação de módulo na Galeria do PowerShell, comandos e funções não especificados não serão populados corretamente na Galeria.</span><span class="sxs-lookup"><span data-stu-id="40e70-116">We notice that a lot of module authors would like to specify “\*” in exported values such as FunctionsToExport, CmdletsToExport, etc. During module publishing to PowerShell Gallery, unspecified functions and commands will not be populated properly onto the Gallery.</span></span> <span data-ttu-id="40e70-117">Portanto, sugerimos que os autores de módulos atualizem seus manifestos com valores adequados.</span><span class="sxs-lookup"><span data-stu-id="40e70-117">Therefore, we suggest module authors update their manifests with proper values.</span></span>

<span data-ttu-id="40e70-118">Caso tenha módulos que exportaram propriedades, Update-ModuleManifest preencherá o arquivo de manifesto especificado com informações sobre as funções, cmdlets, variáveis, etc., exportados:</span><span class="sxs-lookup"><span data-stu-id="40e70-118">If you have modules that have exported properties, Update-ModuleManifest will fill the specified manifest file with information from exported functions, cmdlets, variables etc:</span></span>
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

<span data-ttu-id="40e70-119">Após Update-ModuleManifest:</span><span class="sxs-lookup"><span data-stu-id="40e70-119">After Update-ModuleManifest:</span></span>
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

<span data-ttu-id="40e70-120">Para cada módulo, há também campos de metadados associados a ele.</span><span class="sxs-lookup"><span data-stu-id="40e70-120">For each module, there are also metadata fields associated with it.</span></span> <span data-ttu-id="40e70-121">Para exibir os metadados corretamente na Galeria do PowerShell, é possível usar Update-ModuleManifest para popular esses campos em PrivateData.</span><span class="sxs-lookup"><span data-stu-id="40e70-121">In order to display metadata properly on PowrShell Gallery, you can use Update-ModuleManifest to populate those fields under PrivateData.</span></span>

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

<span data-ttu-id="40e70-122">A tabela de hash PrivateData do modelo de arquivo de manifesto tem as seguintes propriedades</span><span class="sxs-lookup"><span data-stu-id="40e70-122">PrivateData hashtable from the manifest file template has the following properties</span></span>

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```