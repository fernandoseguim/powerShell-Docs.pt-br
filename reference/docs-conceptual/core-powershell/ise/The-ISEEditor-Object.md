---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: O objeto ISEEditor
ms.openlocfilehash: 149eda44fea5b02324442970324e3010015e7ae5
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2017
---
# <a name="the-iseeditor-object"></a>O objeto ISEEditor
  Um objeto **ISEEditor** é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEEditor. O painel de Console é um objeto **ISEEditor**. Cada objeto [ISEFile](The-ISEFile-Object.md) tem um objeto **ISEEditor** associado. As seções a seguir listam os métodos e as propriedades de um objeto **ISEEditor**.

## <a name="methods"></a>Métodos

### <a name="clear"></a>Clear\(\)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Apaga o texto no editor.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Rola o editor de modo que a linha que corresponde ao valor do parâmetro **lineNumber** especificado fique visível. Gerará uma exceção se o número de linha especificado estiver fora do intervalo de 1, último número da linha, que define os números de linha válidos.

 **lineNumber** O número da linha que deve ficar visível.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Focus\(\)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Define o foco para o editor.

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Obtém o comprimento da linha como um inteiro para a linha especificada pelo número de linha.

 **lineNumber** O número da linha cujo comprimento será obtido.

 **Returns** O comprimento da linha no número de linha especificado.

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Moverá o cursor do sistema para o caractere correspondente, se a propriedade **CanGoToMatch** do objeto editor for **$true**, o que ocorrerá quando o cursor vier imediatamente antes de um parêntese de abertura, colchete ou chave – \(,\[,{ – ou imediatamente após um parêntese de fechamento, colchete ou chave – \),\],}.  O cursor é colocado antes de um caractere de abertura ou depois de um caractere de fechamento. Se a propriedade **CanGoToMatch** for **$false**, então esse método nada fará.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a>InsertText\( text \)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Substitui a seleção por texto ou inserções de texto na posição do cursor atual.

 **text** – cadeia de caracteres, o texto a ser inserido.

 Veja o [Exemplo de script](#-scripting-example), posteriormente neste tópico.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Select\( startLine, startColumn, endLine, endColumn \)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Seleciona o texto dos parâmetros **startLine**, **startColumn**, **endLine** e **endColumn**.

 **startLine** – inteiro, a linha na qual a seleção começa.

 **startColumn** – inteiro, a coluna na linha inicial na qual a seleção começa.

 **endLine** – inteiro, a linha na qual a seleção é encerrada.

 **endColumn** – inteiro, a coluna na linha final na qual a seleção é encerrada.

 Veja o [Exemplo de script](#-scripting-example), posteriormente neste tópico.

### <a name="selectcaretline"></a>SelectCaretLine\(\)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Seleciona toda a linha de texto que contém atualmente o circunflexo.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Define a posição do cursor no número de linha e no número da coluna. Gera uma exceção se o número de linha do cursor ou o número da coluna do cursor estiverem fora de seus respectivos intervalos válidos.

 **lineNumber** – inteiro, o número de linha do cursor do sistema.

 **columnNumber** – inteiro, o número da coluna do cursor do sistema.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Faz com que toda a estrutura de tópicos se expanda ou se recolha.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Propriedades

### <a name="cangotomatch"></a>CanGoToMatch
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade booliana somente leitura para indicar se o cursor está ao lado de um parêntese, colchete ou chave – \(\), \[\], {}. Se o cursor estiver imediatamente antes do caractere de abertura ou imediatamente após o caractere de fechamento de um par, o valor da propriedade será **$true**. Caso contrário é **$false**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o número da coluna que corresponde à posição do cursor.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o número da linha que contém o cursor.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a linha completa de texto que contém o cursor.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a contagem de linha do editor.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o texto selecionado do editor.

 Veja o [Exemplo de script](#-scripting-example), posteriormente neste tópico.

### <a name="text"></a>Texto
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade de leitura/gravação que obtém ou define o texto no editor.

 Veja o [Exemplo de script](#-scripting-example), posteriormente neste tópico.

## <a name="scripting-example"></a>Exemplo de Script

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

## <a name="see-also"></a>Consulte Também
- [O objeto ISEFile](The-ISEFile-Object.md) 
- [O objeto PowerShellTab](The-PowerShellTab-Object.md) 
- [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  
