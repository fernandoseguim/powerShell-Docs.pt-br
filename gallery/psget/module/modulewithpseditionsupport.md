---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: modulewithpseditionsupport
ms.openlocfilehash: 8122756b78e18fe55daef5c46dc299b87ddcaf1a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="modules-with-compatible-powershell-editions" class="xliff"></a>
# Módulos com as edições compatíveis do PowerShell
Da versão 5.1 em diante, o PowerShell está disponível nas edições diferentes que denotam diferentes conjuntos de recursos e compatibilidade de plataforma.

- **Desktop Edition:** criada no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows, como Server Core e Área de Trabalho do Windows.
- **Core Edition:** criada no .NET Core e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell executando em edições de superfície reduzida do Windows, como o Nano Server e Windows IoT.

<a id="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable" class="xliff"></a>
## A edição de execução do PowerShell é mostrada na propriedade PSEdition do $PSVersionTable.
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

<a id="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later" class="xliff"></a>
## Os autores de módulo podem declarar seus módulos para serem compatíveis com uma ou mais edições do PowerShell usando a chave de manifesto do módulo CompatiblePSEditions. Essa chave só tem suporte no PowerShell 5.1 ou posterior.
*OBSERVAÇÃO:* quando um manifesto de módulo for especificado com a chave CompatiblePSEditions, ele não poderá ser importado em versões anteriores do PowerShell.

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
Ao obter uma lista de módulos disponíveis, você pode filtrar a lista por edição do PowerShell.
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

<a id="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core" class="xliff"></a>
## Os autores de módulo podem publicar um único módulo destinado a uma ou ambas as edições do PowerShell (Desktop e Core) 

Um único módulo pode trabalhar em edições de Desktop e Core, nesse módulo, o autor tem que adicionar a lógica necessária em qualquer RootModule ou no manifesto do módulo usando a variável $PSEdition.
Os módulos podem ter dois conjuntos de DLLs compilados visando o CoreCLR e FullCLR.
Aqui estão as duas opções para empacotar seu módulo com a lógica de carregamento de dlls apropriadas.

<a id="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell" class="xliff"></a>
### Opção 1: empacotando um módulo para o direcionamento de várias versões e várias edições do PowerShell

<a id="module-folder-contents" class="xliff"></a>
#### Conteúdo de Pastas do Módulo
- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll 
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll 
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll 
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll 
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll 
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll 
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

<a id="contents-of-psscriptanalyzerpsd1-file" class="xliff"></a>
#### Conteúdo do arquivo PSScriptAnalyzer.psd1

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

<a id="contents-of-psscriptanalyzerpsm1-file" class="xliff"></a>
#### Conteúdo do arquivo PSScriptAnalyzer.psm1
Abaixo, a lógica carrega os assemblies necessários, dependendo da edição atual ou da versão.

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

<a id="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules" class="xliff"></a>
### Opção 2: usar a variável $PSEdition no arquivo PSD1 para carregar as DLLs apropriadas e módulos aninhados/exigidos

No PS 5.1 ou mais recente, a variável global $PSEdition é permitida no arquivo de manifesto de módulo.
Usando essa variável, autor de módulo pode especificar os valores condicionais no arquivo de manifesto de módulo. A variável de $PSEdition pode ser referenciada no modo de linguagem restrita ou em uma seção de dados. 

*OBSERVAÇÃO:* quando um manifesto de módulo for especificado com a chave CompatiblePSEditions ou usar a variável $PSEdition, ele não poderá ser importado em versões anteriores do PowerShell.


<a id="sample-module-manifest-file-with-compatiblepseditions-key" class="xliff"></a>
#### Arquivo de manifesto de módulo de exemplo com chave CompatiblePSEditions

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

<a id="module-contents" class="xliff"></a>
#### Conteúdos do módulo

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

<a id="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditoncore" class="xliff"></a>
## Os usuários da Galeria do PowerShell podem encontrar a lista de módulos de suporte em uma edição do PowerShell específica usando as marcas PSEdition_Desktop e PSEditon_Core.
Módulos sem as marcas PSEdition_Desktop e PSEditon_Core funcionam corretamente em edições do PowerShell Desktop.

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEditon_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEditon_Core

```


<a id="more-details" class="xliff"></a>
## Mais detalhes
<a id="scripts-with-pseditionsscriptscriptwithpseditionsupportmd" class="xliff"></a>
### [Scripts com PSEditions](../script/scriptwithpseditionsupport.md)
<a id="pseditions-support-on-powershellgallerypsgallerypsgallerypseditionsmd" class="xliff"></a>
### [Suporte do PSEditions na PowerShellGallery](../../psgallery/psgallery_pseditions.md)
<a id="update-module-manifest-psgetupdate-modulemanifestmd" class="xliff"></a>
### [Atualizar o manifesto de módulo] (./psget_update-modulemanifest.md)

