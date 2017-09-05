---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: O objeto ISEEditor
ms.assetid: 0101daf8-4e31-4e4c-ab89-01d95dcb8f46
ms.openlocfilehash: e2ddb0de1089c832f130e1f5c7c8dcb199aca2fa
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2017
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="4ce00-103">O objeto ISEEditor</span><span class="sxs-lookup"><span data-stu-id="4ce00-103">The ISEEditor Object</span></span>
  <span data-ttu-id="4ce00-104">Um objeto **ISEEditor** é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="4ce00-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="4ce00-105">O painel de Console é um objeto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="4ce00-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="4ce00-106">Cada objeto [ISEFile](The-ISEFile-Object.md) tem um objeto **ISEEditor** associado.</span><span class="sxs-lookup"><span data-stu-id="4ce00-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="4ce00-107">As seções a seguir listam os métodos e as propriedades de um objeto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="4ce00-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="4ce00-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="4ce00-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="4ce00-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="4ce00-109">Clear\(\)</span></span>
  <span data-ttu-id="4ce00-110">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-111">Apaga o texto no editor.</span><span class="sxs-lookup"><span data-stu-id="4ce00-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="4ce00-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="4ce00-112">EnsureVisible\(int lineNumber\)</span></span>
  <span data-ttu-id="4ce00-113">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-114">Rola o editor de modo que a linha que corresponde ao valor do parâmetro **lineNumber** especificado fique visível.</span><span class="sxs-lookup"><span data-stu-id="4ce00-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="4ce00-115">Gerará uma exceção se o número de linha especificado estiver fora do intervalo de 1, último número da linha, que define os números de linha válidos.</span><span class="sxs-lookup"><span data-stu-id="4ce00-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

 <span data-ttu-id="4ce00-116">**lineNumber** O número da linha que deve ficar visível.</span><span class="sxs-lookup"><span data-stu-id="4ce00-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="4ce00-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="4ce00-117">Focus\(\)</span></span>
  <span data-ttu-id="4ce00-118">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-119">Define o foco para o editor.</span><span class="sxs-lookup"><span data-stu-id="4ce00-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="4ce00-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="4ce00-120">GetLineLength\(int lineNumber \)</span></span>
  <span data-ttu-id="4ce00-121">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-122">Obtém o comprimento da linha como um inteiro para a linha especificada pelo número de linha.</span><span class="sxs-lookup"><span data-stu-id="4ce00-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

 <span data-ttu-id="4ce00-123">**lineNumber** O número da linha cujo comprimento será obtido.</span><span class="sxs-lookup"><span data-stu-id="4ce00-123">**lineNumber** The number of the line of which to get the length.</span></span>

 <span data-ttu-id="4ce00-124">**Returns** O comprimento da linha no número de linha especificado.</span><span class="sxs-lookup"><span data-stu-id="4ce00-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="4ce00-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="4ce00-125">GoToMatch\(\)</span></span>
  <span data-ttu-id="4ce00-126">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="4ce00-127">Moverá o cursor do sistema para o caractere correspondente, se a propriedade **CanGoToMatch** do objeto editor for **$true**, o que ocorrerá quando o cursor vier imediatamente antes de um parêntese de abertura, colchete ou chave – \(,\[,{ – ou imediatamente após um parêntese de fechamento, colchete ou chave – \),\],}.</span><span class="sxs-lookup"><span data-stu-id="4ce00-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="4ce00-128">O cursor é colocado antes de um caractere de abertura ou depois de um caractere de fechamento.</span><span class="sxs-lookup"><span data-stu-id="4ce00-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="4ce00-129">Se a propriedade **CanGoToMatch** for **$false**, então esse método nada fará.</span><span class="sxs-lookup"><span data-stu-id="4ce00-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span> <span data-ttu-id="4ce00-130">Consulte [CanGoToMatch]().</span><span class="sxs-lookup"><span data-stu-id="4ce00-130">See [CanGoToMatch]().</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a><span data-ttu-id="4ce00-131">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="4ce00-131">InsertText\( text \)</span></span>
  <span data-ttu-id="4ce00-132">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-132">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-133">Substitui a seleção por texto ou inserções de texto na posição do cursor atual.</span><span class="sxs-lookup"><span data-stu-id="4ce00-133">Replaces the selection with text or inserts text at the current caret position.</span></span>

 <span data-ttu-id="4ce00-134">**text** – cadeia de caracteres, o texto a ser inserido.</span><span class="sxs-lookup"><span data-stu-id="4ce00-134">**text** - String The text to insert.</span></span>

 <span data-ttu-id="4ce00-135">Veja o [Exemplo de script](), posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="4ce00-135">See the [Scripting Example]() later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="4ce00-136">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="4ce00-136">Select\( startLine, startColumn, endLine, endColumn \)</span></span>
  <span data-ttu-id="4ce00-137">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-137">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-138">Seleciona o texto dos parâmetros **startLine**, **startColumn**, **endLine** e **endColumn**.</span><span class="sxs-lookup"><span data-stu-id="4ce00-138">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

 <span data-ttu-id="4ce00-139">**startLine** – inteiro, a linha na qual a seleção começa.</span><span class="sxs-lookup"><span data-stu-id="4ce00-139">**startLine** - Integer The line where the selection starts.</span></span>

 <span data-ttu-id="4ce00-140">**startColumn** – inteiro, a coluna na linha inicial na qual a seleção começa.</span><span class="sxs-lookup"><span data-stu-id="4ce00-140">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

 <span data-ttu-id="4ce00-141">**endLine** – inteiro, a linha na qual a seleção é encerrada.</span><span class="sxs-lookup"><span data-stu-id="4ce00-141">**endLine** - Integer The line where the selection ends.</span></span>

 <span data-ttu-id="4ce00-142">**endColumn** – inteiro, a coluna na linha final na qual a seleção é encerrada.</span><span class="sxs-lookup"><span data-stu-id="4ce00-142">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

 <span data-ttu-id="4ce00-143">Veja o [Exemplo de script](), posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="4ce00-143">See the  [Scripting Example]() later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="4ce00-144">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="4ce00-144">SelectCaretLine\(\)</span></span>
  <span data-ttu-id="4ce00-145">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-145">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-146">Seleciona toda a linha de texto que contém atualmente o circunflexo.</span><span class="sxs-lookup"><span data-stu-id="4ce00-146">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="4ce00-147">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="4ce00-147">SetCaretPosition\( lineNumber, columnNumber \)</span></span>
  <span data-ttu-id="4ce00-148">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-148">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-149">Define a posição do cursor no número de linha e no número da coluna.</span><span class="sxs-lookup"><span data-stu-id="4ce00-149">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="4ce00-150">Gera uma exceção se o número de linha do cursor ou o número da coluna do cursor estiverem fora de seus respectivos intervalos válidos.</span><span class="sxs-lookup"><span data-stu-id="4ce00-150">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

 <span data-ttu-id="4ce00-151">**lineNumber** – inteiro, o número de linha do cursor do sistema.</span><span class="sxs-lookup"><span data-stu-id="4ce00-151">**lineNumber** - Integer The caret line number.</span></span>

 <span data-ttu-id="4ce00-152">**columnNumber** – inteiro, o número da coluna do cursor do sistema.</span><span class="sxs-lookup"><span data-stu-id="4ce00-152">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="4ce00-153">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="4ce00-153">ToggleOutliningExpansion\(\)</span></span>
  <span data-ttu-id="4ce00-154">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="4ce00-155">Faz com que toda a estrutura de tópicos se expanda ou se recolha.</span><span class="sxs-lookup"><span data-stu-id="4ce00-155">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="4ce00-156">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4ce00-156">Properties</span></span>

