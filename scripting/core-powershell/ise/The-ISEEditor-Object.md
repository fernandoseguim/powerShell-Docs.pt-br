---
title: O objeto ISEEditor
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0101daf8-4e31-4e4c-ab89-01d95dcb8f46
---
# O objeto ISEEditor
  Um objeto **ISEEditor** é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEEditor. O painel de Console é um objeto **ISEEditor**. Cada objeto [ISEFile](The-ISEFile-Object.md) tem um objeto **ISEEditor** associado. As seções a seguir listam os métodos e as propriedades de um objeto **ISEEditor**.

## Métodos

### Clear()
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Apaga o texto no editor.

```
# Clears the text in the Console pane.
$psIse.CurrentPowerShellTab.ConsolePane.Clear()

```

### EnsureVisible(int lineNumber)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Rola o editor de modo que a linha que corresponde ao valor do parâmetro **lineNumber** especificado fique visível. Gerará uma exceção se o número de linha especificado estiver fora do intervalo de 1, último número da linha, que define os números de linha válidos.

 **lineNumber**
 O número da linha que deve ficar visível.

```
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psIse.CurrentFile.Editor.EnsureVisible(5)

```

### Focus()
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Define o foco para o editor.

```
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### GetLineLength(int lineNumber )
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Obtém o comprimento da linha como um inteiro para a linha especificada pelo número de linha.

 **lineNumber**
 O número da linha do qual obter o comprimento.

 **Retorna**
 O comprimento da linha para a linha especificada no número de linha.

```
# Gets the length of the first line in the text of the Command pane. 
$psIse.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### GoToMatch()
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Move o cursor para o caractere correspondente, se a propriedade **CanGoToMatch** do objeto editor for **$true**, que ocorre quando o cursor vem imediatamente antes de um parêntese de abertura, colchete ou chave - (,[,{ - ou imediatamente após um parêntese de fechamento, colchete ou chave - ),],}.  O cursor é colocado antes de um caractere de abertura ou depois de um caractere de fechamento. Se a propriedade **CanGoToMatch** for **$false**, então esse método nada fará. Consulte [CanGoToMatch](#cangotomatch).

```
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### InsertText( text )
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Substitui a seleção por texto ou inserções de texto na posição do cursor atual.

 **text** \- String
 O texto a ser inserido.

 Veja o [Exemplo de script](#example), posteriormente neste tópico.

### Select( startLine, startColumn, endLine, endColumn )
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Seleciona o texto dos parâmetros **startLine**, **startColumn**, **endLine** e **endColumn**.

 **startLine** - Inteiro
 A linha em que a seleção começa.

 **startColumn** - Inteiro
 A coluna dentro da linha de início na qual a seleção começa.

 **endLine** - Inteiro
 A linha em que a seleção termina.

 **endColumn** - Inteiro
 A coluna dentro da linha final na qual a seleção termina.

 Veja o [Exemplo de script](#example), posteriormente neste tópico.

### SelectCaretLine()
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Seleciona toda a linha de texto que contém atualmente o circunflexo.

```
# First, set the caret position on line 5.
$psIse.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psIse.CurrentFile.Editor.SelectCaretLine()

```

### SetCaretPosition( lineNumber, columnNumber )
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Define a posição do cursor no número de linha e no número da coluna. Gera uma exceção se o número de linha do cursor ou o número da coluna do cursor estiverem fora de seus respectivos intervalos válidos.

 **lineNumber** - Inteiro
 O número de linha do cursor.

 **columnNumber** - Inteiro
 O número de coluna do cursor.

```
# Set the CaretPosition.
$psIse.CurrentFile.Editor.SetCaretPosition(5,1)
```

### ToggleOutliningExpansion()
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Faz com que toda a estrutura de tópicos se expanda ou se recolha.

```
# Toggle the outlining expansion
$psIse.CurrentFile.Editor.ToggleOutliningExpansion()

```

## Propriedades

###  <a name="CanGoToMatch"></a> CanGoToMatch
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade booliana de leitura/gravação para indicar se o cursor está ao lado de um parêntese, colchete ou chave – \ (\), \ [\], {}. Se o cursor estiver imediatamente antes do caractere de abertura ou imediatamente após o caractere de fechamento de um par, o valor da propriedade será **$true**. Caso contrário será **$false**.

```
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psIse.CurrentFile.Editor.CanGoToMatch

```

###  <a name="CaretColumn"></a> CaretColumn
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que recebe o número da coluna que corresponde à posição do cursor.

```
# Get the CaretColumn.
$psIse.CurrentFile.Editor.CaretColumn

```

###  <a name="CaretLine"></a> CaretLine
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o número da linha que contém o cursor.

```
# Get the CaretLine.
$psIse.CurrentFile.Editor.CaretLine

```

###  <a name="caretlinetext"></a> CaretLineText
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a linha completa de texto que contém o cursor.

```
# Get all of the text on the line that contains the caret.
$psIse.CurrentFile.Editor.CaretLineText

```

###  <a name="LineCount"></a> LineCount
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a contagem de linha do editor.

```
# Get the LineCount.
$psIse.CurrentFile.Editor.LineCount

```

###  <a name="SelectedText"></a> SelectedText
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o texto selecionado do editor.

 Veja o [Exemplo de script](#example), posteriormente neste tópico.

###  <a name="Text"></a> Texto
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém ou define o texto no editor.

 Veja o [Exemplo de script](#example), posteriormente neste tópico.

##  <a name="example"></a> Exemplo de Script

```

# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase. 
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor=$psIse.CurrentFile.Editor
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

## Consulte Também
 [O objeto ISEFile](The-ISEFile-Object.md) 
 [O objeto PowerShellTab](The-PowerShellTab-Object.md) 
 [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [A hierarquia de modelo do objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


