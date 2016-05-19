---
title: O objeto ISESnippetCollection
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
---
# O objeto ISESnippetCollection
  O objeto **ISESnippetCollection** é uma coleção de objetos **ISESnippet**. A coleção de arquivos associada a um objeto **PowerShellTab** é um membro dessa classe. Um exemplo é a coleção **$psISE.CurrentPowerShellTab.Files**.

## Métodos

### Load( FilePathName)
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Carrega um arquivo .snippets.ps1xml que contém os trechos de código definidos pelo usuário. A maneira mais fácil de criar trechos de código é usar o novo cmdlet New-IseSnippet, que armazena automaticamente em sua pasta de perfil para que sejam carregados sempre que você iniciar o ISE do Windows PowerShell.

 **FilePathName** – Cadeia de caracteres
 O caminho e nome de arquivo para um arquivo .snippets.ps1xml que contém definições de trecho de código.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## Consulte Também
 [O ISESnippetObject](The-ISESnippetObject.md) 
 [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [A hierarquia de modelo do objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