###  <span data-ttu-id="4ce00-157"><a name="CanGoToMatch"></a> CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="4ce00-157"><a name="CanGoToMatch"></a> CanGoToMatch</span></span>
  <span data-ttu-id="4ce00-158">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-158">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="4ce00-159">A propriedade booliana somente leitura para indicar se o cursor está ao lado de um parêntese, colchete ou chave – \(\), \[\], {}.</span><span class="sxs-lookup"><span data-stu-id="4ce00-159">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="4ce00-160">Se o cursor estiver imediatamente antes do caractere de abertura ou imediatamente após o caractere de fechamento de um par, o valor da propriedade será **$true**.</span><span class="sxs-lookup"><span data-stu-id="4ce00-160">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="4ce00-161">Caso contrário é **$false**.</span><span class="sxs-lookup"><span data-stu-id="4ce00-161">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

###  <span data-ttu-id="4ce00-162"><a name="CaretColumn"></a> CaretColumn</span><span class="sxs-lookup"><span data-stu-id="4ce00-162"><a name="CaretColumn"></a> CaretColumn</span></span>
  <span data-ttu-id="4ce00-163">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-163">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-164">A propriedade somente leitura que obtém o número da coluna que corresponde à posição do cursor.</span><span class="sxs-lookup"><span data-stu-id="4ce00-164">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

