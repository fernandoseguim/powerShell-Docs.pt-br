---
title: O objeto ISEFile
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
---
# O objeto ISEFile
  Um objeto **ISEFile** representa um arquivo no ISE (Ambiente de Script Integrado) do Windows PowerShell®. É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEFile. Este tópico lista os métodos e as propriedades do membro. O **$psISE.CurrentFile** e os arquivos da coleção de arquivos em uma guia do PowerShell são todas as instâncias da classe Microsoft.PowerShell.Host.ISE.ISEFile.

## Métodos

###  <a name="save-override"></a> Save( [saveEncoding] )
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Salva o arquivo no disco.

 **[saveEncoding]** – opcional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 Um parâmetro de codificação de caractere opcional a ser usado no arquivo salvo. O valor padrão é **UTF8**.

 **Exceções**
 -   **System.IO.IOException**: não foi possível salvar o arquivo.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

###  <a name="saveas"></a> SaveAs(filename, [saveEncoding])
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Salva o arquivo com o nome de arquivo e codificação especificados.

 **filename** \- String
 O nome a ser usado para salvar o arquivo.

 **[saveEncoding]** – opcional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 Um parâmetro de codificação de caractere opcional a ser usado no arquivo salvo. O valor padrão é **UTF8**.

 **Exceções**
 -   **System.ArgumentNullException**: o parâmetro **filename** é nulo.

-   **System.ArgumentException**: o parâmetro **filename** está vazio.

-   **System.IO.IOException**: não foi possível salvar o arquivo.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## Propriedades

###  <a name="Displayname"></a> DisplayName
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a cadeia que contém o nome de exibição deste arquivo. O nome é mostrado na guia **Arquivo** na parte superior do editor. A presença de um asterisco (*) ao final do nome indica que o arquivo tem alterações que não foram salvas.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

###  <a name="Editor"></a> Editor
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o [objeto editor](The-ISEEditor-Object.md) usado para o arquivo especificado.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

###  <a name="Encoding"></a> Codificando
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a codificação original do arquivo. Este é um objeto **System.Text.Encoding**.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

###  <a name="FullPath"></a> FullPath
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a cadeia que especifica o caminho completo do arquivo aberto.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

###  <a name="IsSaved"></a> IsSaved
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade booliana somente leitura que retornará **$true** se o arquivo foi salvo depois de ter sido modificado pela última vez.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

###  <a name="IsUntitled"></a> IsUntitled
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que retorna **$true** se o arquivo nunca recebeu um título.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## Consulte Também
 [O ISEFileCollectionObject](The-ISEFileCollection-Object.md) 
 [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [A hierarquia de modelo do objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


