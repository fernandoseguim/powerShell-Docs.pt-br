---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Ajuda da linha de comando do PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: b2236decb3295ee5b543f72f083e516c91fa4b5f
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="8560a-103">Ajuda da linha de comando do PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="8560a-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="8560a-104">Inicia uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8560a-104">Starts a Windows PowerShell session.</span></span> <span data-ttu-id="8560a-105">Você pode usar o PowerShell.exe para iniciar uma sessão do Windows PowerShell na linha de comando de outra ferramenta, como Cmd.exe, ou usá-lo na linha de comando do Windows PowerShell para iniciar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="8560a-105">You can use PowerShell.exe to start a Windows PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the Windows PowerShell command line to start a new session.</span></span> <span data-ttu-id="8560a-106">Use os parâmetros para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="8560a-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="8560a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8560a-107">Syntax</span></span>

```syntax
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

## <a name="parameters"></a><span data-ttu-id="8560a-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8560a-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="8560a-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="8560a-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="8560a-110">Aceita uma versão de cadeia de caracteres com codificação de base 64 de um comando.</span><span class="sxs-lookup"><span data-stu-id="8560a-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="8560a-111">Use esse parâmetro para enviar comandos ao Windows PowerShell que exigem aspas complexas ou chaves.</span><span class="sxs-lookup"><span data-stu-id="8560a-111">Use this parameter to submit commands to Windows PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="8560a-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="8560a-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="8560a-113">Define a política de execução padrão para a sessão atual e o salva-a na variável de ambiente $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="8560a-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="8560a-114">Esse parâmetro não altera a política de execução do Windows PowerShell que está definida no Registro.</span><span class="sxs-lookup"><span data-stu-id="8560a-114">This parameter does not change the Windows PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="8560a-115">Para saber mais sobre as políticas de execução do Windows PowerShell, incluindo uma lista de valores válidos, confira about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="8560a-115">For information about Windows PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="8560a-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="8560a-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="8560a-117">Executa o script especificado no escopo local ("dot-sourced") para que as funções e variáveis que o script criar estejam disponíveis na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="8560a-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="8560a-118">Insira o caminho do arquivo de script e quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8560a-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="8560a-119">**File** deve ser o último parâmetro no comando, pois todos os caracteres digitados após nome do parâmetro **File** são interpretados como o caminho do arquivo de script seguido pelos parâmetros do script e seus valores.</span><span class="sxs-lookup"><span data-stu-id="8560a-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="8560a-120">Você pode incluir os parâmetros de um script e os valores de parâmetro no valor do parâmetro **File**.</span><span class="sxs-lookup"><span data-stu-id="8560a-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="8560a-121">Por exemplo: `-File .\Get-Script.ps1 -Domain Central` Observe que os parâmetros passados para o script são passados como cadeias de caracteres literais (após a interpretação do shell atual).</span><span class="sxs-lookup"><span data-stu-id="8560a-121">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="8560a-122">Por exemplo, se você estiver no cmd.exe e quiser para passar um valor de variável de ambiente, use a sintaxe do cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` Se você usar a sintaxe do PowerShell, neste exemplo, o script receberá o literal "$env:windir" e não o valor dessa variável de ambiente: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="8560a-122">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="8560a-123">Normalmente, os parâmetros de opção de um script são incluídos ou omitidos.</span><span class="sxs-lookup"><span data-stu-id="8560a-123">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="8560a-124">Por exemplo, o comando a seguir usa o parâmetro **All** do arquivo de script Get-Script.ps1: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="8560a-124">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="8560a-125">\-InputFormat {Texto | XML}</span><span class="sxs-lookup"><span data-stu-id="8560a-125">\-InputFormat {Text | XML}</span></span>
<span data-ttu-id="8560a-126">Descreve o formato dos dados enviados ao Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8560a-126">Describes the format of data sent to Windows PowerShell.</span></span> <span data-ttu-id="8560a-127">Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="8560a-127">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="8560a-128">-Mta</span><span class="sxs-lookup"><span data-stu-id="8560a-128">-Mta</span></span>
<span data-ttu-id="8560a-129">Inicia o Windows PowerShell usando um multi-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="8560a-129">Starts Windows PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="8560a-130">Este parâmetro é introduzido no Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="8560a-130">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="8560a-131">No Windows PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="8560a-131">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="8560a-132">No Windows PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="8560a-132">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="8560a-133">-NoExit</span><span class="sxs-lookup"><span data-stu-id="8560a-133">-NoExit</span></span>
<span data-ttu-id="8560a-134">Não é encerrado depois de executar comandos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="8560a-134">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="8560a-135">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="8560a-135">-NoLogo</span></span>
<span data-ttu-id="8560a-136">Oculta a faixa de direitos autorais na inicialização.</span><span class="sxs-lookup"><span data-stu-id="8560a-136">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="8560a-137">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="8560a-137">-NonInteractive</span></span>
<span data-ttu-id="8560a-138">Não exibe um prompt interativo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="8560a-138">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="8560a-139">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="8560a-139">-NoProfile</span></span>
<span data-ttu-id="8560a-140">Não carrega o perfil do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8560a-140">Does not load the Windows PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="8560a-141">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="8560a-141">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="8560a-142">Determina como a saída do Windows PowerShell é formatada.</span><span class="sxs-lookup"><span data-stu-id="8560a-142">Determines how output from Windows PowerShell is formatted.</span></span> <span data-ttu-id="8560a-143">Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="8560a-143">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="8560a-144">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="8560a-144">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="8560a-145">Carrega o arquivo do console do Windows PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="8560a-145">Loads the specified Windows PowerShell console file.</span></span> <span data-ttu-id="8560a-146">Insira o caminho e o nome do arquivo de console.</span><span class="sxs-lookup"><span data-stu-id="8560a-146">Enter the path and name of the console file.</span></span> <span data-ttu-id="8560a-147">Para criar um arquivo de console, use o cmdlet [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8560a-147">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in Windows PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="8560a-148">-Sta</span><span class="sxs-lookup"><span data-stu-id="8560a-148">-Sta</span></span>
<span data-ttu-id="8560a-149">Inicia o Windows PowerShell usando um single-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="8560a-149">Starts Windows PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="8560a-150">No Windows PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="8560a-150">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="8560a-151">No Windows PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="8560a-151">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-windows-powershell-version"></a><span data-ttu-id="8560a-152">-Version <Windows PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="8560a-152">-Version <Windows PowerShell Version></span></span>
<span data-ttu-id="8560a-153">Inicia a versão especificada do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8560a-153">Starts the specified version of Windows PowerShell.</span></span> <span data-ttu-id="8560a-154">A versão que você especificar deve estar instalada no sistema.</span><span class="sxs-lookup"><span data-stu-id="8560a-154">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="8560a-155">Se o Windows PowerShell 3.0 estiver instalado no computador, os valores válidos serão "3.0" e "2.0".</span><span class="sxs-lookup"><span data-stu-id="8560a-155">If Windows PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="8560a-156">O valor padrão é “3.0”.</span><span class="sxs-lookup"><span data-stu-id="8560a-156">The default value is "3.0".</span></span>

