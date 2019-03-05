---
title: Uso do Visual Studio Code para desenvolvimento do PowerShell
description: Uso do Visual Studio Code para desenvolvimento do PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 1e9b9d811a39656327af2810bd6dc8aaf3fde3a4
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251380"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="3547e-103">Uso do Visual Studio Code para desenvolvimento do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3547e-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="3547e-104">Além do [PowerShell ISE][ise], o PowerShell também tem suporte no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3547e-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="3547e-105">Além disso, o ISE não é compatível com o PowerShell Core, embora haja suporte do Visual Studio Code para o PowerShell Core em todas as plataformas (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="3547e-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="3547e-106">Você pode usar o Visual Studio Code no Windows com o PowerShell versão 5 usando o Windows 10 ou instalando o [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para sistemas operacionais do Windows de nível baixo (por exemplo, Windows 8.1 etc.).</span><span class="sxs-lookup"><span data-stu-id="3547e-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="3547e-107">Antes de iniciá-lo, verifique se o PowerShell existe no sistema.</span><span class="sxs-lookup"><span data-stu-id="3547e-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="3547e-108">Para cargas de trabalho modernas no Windows, macOS e Linux, consulte:</span><span class="sxs-lookup"><span data-stu-id="3547e-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="3547e-109">[Instalar o PowerShell Core no Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="3547e-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="3547e-110">[Instalar o PowerShell Core no macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="3547e-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="3547e-111">[Instalação do PowerShell Core no Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="3547e-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="3547e-112">Para cargas de trabalho tradicionais do Windows PowerShell, veja [instalação do Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="3547e-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="3547e-113">Edição com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3547e-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="3547e-114">1. Instalação do Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3547e-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="3547e-115">**Linux**: siga as instruções de instalação na página [Execução do código VS no Linux](https://code.visualstudio.com/docs/setup/linux)</span><span class="sxs-lookup"><span data-stu-id="3547e-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="3547e-116">**macOS**: siga as instruções de instalação na página [Execução do código VS no macOS](https://code.visualstudio.com/docs/setup/mac)</span><span class="sxs-lookup"><span data-stu-id="3547e-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="3547e-117">No macOS, você deve instalar o OpenSSL para que a extensão do PowerShell funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="3547e-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="3547e-118">A maneira mais fácil de fazer isso é instalar o [Homebrew](https://brew.sh/) e, em seguida, executar `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="3547e-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="3547e-119">Agora, o VS Code pode carregar a extensão do PowerShell com êxito.</span><span class="sxs-lookup"><span data-stu-id="3547e-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="3547e-120">**Windows**: siga as instruções de instalação na página [Execução do código VS no Windows](https://code.visualstudio.com/docs/setup/windows)</span><span class="sxs-lookup"><span data-stu-id="3547e-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="3547e-121">2. Instalação da extensão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3547e-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="3547e-122">Inicie o aplicativo Visual Studio Code pelo:</span><span class="sxs-lookup"><span data-stu-id="3547e-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="3547e-123">**Windows**: digitando `code` na sua sessão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3547e-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="3547e-124">**Linux**: digitando `code` em seu terminal</span><span class="sxs-lookup"><span data-stu-id="3547e-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="3547e-125">**macOS**: digitando `code` em seu terminal</span><span class="sxs-lookup"><span data-stu-id="3547e-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="3547e-126">Inicie **Abertura rápida** pressionando **Ctrl+P** (**Cmd+P** no Mac).</span><span class="sxs-lookup"><span data-stu-id="3547e-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="3547e-127">Na Abertura rápida, digite `ext install powershell` e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="3547e-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="3547e-128">A exibição **Extensões** será aberta na barra lateral.</span><span class="sxs-lookup"><span data-stu-id="3547e-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="3547e-129">Selecione a extensão do PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3547e-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="3547e-130">Você deve ver algo como:</span><span class="sxs-lookup"><span data-stu-id="3547e-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="3547e-132">Clique no botão **Instalar** na extensão do PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3547e-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="3547e-133">Após a instalação, você verá que o botão **Instalar** mudará para **Recarregar**.</span><span class="sxs-lookup"><span data-stu-id="3547e-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="3547e-134">Clique em **Recarregar**.</span><span class="sxs-lookup"><span data-stu-id="3547e-134">Click on **Reload**.</span></span>
- <span data-ttu-id="3547e-135">Depois de recarregar o Visual Studio Code, você está pronto para edição.</span><span class="sxs-lookup"><span data-stu-id="3547e-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="3547e-136">Por exemplo, para criar um novo arquivo, clique em **Arquivo -> Novo**.</span><span class="sxs-lookup"><span data-stu-id="3547e-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="3547e-137">Para salvá-lo, clique em **Arquivo -> Salvar** e, em seguida, forneça um nome de arquivo. Digamos `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="3547e-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="3547e-138">Para fechar o arquivo, clique no "x" ao lado do nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="3547e-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="3547e-139">Para sair do Visual Studio Code, **Arquivo -> Sair**.</span><span class="sxs-lookup"><span data-stu-id="3547e-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="3547e-140">Instalando a extensão do PowerShell em sistemas restritos</span><span class="sxs-lookup"><span data-stu-id="3547e-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="3547e-141">Alguns sistemas são configurados de forma que exige que todas as assinaturas de código a ser verificada e, portanto, requer o Editor do PowerShell dos serviços a serem aprovadas manualmente para executar o sistema.</span><span class="sxs-lookup"><span data-stu-id="3547e-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="3547e-142">Uma atualização de diretiva de grupo que altera a política de execução é uma causa provável se você instalou a extensão do PowerShell, mas está atingindo um erro como:</span><span class="sxs-lookup"><span data-stu-id="3547e-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="3547e-143">Para aprovar manualmente serviços do Editor do PowerShell e, portanto, a extensão do PowerShell para VSCode abrem um prompt e execução do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3547e-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="3547e-144">Você será solicitado com "Você deseja executar o software desse editor não confiáveis?"</span><span class="sxs-lookup"><span data-stu-id="3547e-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="3547e-145">Tipo `R` para executar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="3547e-145">Type `R` to run the file.</span></span> <span data-ttu-id="3547e-146">Em seguida, abra o Visual Studio Code e verifique se a extensão do PowerShell está funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="3547e-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="3547e-147">Se você ainda tiver problemas de Introdução, fale na [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="3547e-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="3547e-148">Uso de uma versão instalada específica do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3547e-148">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="3547e-149">Se quiser usar uma instalação específica do PowerShell com o Visual Studio Code, precisará adicionar uma nova variável ao arquivo de configurações do usuário.</span><span class="sxs-lookup"><span data-stu-id="3547e-149">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="3547e-150">Clique em **Arquivo -> Preferências -> Configurações**</span><span class="sxs-lookup"><span data-stu-id="3547e-150">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="3547e-151">Dois painéis de editor serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="3547e-151">Two editor panes appear.</span></span>
   <span data-ttu-id="3547e-152">No painel mais à direita (`settings.json`), insira a configuração abaixo apropriada para seu sistema operacional entre as duas chaves (`{` e `}`) e substitua a **\<versão\>** pela versão do PowerShell instalada:</span><span class="sxs-lookup"><span data-stu-id="3547e-152">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="3547e-153">Substitua a configuração pelo caminho para o executável desejado do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3547e-153">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="3547e-154">Salve o arquivo de configurações e reinicie o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3547e-154">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="3547e-155">Definições de configuração para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3547e-155">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="3547e-156">Usando as etapas no parágrafo anterior, você pode adicionar configurações no `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="3547e-156">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="3547e-157">Recomendamos as seguintes definições de configuração para o Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="3547e-157">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="3547e-158">Se você não quiser que essas configurações afetam todos os tipos de arquivos, o VSCode também permite que configurações por idioma.</span><span class="sxs-lookup"><span data-stu-id="3547e-158">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="3547e-159">Criar uma configuração específica da linguagem, colocando as configurações um `[<language-name>]` campo.</span><span class="sxs-lookup"><span data-stu-id="3547e-159">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="3547e-160">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3547e-160">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="3547e-161">Para obter mais informações sobre o arquivo de codificação no VS Code, consulte [Entendendo a codificação do arquivo](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="3547e-161">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="3547e-162">Depuração com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3547e-162">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="3547e-163">Depuração sem espaço de trabalho</span><span class="sxs-lookup"><span data-stu-id="3547e-163">No-workspace debugging</span></span>

<span data-ttu-id="3547e-164">A partir da versão do Visual Studio Code 1.9, você pode depurar scripts do PowerShell sem a necessidade de abrir a pasta que contém o script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3547e-164">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="3547e-165">Abra o arquivo de script do PowerShell com **arquivo -> Abrir arquivo...** , defina um ponto de interrupção em uma linha (pressione F9) e, em seguida, pressione F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="3547e-165">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="3547e-166">Será exibido o painel de ações de depuração, que permite que você interrompa o depurador, execute em etapas, retome e pare a depuração.</span><span class="sxs-lookup"><span data-stu-id="3547e-166">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="3547e-167">Depuração do workspace</span><span class="sxs-lookup"><span data-stu-id="3547e-167">Workspace debugging</span></span>

<span data-ttu-id="3547e-168">A depuração do workspace refere-se a depuração no contexto de uma pasta que você abriu no Visual Studio Code usando **Abrir Pasta...**  do menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="3547e-168">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="3547e-169">A pasta que você abrir normalmente é a pasta do projeto do PowerShell e/ou a raiz do repositório Git.</span><span class="sxs-lookup"><span data-stu-id="3547e-169">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="3547e-170">Mesmo nesse modo, você pode iniciar a depuração de script do PowerShell selecionado no momento pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="3547e-170">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="3547e-171">No entanto, a depuração do workspace permite definir várias configurações de depuração diferentes de depurar apenas o arquivo aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="3547e-171">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="3547e-172">Por exemplo, você pode adicionar configurações para:</span><span class="sxs-lookup"><span data-stu-id="3547e-172">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="3547e-173">Iniciar testes Pester no depurador</span><span class="sxs-lookup"><span data-stu-id="3547e-173">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="3547e-174">Abrir um arquivo específico com argumentos no depurador</span><span class="sxs-lookup"><span data-stu-id="3547e-174">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="3547e-175">Inicie uma sessão interativa no depurador</span><span class="sxs-lookup"><span data-stu-id="3547e-175">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="3547e-176">Anexar o depurador a um processo de host do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3547e-176">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="3547e-177">Siga estas etapas para criar o arquivo de configuração de depuração:</span><span class="sxs-lookup"><span data-stu-id="3547e-177">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="3547e-178">Abra a exibição **Depurar** pressionando **Ctrl+Shift+D** (**Cmd+Shift+D** no Mac).</span><span class="sxs-lookup"><span data-stu-id="3547e-178">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="3547e-179">Pressione o ícone de engrenagem **Configurar** na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="3547e-179">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="3547e-180">O Visual Studio Code solicitará que você **Selecione o Ambiente**.</span><span class="sxs-lookup"><span data-stu-id="3547e-180">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="3547e-181">Escolha **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="3547e-181">Choose **PowerShell**.</span></span>

  <span data-ttu-id="3547e-182">Quando você fizer isso, o Visual Studio Code criará um diretório e um arquivo ".vscode\launch.json" na raiz da sua pasta de workspace.</span><span class="sxs-lookup"><span data-stu-id="3547e-182">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="3547e-183">A configuração de depuração é armazena nesse local.</span><span class="sxs-lookup"><span data-stu-id="3547e-183">This is where your debug configuration is stored.</span></span> <span data-ttu-id="3547e-184">Quando os arquivos estão em um repositório Git, normalmente deseja-se confirmar o arquivo launch.json.</span><span class="sxs-lookup"><span data-stu-id="3547e-184">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="3547e-185">O conteúdo do arquivo launch.json é:</span><span class="sxs-lookup"><span data-stu-id="3547e-185">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="3547e-186">Isso representa os cenários comuns de depuração.</span><span class="sxs-lookup"><span data-stu-id="3547e-186">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="3547e-187">No entanto, ao abrir este arquivo no editor, você vê um botão **Adicionar Configuração...**.</span><span class="sxs-lookup"><span data-stu-id="3547e-187">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="3547e-188">Você pode pressionar esse botão para adicionar mais configurações de depuração do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3547e-188">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="3547e-189">Uma configuração útil a ser adicionada é **PowerShell: Iniciar o Script**.</span><span class="sxs-lookup"><span data-stu-id="3547e-189">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="3547e-190">Com essa configuração, você pode especificar um arquivo específico com argumentos opcionais que devem ser iniciado sempre que você pressionar F5, não importa qual arquivo está ativo no momento no editor.</span><span class="sxs-lookup"><span data-stu-id="3547e-190">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="3547e-191">Quando a configuração de depuração é estabelecida, selecione qual configuração você deseja usar durante uma sessão de depuração, selecionando uma no menu suspenso de configuração de depuração na barra de ferramentas da exibição **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="3547e-191">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="3547e-192">Há alguns blogs que podem ser úteis para você começar a usar a extensão do PowerShell para o Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="3547e-192">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="3547e-193">[Extensão do PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="3547e-193">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="3547e-194">[Gravar e depurar scripts do PowerShell no Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="3547e-194">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="3547e-195">[Orientação sobre depuração no Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="3547e-195">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="3547e-196">[Depuração do PowerShell no Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="3547e-196">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="3547e-197">[Introdução ao desenvolvimento do PowerShell no Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="3547e-197">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="3547e-198">[Recursos de edição do Visual Studio Code para desenvolvimento do PowerShell – parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="3547e-198">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="3547e-199">[Recursos de edição do Visual Studio Code para desenvolvimento do PowerShell – parte 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="3547e-199">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="3547e-200">[Depuração de script do PowerShell no Visual Studio Code– parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="3547e-200">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="3547e-201">[Depuração de script do PowerShell no Visual Studio Code– parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="3547e-201">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="3547e-202">Extensão do PowerShell para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3547e-202">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="3547e-203">O código-fonte da extensão do PowerShell pode ser encontrado no [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="3547e-203">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
