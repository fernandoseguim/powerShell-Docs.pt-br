---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: O ISESnippetObject
ms.technology: powershell
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 51ecf1261857e278c6d02ecb3cce16454ecfd4c4
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-isesnippetobject"></a>O ISESnippetObject
  Um objeto **ISESnippet** é uma instância da classe Microsoft.PowerShell.Host.ISE.ISESnippet. Os membros da coleção **$psISE.CurrentPowerShellTab.Snippets** são exemplos de objetos **ISESnippet**. A maneira mais fácil de criar um trecho de código é usar o cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).

## <a name="properties"></a>Propriedades

###  <a name="a-namedisplaynamea-author"></a><a name="DisplayName"></a> Author
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade somente leitura que recebe o nome do autor do trecho de código.

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

###  <a name="a-nameactiona-codefragment"></a><a name="Action"></a> CodeFragment
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade somente leitura que obtém o fragmento de código a ser inserido no editor.

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

###  <a name="a-nameshortcuta-shortcut"></a><a name="Shortcut"></a> Atalho
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade somente leitura que obtém o atalho de teclado do Windows do item de menu.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Consulte Também
- [O objeto ISESnippetCollection](The-ISESnippetCollection-Object.md) 
- [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  
