---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: O objeto ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 276e8f04a827e18999b5b3ecb08f47de4f4b23b1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951385"
---
# <a name="the-isefile-object"></a>O objeto ISEFile

Um objeto **ISEFile** representa um arquivo no ISE (Ambiente de Script Integrado) do Windows PowerShell®. É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEFile. Este tópico lista os métodos e as propriedades do membro. O **$psISE.CurrentFile** e os arquivos da coleção de arquivos em uma guia do PowerShell são todas as instâncias da classe Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Métodos

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)

Suportado no Windows PowerShell ISE 2.0 e posteriores.

Salva o arquivo no disco.

**\[saveEncoding\]** – [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) opcional Um parâmetro opcional de codificação de caracteres a ser usado para o arquivo salvo. O valor padrão é **UTF8**.

### <a name="exceptions"></a>Exceções

- **System.IO.IOException**: não foi possível salvar o arquivo.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(filename, \[saveEncoding\]\)

Suportado no Windows PowerShell ISE 2.0 e posteriores.

Salva o arquivo com o nome de arquivo e codificação especificados.

**filename** – cadeia de caracteres, o nome a ser usado para salvar o arquivo.

**\[saveEncoding\]** – [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) opcional Um parâmetro opcional de codificação de caracteres a ser usado para o arquivo salvo. O valor padrão é **UTF8**.

### <a name="exceptions"></a>Exceções

- **System.ArgumentNullException**: o parâmetro **filename** é nulo.
- **System.ArgumentException**: o parâmetro **filename** está vazio.
- **System.IO.IOException**: não foi possível salvar o arquivo.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Propriedades

### <a name="displayname"></a>DisplayName

Suportado no Windows PowerShell ISE 2.0 e posteriores.

A propriedade somente leitura que obtém a cadeia que contém o nome de exibição deste arquivo. O nome é mostrado na guia **Arquivo** na parte superior do editor. A presença de um asterisco \(\*\) ao final do nome indica que o arquivo tem alterações que não foram salvas.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Editor

Suportado no Windows PowerShell ISE 2.0 e posteriores.

A propriedade somente leitura que obtém o [objeto editor](The-ISEEditor-Object.md) usado para o arquivo especificado.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Codificando

Suportado no Windows PowerShell ISE 2.0 e posteriores.

A propriedade somente leitura que obtém a codificação original do arquivo. Este é um objeto **System.Text.Encoding**.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Suportado no Windows PowerShell ISE 2.0 e posteriores.

A propriedade somente leitura que obtém a cadeia de caracteres que especifica o caminho completo do arquivo aberto.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

Suportado no Windows PowerShell ISE 2.0 e posteriores.

A propriedade Boolean somente leitura que retornará **$true** se o arquivo foi salvo depois de ter sido modificado pela última vez.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Suportado no Windows PowerShell ISE 2.0 e posteriores.

A propriedade somente leitura que retornará **$true** se o arquivo nunca recebeu um título.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Consulte Também

- [O ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Objetivo do modelo de objeto de script do ISE do Windows PowerShell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)