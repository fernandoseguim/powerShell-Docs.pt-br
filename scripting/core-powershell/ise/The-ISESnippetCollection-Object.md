---
title: O objeto ISESnippetCollection
ms.date: 2016-05-11
keywords: PowerShell, cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: d8b5db28b0a8ce24d35b2684dd473bdea104d225
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
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

  
