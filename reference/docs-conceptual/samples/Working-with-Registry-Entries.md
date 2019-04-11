---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Trabalhando com entradas do Registro
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 667d17d0d62745a27ffef5f1912336b72f74c2a9
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293071"
---
# <a name="working-with-registry-entries"></a>Trabalhando com entradas do Registro

Como entradas do registro são propriedades de chaves e, como tal, não podem ser navegadas diretamente, precisamos usar uma abordagem ligeiramente diferente ao trabalhar com elas.

## <a name="listing-registry-entries"></a>Listando as entradas do registro

Há diversas maneiras de examinar as entradas do registro. A maneira mais simples é obter os nomes de propriedade associados a uma chave. Por exemplo, para ver os nomes das entradas na chave do registro `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`. Chaves do registro possuem uma propriedade com o nome genérico de "Property", que é uma lista de entradas do registro na chave.
O comando a seguir seleciona a propriedade Property e expande os itens para que eles sejam exibidos em uma lista:

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Para exibir as entradas do Registro em um formato mais legível, use `Get-ItemProperty`:

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

Todas as propriedades relacionadas ao Windows PowerShell para a chave são precedidas por "PS", tal como **PSPath**, **PSParentPath**, **PSChildName** e **PSProvider**.

Você pode usar a notação `*.*` para se referir ao local atual. Você pode usar `Set-Location` para primeiro mudar para o contêiner do registro **CurrentVersion**:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Como alternativa, você pode usar o HKLM PSDrive interno com `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Você pode então usar a notação `*.*` para o local atual listar as propriedades sem especificar um caminho completo:

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

A expansão de caminho funciona da mesma maneira que no sistema de arquivos e, portanto, nesse local, é possível obter a listagem de **ItemProperty** para `HKLM:\SOFTWARE\Microsoft\Windows\Help` usando `Get-ItemProperty -Path ..\Help`.

## <a name="getting-a-single-registry-entry"></a>Obtendo uma única entrada de registro

Se você desejar obter uma entrada específica de uma chave do registro, poderá usar várias abordagens. Este exemplo localiza o valor de **DevicePath** em `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Com `Get-ItemProperty`, use o parâmetro **Path** para especificar o nome da chave e o parâmetro **Name** para especificar o nome da entrada **DevicePath**.

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
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
> Embora `Get-ItemProperty` tenha os parâmetros **Filter**, **Include** e **Exclude**, eles não podem ser usados para filtrar pelo nome da propriedade. Esses parâmetros se referem às chaves do registro, que são caminhos de item e não entradas do registro. Entradas de registro são propriedades do item.

Outra opção é usar a ferramenta de linha de comando Reg.exe. Para obter ajuda com reg.exe, digite `reg.exe /?` em um prompt de comando. Para localizar a entrada DevicePath, use reg.exe, conforme mostrado no comando a seguir:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Você também pode usar o objeto COM **WshShell** para localizar algumas entradas do registro, embora esse método não funcione com dados binários grandes ou nomes de entrada do Registro que incluam caracteres como "\\"). Acrescente o nome da propriedade ao caminho do item com um separador \\:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a>Configuração de uma única entrada de registro

Se você quiser obter uma entrada específica em uma chave do registro, pode usar várias abordagens. Este exemplo modifica a entrada **Path** em `HKEY_CURRENT_USER\Environment`. A entrada **Path** especifica onde localizar os arquivos executáveis.

1. Recupere o valor atual da entrada **Path** usando `Get-ItemProperty`.
2. Adicionar o novo valor, separando-o com um `;`.
3. Use `Set-ItemProperty` com a chave especificada, o nome da entrada e o valor para modificar a entrada do registro.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Embora `Set-ItemProperty` tenha os parâmetros **Filter**, **Include** e **Exclude**, eles não podem ser usados para filtrar pelo nome da propriedade. Esses parâmetros se referem às chaves do registro, (que são caminhos de item e não entradas do registro) que são propriedades do item.

Outra opção é usar a ferramenta de linha de comando Reg.exe. Para obter ajuda com reg.exe, digite **reg.exe /?**
em um prompt de comando.

O exemplo a seguir altera a entrada **Path** ao remover o caminho adicionado no exemplo acima.
`Get-ItemProperty` ainda é usado para recuperar o valor atual para evitar ter que analisar a cadeia de caracteres retornada de `reg query`. Os métodos **SubString** e **LastIndexOf** são usados para recuperar o último caminho adicionado à entrada **Path**.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a>Criando novas entradas do registro

Para adicionar uma nova entrada denominada "PowerShellPath" à chave **CurrentVersion**, use `New-ItemProperty` com o caminho para a chave, o nome da entrada e o valor da entrada. Neste exemplo, obtemos o valor da variável `$PSHome` do Windows PowerShell, que armazena o caminho para o diretório de instalação do Windows PowerShell.

Você pode adicionar a nova entrada à chave usando o seguinte comando, e ele também retorna informações sobre a nova entrada:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
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

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Você também pode substituir um valor de entrada do registro pré-existente adicionando o parâmetro **Force** a qualquer comando `New-ItemProperty`.

## <a name="renaming-registry-entries"></a>Renomeando entradas do registro

Para renomear a entrada **PowerShellPath** como "PSHome", use `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Para exibir o valor renomeado, adicione o parâmetro **PassThru** ao comando.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a>Excluindo entradas do registro

Para excluir as duas entradas do registro PSHome e PowerShellPath, use `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
