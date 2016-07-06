---
title: Trabalhando com entradas do Registro
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: d7fb731bc2527e324271bc75f00112a67a1147e3

---

# Trabalhando com entradas do Registro
Como entradas do registro são propriedades de chaves e, como tal, não podem ser navegadas diretamente, precisamos usar uma abordagem ligeiramente diferente ao trabalhar com elas.

### Listando as entradas do registro
Há diversas maneiras de examinar as entradas do registro. A maneira mais simples é obter os nomes de propriedade associados a uma chave. Por exemplo, para ver os nomes das entradas na chave do Registro **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get\-Item**. Chaves do registro possuem uma propriedade com o nome genérico de "Property", que é uma lista de entradas do registro na chave. O comando a seguir seleciona a propriedade Property e expande os itens para que eles sejam exibidos em uma lista:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Para exibir as entradas do Registro em um formato mais legível, use **Get\-ItemProperty**:

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

Todas as propriedades relacionadas ao Windows PowerShell da chave são precedidas por “PS”, como **PSPath**, **PSParentPath**, **PSChildName** e **PSProvider**.

Você pode usar a notação “**.**” para referir-se ao local atual. Você pode usar **Set\-Location** para mudar primeiramente para o contêiner do Registro **CurrentVersion**:

```
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Como alternativa, é possível usar o HKLM PSDrive interno com **Set\-Location**:

```
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Você pode então usar a notação “**.**” para o local atual listar as propriedades sem especificar um caminho completo:

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

A expansão de caminho funciona da mesma maneira que no sistema de arquivos e, portanto, nesse local, é possível obter a listagem de **ItemProperty** para **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** usando **Get\-ItemProperty \-Path ..\\Help**.

### Obtendo uma única entrada de registro
Se você desejar obter uma entrada específica de uma chave do registro, poderá usar várias abordagens. Este exemplo encontra o valor de **DevicePath** em **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.

Com **Get\-ItemProperty**, use o parâmetro **Path** para especificar o nome da chave e o parâmetro **Name** para especificar o nome da entrada **DevicePath**.

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

Esse comando retorna as propriedades padrão do Windows PowerShell, bem como a propriedade **DevicePath**.

> [!NOTE]
> Embora **Get\-ItemProperty** tenha os parâmetros **Filter**, **Include** e **Exclude**, eles não podem ser usados para filtrar pelo nome da propriedade. Esses parâmetros se referem às chaves do registro, (que são caminhos de item e não entradas do registro) que são propriedades do item.

Outra opção é usar a ferramenta de linha de comando Reg.exe. Para obter ajuda com reg.exe, digite **reg.exe \/?** em um prompt de comando. Para localizar a entrada DevicePath, use reg.exe, conforme mostrado no comando a seguir:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Você também pode usar o objeto **WshShell COM** para localizar algumas entradas do Registro, embora esse método não funcione com dados binários grandes ou nomes de entrada do Registro que incluam caracteres como "\\"). Acrescente o nome da propriedade ao caminho do item com um separador \\:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### Criando novas entradas do registro
Para adicionar uma nova entrada denominada “PowerShellPath” à chave **CurrentVersion**, use **New\-ItemProperty** com o caminho para a chave, o nome da entrada e o valor da entrada. Neste exemplo, obtemos o valor da variável do Windows PowerShell **$PSHome**, que armazena o caminho para o diretório de instalação do Windows PowerShell.

Você pode adicionar a nova entrada à chave usando o seguinte comando, e ele também retorna informações sobre a nova entrada:

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

O **PropertyType** deve ter o mesmo nome de um membro da enumeração **Microsoft.Win32.RegistryValueKind** da tabela a seguir:

|Valor de PropertyType|Significado|
|----------------------|-----------|
|Binário|Dados binários|
|DWord|Um número UInt32 válido|
|ExpandString|Uma cadeia de caracteres que pode conter variáveis de ambiente que são expandidos dinamicamente|
|MultiString|Uma cadeia de caracteres de várias linhas|
|Cadeia de caracteres|Qualquer valor de cadeia de caracteres|
|QWord|8 bytes de dados binários|

> [!NOTE]
> Você pode adicionar uma entrada de Registro em vários locais, especificando uma matriz de valores para o parâmetro **Path**:

```
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

Você também pode substituir um valor de entrada do Registro pré-\-existente adicionando o parâmetro **Force** a qualquer comando **New\-ItemProperty**.

### Renomeando entradas do registro
Para renomear a entrada **PowerShellPath** como “PSHome”, use **Rename\-ItemProperty**:

```
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Para exibir o valor renomeado, adicione o parâmetro **PassThru** ao comando.

```
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### Excluindo entradas do registro
Para excluir ambas as entradas do Registro PSHome e PowerShellPath, use **Remove\-ItemProperty**:

```
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```




<!--HONumber=Jun16_HO4-->


