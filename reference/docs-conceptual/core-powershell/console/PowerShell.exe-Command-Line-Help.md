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
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="b7dc8-103">Ajuda da linha de comando do PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="b7dc8-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="b7dc8-104">É possível usar o PowerShell.exe para iniciar uma sessão do PowerShell na linha de comando de outra ferramenta, como Cmd.exe, ou usá-lo na linha de comando do PowerShell para iniciar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="b7dc8-105">Use os parâmetros para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7dc8-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7dc8-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="b7dc8-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7dc8-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="b7dc8-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="b7dc8-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="b7dc8-109">Aceita uma versão de cadeia de caracteres com codificação de base 64 de um comando.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="b7dc8-110">Use esse parâmetro para enviar comandos ao PowerShell que exigem aspas ou chaves complexas.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="b7dc8-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="b7dc8-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="b7dc8-112">Define a política de execução padrão para a sessão atual e o salva-a na variável de ambiente $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="b7dc8-113">Esse parâmetro não altera a política de execução do PowerShell definida no Registro.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="b7dc8-114">Para saber mais sobre as políticas de execução do PowerShell, inclusive uma lista de valores válidos, confira [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="b7dc8-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="b7dc8-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="b7dc8-116">Executa o script especificado no escopo local ("dot-sourced") para que as funções e variáveis que o script criar estejam disponíveis na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="b7dc8-117">Insira o caminho do arquivo de script e quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="b7dc8-118">**File** deve ser o último parâmetro no comando.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="b7dc8-119">Todos os valores digitados após o parâmetro **-File** são interpretados como o caminho do arquivo de script e os parâmetros passados para esse script.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="b7dc8-120">Os parâmetros passados para o script são passados como cadeias de caracteres literais (após a interpretação do shell atual).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="b7dc8-121">Por exemplo, se você estiver em cmd.exe e quiser passar um valor de variável de ambiente, você usaria a sintaxe cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="b7dc8-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="b7dc8-122">Em contraste, executando `powershell.exe -File .\test.ps1 -TestParam $env:windir` nos resultados de cmd.exe no script de recebimento de cadeia de caracteres literal `$env:windir` porque ele não tem significado especial para o shell cmd.exe atual.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="b7dc8-123">O `$env:windir` estilo de referência de variável de ambiente _pode_ ser usada dentro de um `-Command` parâmetro, uma vez que existe, ele será interpretado como código do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="b7dc8-124">\-InputFormat {Texto | XML}</span><span class="sxs-lookup"><span data-stu-id="b7dc8-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="b7dc8-125">Descreve o formato dos dados enviados ao PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="b7dc8-126">Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="b7dc8-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="b7dc8-127">-Mta</span></span>

<span data-ttu-id="b7dc8-128">Inicia o PowerShell usando um multi-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="b7dc8-129">Este parâmetro é introduzido no PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="b7dc8-130">No PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="b7dc8-131">No PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="b7dc8-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="b7dc8-132">-NoExit</span></span>

<span data-ttu-id="b7dc8-133">Não sai depois de executar comandos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="b7dc8-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="b7dc8-134">-NoLogo</span></span>

<span data-ttu-id="b7dc8-135">Oculta a faixa de direitos autorais na inicialização.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="b7dc8-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="b7dc8-136">-NonInteractive</span></span>

<span data-ttu-id="b7dc8-137">Não exibe um prompt interativo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="b7dc8-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="b7dc8-138">-NoProfile</span></span>

<span data-ttu-id="b7dc8-139">Não carrega o perfil do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="b7dc8-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="b7dc8-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="b7dc8-141">Determina como a saída do PowerShell é formatada.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="b7dc8-142">Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="b7dc8-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="b7dc8-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="b7dc8-144">Carrega o arquivo de console do PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="b7dc8-145">Insira o caminho e o nome do arquivo de console.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="b7dc8-146">Para criar um arquivo de console, use o cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="b7dc8-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="b7dc8-147">-Sta</span></span>

<span data-ttu-id="b7dc8-148">Inicia o PowerShell usando um single-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="b7dc8-149">No PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="b7dc8-150">No PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="b7dc8-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="b7dc8-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="b7dc8-152">Inicia a versão especificada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="b7dc8-153">A versão que você especificar deve estar instalada no sistema.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="b7dc8-154">Se o PowerShell 3.0 estiver instalado no computador, os valores válidos serão "2.0" e "3.0".</span><span class="sxs-lookup"><span data-stu-id="b7dc8-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="b7dc8-155">O valor padrão é “3.0”.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-155">The default value is "3.0".</span></span>

<span data-ttu-id="b7dc8-156">Se o PowerShell 3.0 não estiver instalado, o único valor válido será "2.0".</span><span class="sxs-lookup"><span data-stu-id="b7dc8-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="b7dc8-157">Outros valores são ignorados.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-157">Other values are ignored.</span></span>

<span data-ttu-id="b7dc8-158">Para saber mais, consulte [Instalar o Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="b7dc8-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="b7dc8-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="b7dc8-160">Define o estilo da janela da sessão.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-160">Sets the window style for the session.</span></span> <span data-ttu-id="b7dc8-161">Os valores válidos são Normal, Minimized, Maximized e Hidden.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="b7dc8-162">-Command</span><span class="sxs-lookup"><span data-stu-id="b7dc8-162">-Command</span></span>

<span data-ttu-id="b7dc8-163">Executa os comandos especificados (com quaisquer parâmetros) como se eles fossem digitados no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="b7dc8-164">Após a execução, PowerShell é encerrado, a menos que o **NoExit** parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="b7dc8-165">Qualquer texto após `-Command` é enviado como uma única linha de comando para o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="b7dc8-166">Isso é diferente de como o `-File` manipula os parâmetros enviados a um script.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="b7dc8-167">O valor de `-Command` pode ser "-", uma cadeia de caracteres ou um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="b7dc8-168">Os resultados do comando são retornados para o shell pai como objetos XML desserializados, não objetos vivos.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="b7dc8-169">Se o valor de `-Command` é "-", o texto do comando será lido da entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="b7dc8-170">Quando o valor de `-Command` é uma cadeia de caracteres **comando** _deve_ ser o último parâmetro especificado, pois qualquer caractere digitado depois do comando será interpretado como os argumentos de comando.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="b7dc8-171">O **comando** parâmetro aceita apenas um bloco de script para execução quando ele pode reconhecer o valor passado para `-Command` como um tipo de ScriptBlock.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="b7dc8-172">Isso é _apenas_ possível durante a execução PowerShell.exe do outro host do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="b7dc8-173">O ScriptBlock tipo pode estar contido em um existente, analisado pelo PowerShell, retornado de uma expressão ou variável de host como um bloco de script literal entre chaves `{}`, antes de ser passado para PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="b7dc8-174">Em cmd.exe, há algo como um bloco de script (ou tipo ScriptBlock), portanto, o valor passado para **comando** serão _sempre_ ser uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="b7dc8-175">Você pode escrever um bloco de script dentro de cadeia de caracteres, mas em vez de que está sendo executado ele se comportará exatamente como se você tivesse digitado-lo em um prompt do PowerShell típico, imprimir o conteúdo do script de saída de bloqueio volta para você.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="b7dc8-176">Uma cadeia de caracteres passada para `-Command` ainda serão executadas como PowerShell, portanto, as chaves de bloco script geralmente não são necessárias em primeiro lugar durante a execução do cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="b7dc8-177">Para executar um bloco de script embutido definido dentro de uma cadeia de caracteres, o [operador de chamada](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` pode ser usado:</span><span class="sxs-lookup"><span data-stu-id="b7dc8-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="b7dc8-178">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="b7dc8-178">-Help, -?, /?</span></span>

<span data-ttu-id="b7dc8-179">Mostra a sintaxe de powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="b7dc8-180">Se você estiver digitando um comando do PowerShell.exe no PowerShell, adicione um hífen (-) ao início dos parâmetros do comando, não uma barra (/).</span><span class="sxs-lookup"><span data-stu-id="b7dc8-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="b7dc8-181">Você pode usar um hífen ou uma barra "/" no Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="b7dc8-182">Observação de solução de problemas: no PowerShell 2.0, a inicialização de alguns programas no console do Windows PowerShell falha com um LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="b7dc8-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="b7dc8-183">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="b7dc8-183">EXAMPLES</span></span>

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
