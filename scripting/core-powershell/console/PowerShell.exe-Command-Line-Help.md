---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Ajuda da linha de comando do PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 9c56f09ac186b0c3a64cce6700740ca1ba6abd06
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="c182d-103">Ajuda da linha de comando do PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="c182d-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="c182d-104">Inicia uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c182d-104">Starts a Windows PowerShell session.</span></span> <span data-ttu-id="c182d-105">Você pode usar o PowerShell.exe para iniciar uma sessão do Windows PowerShell na linha de comando de outra ferramenta, como Cmd.exe, ou usá-lo na linha de comando do Windows PowerShell para iniciar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="c182d-105">You can use PowerShell.exe to start a Windows PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the Windows PowerShell command line to start a new session.</span></span> <span data-ttu-id="c182d-106">Use os parâmetros para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="c182d-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="c182d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c182d-107">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="c182d-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c182d-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="c182d-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="c182d-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="c182d-110">Aceita uma versão de cadeia de caracteres com codificação de base 64 de um comando.</span><span class="sxs-lookup"><span data-stu-id="c182d-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="c182d-111">Use esse parâmetro para enviar comandos ao Windows PowerShell que exigem aspas complexas ou chaves.</span><span class="sxs-lookup"><span data-stu-id="c182d-111">Use this parameter to submit commands to Windows PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="c182d-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="c182d-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="c182d-113">Define a política de execução padrão para a sessão atual e o salva-a na variável de ambiente $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="c182d-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="c182d-114">Esse parâmetro não altera a política de execução do Windows PowerShell que está definida no Registro.</span><span class="sxs-lookup"><span data-stu-id="c182d-114">This parameter does not change the Windows PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="c182d-115">Para saber mais sobre as políticas de execução do Windows PowerShell, incluindo uma lista de valores válidos, confira about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="c182d-115">For information about Windows PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="c182d-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="c182d-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="c182d-117">Executa o script especificado no escopo local ("dot-sourced") para que as funções e variáveis que o script criar estejam disponíveis na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="c182d-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="c182d-118">Insira o caminho do arquivo de script e quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c182d-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="c182d-119">**File** deve ser o último parâmetro no comando, pois todos os caracteres digitados após nome do parâmetro **File** são interpretados como o caminho do arquivo de script seguido pelos parâmetros do script e seus valores.</span><span class="sxs-lookup"><span data-stu-id="c182d-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="c182d-120">Você pode incluir os parâmetros de um script e os valores de parâmetro no valor do parâmetro **File**.</span><span class="sxs-lookup"><span data-stu-id="c182d-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="c182d-121">Por exemplo: `-File .\Get-Script.ps1 -Domain Central`</span><span class="sxs-lookup"><span data-stu-id="c182d-121">For example: `-File .\Get-Script.ps1 -Domain Central`</span></span>

