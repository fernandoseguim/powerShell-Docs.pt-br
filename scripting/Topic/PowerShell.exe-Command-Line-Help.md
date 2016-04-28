---
title: Ajuda da linha de comando do PowerShell.exe
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
---
# Ajuda da linha de comando do PowerShell.exe
Inicia uma sessão do Windows PowerShell. Você pode usar o PowerShell.exe para iniciar uma sessão do Windows PowerShell na linha de comando de outra ferramenta, como Cmd.exe, ou usá-lo na linha de comando do Windows PowerShell para iniciar uma nova sessão. Use os parâmetros para personalizar a sessão.

## Sintaxe

```
PowerShell[.exe]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-InputFormat {Text | XML}] 
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive] 
       [-NoProfile] 
       [-OutputFormat {Text | XML}] 
       [-PSConsoleFile <FilePath> | -Version <Windows PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
       [-File <FilePath> [<Args>]]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

## Parâmetros

### -EncodedCommand <Base64EncodedCommand>
Aceita uma versão de cadeia de caracteres com codificação de base 64 de um comando. Use esse parâmetro para enviar comandos ao Windows PowerShell que exigem aspas complexas ou chaves.

### -ExecutionPolicy <ExecutionPolicy>
Define a política de execução padrão para a sessão atual e o salva-a na variável de ambiente $env:PSExecutionPolicyPreference. Esse parâmetro não altera a política de execução do Windows PowerShell que está definida no Registro. Para obter mais informações sobre as políticas de execução do Windows PowerShell, incluindo uma lista de valores válidos, consulte about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).

### -File <FilePath> [<Parameters>]
Executa o script especificado no escopo local ("dot-sourced"), para que as funções e variáveis que o script criar estejam disponíveis na sessão atual. Insira o caminho do arquivo de script e quaisquer parâmetros. **File** deve ser o último parâmetro no comando, pois todos os caracteres digitados após nome do parâmetro **File** são interpretados como o caminho do arquivo de script seguido pelos parâmetros do script e seus valores.

Você pode incluir os parâmetros de um script e os valores de parâmetro no valor do parâmetro **File**. Por exemplo: `-File .\Get-Script.ps1 -Domain Central`

Normalmente, os parâmetros de opção de um script são incluídos ou omitidos. Por exemplo, o comando a seguir usa o parâmetro **All** do arquivo de script Get-Script.ps1: `-File .\Get-Script.ps1 -All`

Em casos raros, pode ser necessário fornecer um valor booliano para um parâmetro de opção. Para fornecer um valor booliano para um parâmetro de opção no valor do parâmetro **File**, coloque o nome do parâmetro e o valor entre chaves, desta forma: `-File .\Get-Script.ps1 {-All:$False}`

### -InputFormat {Text | XML}
Descreve o formato dos dados enviados ao Windows PowerShell. Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).

### -Mta
Inicia o Windows PowerShell usando um multi-threaded apartment. [!INCLUDE[ps_sdk_paramintrodps3](../Token/ps_sdk_paramintrodps3_md.md)] No [!INCLUDE[psversion3](../Token/psversion3_md.md)], o STA (Single-Threaded Apartment) é o padrão. No [!INCLUDE[psversion2](../Token/psversion2_md.md)], MTA (Multi-Threaded Apartment) é o padrão.

### -NoExit
Não é encerrado depois de executar comandos de inicialização.

### -NoLogo
Oculta a faixa de direitos autorais na inicialização.

### -NonInteractive
Não exibe um prompt interativo para o usuário.

### -NoProfile
Não carrega o perfil do Windows PowerShell.

### -OutputFormat {Text | XML}
Determina como a saída do Windows PowerShell é formatada. Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).

### -PSConsoleFile <FilePath>
Carrega o arquivo do console do Windows PowerShell especificado. Insira o caminho e o nome do arquivo de console. Para criar um arquivo de console, use o cmdlet [Export-Console](assetId:///4bab1c02-9e61-4aaf-9957-11d1934ef4ef) do Windows PowerShell.

### -Sta
Inicia o Windows PowerShell usando um single-threaded apartment. No [!INCLUDE[psversion3](../Token/psversion3_md.md)], o STA (Single-Threaded Apartment) é o padrão. No [!INCLUDE[psversion2](../Token/psversion2_md.md)], MTA (Multi-Threaded Apartment) é o padrão.

### -Version <Windows PowerShell Version>
Inicia a versão especificada do Windows PowerShell. A versão que você especificar deve estar instalada no sistema. Se [!INCLUDE[psversion3](../Token/psversion3_md.md)] estiver instalado no computador, os valores válidos serão "2.0" e "3.0". O valor padrão é “3.0”.

Se [!INCLUDE[psversion3](../Token/psversion3_md.md)] não estiver instalado, o único valor válido será "2.0". Outros valores são ignorados.

Para obter mais informações, consulte "Instalar o Windows PowerShell" na [Introdução ao Fluxo de Trabalho do Windows PowerShell [MSDN ANTIGO]](assetId:///69555d95-b481-43e1-86e7-b46d68b3e2dd).

### -WindowStyle <Window style>
Define o estilo da janela da sessão. Os valores válidos são Normal, Minimized, Maximized e Hidden.

### -Command
Executa os comandos especificados (e quaisquer parâmetros) da maneira como eles foram digitados no prompt de comando do Windows PowerShell e, em seguida, encerra a sessão, a menos que o parâmetro NoExit seja especificado.

O valor do Comando pode ser "-", uma cadeia de caracteres. ou um bloco de script. Se o valor do comando for "-", o texto do comando será lido da entrada padrão.

Blocos de script devem ser colocados entre chaves ({}). Você pode especificar um bloco de script apenas quando o PowerShell.exe no Windows PowerShell estiver em execução. Os resultados do script são retornados para o shell pai como objetos XML desserializados, não objetos vivos.

Se o valor do comando for uma cadeia de caracteres, **Command** deverá ser o último parâmetro no comando, pois qualquer caractere digitado depois do comando será interpretado como os argumentos de comando.

Para gravar uma cadeia de caracteres que executa um comando do Windows PowerShell, use o formato:

```
"& {<command>}"
```

no qual as aspas indicam uma cadeia de caracteres e o operador de invocação (&) faz com que o comando seja executado.

### -Help, -?, /?
Mostra esta mensagem. Se você estiver digitando um comando do PowerShell.exe no Windows PowerShell, adicione um hífen (-) ao início dos parâmetros do comando, não uma barra "/". Você pode usar um hífen ou uma barra "/" no Cmd.exe.

> [!NOTE]
> Observação de solução de problemas: no Windows PowerShell 2.0, a inicialização de alguns programas no console do Windows PowerShell falha com um LastExitCode 0xc0000142.

## EXEMPLOS

```
PowerShell -PSConsoleFile sqlsnapin.psc1

PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

PowerShell -Command {Get-EventLog -LogName security}

PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```



<!--HONumber=Apr16_HO1-->


