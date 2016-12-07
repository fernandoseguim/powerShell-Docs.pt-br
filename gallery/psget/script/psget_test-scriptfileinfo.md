---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: psget_test scriptfileinfo
ms.technology: powershell
ms.openlocfilehash: 570ad7e878195f36e1d0831c504301bcee647a7d
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="test-scriptfileinfo"></a>Test-ScriptFileInfo

Valida o bloco de comentário dos metadados de um arquivo de script.

## <a name="description"></a>Descrição

O cmdlet Test-ScriptFileInfo valida o bloco de comentário no início de um script que será publicado com o cmdlet Publish-Script.
Se o bloco de comentário dos metadados tiver um erro, esse cmdlet retornará informações sobre onde o erro está localizado e como corrigi-lo.

## <a name="cmdlet-syntax"></a>Sintaxe do cmdlet

```powershell
Get-Command -Name Test-ScriptFileInfo -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Referência da ajuda online sobre cmdlets

[Test-ScriptFileInfo](http://go.microsoft.com/fwlink/?LinkId=619791)

## <a name="example-commands"></a>Comandos de exemplo
```powershell
# Create a new script file with minimum required metadata values
New-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1 -Description "Script file description goes here"

Get-Content -Path C:\ScriptSharingDemo\Demo-Script.ps1
<#PSScriptInfo
.VERSION 1.0
.GUID 926b47c3-6af2-4b18-b6f5-8b813a9e93ab
.AUTHOR manikb
.COMPANYNAME
.COPYRIGHT
.TAGS
.LICENSEURI
.PROJECTURI
.ICONURI
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
#>
<#
.DESCRIPTION
Script file description goes here
#>
Param()

# Validate and get the script metadata
Test-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1
Version Name Author Description
------- ---- ------ -----------
1.0 Demo-Script manikb Script file description goes here

# This command tests the script file Test-Runbook.ps1 and uses the pipeline operator to pass the results to the Format-List cmdlet to format the results.
Test-ScriptFileInfo -Path D:\code\Test-Runbook.ps1 | Format-List *

# This command tests the script file Hello-World.ps1, which has no metadata associated with it.
Test-ScriptFileInfo -Path C:\code\Hello-World.ps1
Test-ScriptFileInfo : PSScriptInfo is not specified in the script file 'C:\code\Hello-World.ps1'. You can use the Update-ScriptFileInfo with -Force or New-ScriptFileInfo cmdlet to add the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo -Path C:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (C:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException
    + FullyQualifiedErrorId : MissingPSScriptInfo,Test-ScriptFileInfo

```

