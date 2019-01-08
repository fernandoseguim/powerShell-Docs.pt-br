---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: O objeto ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400576"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="fc4e2-103">O objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="fc4e2-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="fc4e2-104">O objeto **ISESnippetCollection** é uma coleção de objetos **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="fc4e2-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="fc4e2-105">A coleção de arquivos associada a um objeto **PowerShellTab** é um membro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="fc4e2-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="fc4e2-106">Um exemplo é a coleção **$psISE.CurrentPowerShellTab.Files**.</span><span class="sxs-lookup"><span data-stu-id="fc4e2-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="fc4e2-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="fc4e2-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="fc4e2-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="fc4e2-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="fc4e2-109">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="fc4e2-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="fc4e2-110">Carrega um arquivo .snippets.ps1xml que contém os snippets definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="fc4e2-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="fc4e2-111">A maneira mais fácil de criar snippets é usar o novo cmdlet New-IseSnippet, que os armazena automaticamente em sua pasta de perfil para que sejam carregados sempre que você iniciar o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc4e2-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="fc4e2-112">**FilePathName** – a cadeia de caracteres, o caminho e o nome de arquivo para um arquivo .snippets.ps1xml que contém definições de snippet.</span><span class="sxs-lookup"><span data-stu-id="fc4e2-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="fc4e2-113">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="fc4e2-113">See Also</span></span>

- [<span data-ttu-id="fc4e2-114">O ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="fc4e2-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="fc4e2-115">Objetivo do modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc4e2-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="fc4e2-116">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="fc4e2-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)