---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Ajuda da linha de comando do PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952572"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="dbd43-103">Ajuda da linha de comando do PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="dbd43-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="dbd43-104">É possível usar o PowerShell.exe para iniciar uma sessão do PowerShell na linha de comando de outra ferramenta, como Cmd.exe, ou usá-lo na linha de comando do PowerShell para iniciar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="dbd43-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="dbd43-105">Use os parâmetros para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="dbd43-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="dbd43-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbd43-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="dbd43-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dbd43-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="dbd43-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="dbd43-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="dbd43-109">Aceita uma versão de cadeia de caracteres com codificação de base 64 de um comando.</span><span class="sxs-lookup"><span data-stu-id="dbd43-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="dbd43-110">Use esse parâmetro para enviar comandos ao PowerShell que exigem aspas ou chaves complexas.</span><span class="sxs-lookup"><span data-stu-id="dbd43-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="dbd43-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="dbd43-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="dbd43-112">Define a política de execução padrão para a sessão atual e o salva-a na variável de ambiente $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="dbd43-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="dbd43-113">Esse parâmetro não altera a política de execução do PowerShell definida no Registro.</span><span class="sxs-lookup"><span data-stu-id="dbd43-113">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="dbd43-114">Para saber mais sobre as políticas de execução do PowerShell, inclusive uma lista de valores válidos, confira [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="dbd43-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="dbd43-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="dbd43-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="dbd43-116">Executa o script especificado no escopo local ("dot-sourced") para que as funções e variáveis que o script criar estejam disponíveis na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="dbd43-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="dbd43-117">Insira o caminho do arquivo de script e quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="dbd43-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="dbd43-118">**File** deve ser o último parâmetro no comando, pois todos os caracteres digitados após nome do parâmetro **File** são interpretados como o caminho do arquivo de script seguido pelos parâmetros do script e seus valores.</span><span class="sxs-lookup"><span data-stu-id="dbd43-118">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="dbd43-119">Você pode incluir os parâmetros de um script e os valores de parâmetro no valor do parâmetro **File**.</span><span class="sxs-lookup"><span data-stu-id="dbd43-119">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="dbd43-120">Por exemplo: `-File .\Get-Script.ps1 -Domain Central` Observe que os parâmetros passados para o script são passados como cadeias de caracteres literais (após a interpretação do shell atual).</span><span class="sxs-lookup"><span data-stu-id="dbd43-120">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="dbd43-121">Por exemplo, se você estiver no cmd.exe e quiser para passar um valor de variável de ambiente, use a sintaxe do cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` Se você usar a sintaxe do PowerShell, neste exemplo, o script receberá o literal "$env:windir" e não o valor dessa variável de ambiente: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="dbd43-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="dbd43-122">Normalmente, os parâmetros de opção de um script são incluídos ou omitidos.</span><span class="sxs-lookup"><span data-stu-id="dbd43-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="dbd43-123">Por exemplo, o comando a seguir usa o parâmetro **All** do arquivo de script Get-Script.ps1: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="dbd43-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="dbd43-124">\-InputFormat {Texto | XML}</span><span class="sxs-lookup"><span data-stu-id="dbd43-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="dbd43-125">Descreve o formato dos dados enviados ao PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbd43-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="dbd43-126">Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="dbd43-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="dbd43-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="dbd43-127">-Mta</span></span>

<span data-ttu-id="dbd43-128">Inicia o PowerShell usando um multi-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="dbd43-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="dbd43-129">Este parâmetro é introduzido no PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="dbd43-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="dbd43-130">No PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="dbd43-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="dbd43-131">No PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="dbd43-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="dbd43-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="dbd43-132">-NoExit</span></span>

<span data-ttu-id="dbd43-133">Não é encerrado depois de executar comandos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="dbd43-133">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="dbd43-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="dbd43-134">-NoLogo</span></span>

<span data-ttu-id="dbd43-135">Oculta a faixa de direitos autorais na inicialização.</span><span class="sxs-lookup"><span data-stu-id="dbd43-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="dbd43-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="dbd43-136">-NonInteractive</span></span>

<span data-ttu-id="dbd43-137">Não exibe um prompt interativo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="dbd43-137">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="dbd43-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="dbd43-138">-NoProfile</span></span>

<span data-ttu-id="dbd43-139">Não carrega o perfil do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbd43-139">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="dbd43-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="dbd43-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="dbd43-141">Determina como a saída do PowerShell é formatada.</span><span class="sxs-lookup"><span data-stu-id="dbd43-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="dbd43-142">Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="dbd43-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="dbd43-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="dbd43-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="dbd43-144">Carrega o arquivo de console do PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="dbd43-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="dbd43-145">Insira o caminho e o nome do arquivo de console.</span><span class="sxs-lookup"><span data-stu-id="dbd43-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="dbd43-146">Para criar um arquivo de console, use o cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbd43-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="dbd43-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="dbd43-147">-Sta</span></span>

<span data-ttu-id="dbd43-148">Inicia o PowerShell usando um single-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="dbd43-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="dbd43-149">No PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="dbd43-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="dbd43-150">No PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="dbd43-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="dbd43-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="dbd43-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="dbd43-152">Inicia a versão especificada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dbd43-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="dbd43-153">A versão que você especificar deve estar instalada no sistema.</span><span class="sxs-lookup"><span data-stu-id="dbd43-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="dbd43-154">Se o PowerShell 3.0 estiver instalado no computador, os valores válidos serão "2.0" e "3.0".</span><span class="sxs-lookup"><span data-stu-id="dbd43-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="dbd43-155">O valor padrão é “3.0”.</span><span class="sxs-lookup"><span data-stu-id="dbd43-155">The default value is "3.0".</span></span>

<span data-ttu-id="dbd43-156">Se o PowerShell 3.0 não estiver instalado, o único valor válido será "2.0".</span><span class="sxs-lookup"><span data-stu-id="dbd43-156">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="dbd43-157">Outros valores são ignorados.</span><span class="sxs-lookup"><span data-stu-id="dbd43-157">Other values are ignored.</span></span>

<span data-ttu-id="dbd43-158">Para saber mais, confira "[Instalando o Windows PowerShell](../../setup/installing-windows-powershell.md)".</span><span class="sxs-lookup"><span data-stu-id="dbd43-158">For more information, see "[Installing Windows PowerShell](../../setup/installing-windows-powershell.md)".</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="dbd43-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="dbd43-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="dbd43-160">Define o estilo da janela da sessão.</span><span class="sxs-lookup"><span data-stu-id="dbd43-160">Sets the window style for the session.</span></span> <span data-ttu-id="dbd43-161">Os valores válidos são Normal, Minimized, Maximized e Hidden.</span><span class="sxs-lookup"><span data-stu-id="dbd43-161">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="dbd43-162">-Command</span><span class="sxs-lookup"><span data-stu-id="dbd43-162">-Command</span></span>

<span data-ttu-id="dbd43-163">Executa os comandos especificados (e quaisquer parâmetros) como se eles fossem digitados no prompt de comando do PowerShell e, em seguida, encerra a sessão, a menos que o parâmetro NoExit seja especificado.</span><span class="sxs-lookup"><span data-stu-id="dbd43-163">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="dbd43-164">Basicamente, qualquer texto após `-Command` é enviado como uma única linha de comando para o PowerShell (que é diferente de como `-File` manipula os parâmetros enviados para um script).</span><span class="sxs-lookup"><span data-stu-id="dbd43-164">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="dbd43-165">O valor do Comando pode ser "-", uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbd43-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="dbd43-166">ou um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="dbd43-166">or a script block.</span></span> <span data-ttu-id="dbd43-167">Se o valor do comando for "-", o texto do comando será lido da entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="dbd43-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="dbd43-168">Blocos de script devem ser colocados entre chaves ({}).</span><span class="sxs-lookup"><span data-stu-id="dbd43-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="dbd43-169">Será possível especificar um bloco de script apenas quando o PowerShell.exe no PowerShell estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="dbd43-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="dbd43-170">Os resultados do script são retornados para o shell pai como objetos XML desserializados, não objetos vivos.</span><span class="sxs-lookup"><span data-stu-id="dbd43-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="dbd43-171">Se o valor do comando for uma cadeia de caracteres, **Command** deverá ser o último parâmetro no comando, pois qualquer caractere digitado depois do comando será interpretado como os argumentos do comando.</span><span class="sxs-lookup"><span data-stu-id="dbd43-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="dbd43-172">Para gravar uma cadeia de caracteres que executa um comando do PowerShell, use o formato:</span><span class="sxs-lookup"><span data-stu-id="dbd43-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="dbd43-173">no qual as aspas indicam uma cadeia de caracteres e o operador de invocação (&) faz com que o comando seja executado.</span><span class="sxs-lookup"><span data-stu-id="dbd43-173">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="dbd43-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="dbd43-174">-Help, -?, /?</span></span>

<span data-ttu-id="dbd43-175">Mostra esta mensagem.</span><span class="sxs-lookup"><span data-stu-id="dbd43-175">Shows this message.</span></span> <span data-ttu-id="dbd43-176">Se você estiver digitando um comando do PowerShell.exe no PowerShell, adicione um hífen (-) ao início dos parâmetros do comando, não uma barra (/).</span><span class="sxs-lookup"><span data-stu-id="dbd43-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="dbd43-177">Você pode usar um hífen ou uma barra "/" no Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="dbd43-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="dbd43-178">Observação de solução de problemas: no PowerShell 2.0, a inicialização de alguns programas no console do Windows PowerShell falha com um LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="dbd43-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="dbd43-179">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="dbd43-179">EXAMPLES</span></span>

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