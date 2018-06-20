---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: O objeto ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950943"
---
# <a name="the-isesnippetcollection-object"></a>O objeto ISESnippetCollection

O objeto **ISESnippetCollection** é uma coleção de objetos **ISESnippet**. A coleção de arquivos associada a um objeto **PowerShellTab** é um membro dessa classe. Um exemplo é a coleção **$psISE.CurrentPowerShellTab.Files**.

## <a name="methods"></a>Métodos

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

Carrega um arquivo .snippets.ps1xml que contém os trechos de código definidos pelo usuário. A maneira mais fácil de criar trechos de código é usar o novo cmdlet New-IseSnippet, que os armazena automaticamente em sua pasta de perfil para que sejam carregados sempre que você iniciar o ISE do Windows PowerShell.

**FilePathName** – a cadeia de caracteres, o caminho e o nome de arquivo para um arquivo .snippets.ps1xml que contém definições de trecho de código.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Consulte Também

- [O ISESnippetObject](The-ISESnippetObject.md)
- [Objetivo do modelo de objeto de script do ISE do Windows PowerShell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)