<span data-ttu-id="8560a-157">Se o Windows PowerShell 3.0 não estiver instalado, o único valor válido será "2.0".</span><span class="sxs-lookup"><span data-stu-id="8560a-157">If Windows PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="8560a-158">Outros valores são ignorados.</span><span class="sxs-lookup"><span data-stu-id="8560a-158">Other values are ignored.</span></span>

<span data-ttu-id="8560a-159">Para obter mais informações, consulte "Instalar o Windows PowerShell" na [Introdução ao Fluxo de Trabalho do Windows PowerShell [MSDN ANTIGO]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="8560a-159">For more information, see "Installing Windows PowerShell" in the [Getting Started with Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="8560a-160">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="8560a-160">-WindowStyle <Window style></span></span>
<span data-ttu-id="8560a-161">Define o estilo da janela da sessão.</span><span class="sxs-lookup"><span data-stu-id="8560a-161">Sets the window style for the session.</span></span> <span data-ttu-id="8560a-162">Os valores válidos são Normal, Minimized, Maximized e Hidden.</span><span class="sxs-lookup"><span data-stu-id="8560a-162">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="8560a-163">-Command</span><span class="sxs-lookup"><span data-stu-id="8560a-163">-Command</span></span>
<span data-ttu-id="8560a-164">Executa os comandos especificados (e quaisquer parâmetros) da maneira como eles foram digitados no prompt de comando do Windows PowerShell e, em seguida, encerra a sessão, a menos que o parâmetro NoExit seja especificado.</span><span class="sxs-lookup"><span data-stu-id="8560a-164">Executes the specified commands (and any parameters) as though they were typed at the Windows PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="8560a-165">Basicamente, qualquer texto após `-Command` é enviado como uma única linha de comando para o PowerShell (que é diferente de como `-File` manipula os parâmetros enviados para um script).</span><span class="sxs-lookup"><span data-stu-id="8560a-165">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="8560a-166">O valor do Comando pode ser "-", uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8560a-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="8560a-167">ou um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="8560a-167">or a script block.</span></span> <span data-ttu-id="8560a-168">Se o valor do comando for "-", o texto do comando será lido da entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="8560a-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="8560a-169">Blocos de script devem ser colocados entre chaves ({}).</span><span class="sxs-lookup"><span data-stu-id="8560a-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="8560a-170">Você pode especificar um bloco de script apenas quando o PowerShell.exe no Windows PowerShell estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="8560a-170">You can specify a script block only when running PowerShell.exe in Windows PowerShell.</span></span> <span data-ttu-id="8560a-171">Os resultados do script são retornados para o shell pai como objetos XML desserializados, não objetos vivos.</span><span class="sxs-lookup"><span data-stu-id="8560a-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="8560a-172">Se o valor do comando for uma cadeia de caracteres, **Command** deverá ser o último parâmetro no comando, pois qualquer caractere digitado depois do comando será interpretado como os argumentos do comando.</span><span class="sxs-lookup"><span data-stu-id="8560a-172">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="8560a-173">Para gravar uma cadeia de caracteres que executa um comando do Windows PowerShell, use o formato:</span><span class="sxs-lookup"><span data-stu-id="8560a-173">To write a string that runs a Windows PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="8560a-174">no qual as aspas indicam uma cadeia de caracteres e o operador de invocação (&) faz com que o comando seja executado.</span><span class="sxs-lookup"><span data-stu-id="8560a-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="8560a-175">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="8560a-175">-Help, -?, /?</span></span>
<span data-ttu-id="8560a-176">Mostra esta mensagem.</span><span class="sxs-lookup"><span data-stu-id="8560a-176">Shows this message.</span></span> <span data-ttu-id="8560a-177">Se você estiver digitando um comando do PowerShell.exe no Windows PowerShell, adicione um hífen (-) ao início dos parâmetros do comando, não uma barra (/).</span><span class="sxs-lookup"><span data-stu-id="8560a-177">If you are typing a PowerShell.exe command in Windows PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="8560a-178">Você pode usar um hífen ou uma barra "/" no Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="8560a-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="8560a-179">Observação de solução de problemas: no Windows PowerShell 2.0, a inicialização de alguns programas no console do Windows PowerShell falha com um LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="8560a-179">Troubleshooting Note: In Windows PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="8560a-180">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="8560a-180">EXAMPLES</span></span>

```
PowerShell -PSConsoleFile sqlsnapin.psc1

PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

PowerShell -Command "Get-EventLog -LogName security"

# in an existing PowerShell session that understands the curly braces mean a script block
PowerShell -Command {Get-EventLog -LogName security}

PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

