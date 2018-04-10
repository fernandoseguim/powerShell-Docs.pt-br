# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="10089-101">Uso do Visual Studio Code para desenvolvimento do PowerShell</span><span class="sxs-lookup"><span data-stu-id="10089-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="10089-102">Além do [PowerShell ISE][ise], o PowerShell também tem suporte no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="10089-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="10089-103">Além disso, o ISE não é compatível com o PowerShell Core, embora haja suporte do Visual Studio Code para o PowerShell Core em todas as plataformas (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="10089-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="10089-104">Você pode usar o Visual Studio Code no Windows com o PowerShell versão 5 usando o Windows 10 ou instalando o [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para sistemas operacionais do Windows de nível baixo (por exemplo, Windows 8.1 etc.).</span><span class="sxs-lookup"><span data-stu-id="10089-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="10089-105">Antes de iniciá-lo, verifique se o PowerShell existe no sistema.</span><span class="sxs-lookup"><span data-stu-id="10089-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="10089-106">Para cargas de trabalho modernas no Windows, macOS e Linux, consulte:</span><span class="sxs-lookup"><span data-stu-id="10089-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="10089-107">[Instalação do PowerShell Core no macOS e Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="10089-107">[Installing PowerShell Core on macOS and Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="10089-108">[Instalação do PowerShell Core no Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="10089-108">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="10089-109">Para cargas de trabalho tradicionais do Windows PowerShell, veja [instalação do Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="10089-109">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="10089-110">Edição com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="10089-110">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="10089-111">1. Instalação do Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="10089-111">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="10089-112">**Linux**: siga as instruções de instalação na página [Execução do código VS no Linux](https://code.visualstudio.com/docs/setup/linux)</span><span class="sxs-lookup"><span data-stu-id="10089-112">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="10089-113">**macOS**: siga as instruções de instalação na página [Execução do código VS no macOS](https://code.visualstudio.com/docs/setup/mac)</span><span class="sxs-lookup"><span data-stu-id="10089-113">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10089-114">No macOS, você deve instalar o OpenSSL para que a extensão do PowerShell funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="10089-114">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="10089-115">A maneira mais fácil de fazer isso é instalar o [Homebrew](http://brew.sh/) e, em seguida, executar `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="10089-115">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="10089-116">Agora, a extensão do PowerShell será capaz de carregar com êxito.</span><span class="sxs-lookup"><span data-stu-id="10089-116">The PowerShell extension will now be able to load successfully.</span></span>

