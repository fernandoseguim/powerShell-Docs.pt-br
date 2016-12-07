---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: script psget_update
ms.technology: powershell
ms.openlocfilehash: b95ab77ba04d70d470a9740b452f415c872f8fa7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="update-script"></a>Update-Script

O cmdlet Update-Script permite a atualização in-loco dos arquivos de script que foram instalados usando o cmdlet Install-Script.

## <a name="description"></a>Descrição

O cmdlet Update-Script atualiza o script especificado do repositório em que ele foi instalado anteriormente.

## <a name="cmdlet-syntax"></a>Sintaxe do cmdlet

```powershell
Get-Command -Name Update-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Referência da ajuda online sobre cmdlets

[Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787)

## <a name="example-commands"></a>Comandos de exemplo
```powershell
Install-Script -Name Fabrikam-Script -RequiredVersion 1.0 -Repository GalleryINT -Scope
Get-InstalledScript -Name Fabrikam-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Fabrikam-Script Script GalleryINT Description for the Fabrikam-Script script

# Update a specific script to the required version
Update-Script -Name Fabrikam-Script -RequiredVersion 1.5
Get-InstalledScript -Name Fabrikam-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.5 Fabrikam-Script Script GalleryINT Description for the Fabrikam-Script script

# Update all installed scripts
Install-Script -Name Fabrikam-ServerScript -RequiredVersion 1.0 -Repository GalleryINT -Scope CurrentUser
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
1.5 Fabrikam-Script Script GalleryINT Description for the Fabrikam-Script script
1.0 Fabrikam-ServerScript Script GalleryINT Description for the Fabrikam-ServerScript script
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script

Update-Script
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Fabrikam-Script Script GalleryINT Description for the Fabrikam-Script script
2.5 Fabrikam-ServerScript Script GalleryINT Description for the Fabrikam-ServerScript script
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
```