<span data-ttu-id="c182d-122">Normalmente, os parâmetros de opção de um script são incluídos ou omitidos.</span><span class="sxs-lookup"><span data-stu-id="c182d-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="c182d-123">Por exemplo, o comando a seguir usa o parâmetro **All** do arquivo de script Get-Script.ps1: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="c182d-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="c182d-124">Em casos raros, pode ser necessário fornecer um valor booliano para um parâmetro de opção.</span><span class="sxs-lookup"><span data-stu-id="c182d-124">In rare cases, you might need to provide a Boolean value for a switch parameter.</span></span> <span data-ttu-id="c182d-125">Para fornecer um valor booliano para um parâmetro de opção no valor do parâmetro **File**, coloque o nome do parâmetro e o valor entre chaves, desta forma: `-File .\Get-Script.ps1 {-All:$False}`</span><span class="sxs-lookup"><span data-stu-id="c182d-125">To provide a Boolean value for a switch parameter in the value of the **File** parameter, enclose the parameter name and value in curly braces, such as the following: `-File .\Get-Script.ps1 {-All:$False}`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="c182d-126">-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="c182d-126">-InputFormat {Text | XML}</span></span>
<span data-ttu-id="c182d-127">Descreve o formato dos dados enviados ao Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c182d-127">Describes the format of data sent to Windows PowerShell.</span></span> <span data-ttu-id="c182d-128">Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="c182d-128">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="c182d-129">-Mta</span><span class="sxs-lookup"><span data-stu-id="c182d-129">-Mta</span></span>
<span data-ttu-id="c182d-130">Inicia o Windows PowerShell usando um multi-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="c182d-130">Starts Windows PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="c182d-131">Este parâmetro é introduzido no Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c182d-131">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="c182d-132">No Windows PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c182d-132">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="c182d-133">No Windows PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c182d-133">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="c182d-134">-NoExit</span><span class="sxs-lookup"><span data-stu-id="c182d-134">-NoExit</span></span>
<span data-ttu-id="c182d-135">Não é encerrado depois de executar comandos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="c182d-135">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="c182d-136">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="c182d-136">-NoLogo</span></span>
<span data-ttu-id="c182d-137">Oculta a faixa de direitos autorais na inicialização.</span><span class="sxs-lookup"><span data-stu-id="c182d-137">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="c182d-138">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="c182d-138">-NonInteractive</span></span>
<span data-ttu-id="c182d-139">Não exibe um prompt interativo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="c182d-139">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="c182d-140">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="c182d-140">-NoProfile</span></span>
<span data-ttu-id="c182d-141">Não carrega o perfil do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c182d-141">Does not load the Windows PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="c182d-142">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="c182d-142">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="c182d-143">Determina como a saída do Windows PowerShell é formatada.</span><span class="sxs-lookup"><span data-stu-id="c182d-143">Determines how output from Windows PowerShell is formatted.</span></span> <span data-ttu-id="c182d-144">Os valores válidos são "Text" (cadeias de caracteres de texto) ou "XML" (formato CLIXML serializado).</span><span class="sxs-lookup"><span data-stu-id="c182d-144">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="c182d-145">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="c182d-145">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="c182d-146">Carrega o arquivo do console do Windows PowerShell especificado.</span><span class="sxs-lookup"><span data-stu-id="c182d-146">Loads the specified Windows PowerShell console file.</span></span> <span data-ttu-id="c182d-147">Insira o caminho e o nome do arquivo de console.</span><span class="sxs-lookup"><span data-stu-id="c182d-147">Enter the path and name of the console file.</span></span> <span data-ttu-id="c182d-148">Para criar um arquivo de console, use o cmdlet [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c182d-148">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in Windows PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="c182d-149">-Sta</span><span class="sxs-lookup"><span data-stu-id="c182d-149">-Sta</span></span>
<span data-ttu-id="c182d-150">Inicia o Windows PowerShell usando um single-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="c182d-150">Starts Windows PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="c182d-151">No Windows PowerShell 3.0, o STA (Single-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c182d-151">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="c182d-152">No Windows PowerShell 2.0, o MTA (Multi-Threaded Apartment) é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c182d-152">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-windows-powershell-version"></a><span data-ttu-id="c182d-153">-Version <Windows PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="c182d-153">-Version <Windows PowerShell Version></span></span>
<span data-ttu-id="c182d-154">Inicia a versão especificada do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c182d-154">Starts the specified version of Windows PowerShell.</span></span> <span data-ttu-id="c182d-155">A versão que você especificar deve estar instalada no sistema.</span><span class="sxs-lookup"><span data-stu-id="c182d-155">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="c182d-156">Se o Windows PowerShell 3.0 estiver instalado no computador, os valores válidos serão "3.0" e "2.0".</span><span class="sxs-lookup"><span data-stu-id="c182d-156">If Windows PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="c182d-157">O valor padrão é “3.0”.</span><span class="sxs-lookup"><span data-stu-id="c182d-157">The default value is "3.0".</span></span>

<span data-ttu-id="c182d-158">Se o Windows PowerShell 3.0 não estiver instalado, o único valor válido será "2.0".</span><span class="sxs-lookup"><span data-stu-id="c182d-158">If Windows PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="c182d-159">Outros valores são ignorados.</span><span class="sxs-lookup"><span data-stu-id="c182d-159">Other values are ignored.</span></span>

<span data-ttu-id="c182d-160">Para obter mais informações, consulte "Instalar o Windows PowerShell" na [Introdução ao Fluxo de Trabalho do Windows PowerShell [MSDN ANTIGO]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="c182d-160">For more information, see "Installing Windows PowerShell" in the [Getting Started with Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="c182d-161">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="c182d-161">-WindowStyle <Window style></span></span>
<span data-ttu-id="c182d-162">Define o estilo da janela da sessão.</span><span class="sxs-lookup"><span data-stu-id="c182d-162">Sets the window style for the session.</span></span> <span data-ttu-id="c182d-163">Os valores válidos são Normal, Minimized, Maximized e Hidden.</span><span class="sxs-lookup"><span data-stu-id="c182d-163">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="c182d-164">-Command</span><span class="sxs-lookup"><span data-stu-id="c182d-164">-Command</span></span>
<span data-ttu-id="c182d-165">Executa os comandos especificados (e quaisquer parâmetros) da maneira como eles foram digitados no prompt de comando do Windows PowerShell e, em seguida, encerra a sessão, a menos que o parâmetro NoExit seja especificado.</span><span class="sxs-lookup"><span data-stu-id="c182d-165">Executes the specified commands (and any parameters) as though they were typed at the Windows PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>

<span data-ttu-id="c182d-166">O valor do Comando pode ser "-", uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c182d-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="c182d-167">ou um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="c182d-167">or a script block.</span></span> <span data-ttu-id="c182d-168">Se o valor do comando for "-", o texto do comando será lido da entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="c182d-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="c182d-169">Blocos de script devem ser colocados entre chaves ({}).</span><span class="sxs-lookup"><span data-stu-id="c182d-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="c182d-170">Você pode especificar um bloco de script apenas quando o PowerShell.exe no Windows PowerShell estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="c182d-170">You can specify a script block only when running PowerShell.exe in Windows PowerShell.</span></span> <span data-ttu-id="c182d-171">Os resultados do script são retornados para o shell pai como objetos XML desserializados, não objetos vivos.</span><span class="sxs-lookup"><span data-stu-id="c182d-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="c182d-172">Se o valor do comando for uma cadeia de caracteres, **Command** deverá ser o último parâmetro no comando, pois qualquer caractere digitado depois do comando será interpretado como os argumentos de comando.</span><span class="sxs-lookup"><span data-stu-id="c182d-172">If the value of Command is a string, **Command** must be the last parameter in the command , because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="c182d-173">Para gravar uma cadeia de caracteres que executa um comando do Windows PowerShell, use o formato:</span><span class="sxs-lookup"><span data-stu-id="c182d-173">To write a string that runs a Windows PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="c182d-174">no qual as aspas indicam uma cadeia de caracteres e o operador de invocação (&) faz com que o comando seja executado.</span><span class="sxs-lookup"><span data-stu-id="c182d-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="c182d-175">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="c182d-175">-Help, -?, /?</span></span>
<span data-ttu-id="c182d-176">Mostra esta mensagem.</span><span class="sxs-lookup"><span data-stu-id="c182d-176">Shows this message.</span></span> <span data-ttu-id="c182d-177">Se você estiver digitando um comando do PowerShell.exe no Windows PowerShell, adicione um hífen (-) ao início dos parâmetros do comando, não uma barra (/).</span><span class="sxs-lookup"><span data-stu-id="c182d-177">If you are typing a PowerShell.exe command in Windows PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="c182d-178">Você pode usar um hífen ou uma barra "/" no Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="c182d-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="c182d-179">Observação de solução de problemas: no Windows PowerShell 2.0, a inicialização de alguns programas no console do Windows PowerShell falha com um LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="c182d-179">Troubleshooting Note: In Windows PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="c182d-180">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="c182d-180">EXAMPLES</span></span>

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

