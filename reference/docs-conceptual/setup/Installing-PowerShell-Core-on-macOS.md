# <a name="installing-powershell-core-on-macos"></a>Instalar o PowerShell Core no macOS

O PowerShell Core oferece suporte para macOS 10.12 e superior.
Todos os pacotes estão disponíveis na nossa página [versões][] do GitHub.
Depois de instalar o pacote, execute `pwsh` em um terminal.

### <a name="installation-via-homebrew-on-macos-1012"></a>Instalação por meio do Homebrew no macOS 10.12+

[Homebrew][brew] é o gerenciador de pacotes preferido para macOS.
Em uma janela de terminal, digite `brew` para executar o Homebrew.  Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].

> [!NOTE]
> Se você já tinha o Homebrew instalado, convém executar "brew update-reset" e "brew update".
```sh
brew update-reset
brew update
```

> Versões mais antigas do Homebrew usavam 'caskroom/cask', que foi preterido, e migraram para 'homebrew/cask'.  Saiba mais em [Homebrew-cask][cask]. Use o comando 'brew tap' para listar os toques atuais.  Se você vir 'caskroom/cask' use 'brew update' para que o Homebrew migre os toques.

```sh
brew tap
brew update
```

Após a instalação/atualização do Homebrew, é fácil instalar o PowerShell.

Para instalar o PowerShell:

```sh
brew cask install powershell
```

Por fim, verifique se a instalação está funcionando corretamente:

```sh
pwsh
```

Para sair do PowerShell e retornar ao bash, use o comando 'exit'. 
```sh
exit
```

Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar o PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas é necessário sair e entrar novamente no shell do PowerShell para concluir a atualização e atualizar os valores mostrados em $PSVersionTable.

### <a name="installing-preview-via-homebrew-on-macos-1012"></a>Instalar a versão prévia por meio do Homebrew no macOS 10.12 +

[Homebrew][brew] é o gerenciador de pacotes preferido para macOS.
Em uma janela de terminal, digite `brew` para executar o Homebrew.  Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].

> [!NOTE]
> Se você já tinha o Homebrew instalado, convém executar "brew update-reset" e "brew update".
```sh
brew update-reset
brew update
```

Em seguida, você deve tocar no repositório casks `versions` para obter o pacote da versão prévia:

```sh
brew tap homebrew/cask-versions
```

Para instalar a versão prévia do PowerShell:

```sh
brew cask install powershell-preview
```

Por fim, verifique se a instalação está funcionando corretamente:

```sh
pwsh-preview
```

Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar a versão prévia do PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas é necessário sair e entrar novamente no shell do PowerShell para concluir a atualização e atualizar os valores mostrados em $PSVersionTable.

### <a name="installation-via-direct-download"></a>Instalação por meio de download direto

Faça o download do pacote PKG `powershell-6.0.2-osx.10.12-x64.pkg` da página [versões][] em seu computador com macOS.

Clique duas vezes no arquivo e siga os prompts, ou instale-o do terminal:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Arquivos binários

Arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas macOS e Linux para habilitar cenários de implantação avançada.

### <a name="installing-binary-archives-on-macos"></a>Instalação de arquivos binários no macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a>Desinstalação do PowerShell Core

Se você instalou o PowerShell com Homebrew, a desinstalação é fácil:

```sh
brew cask uninstall powershell
```

Se você instalou o PowerShell por meio de download direto, o PowerShell deve ser removido manualmente:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Para remover os caminhos adicionais do PowerShell, confira a seção [caminhos][] neste documento e remova os caminhos desejados com `sudo rm`.

> [!NOTE]
> Isso não é necessário se você tiver instalado usando o Homebrew.

[caminhos]:#paths

## <a name="paths"></a>Caminhos

* `$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`
* Perfis de usuário serão lidos de `~/.config/powershell/profile.ps1`
* Perfis padrão serão lidos de `$PSHOME/profile.ps1`
* Módulos de usuário serão lidos de `~/.local/share/powershell/Modules`
* Módulos compartilhados serão lidos de `/usr/local/share/powershell/Modules`
* Módulos padrão serão lidos de `$PSHOME/Modules`
* Histórico de PSReadline será gravado em `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Os perfis respeitam a configuração por host do PowerShell.
Então, os perfis de host específicos padrão existe no `Microsoft.PowerShell_profile.ps1` nas mesmas localizações.

O PowerShell respeita a [Especificação de Diretório Base XDG][xdg-bds] no macOS.

Como o macOS é uma derivação do BSD, o prefixo `/usr/local` é usado em vez de `/opt`.
Portanto, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`, e o symlink é colocado em `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Recursos adicionais

* [Homebrew Web][brew]
* [Repositório do Homebrew no Github][GitHub]
* [Homebrew-Cask][cask]


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
