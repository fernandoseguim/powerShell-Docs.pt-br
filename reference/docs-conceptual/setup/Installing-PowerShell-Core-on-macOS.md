---
title: Instalar o PowerShell Core no macOS
description: Informações sobre a instalação do PowerShell Core no macOS
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998496"
---
# <a name="installing-powershell-core-on-macos"></a>Instalar o PowerShell Core no macOS

O PowerShell Core oferece suporte para macOS 10.12 e superior.
Todos os pacotes estão disponíveis na nossa página [Lançamentos][] do GitHub.
Depois de instalar o pacote, execute `pwsh` em um terminal.

## <a name="about-brew"></a>Sobre Brew

[Homebrew][brew] é o gerenciador de pacotes preferido para macOS.
Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Instalação da versão estável mais recente por meio do Homebrew no macOS 10.12 ou superior

Confira [Sobre Brew](#about-brew) para obter mais informações sobre Brew.

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
> Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas é necessário sair e entrar novamente no shell do PowerShell para concluir a atualização e atualizar os valores mostrados em $PSVersionTable.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Instalação da versão prévia estável mais recente por meio do Homebrew no macOS 10.12 ou superior

Confira [Sobre Brew](#about-brew) para obter mais informações sobre Brew.

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

Instale o [OpenSSL](#install-openssl), pois isso é necessário para operações CIM e comunicação remota do PowerShell.

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

Instale o [OpenSSL](#install-openssl), pois isso é necessário para operações CIM e comunicação remota do PowerShell.

## <a name="installing-dependencies"></a>Instalar dependências

### <a name="install-xcode-command-line-tools"></a>Instalar ferramentas da linha de comando XCode

```shell
xcode-select -install
```

### <a name="install-openssl"></a>Instalar OpenSSL

O OpenSSL é necessário para operações CIM e comunicação remota do PowerShell.  Você pode instalar por meio de MacPorts ou Brew.

#### <a name="install-openssl-via-brew"></a>Instalar o OpenSSL por meio de Brew

Confira [Sobre Brew](#about-brew) para obter mais informações sobre Brew.

Execute `brew install openssl` para instalar o OpenSSL.

#### <a name="install-openssl-via-macports"></a>Instalar o OpenSSL por meio de MacPorts

1. Instalar as [ferramentas da linha de comando XCode](#install-xcode-command-line-tools)
1. Instale MacPorts.
   Confira o [guia de instalação](https://guide.macports.org/chunked/installing.macports.html) se precisar de instruções.
1. Atualizar MacPorts executando `sudo port selfupdate`
1. Atualizar pacotes de MacPorts executando `sudo port upgrade outdated`
1. Instalar o OpenSSL executando `sudo port instal openssl`
1. Vincule as bibliotecas para que o PowerShell possa usá-las.

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
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
Portanto, `$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`, e o link simbólico é colocado em `/usr/local/bin/pwsh`.

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
