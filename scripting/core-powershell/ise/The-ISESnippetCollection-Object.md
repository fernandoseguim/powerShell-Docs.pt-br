---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: O objeto ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="b2ede-103">O objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="b2ede-103">The ISESnippetCollection Object</span></span>
  <span data-ttu-id="b2ede-104">O objeto **ISESnippetCollection** é uma coleção de objetos **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="b2ede-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="b2ede-105">A coleção de arquivos associada a um objeto **PowerShellTab** é um membro dessa classe.</span><span class="sxs-lookup"><span data-stu-id="b2ede-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="b2ede-106">Um exemplo é a coleção **$psISE.CurrentPowerShellTab.Files**.</span><span class="sxs-lookup"><span data-stu-id="b2ede-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="b2ede-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="b2ede-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="b2ede-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="b2ede-108">Load\( FilePathName \)</span></span>
  <span data-ttu-id="b2ede-109">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="b2ede-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="b2ede-110">Carrega um arquivo .snippets.ps1xml que contém os trechos de código definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b2ede-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="b2ede-111">A maneira mais fácil de criar trechos de código é usar o novo cmdlet New-IseSnippet, que os armazena automaticamente em sua pasta de perfil para que sejam carregados sempre que você iniciar o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2ede-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

 <span data-ttu-id="b2ede-112">**FilePathName** – a cadeia de caracteres, o caminho e o nome de arquivo para um arquivo .snippets.ps1xml que contém definições de trecho de código.</span><span class="sxs-lookup"><span data-stu-id="b2ede-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a><span data-ttu-id="b2ede-113">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b2ede-113">See Also</span></span>
- [<span data-ttu-id="b2ede-114">O ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="b2ede-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md) 
- [<span data-ttu-id="b2ede-115">O modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2ede-115">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="b2ede-116">Referência de modelo de objeto do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2ede-116">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="b2ede-117">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="b2ede-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
