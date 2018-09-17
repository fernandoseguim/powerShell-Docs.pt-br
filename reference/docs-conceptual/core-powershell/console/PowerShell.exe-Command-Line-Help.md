---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Ajuda da linha de comando do PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133065"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="70a52-103">Ajuda da linha de comando do PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="70a52-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="70a52-104">É possível usar o PowerShell.exe para iniciar uma sessão do PowerShell na linha de comando de outra ferramenta, como Cmd.exe, ou usá-lo na linha de comando do PowerShell para iniciar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="70a52-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="70a52-105">Use os parâmetros para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="70a52-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="70a52-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70a52-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="70a52-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70a52-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="70a52-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="70a52-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="70a52-109">Aceita uma versão de cadeia de caracteres com codificação de base 64 de um comando.</span><span class="sxs-lookup"><span data-stu-id="70a52-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="70a52-110">Use esse parâmetro para enviar comandos ao PowerShell que exigem aspas ou chaves complexas.</span><span class="sxs-lookup"><span data-stu-id="70a52-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="70a52-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="70a52-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="70a52-112">Define a política de execução padrão para a sessão atual e o salva-a na variável de ambiente $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="70a52-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="70a52-113">Esse parâmetro não altera a política de execução do PowerShell definida no Registro.</span><span class="sxs-lookup"><span data-stu-id="70a52-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="70a52-114">Para saber mais sobre as políticas de execução do PowerShell, inclusive uma lista de valores válidos, confira [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="70a52-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="70a52-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="70a52-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="70a52-116">Executa o script especificado no escopo local ("dot-sourced") para que as funções e variáveis que o script criar estejam disponíveis na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="70a52-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="70a52-117">Insira o caminho do arquivo de script e quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="70a52-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="70a52-118">**File** deve ser o último parâmetro no comando.</span><span class="sxs-lookup"><span data-stu-id="70a52-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="70a52-119">Todos os valores digitados após o parâmetro **-File** são interpretados como o caminho do arquivo de script e os parâmetros passados para esse script.</span><span class="sxs-lookup"><span data-stu-id="70a52-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="70a52-120">Os parâmetros passados para o script são passados como cadeias de caracteres literais (após a interpretação do shell atual).</span><span class="sxs-lookup"><span data-stu-id="70a52-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="70a52-121">Por exemplo, se você estiver no cmd.exe e quiser para passar um valor de variável de ambiente, use a sintaxe do cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` Neste exemplo, o script recebe a cadeia de caracteres literal `$env:windir` e não o valor dessa variável de ambiente: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="70a52-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="70a52-122">\-InputFormat {Texto | XML}</span><span class="sxs-lookup"><span data-stu-id="70a52-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="70a52-123">Descreve o formato dos dados enviados ao PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70a52-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="70a52-124">Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="70a52-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="70a52-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="70a52-125">-Mta</span></span>

<span data-ttu-id="70a52-126">Inicia o PowerShell usando um multi-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="70a52-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="70a52-127">Este parâmetro é introduzido no PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="70a52-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="70a52-128">No PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="70a52-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="70a52-129">No PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="70a52-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="70a52-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="70a52-130">-NoExit</span></span>

<span data-ttu-id="70a52-131">Não sai depois de executar comandos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="70a52-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="70a52-132">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="70a52-132">-NoLogo</span></span>

<span data-ttu-id="70a52-133">Oculta a faixa de direitos autorais na inicialização.</span><span class="sxs-lookup"><span data-stu-id="70a52-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="70a52-134">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="70a52-134">-NonInteractive</span></span>

<span data-ttu-id="70a52-135">Não exibe um prompt interativo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="70a52-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="70a52-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="70a52-136">-NoProfile</span></span>

<span data-ttu-id="70a52-137">Não carrega o perfil do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70a52-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="70a52-138">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="70a52-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="70a52-139">Determina como a saída do PowerShell é formatada.</span><span class="sxs-lookup"><span data-stu-id="70a52-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="70a52-140">Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="70a52-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="70a52-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="70a52-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="70a52-142">Carrega o arquivo de console do PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="70a52-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="70a52-143">Insira o caminho e o nome do arquivo de console.</span><span class="sxs-lookup"><span data-stu-id="70a52-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="70a52-144">Para criar um arquivo de console, use o cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70a52-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="70a52-145">-Sta</span><span class="sxs-lookup"><span data-stu-id="70a52-145">-Sta</span></span>

<span data-ttu-id="70a52-146">Inicia o PowerShell usando um single-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="70a52-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="70a52-147">No PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="70a52-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="70a52-148">No PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="70a52-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="70a52-149">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="70a52-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="70a52-150">Inicia a versão especificada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70a52-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="70a52-151">A versão que você especificar deve estar instalada no sistema.</span><span class="sxs-lookup"><span data-stu-id="70a52-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="70a52-152">Se o PowerShell 3.0 estiver instalado no computador, os valores válidos serão "2.0" e "3.0".</span><span class="sxs-lookup"><span data-stu-id="70a52-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="70a52-153">O valor padrão é “3.0”.</span><span class="sxs-lookup"><span data-stu-id="70a52-153">The default value is "3.0".</span></span>

<span data-ttu-id="70a52-154">Se o PowerShell 3.0 não estiver instalado, o único valor válido será "2.0".</span><span class="sxs-lookup"><span data-stu-id="70a52-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="70a52-155">Outros valores são ignorados.</span><span class="sxs-lookup"><span data-stu-id="70a52-155">Other values are ignored.</span></span>

<span data-ttu-id="70a52-156">Para saber mais, consulte [Instalar o Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="70a52-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="70a52-157">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="70a52-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="70a52-158">Define o estilo da janela da sessão.</span><span class="sxs-lookup"><span data-stu-id="70a52-158">Sets the window style for the session.</span></span> <span data-ttu-id="70a52-159">Os valores válidos são Normal, Minimized, Maximized e Hidden.</span><span class="sxs-lookup"><span data-stu-id="70a52-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="70a52-160">-Command</span><span class="sxs-lookup"><span data-stu-id="70a52-160">-Command</span></span>

<span data-ttu-id="70a52-161">Executa os comandos especificados (com quaisquer parâmetros) como se eles fossem digitados no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70a52-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="70a52-162">Após a execução, o PowerShell é encerrado, a menos que o parâmetro `-NoExit` tenha sido especificado.</span><span class="sxs-lookup"><span data-stu-id="70a52-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="70a52-163">Qualquer texto após `-Command` é enviado como uma única linha de comando para o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70a52-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="70a52-164">Isso é diferente de como o `-File` manipula os parâmetros enviados a um script.</span><span class="sxs-lookup"><span data-stu-id="70a52-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="70a52-165">O valor do Comando pode ser "-", uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="70a52-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="70a52-166">ou um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="70a52-166">or a script block.</span></span> <span data-ttu-id="70a52-167">Se o valor do comando for "-", o texto do comando será lido da entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="70a52-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="70a52-168">Os blocos de script devem ser colocados entre chaves ({}).</span><span class="sxs-lookup"><span data-stu-id="70a52-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="70a52-169">Será possível especificar um bloco de script apenas quando o PowerShell.exe no PowerShell estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="70a52-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="70a52-170">Os resultados do script são retornados para o shell pai como objetos XML desserializados, não objetos vivos.</span><span class="sxs-lookup"><span data-stu-id="70a52-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="70a52-171">Se o valor do comando for uma cadeia de caracteres, **Command** deverá ser o último parâmetro no comando, pois qualquer caractere digitado depois do comando será interpretado como os argumentos do comando.</span><span class="sxs-lookup"><span data-stu-id="70a52-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="70a52-172">Para gravar uma cadeia de caracteres que executa um comando do PowerShell, use o formato:</span><span class="sxs-lookup"><span data-stu-id="70a52-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="70a52-173">As aspas indicam uma cadeia de caracteres e o operador de invocação (&) faz com que o comando seja executado.</span><span class="sxs-lookup"><span data-stu-id="70a52-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="70a52-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="70a52-174">-Help, -?, /?</span></span>

<span data-ttu-id="70a52-175">Mostra a sintaxe de powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="70a52-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="70a52-176">Se você estiver digitando um comando do PowerShell.exe no PowerShell, adicione um hífen (-) ao início dos parâmetros do comando, não uma barra (/).</span><span class="sxs-lookup"><span data-stu-id="70a52-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="70a52-177">Você pode usar um hífen ou uma barra "/" no Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="70a52-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="70a52-178">Observação de solução de problemas: no PowerShell 2.0, a inicialização de alguns programas no console do Windows PowerShell falha com um LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="70a52-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="70a52-179">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="70a52-179">EXAMPLES</span></span>

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
