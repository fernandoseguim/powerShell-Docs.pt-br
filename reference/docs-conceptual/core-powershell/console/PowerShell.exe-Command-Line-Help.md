---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Ajuda da linha de comando do PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 03c7672ee72698fe88a73e99702ceaadf87e702f
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51691823"
---
# <a name="powershellexe-command-line-help"></a>Ajuda da linha de comando do PowerShell.exe

É possível usar o PowerShell.exe para iniciar uma sessão do PowerShell na linha de comando de outra ferramenta, como Cmd.exe, ou usá-lo na linha de comando do PowerShell para iniciar uma nova sessão. Use os parâmetros para personalizar a sessão.

## <a name="syntax"></a>Sintaxe

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>Parâmetros

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Aceita uma versão de cadeia de caracteres com codificação de base 64 de um comando. Use esse parâmetro para enviar comandos ao PowerShell que exigem aspas ou chaves complexas.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Define a política de execução padrão para a sessão atual e o salva-a na variável de ambiente $env:PSExecutionPolicyPreference. Esse parâmetro não altera a política de execução do PowerShell definida no Registro. Para saber mais sobre as políticas de execução do PowerShell, inclusive uma lista de valores válidos, confira [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]

Executa o script especificado no escopo local ("dot-sourced") para que as funções e variáveis que o script criar estejam disponíveis na sessão atual. Insira o caminho do arquivo de script e quaisquer parâmetros. **File** deve ser o último parâmetro no comando. Todos os valores digitados após o parâmetro **-File** são interpretados como o caminho do arquivo de script e os parâmetros passados para esse script.

Os parâmetros passados para o script são passados como cadeias de caracteres literais (após a interpretação do shell atual). Por exemplo, se você estiver em cmd.exe e quiser passar um valor de variável de ambiente, você usaria a sintaxe cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`

Em contraste, executando `powershell.exe -File .\test.ps1 -TestParam $env:windir` nos resultados de cmd.exe no script de recebimento de cadeia de caracteres literal `$env:windir` porque ele não tem significado especial para o shell cmd.exe atual.
O `$env:windir` estilo de referência de variável de ambiente _pode_ ser usada dentro de um `-Command` parâmetro, uma vez que existe, ele será interpretado como código do PowerShell.

### <a name="-inputformat-text--xml"></a>\-InputFormat {Texto | XML}

Descreve o formato dos dados enviados ao PowerShell. Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).

### <a name="-mta"></a>-Mta

Inicia o PowerShell usando um multi-threaded apartment. Este parâmetro é introduzido no PowerShell 3.0. No PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão. No PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.

### <a name="-noexit"></a>-NoExit

Não sai depois de executar comandos de inicialização.

### <a name="-nologo"></a>-NoLogo

Oculta a faixa de direitos autorais na inicialização.

### <a name="-noninteractive"></a>-NonInteractive

Não exibe um prompt interativo para o usuário.

### <a name="-noprofile"></a>-NoProfile

Não carrega o perfil do PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

Determina como a saída do PowerShell é formatada. Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Carrega o arquivo de console do PowerShell especificado. Insira o caminho e o nome do arquivo de console. Para criar um arquivo de console, use o cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) no PowerShell.

### <a name="-sta"></a>-Sta

Inicia o PowerShell usando um single-threaded apartment. No PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão. No PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

Inicia a versão especificada do PowerShell. A versão que você especificar deve estar instalada no sistema. Se o PowerShell 3.0 estiver instalado no computador, os valores válidos serão "2.0" e "3.0". O valor padrão é “3.0”.

Se o PowerShell 3.0 não estiver instalado, o único valor válido será "2.0". Outros valores são ignorados.

Para saber mais, consulte [Instalar o Windows PowerShell](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Define o estilo da janela da sessão. Os valores válidos são Normal, Minimized, Maximized e Hidden.

### <a name="-command"></a>-Command

Executa os comandos especificados (com quaisquer parâmetros) como se eles fossem digitados no prompt de comando do PowerShell.
Após a execução, PowerShell é encerrado, a menos que o **NoExit** parâmetro for especificado.
Qualquer texto após `-Command` é enviado como uma única linha de comando para o PowerShell.
Isso é diferente de como o `-File` manipula os parâmetros enviados a um script.

O valor de `-Command` pode ser "-", uma cadeia de caracteres ou um bloco de script.
Os resultados do comando são retornados para o shell pai como objetos XML desserializados, não objetos vivos.

Se o valor de `-Command` é "-", o texto do comando será lido da entrada padrão.

Quando o valor de `-Command` é uma cadeia de caracteres **comando** _deve_ ser o último parâmetro especificado, pois qualquer caractere digitado depois do comando será interpretado como os argumentos de comando.

O **comando** parâmetro aceita apenas um bloco de script para execução quando ele pode reconhecer o valor passado para `-Command` como um tipo de ScriptBlock.
Isso é _apenas_ possível durante a execução PowerShell.exe do outro host do PowerShell.
O ScriptBlock tipo pode estar contido em um existente, analisado pelo PowerShell, retornado de uma expressão ou variável de host como um bloco de script literal entre chaves `{}`, antes de ser passado para PowerShell.exe.

Em cmd.exe, há algo como um bloco de script (ou tipo ScriptBlock), portanto, o valor passado para **comando** serão _sempre_ ser uma cadeia de caracteres.
Você pode escrever um bloco de script dentro de cadeia de caracteres, mas em vez de que está sendo executado ele se comportará exatamente como se você tivesse digitado-lo em um prompt do PowerShell típico, imprimir o conteúdo do script de saída de bloqueio volta para você.

Uma cadeia de caracteres passada para `-Command` ainda serão executadas como PowerShell, portanto, as chaves de bloco script geralmente não são necessárias em primeiro lugar durante a execução do cmd.exe.
Para executar um bloco de script embutido definido dentro de uma cadeia de caracteres, o [operador de chamada](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` pode ser usado:

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

Mostra a sintaxe de powershell.exe. Se você estiver digitando um comando do PowerShell.exe no PowerShell, adicione um hífen (-) ao início dos parâmetros do comando, não uma barra (/). Você pode usar um hífen ou uma barra "/" no Cmd.exe.

> [!NOTE]
> Observação de solução de problemas: no PowerShell 2.0, a inicialização de alguns programas no console do Windows PowerShell falha com um LastExitCode 0xc0000142.

## <a name="examples"></a>EXEMPLOS

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
