---
title: Instalar o PowerShell Core no macOS
description: Informações sobre a instalação do PowerShell Core no macOS
ms.date: 08/06/2018
ms.openlocfilehash: 042c933dfa83f3ab52e315036e4f817145116d00
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611480"
---
# <a name="installing-powershell-core-on-macos"></a>Instalar o PowerShell Core no macOS

O PowerShell Core oferece suporte para macOS 10.12 e superior.
Todos os pacotes estão disponíveis na nossa página [Lançamentos][] do GitHub.
Depois de instalar o pacote, execute `pwsh` em um terminal.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Instalação da versão estável mais recente por meio do Homebrew no macOS 10.12 ou superior

[Homebrew][brew] é o gerenciador de pacotes preferido para macOS.
Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].

Agora, você pode instalar o PowerShell:

```sh
brew cask install powershell
```

Por fim, verifique se a instalação está funcionando corretamente:

```sh
pwsh
```

Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar o PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas será necessário sair e entrar novamente no shell do PowerShell para concluir a atualização.
> e atualizar os valores mostrados em $PSVersionTable.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Instalação da versão prévia estável mais recente por meio do Homebrew no macOS 10.12 ou superior

[Homebrew][brew] é o gerenciador de pacotes preferido para macOS.
Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].

Depois da instalação do Homebrew, é fácil instalar o PowerShell.
Primeiro, instale [Cask-Versions][cask-versions], que permite instalar versões alternativas de pacotes cask:

```sh
brew tap homebrew/cask-versions
```

Agora, você pode instalar o PowerShell:

```sh
brew cask install powershell-preview
```

Por fim, verifique se a instalação está funcionando corretamente:

```sh
pwsh-preview
```

Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar o PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas será necessário sair e entrar novamente no shell do PowerShell para concluir a atualização.
> e atualizar os valores mostrados em $PSVersionTable.

## <a name="installation-via-direct-download"></a>Instalação por meio de download direto

Baixe o pacote PKG `powershell-6.1.0-osx-x64.pkg`
na página [Lançamentos][] no computador com macOS.

Clique duas vezes no arquivo e siga os prompts, ou instale-o do terminal:

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a>Arquivos binários

Os arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas macOS a fim de habilitar cenários de implantação avançada.

### <a name="installing-binary-archives-on-macos"></a>Instalação de arquivos binários no macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
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

Para remover os caminhos adicionais do PowerShell, confira a seção [caminhos](#paths) neste documento e remova os caminhos desejados com `sudo rm`.

> [!NOTE]
> Isso não é necessário se você tiver instalado usando o Homebrew.

## <a name="paths"></a>Caminhos

* `$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`
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
Portanto, `$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`, e o symlink é colocado em `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Recursos adicionais

* [Homebrew Web][brew]
* [Repositório do Homebrew no Github][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Lançamentos]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
