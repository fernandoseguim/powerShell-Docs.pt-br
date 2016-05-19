---
title: O ISESnippetObject
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
---
# O ISESnippetObject
  Um objeto **ISESnippet** é uma instância da classe Microsoft.PowerShell.Host.ISE.ISESnippet. Os membros da coleção **$psISE.CurrentPowerShellTab.Snippets** são exemplos de objetos **ISESnippet**. A maneira mais fácil de criar um trecho de código é usar o cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).

## Propriedades

###  <a name="DisplayName"></a> Autor
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade somente leitura que recebe o nome do autor do trecho de código.

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

###  <a name="Action"></a> CodeFragment
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade somente leitura que obtém o fragmento de código a ser inserido no editor.

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

###  <a name="Shortcut"></a> Atalho
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade somente leitura que obtém o atalho de teclado do Windows do item de menu.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## Consulte Também
 [O objeto ISESnippetCollection](The-ISESnippetCollection-Object.md) 
 [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [A hierarquia de modelo do objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


