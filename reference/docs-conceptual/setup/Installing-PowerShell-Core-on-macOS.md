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
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="b0c4a-103">Instalar o PowerShell Core no macOS</span><span class="sxs-lookup"><span data-stu-id="b0c4a-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="b0c4a-104">O PowerShell Core oferece suporte para macOS 10.12 e superior.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="b0c4a-105">Todos os pacotes estão disponíveis na nossa página [Lançamentos][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="b0c4a-106">Depois de instalar o pacote, execute `pwsh` em um terminal.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="b0c4a-107">Sobre Brew</span><span class="sxs-lookup"><span data-stu-id="b0c4a-107">About Brew</span></span>

<span data-ttu-id="b0c4a-108">[Homebrew][brew] é o gerenciador de pacotes preferido para macOS.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="b0c4a-109">Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="b0c4a-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="b0c4a-110">Instalação da versão estável mais recente por meio do Homebrew no macOS 10.12 ou superior</span><span class="sxs-lookup"><span data-stu-id="b0c4a-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="b0c4a-111">Confira [Sobre Brew](#about-brew) para obter mais informações sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b0c4a-112">Agora, você pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="b0c4a-113">Por fim, verifique se a instalação está funcionando corretamente:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="b0c4a-114">Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="b0c4a-115">Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas é necessário sair e entrar novamente no shell do PowerShell para concluir a atualização e atualizar os valores mostrados em $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="b0c4a-116">Instalação da versão prévia estável mais recente por meio do Homebrew no macOS 10.12 ou superior</span><span class="sxs-lookup"><span data-stu-id="b0c4a-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="b0c4a-117">Confira [Sobre Brew](#about-brew) para obter mais informações sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b0c4a-118">Depois da instalação do Homebrew, é fácil instalar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="b0c4a-119">Primeiro, instale [Cask-Versions][cask-versions], que permite instalar versões alternativas de pacotes cask:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="b0c4a-120">Agora, você pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="b0c4a-121">Por fim, verifique se a instalação está funcionando corretamente:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="b0c4a-122">Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="b0c4a-123">Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas será necessário sair e entrar novamente no shell do PowerShell para concluir a atualização.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="b0c4a-124">e atualizar os valores mostrados em $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="b0c4a-125">Instalação por meio de download direto</span><span class="sxs-lookup"><span data-stu-id="b0c4a-125">Installation via Direct Download</span></span>

<span data-ttu-id="b0c4a-126">Baixe o pacote PKG `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="b0c4a-127">na página [Lançamentos][] no computador com macOS.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="b0c4a-128">Clique duas vezes no arquivo e siga os prompts, ou instale-o do terminal:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="b0c4a-129">Instale o [OpenSSL](#install-openssl), pois isso é necessário para operações CIM e comunicação remota do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="b0c4a-130">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="b0c4a-130">Binary Archives</span></span>

<span data-ttu-id="b0c4a-131">Os arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas macOS a fim de habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="b0c4a-132">Instalação de arquivos binários no macOS</span><span class="sxs-lookup"><span data-stu-id="b0c4a-132">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="b0c4a-133">Instale o [OpenSSL](#install-openssl), pois isso é necessário para operações CIM e comunicação remota do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="b0c4a-134">Instalar dependências</span><span class="sxs-lookup"><span data-stu-id="b0c4a-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="b0c4a-135">Instalar ferramentas da linha de comando XCode</span><span class="sxs-lookup"><span data-stu-id="b0c4a-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="b0c4a-136">Instalar OpenSSL</span><span class="sxs-lookup"><span data-stu-id="b0c4a-136">Install OpenSSL</span></span>

<span data-ttu-id="b0c4a-137">O OpenSSL é necessário para operações CIM e comunicação remota do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="b0c4a-138">Você pode instalar por meio de MacPorts ou Brew.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="b0c4a-139">Instalar o OpenSSL por meio de Brew</span><span class="sxs-lookup"><span data-stu-id="b0c4a-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="b0c4a-140">Confira [Sobre Brew](#about-brew) para obter mais informações sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b0c4a-141">Execute `brew install openssl` para instalar o OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="b0c4a-142">Instalar o OpenSSL por meio de MacPorts</span><span class="sxs-lookup"><span data-stu-id="b0c4a-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="b0c4a-143">Instalar as [ferramentas da linha de comando XCode](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="b0c4a-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="b0c4a-144">Instale MacPorts.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-144">Install MacPorts.</span></span>
   <span data-ttu-id="b0c4a-145">Confira o [guia de instalação](https://guide.macports.org/chunked/installing.macports.html) se precisar de instruções.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="b0c4a-146">Atualizar MacPorts executando `sudo port selfupdate`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="b0c4a-147">Atualizar pacotes de MacPorts executando `sudo port upgrade outdated`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="b0c4a-148">Instalar o OpenSSL executando `sudo port instal openssl`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="b0c4a-149">Vincule as bibliotecas para que o PowerShell possa usá-las.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="b0c4a-150">Desinstalação do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="b0c4a-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="b0c4a-151">Se você instalou o PowerShell com Homebrew, a desinstalação é fácil:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="b0c4a-152">Se você instalou o PowerShell por meio de download direto, o PowerShell deve ser removido manualmente:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="b0c4a-153">Para remover os caminhos adicionais do PowerShell, confira a seção [caminhos](#paths) neste documento e remova os caminhos desejados com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="b0c4a-154">Isso não é necessário se você tiver instalado usando o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="b0c4a-155">Caminhos</span><span class="sxs-lookup"><span data-stu-id="b0c4a-155">Paths</span></span>

* <span data-ttu-id="b0c4a-156">`$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="b0c4a-157">Perfis de usuário serão lidos de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="b0c4a-158">Perfis padrão serão lidos de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="b0c4a-159">Módulos de usuário serão lidos de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b0c4a-160">Módulos compartilhados serão lidos de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b0c4a-161">Módulos padrão serão lidos de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="b0c4a-162">Histórico de PSReadline será gravado em `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="b0c4a-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b0c4a-163">Os perfis respeitam a configuração por host do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="b0c4a-164">Então, os perfis de host específicos padrão existe no `Microsoft.PowerShell_profile.ps1` nas mesmas localizações.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b0c4a-165">O PowerShell respeita a [Especificação de Diretório Base XDG][xdg-bds] no macOS.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="b0c4a-166">Como o macOS é uma derivação do BSD, o prefixo `/usr/local` é usado em vez de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="b0c4a-167">Portanto, `$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`, e o link simbólico é colocado em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b0c4a-168">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b0c4a-168">Additional Resources</span></span>

* <span data-ttu-id="b0c4a-169">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="b0c4a-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="b0c4a-170">[Repositório do Homebrew no Github][GitHub]</span><span class="sxs-lookup"><span data-stu-id="b0c4a-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="b0c4a-171">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="b0c4a-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Lançamentos]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
