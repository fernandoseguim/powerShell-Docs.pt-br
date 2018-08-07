# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="8dc12-101">Instalar o PowerShell Core no macOS</span><span class="sxs-lookup"><span data-stu-id="8dc12-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="8dc12-102">O PowerShell Core oferece suporte para macOS 10.12 e superior.</span><span class="sxs-lookup"><span data-stu-id="8dc12-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="8dc12-103">Todos os pacotes estão disponíveis na nossa página [versões][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="8dc12-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="8dc12-104">Depois de instalar o pacote, execute `pwsh` em um terminal.</span><span class="sxs-lookup"><span data-stu-id="8dc12-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="8dc12-105">Instalação por meio do Homebrew no macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="8dc12-105">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="8dc12-106">[Homebrew][brew] é o gerenciador de pacotes preferido para macOS.</span><span class="sxs-lookup"><span data-stu-id="8dc12-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="8dc12-107">Em uma janela de terminal, digite `brew` para executar o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="8dc12-107">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="8dc12-108">Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="8dc12-108">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="8dc12-109">Se você já tinha o Homebrew instalado, convém executar "brew update-reset" e "brew update".</span><span class="sxs-lookup"><span data-stu-id="8dc12-109">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="8dc12-110">Versões mais antigas do Homebrew usavam 'caskroom/cask', que foi preterido, e migraram para 'homebrew/cask'.</span><span class="sxs-lookup"><span data-stu-id="8dc12-110">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="8dc12-111">Saiba mais em [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="8dc12-111">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="8dc12-112">Use o comando 'brew tap' para listar os toques atuais.</span><span class="sxs-lookup"><span data-stu-id="8dc12-112">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="8dc12-113">Se você vir 'caskroom/cask' use 'brew update' para que o Homebrew migre os toques.</span><span class="sxs-lookup"><span data-stu-id="8dc12-113">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="8dc12-114">Após a instalação/atualização do Homebrew, é fácil instalar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8dc12-114">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="8dc12-115">Para instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8dc12-115">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="8dc12-116">Por fim, verifique se a instalação está funcionando corretamente:</span><span class="sxs-lookup"><span data-stu-id="8dc12-116">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="8dc12-117">Para sair do PowerShell e retornar ao bash, use o comando 'exit'.</span><span class="sxs-lookup"><span data-stu-id="8dc12-117">To exit PowerShell, and return to bash, use the 'exit' command.</span></span> 
```sh
exit
```

<span data-ttu-id="8dc12-118">Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8dc12-118">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="8dc12-119">Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas é necessário sair e entrar novamente no shell do PowerShell para concluir a atualização e atualizar os valores mostrados em $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="8dc12-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="8dc12-120">Instalar a versão prévia por meio do Homebrew no macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="8dc12-120">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="8dc12-121">[Homebrew][brew] é o gerenciador de pacotes preferido para macOS.</span><span class="sxs-lookup"><span data-stu-id="8dc12-121">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="8dc12-122">Em uma janela de terminal, digite `brew` para executar o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="8dc12-122">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="8dc12-123">Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="8dc12-123">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="8dc12-124">Se você já tinha o Homebrew instalado, convém executar "brew update-reset" e "brew update".</span><span class="sxs-lookup"><span data-stu-id="8dc12-124">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="8dc12-125">Em seguida, você deve tocar no repositório casks `versions` para obter o pacote da versão prévia:</span><span class="sxs-lookup"><span data-stu-id="8dc12-125">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="8dc12-126">Para instalar a versão prévia do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8dc12-126">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="8dc12-127">Por fim, verifique se a instalação está funcionando corretamente:</span><span class="sxs-lookup"><span data-stu-id="8dc12-127">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="8dc12-128">Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar a versão prévia do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8dc12-128">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="8dc12-129">Os comandos acima podem ser chamados por meio de um host do PowerShell (pwsh), mas é necessário sair e entrar novamente no shell do PowerShell para concluir a atualização e atualizar os valores mostrados em $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="8dc12-129">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="8dc12-130">Instalação por meio de download direto</span><span class="sxs-lookup"><span data-stu-id="8dc12-130">Installation via Direct Download</span></span>

<span data-ttu-id="8dc12-131">Faça o download do pacote PKG `powershell-6.0.2-osx.10.12-x64.pkg` da página [versões][] em seu computador com macOS.</span><span class="sxs-lookup"><span data-stu-id="8dc12-131">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="8dc12-132">Clique duas vezes no arquivo e siga os prompts, ou instale-o do terminal:</span><span class="sxs-lookup"><span data-stu-id="8dc12-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="8dc12-133">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="8dc12-133">Binary Archives</span></span>

<span data-ttu-id="8dc12-134">Arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas macOS e Linux para habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="8dc12-134">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="8dc12-135">Instalação de arquivos binários no macOS</span><span class="sxs-lookup"><span data-stu-id="8dc12-135">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="8dc12-136">Desinstalação do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8dc12-136">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="8dc12-137">Se você instalou o PowerShell com Homebrew, a desinstalação é fácil:</span><span class="sxs-lookup"><span data-stu-id="8dc12-137">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="8dc12-138">Se você instalou o PowerShell por meio de download direto, o PowerShell deve ser removido manualmente:</span><span class="sxs-lookup"><span data-stu-id="8dc12-138">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="8dc12-139">Para remover os caminhos adicionais do PowerShell, confira a seção [caminhos][] neste documento e remova os caminhos desejados com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="8dc12-139">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="8dc12-140">Isso não é necessário se você tiver instalado usando o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="8dc12-140">This is not necessary if you installed with Homebrew.</span></span>

[caminhos]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="8dc12-142">Caminhos</span><span class="sxs-lookup"><span data-stu-id="8dc12-142">Paths</span></span>

* <span data-ttu-id="8dc12-143">`$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="8dc12-143">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="8dc12-144">Perfis de usuário serão lidos de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8dc12-144">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="8dc12-145">Perfis padrão serão lidos de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8dc12-145">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="8dc12-146">Módulos de usuário serão lidos de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8dc12-146">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8dc12-147">Módulos compartilhados serão lidos de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8dc12-147">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8dc12-148">Módulos padrão serão lidos de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="8dc12-148">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="8dc12-149">Histórico de PSReadline será gravado em `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="8dc12-149">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="8dc12-150">Os perfis respeitam a configuração por host do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8dc12-150">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="8dc12-151">Então, os perfis de host específicos padrão existe no `Microsoft.PowerShell_profile.ps1` nas mesmas localizações.</span><span class="sxs-lookup"><span data-stu-id="8dc12-151">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="8dc12-152">O PowerShell respeita a [Especificação de Diretório Base XDG][xdg-bds] no macOS.</span><span class="sxs-lookup"><span data-stu-id="8dc12-152">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="8dc12-153">Como o macOS é uma derivação do BSD, o prefixo `/usr/local` é usado em vez de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="8dc12-153">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="8dc12-154">Portanto, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`, e o symlink é colocado em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="8dc12-154">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8dc12-155">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="8dc12-155">Additional Resources</span></span>

* <span data-ttu-id="8dc12-156">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="8dc12-156">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="8dc12-157">[Repositório do Homebrew no Github][GitHub]</span><span class="sxs-lookup"><span data-stu-id="8dc12-157">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="8dc12-158">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="8dc12-158">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