- <span data-ttu-id="10089-117">**Windows**: siga as instruções de instalação na página [Execução do código VS no Windows](https://code.visualstudio.com/docs/setup/windows)</span><span class="sxs-lookup"><span data-stu-id="10089-117">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="10089-118">2. Instalação da extensão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="10089-118">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="10089-119">Inicie o aplicativo Visual Studio Code pelo:</span><span class="sxs-lookup"><span data-stu-id="10089-119">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="10089-120">**Windows**: digitando `code` na sua sessão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="10089-120">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="10089-121">**Linux**: digitando `code` em seu terminal</span><span class="sxs-lookup"><span data-stu-id="10089-121">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="10089-122">**macOS**: digitando `code` em seu terminal</span><span class="sxs-lookup"><span data-stu-id="10089-122">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="10089-123">Inicie **Abertura rápida** pressionando **Ctrl+P** (**Cmd+P** no Mac).</span><span class="sxs-lookup"><span data-stu-id="10089-123">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="10089-124">Na Abertura rápida, digite `ext install powershell` e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="10089-124">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="10089-125">A exibição **Extensões** será aberta na barra lateral.</span><span class="sxs-lookup"><span data-stu-id="10089-125">The **Extensions** view will open on the Side Bar.</span></span> <span data-ttu-id="10089-126">Selecione a extensão do PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10089-126">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="10089-127">Você verá algo como abaixo:</span><span class="sxs-lookup"><span data-stu-id="10089-127">You will see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="10089-129">Clique no botão **Instalar** na extensão do PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10089-129">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="10089-130">Após a instalação, você verá que o botão **Instalar** mudará para **Recarregar**.</span><span class="sxs-lookup"><span data-stu-id="10089-130">After the install, you will see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="10089-131">Clique em **Recarregar**.</span><span class="sxs-lookup"><span data-stu-id="10089-131">Click on **Reload**.</span></span>
- <span data-ttu-id="10089-132">Depois de recarregar o Visual Studio Code, você está pronto para edição.</span><span class="sxs-lookup"><span data-stu-id="10089-132">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="10089-133">Por exemplo, para criar um novo arquivo, clique em **Arquivo -> Novo**.</span><span class="sxs-lookup"><span data-stu-id="10089-133">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="10089-134">Para salvá-lo, clique em **Arquivo -> Salvar** e, em seguida, forneça um nome de arquivo. Digamos `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="10089-134">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="10089-135">Para fechar o arquivo, clique no "x" ao lado do nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="10089-135">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="10089-136">Para sair do Visual Studio Code, **Arquivo -> Sair**.</span><span class="sxs-lookup"><span data-stu-id="10089-136">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="10089-137">Uso de uma versão instalada específica do PowerShell</span><span class="sxs-lookup"><span data-stu-id="10089-137">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="10089-138">Se quiser usar uma instalação específica do PowerShell com o Visual Studio Code, você precisará adicionar uma nova variável ao arquivo de configurações do usuário.</span><span class="sxs-lookup"><span data-stu-id="10089-138">If you wish to use a specific installation of PowerShell with Visual Studio Code, you will need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="10089-139">Clique em **Arquivo -> Preferências -> Configurações**</span><span class="sxs-lookup"><span data-stu-id="10089-139">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="10089-140">Dois painéis de editor serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="10089-140">Two editor panes will appear.</span></span>
   <span data-ttu-id="10089-141">No painel mais à direita (`settings.json`), insira a configuração abaixo apropriada para seu sistema operacional entre as duas chaves (`{` e `}`) e substitua *<version>* pela versão do PowerShell instalada:</span><span class="sxs-lookup"><span data-stu-id="10089-141">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="10089-142">Substitua a configuração pelo caminho para o executável desejado do PowerShell</span><span class="sxs-lookup"><span data-stu-id="10089-142">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="10089-143">Salve o arquivo de configurações e reinicie o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="10089-143">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="10089-144">Definições de configuração para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="10089-144">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="10089-145">Usando as etapas no parágrafo anterior, você pode adicionar configurações no `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="10089-145">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="10089-146">Recomendamos as seguintes definições de configuração para o Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="10089-146">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="10089-147">Depuração com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="10089-147">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="10089-148">Depuração sem espaço de trabalho</span><span class="sxs-lookup"><span data-stu-id="10089-148">No-workspace debugging</span></span>

<span data-ttu-id="10089-149">A partir da versão do Visual Studio Code 1.9, você pode depurar scripts do PowerShell sem a necessidade de abrir a pasta que contém o script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10089-149">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="10089-150">Basta abrir o arquivo de script do PowerShell usando **Arquivo -> Abrir Arquivo...** , definir um ponto de interrupção em uma linha (pressione F9) e, em seguida, pressionar F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="10089-150">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="10089-151">Será exibido o painel de ações de depuração que permite que você interrompa o depurador, execute em etapas, retome e pare a depuração.</span><span class="sxs-lookup"><span data-stu-id="10089-151">You will see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="10089-152">Depuração do espaço de trabalho</span><span class="sxs-lookup"><span data-stu-id="10089-152">Workspace debugging</span></span>

<span data-ttu-id="10089-153">A depuração do espaço de trabalho refere-se a depuração no contexto de uma pasta que você abriu no Visual Studio Code usando **Abrir Pasta...**  do menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="10089-153">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="10089-154">A pasta que você abrir normalmente é a pasta do projeto do PowerShell e/ou a raiz do repositório Git.</span><span class="sxs-lookup"><span data-stu-id="10089-154">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="10089-155">Mesmo nesse modo, você pode iniciar a depuração de script do PowerShell selecionado no momento pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="10089-155">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="10089-156">No entanto, a depuração do espaço de trabalho permite definir várias configurações de depuração diferentes de depurar apenas o arquivo aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="10089-156">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="10089-157">Por exemplo, você pode adicionar configurações para:</span><span class="sxs-lookup"><span data-stu-id="10089-157">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="10089-158">Iniciar testes Pester no depurador</span><span class="sxs-lookup"><span data-stu-id="10089-158">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="10089-159">Abrir um arquivo específico com argumentos no depurador</span><span class="sxs-lookup"><span data-stu-id="10089-159">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="10089-160">Inicie uma sessão interativa no depurador</span><span class="sxs-lookup"><span data-stu-id="10089-160">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="10089-161">Anexar o depurador a um processo de host do PowerShell</span><span class="sxs-lookup"><span data-stu-id="10089-161">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="10089-162">Siga estas etapas para criar o arquivo de configuração de depuração:</span><span class="sxs-lookup"><span data-stu-id="10089-162">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="10089-163">Abra a exibição **Depurar** pressionando **Ctrl+Shift+D** (**Cmd+Shift+D** no Mac).</span><span class="sxs-lookup"><span data-stu-id="10089-163">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="10089-164">Pressione o ícone de engrenagem **Configurar** na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="10089-164">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="10089-165">O Visual Studio Code solicitará que você **Selecione Ambiente**.</span><span class="sxs-lookup"><span data-stu-id="10089-165">Visual Studio Code will prompt you to **Select Environment**.</span></span>
   <span data-ttu-id="10089-166">Escolha **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="10089-166">Choose **PowerShell**.</span></span>

   <span data-ttu-id="10089-167">Quando você fizer isso, o Visual Studio Code criará um diretório e um arquivo ".vscode\launch.json" na raiz da sua pasta de espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="10089-167">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="10089-168">A configuração de depuração é armazena nesse local.</span><span class="sxs-lookup"><span data-stu-id="10089-168">This is where your debug configuration is stored.</span></span> <span data-ttu-id="10089-169">Se os arquivos estiverem em um repositório Git, normalmente você desejará confirmar o arquivo launch.json.</span><span class="sxs-lookup"><span data-stu-id="10089-169">If your files are in a Git repository, you will typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="10089-170">O conteúdo do arquivo launch.json é:</span><span class="sxs-lookup"><span data-stu-id="10089-170">The contents of the launch.json file are:</span></span>

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
}
```

<span data-ttu-id="10089-171">Isso representa os cenários comuns de depuração.</span><span class="sxs-lookup"><span data-stu-id="10089-171">This represents the common debug scenarios.</span></span>
<span data-ttu-id="10089-172">No entanto, ao abrir este arquivo no editor, você vê um botão **Adicionar Configuração...**.</span><span class="sxs-lookup"><span data-stu-id="10089-172">However, when you open this file in the editor, you will see an **Add Configuration...** button.</span></span>
<span data-ttu-id="10089-173">Você pode pressionar esse botão para adicionar mais configurações de depuração do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10089-173">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="10089-174">Uma configuração útil a ser adicionada é **PowerShell: Iniciar o Script**.</span><span class="sxs-lookup"><span data-stu-id="10089-174">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="10089-175">Com essa configuração, você pode especificar um arquivo específico com argumentos opcionais que devem ser iniciado sempre que você pressionar F5, não importa qual arquivo está ativo no momento no editor.</span><span class="sxs-lookup"><span data-stu-id="10089-175">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="10089-176">Quando a configuração de depuração é estabelecida, selecione qual configuração você deseja usar durante uma sessão de depuração, selecionando uma no menu suspenso de configuração de depuração na barra de ferramentas da exibição **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="10089-176">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="10089-177">Há alguns blogs que podem ser úteis para você começar a usar a extensão do PowerShell para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="10089-177">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="10089-178">Visual Studio Code: [extensão do PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="10089-178">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="10089-179">[Gravar e depurar scripts do PowerShell no Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="10089-179">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="10089-180">[Orientação sobre depuração no Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="10089-180">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="10089-181">[Depuração do PowerShell no Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="10089-181">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="10089-182">[Introdução ao desenvolvimento do PowerShell no Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="10089-182">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="10089-183">[Recursos de edição do Visual Studio Code para desenvolvimento do PowerShell – parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="10089-183">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="10089-184">[Recursos de edição do Visual Studio Code para desenvolvimento do PowerShell – parte 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="10089-184">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="10089-185">[Depuração de script do PowerShell no Visual Studio Code– parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="10089-185">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="10089-186">[Depuração de script do PowerShell no Visual Studio Code– parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="10089-186">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-macOS-and-Linux.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="10089-187">Extensão do PowerShell para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="10089-187">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="10089-188">O código-fonte da extensão do PowerShell pode ser encontrado no [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="10089-188">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>