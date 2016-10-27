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
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: ceb3ee918e594d23b3ba2e097d197dd0ff6a0971

---

# Save-Script

O cmdlet Save-Script permite examinar o arquivo de script salvando-o em um local especificado.

## Descrição

O cmdlet Save-Script salva o script especificado.

## Sintaxe do cmdlet

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## Referência da ajuda online sobre cmdlets

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## Comandos de exemplo

### Exemplo 1: Salvar um script de um repositório
Este comando salva a versão mais recente do script Fabrikam-ClientScript do repositório GalleryINT na pasta local C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### Exemplo 2: Salvar uma versão de um script por tubulação do cmdlet Find-Script

O primeiro comando localiza a versão 1.5 de Fabrikam-ClientScript do repositório GalleryINT e a salva na pasta C:\ScriptSharingDemo

O segundo comando valida os metadados do script salvo.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```




<!--HONumber=Oct16_HO2-->