###  <span data-ttu-id="4ce00-165"><a name="CaretLine"></a> CaretLine</span><span class="sxs-lookup"><span data-stu-id="4ce00-165"><a name="CaretLine"></a> CaretLine</span></span>
  <span data-ttu-id="4ce00-166">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-166">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-167">A propriedade somente leitura que obtém o número da linha que contém o cursor.</span><span class="sxs-lookup"><span data-stu-id="4ce00-167">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

###  <span data-ttu-id="4ce00-168"><a name="CaretLineText"></a> CaretLineText</span><span class="sxs-lookup"><span data-stu-id="4ce00-168"><a name="CaretLineText"></a> CaretLineText</span></span>
  <span data-ttu-id="4ce00-169">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-170">A propriedade somente leitura que obtém a linha completa de texto que contém o cursor.</span><span class="sxs-lookup"><span data-stu-id="4ce00-170">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

###  <span data-ttu-id="4ce00-171"><a name="LineCount"></a> LineCount</span><span class="sxs-lookup"><span data-stu-id="4ce00-171"><a name="LineCount"></a> LineCount</span></span>
  <span data-ttu-id="4ce00-172">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-172">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-173">A propriedade somente leitura que obtém a contagem de linha do editor.</span><span class="sxs-lookup"><span data-stu-id="4ce00-173">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

###  <span data-ttu-id="4ce00-174"><a name="SelectedText"></a> SelectedText</span><span class="sxs-lookup"><span data-stu-id="4ce00-174"><a name="SelectedText"></a> SelectedText</span></span>
  <span data-ttu-id="4ce00-175">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-175">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-176">A propriedade somente leitura que obtém o texto selecionado do editor.</span><span class="sxs-lookup"><span data-stu-id="4ce00-176">The read-only property that gets the selected text from the editor.</span></span>

 <span data-ttu-id="4ce00-177">Veja o [Exemplo de script](), posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="4ce00-177">See the  [Scripting Example]() later in this topic.</span></span>

###  <span data-ttu-id="4ce00-178"><a name="Text"></a> Text</span><span class="sxs-lookup"><span data-stu-id="4ce00-178"><a name="Text"></a> Text</span></span>
  <span data-ttu-id="4ce00-179">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ce00-179">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4ce00-180">A propriedade de leitura/gravação que obtém ou define o texto no editor.</span><span class="sxs-lookup"><span data-stu-id="4ce00-180">The read/write property that gets or sets the text in the editor.</span></span>

 <span data-ttu-id="4ce00-181">Veja o [Exemplo de script](), posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="4ce00-181">See the [Scripting Example]() later in this topic.</span></span>

##  <span data-ttu-id="4ce00-182"><a name="example"></a> Exemplo de Script</span><span class="sxs-lookup"><span data-stu-id="4ce00-182"><a name="example"></a> Scripting Example</span></span>

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase. 
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line. 
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="4ce00-183">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4ce00-183">See Also</span></span>
- [<span data-ttu-id="4ce00-184">O objeto ISEFile</span><span class="sxs-lookup"><span data-stu-id="4ce00-184">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="4ce00-185">O objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="4ce00-185">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="4ce00-186">O modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ce00-186">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="4ce00-187">Referência de modelo de objeto do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ce00-187">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="4ce00-188">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="4ce00-188">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
