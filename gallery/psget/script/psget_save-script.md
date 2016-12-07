---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: script psget_save
ms.technology: powershell
ms.openlocfilehash: 58003350b991ca10b1d8bc65964bbfdd324334b5
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="save-script"></a>Save-Script

O cmdlet Save-Script permite examinar o arquivo de script salvando-o em um local especificado.

## <a name="description"></a>Descrição

O cmdlet Save-Script salva o script especificado.

## <a name="cmdlet-syntax"></a>Sintaxe do cmdlet

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Referência da ajuda online sobre cmdlets

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>Comandos de exemplo

### <a name="example-1-save-a-script-from-a-repository"></a>Exemplo 1: Salvar um script de um repositório
Este comando salva a versão mais recente do script Fabrikam-ClientScript do repositório GalleryINT na pasta local C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Exemplo 2: Salvar uma versão de um script por tubulação do cmdlet Find-Script

O primeiro comando localiza a versão 1.5 de Fabrikam-ClientScript do repositório GalleryINT e a salva na pasta C:\ScriptSharingDemo

O segundo comando valida os metadados do script salvo.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

