---
title: O objeto ISEFileCollection
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
---
# O objeto ISEFileCollection
  O objeto **ISEFileCollection** é uma coleção de objetos **ISEFile**. Um exemplo é a coleção $psISE.CurrentPowerShellTab.Files.

## Métodos

### Add( [fullPath] )
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Cria e retorna um novo arquivo sem título e o adiciona à coleção. A propriedade **IsUntitled** do arquivo criado recentemente é **$true**.

 **[fullPath]** – Cadeia de caracteres opcional
 O caminho totalmente especificado do arquivo. Uma exceção será gerada se você incluir o parâmetro **fullPath** e um caminho relativo ou se você usar um nome de arquivo em vez do caminho completo.

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### Remove( File, [Force] )
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Remove um arquivo especificado da guia atual do PowerShell.

 **File** – Cadeia de caracteres
 O arquivo ISEFile que você deseja remover da coleção. Se o arquivo não tiver sido salvo, esse método disparará uma exceção. Use o parâmetro de comutador **Force** para forçar a remoção de um arquivo que não foi salvo.

 **[Force]** – Booliano opcional
 Se definido como **$true**, concederá permissão para remover o arquivo mesmo se não tiver sido salvo após a última utilização. O padrão é **$false**.

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### SetSelectedFile( selectedFile )
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Seleciona o arquivo especificado pelo parâmetro **selectedFile**.

 **selectedFile** – Microsoft.PowerShell.Host.ISE.ISEFile
 O arquivo ISEFile que você deseja selecionar.

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## Consulte Também
 [O objeto ISEFile](The-ISEFile-Object.md) 
 [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [A hierarquia de modelo do objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


