---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: O ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="the-isesnippetobject"></a>O ISESnippetObject

Um objeto **ISESnippet** é uma instância da classe Microsoft.PowerShell.Host.ISE.ISESnippet. Os membros da coleção **$psISE.CurrentPowerShellTab.Snippets** são exemplos de objetos **ISESnippet**. A maneira mais fácil de criar um trecho de código é usar o cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).

## <a name="properties"></a>Propriedades

### <a name="author"></a>Autor

Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

A propriedade somente leitura que recebe o nome do autor do trecho de código.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

A propriedade somente leitura que obtém o fragmento de código a ser inserido no editor.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Atalho

Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

A propriedade somente leitura que obtém o atalho de teclado do Windows do item de menu.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Consulte Também

- [O objeto ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Objetivo do modelo de objeto de script do ISE do Windows PowerShell](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)