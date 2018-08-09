---
title: Instalar o PowerShell Core no macOS
description: Informações sobre a instalação do PowerShell Core no macOS
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587458"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="39822-103">Instalar o PowerShell Core no macOS</span><span class="sxs-lookup"><span data-stu-id="39822-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="39822-104">O PowerShell Core oferece suporte para macOS 10.12 e superior.</span><span class="sxs-lookup"><span data-stu-id="39822-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="39822-105">Todos os pacotes estão disponíveis na nossa página [versões][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="39822-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="39822-106">Depois de instalar o pacote, execute `pwsh` em um terminal.</span><span class="sxs-lookup"><span data-stu-id="39822-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="39822-107">Instalação por meio do Homebrew no macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="39822-107">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="39822-108">[Homebrew][brew] é o gerenciador de pacotes preferido para macOS.</span><span class="sxs-lookup"><span data-stu-id="39822-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="39822-109">Em uma janela de terminal, digite `brew` para executar o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="39822-109">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="39822-110">Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="39822-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="39822-111">Se você já tinha o Homebrew instalado, convém executar "brew update-reset" e "brew update".</span><span class="sxs-lookup"><span data-stu-id="39822-111">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="39822-112">Versões mais antigas do Homebrew usavam 'caskroom/cask', que foi preterido, e migraram para 'homebrew/cask'.</span><span class="sxs-lookup"><span data-stu-id="39822-112">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="39822-113">Saiba mais em [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="39822-113">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="39822-114">Use o comando 'brew tap' para listar os toques atuais.</span><span class="sxs-lookup"><span data-stu-id="39822-114">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="39822-115">Se você vir 'caskroom/cask' use 'brew update' para que o Homebrew migre os toques.</span><span class="sxs-lookup"><span data-stu-id="39822-115">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="39822-116">Após a instalação/atualização do Homebrew, é fácil instalar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39822-116">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="39822-117">Para instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="39822-117">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="39822-118">Por fim, verifique se a instalação está funcionando corretamente:</span><span class="sxs-lookup"><span data-stu-id="39822-118">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="39822-119">Para sair do PowerShell e retornar ao bash, use o comando 'exit'.</span><span class="sxs-lookup"><span data-stu-id="39822-119">To exit PowerShell, and return to bash, use the 'exit' command.</span></span>
```sh
exit
```

<span data-ttu-id="39822-120">Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="39822-120">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="39822-121">Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas é necessário sair e entrar novamente no shell do PowerShell para concluir a atualização e atualizar os valores mostrados em $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="39822-121">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="39822-122">Instalar a versão prévia por meio do Homebrew no macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="39822-122">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="39822-123">[Homebrew][brew] é o gerenciador de pacotes preferido para macOS.</span><span class="sxs-lookup"><span data-stu-id="39822-123">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="39822-124">Em uma janela de terminal, digite `brew` para executar o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="39822-124">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="39822-125">Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="39822-125">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="39822-126">Se você já tinha o Homebrew instalado, convém executar "brew update-reset" e "brew update".</span><span class="sxs-lookup"><span data-stu-id="39822-126">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="39822-127">Em seguida, você deve tocar no repositório casks `versions` para obter o pacote da versão prévia:</span><span class="sxs-lookup"><span data-stu-id="39822-127">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="39822-128">Para instalar a versão prévia do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="39822-128">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="39822-129">Por fim, verifique se a instalação está funcionando corretamente:</span><span class="sxs-lookup"><span data-stu-id="39822-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="39822-130">Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar a versão prévia do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="39822-130">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="39822-131">Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas é necessário sair e entrar novamente no shell do PowerShell para concluir a atualização e atualizar os valores mostrados em $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="39822-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="39822-132">Instalação por meio de download direto</span><span class="sxs-lookup"><span data-stu-id="39822-132">Installation via Direct Download</span></span>

<span data-ttu-id="39822-133">Faça o download do pacote PKG `powershell-6.0.2-osx.10.12-x64.pkg` da página [versões][] em seu computador com macOS.</span><span class="sxs-lookup"><span data-stu-id="39822-133">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="39822-134">Clique duas vezes no arquivo e siga os prompts, ou instale-o do terminal:</span><span class="sxs-lookup"><span data-stu-id="39822-134">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="39822-135">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="39822-135">Binary Archives</span></span>

<span data-ttu-id="39822-136">Arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas macOS e Linux para habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="39822-136">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="39822-137">Instalação de arquivos binários no macOS</span><span class="sxs-lookup"><span data-stu-id="39822-137">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="39822-138">Desinstalação do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="39822-138">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="39822-139">Se você instalou o PowerShell com Homebrew, a desinstalação é fácil:</span><span class="sxs-lookup"><span data-stu-id="39822-139">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="39822-140">Se você instalou o PowerShell por meio de download direto, o PowerShell deve ser removido manualmente:</span><span class="sxs-lookup"><span data-stu-id="39822-140">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="39822-141">Para remover os caminhos adicionais do PowerShell, confira a seção [caminhos][] neste documento e remova os caminhos desejados com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="39822-141">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="39822-142">Isso não é necessário se você tiver instalado usando o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="39822-142">This is not necessary if you installed with Homebrew.</span></span>

[caminhos]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="39822-144">Caminhos</span><span class="sxs-lookup"><span data-stu-id="39822-144">Paths</span></span>

* <span data-ttu-id="39822-145">`$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="39822-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="39822-146">Perfis de usuário serão lidos de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="39822-146">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="39822-147">Perfis padrão serão lidos de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="39822-147">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="39822-148">Módulos de usuário serão lidos de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="39822-148">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="39822-149">Módulos compartilhados serão lidos de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="39822-149">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="39822-150">Módulos padrão serão lidos de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="39822-150">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="39822-151">Histórico de PSReadline será gravado em `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="39822-151">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="39822-152">Os perfis respeitam a configuração por host do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39822-152">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="39822-153">Então, os perfis de host específicos padrão existe no `Microsoft.PowerShell_profile.ps1` nas mesmas localizações.</span><span class="sxs-lookup"><span data-stu-id="39822-153">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="39822-154">O PowerShell respeita a [Especificação de Diretório Base XDG][xdg-bds] no macOS.</span><span class="sxs-lookup"><span data-stu-id="39822-154">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="39822-155">Como o macOS é uma derivação do BSD, o prefixo `/usr/local` é usado em vez de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="39822-155">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="39822-156">Portanto, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`, e o symlink é colocado em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="39822-156">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="39822-157">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="39822-157">Additional Resources</span></span>

* <span data-ttu-id="39822-158">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="39822-158">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="39822-159">[Repositório do Homebrew no Github][GitHub]</span><span class="sxs-lookup"><span data-stu-id="39822-159">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="39822-160">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="39822-160">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
