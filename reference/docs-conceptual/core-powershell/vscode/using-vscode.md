# <a name="using-visual-studio-code-for-powershell-development"></a>Uso do Visual Studio Code para desenvolvimento do PowerShell

Além do [PowerShell ISE][ise], o PowerShell também tem suporte no Visual Studio Code.
Além disso, o ISE não é compatível com o PowerShell Core, embora haja suporte do Visual Studio Code para o PowerShell Core em todas as plataformas (Windows, macOS e Linux)

Você pode usar o Visual Studio Code no Windows com o PowerShell versão 5 usando o Windows 10 ou instalando o [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) para sistemas operacionais do Windows de nível baixo (por exemplo, Windows 8.1 etc.).

Antes de iniciá-lo, verifique se o PowerShell existe no sistema.
Para cargas de trabalho modernas no Windows, macOS e Linux, consulte:

- [Instalação do PowerShell Core no macOS e Linux][install-pscore-linux]
- [Instalação do PowerShell Core no Windows][install-pscore-windows]

Para cargas de trabalho tradicionais do Windows PowerShell, veja [instalação do Windows PowerShell][install-winps].

## <a name="editing-with-visual-studio-code"></a>Edição com o Visual Studio Code

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Instalação do Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: siga as instruções de instalação na página [Execução do código VS no Linux](https://code.visualstudio.com/docs/setup/linux)

- **macOS**: siga as instruções de instalação na página [Execução do código VS no macOS](https://code.visualstudio.com/docs/setup/mac)

> [!IMPORTANT]
> No macOS, você deve instalar o OpenSSL para que a extensão do PowerShell funcione corretamente.
> A maneira mais fácil de fazer isso é instalar o [Homebrew](http://brew.sh/) e, em seguida, executar `brew install openssl`.
> Agora, a extensão do PowerShell será capaz de carregar com êxito.

- **Windows**: siga as instruções de instalação na página [Execução do código VS no Windows](https://code.visualstudio.com/docs/setup/windows)

### <a name="2-installing-powershell-extension"></a>2. Instalação da extensão do PowerShell

- Inicie o aplicativo Visual Studio Code pelo:
    - **Windows**: digitando `code` na sua sessão do PowerShell
    - **Linux**: digitando `code` em seu terminal
    - **macOS**: digitando `code` em seu terminal

- Inicie **Abertura rápida** pressionando **Ctrl+P** (**Cmd+P** no Mac).
- Na Abertura rápida, digite `ext install powershell` e clique em **Enter**.
- A exibição **Extensões** será aberta na barra lateral. Selecione a extensão do PowerShell da Microsoft.
  Você verá algo como abaixo:

  ![VSCode](../../images/vscode.png)

- Clique no botão **Instalar** na extensão do PowerShell da Microsoft.
- Após a instalação, você verá que o botão **Instalar** mudará para **Recarregar**.
  Clique em **Recarregar**.
- Depois de recarregar o Visual Studio Code, você está pronto para edição.

Por exemplo, para criar um novo arquivo, clique em **Arquivo -> Novo**.
Para salvá-lo, clique em **Arquivo -> Salvar** e, em seguida, forneça um nome de arquivo. Digamos `HelloWorld.ps1`.
Para fechar o arquivo, clique no "x" ao lado do nome de arquivo.
Para sair do Visual Studio Code, **Arquivo -> Sair**.

#### <a name="using-a-specific-installed-version-of-powershell"></a>Uso de uma versão instalada específica do PowerShell

Se quiser usar uma instalação específica do PowerShell com o Visual Studio Code, você precisará adicionar uma nova variável ao arquivo de configurações do usuário.

1. Clique em **Arquivo -> Preferências -> Configurações**
1. Dois painéis de editor serão exibidos.
   No painel mais à direita (`settings.json`), insira a configuração abaixo apropriada para seu sistema operacional entre as duas chaves (`{` e `}`) e substitua  *<version>*  pela versão do PowerShell instalada:

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. Substitua a configuração pelo caminho para o executável desejado do PowerShell
1. Salve o arquivo de configurações e reinicie o Visual Studio Code

#### <a name="configuration-settings-for-visual-studio-code"></a>Definições de configuração para o Visual Studio Code

Usando as etapas no parágrafo anterior, você pode adicionar configurações no `settings.json`.

Recomendamos as seguintes definições de configuração para o Visual Studio Code:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>Depuração com o Visual Studio Code

### <a name="no-workspace-debugging"></a>Depuração sem espaço de trabalho

A partir da versão do Visual Studio Code 1.9, você pode depurar scripts do PowerShell sem a necessidade de abrir a pasta que contém o script do PowerShell.
Basta abrir o arquivo de script do PowerShell usando **Arquivo -> Abrir Arquivo...** , definir um ponto de interrupção em uma linha (pressione F9) e, em seguida, pressionar F5 para iniciar a depuração.
Será exibido o painel de ações de depuração que permite que você interrompa o depurador, execute em etapas, retome e pare a depuração.

### <a name="workspace-debugging"></a>Depuração do espaço de trabalho

A depuração do espaço de trabalho refere-se a depuração no contexto de uma pasta que você abriu no Visual Studio Code usando **Abrir Pasta...**  do menu **Arquivo**.
A pasta que você abrir normalmente é a pasta do projeto do PowerShell e/ou a raiz do repositório Git.

Mesmo nesse modo, você pode iniciar a depuração de script do PowerShell selecionado no momento pressionando F5.
No entanto, a depuração do espaço de trabalho permite definir várias configurações de depuração diferentes de depurar apenas o arquivo aberto no momento.
Por exemplo, você pode adicionar configurações para:

- Iniciar testes Pester no depurador
- Abrir um arquivo específico com argumentos no depurador
- Inicie uma sessão interativa no depurador
- Anexar o depurador a um processo de host do PowerShell

Siga estas etapas para criar o arquivo de configuração de depuração:

1. Abra a exibição **Depurar** pressionando **Ctrl+Shift+D** (**Cmd+Shift+D** no Mac).
1. Pressione o ícone de engrenagem **Configurar** na barra de ferramentas.
1. O Visual Studio Code solicitará que você **Selecione Ambiente**.
   Escolha **PowerShell**.

   Quando você fizer isso, o Visual Studio Code criará um diretório e um arquivo ".vscode\launch.json" na raiz da sua pasta de espaço de trabalho.
   A configuração de depuração é armazena nesse local. Se os arquivos estiverem em um repositório Git, normalmente você desejará confirmar o arquivo launch.json.
   O conteúdo do arquivo launch.json é:

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

Isso representa os cenários comuns de depuração.
No entanto, ao abrir este arquivo no editor, você vê um botão **Adicionar Configuração...**.
Você pode pressionar esse botão para adicionar mais configurações de depuração do PowerShell. Uma configuração útil a ser adicionada é **PowerShell: Iniciar o Script**.
Com essa configuração, você pode especificar um arquivo específico com argumentos opcionais que devem ser iniciado sempre que você pressionar F5, não importa qual arquivo está ativo no momento no editor.

Quando a configuração de depuração é estabelecida, selecione qual configuração você deseja usar durante uma sessão de depuração, selecionando uma no menu suspenso de configuração de depuração na barra de ferramentas da exibição **Depurar**.

Há alguns blogs que podem ser úteis para você começar a usar a extensão do PowerShell para o Visual Studio Code

- Visual Studio Code: [extensão do PowerShell][ps-extension]
- [Gravar e depurar scripts do PowerShell no Visual Studio Code][debug]
- [Orientação sobre depuração no Visual Studio Code][vscode-guide]
- [Depuração do PowerShell no Visual Studio Code][ps-vscode]
- [Introdução ao desenvolvimento do PowerShell no Visual Studio Code][getting-started]
- [Recursos de edição do Visual Studio Code para desenvolvimento do PowerShell – parte 1][editing-part1]
- [Recursos de edição do Visual Studio Code para desenvolvimento do PowerShell – parte 2][editing-part2]
- [Depuração de script do PowerShell no Visual Studio Code– parte 1][debugging-part1]
- [Depuração de script do PowerShell no Visual Studio Code– parte 2][debugging-part2]

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

## <a name="powershell-extension-for-visual-studio-code"></a>Extensão do PowerShell para Visual Studio Code

O código-fonte da extensão do PowerShell pode ser encontrado no [GitHub](https://github.com/PowerShell/vscode-powershell).
