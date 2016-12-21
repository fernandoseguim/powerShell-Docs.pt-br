---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: O objeto ISESnippetCollection
ms.technology: powershell
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: ad6d8ba7a68654f15566d1a74ef6a30898f21c1e
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-isesnippetcollection-object"></a>O objeto ISESnippetCollection
  O objeto **ISESnippetCollection** é uma coleção de objetos **ISESnippet**. A coleção de arquivos associada a um objeto **PowerShellTab** é um membro dessa classe. Um exemplo é a coleção **$psISE.CurrentPowerShellTab.Files**.

## <a name="methods"></a>Métodos

### <a name="load-filepathname-"></a>Load\( FilePathName \)
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Carrega um arquivo .snippets.ps1xml que contém os trechos de código definidos pelo usuário. A maneira mais fácil de criar trechos de código é usar o novo cmdlet New-IseSnippet, que os armazena automaticamente em sua pasta de perfil para que sejam carregados sempre que você iniciar o ISE do Windows PowerShell.

 **FilePathName** – a cadeia de caracteres, o caminho e o nome de arquivo para um arquivo .snippets.ps1xml que contém definições de trecho de código.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a>Consulte Também
- [O ISESnippetObject](The-ISESnippetObject.md) 
- [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  
