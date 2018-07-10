# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="7a9c0-101">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="7a9c0-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="7a9c0-102">É compatível com [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="7a9c0-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="7a9c0-103">Em distribuições Linux sem suporte oficial, tente usar o [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="7a9c0-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="7a9c0-104">Além disso, tente implantar binários do PowerShell diretamente usando o arquivo [`tar.gz` do Linux][tar], mas você precisaria configurar as dependências necessárias com base no sistema operacional em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="7a9c0-105">Todos os pacotes estão disponíveis na nossa página [versões][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="7a9c0-106">Depois de instalar o pacote, execute `pwsh` em um terminal.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="7a9c0-107">Instalando versões prévias</span><span class="sxs-lookup"><span data-stu-id="7a9c0-107">Installing Preview Releases</span></span>

<span data-ttu-id="7a9c0-108">Ao instalar uma versão prévia do PowerShell Core para Linux por meio de um Repositório de Pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="7a9c0-109">A instalação por meio de download direito não é alterada, somente o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="7a9c0-110">Aqui está uma tabela dos comandos para instalar os pacotes estáveis e de versão prévia usando vários gerenciadores de pacotes:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="7a9c0-111">Distribuições</span><span class="sxs-lookup"><span data-stu-id="7a9c0-111">Distrobution(s)</span></span>|<span data-ttu-id="7a9c0-112">Comando estável</span><span class="sxs-lookup"><span data-stu-id="7a9c0-112">Stable Command</span></span> | <span data-ttu-id="7a9c0-113">Comando de versão prévia</span><span class="sxs-lookup"><span data-stu-id="7a9c0-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="7a9c0-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="7a9c0-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="7a9c0-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="7a9c0-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="7a9c0-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="7a9c0-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="7a9c0-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="7a9c0-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="7a9c0-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="7a9c0-119">Instalação por meio do repositório de pacotes – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="7a9c0-120">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7a9c0-121">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-121">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7a9c0-122">Como superusuário, registre o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="7a9c0-123">Daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="7a9c0-124">Instalação por meio de download direto – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="7a9c0-125">Baixe o pacote Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7a9c0-126">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7a9c0-127">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="7a9c0-128">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="7a9c0-129">Desinstalação – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="7a9c0-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="7a9c0-131">Instalação por meio do repositório de pacotes – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="7a9c0-132">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7a9c0-133">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-133">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7a9c0-134">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="7a9c0-135">Instalação por meio de download direto – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="7a9c0-136">Baixe o pacote Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7a9c0-137">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7a9c0-138">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="7a9c0-139">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="7a9c0-140">Desinstalação – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="7a9c0-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="7a9c0-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="7a9c0-142">Foi adicionado suporte para o Ubuntu 17.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="7a9c0-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="7a9c0-143">Instalação por meio do repositório de pacotes – Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="7a9c0-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="7a9c0-144">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7a9c0-145">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-145">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7a9c0-146">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="7a9c0-147">Instalação por meio de download direto – Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="7a9c0-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="7a9c0-148">Baixe o pacote Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7a9c0-149">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7a9c0-150">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="7a9c0-151">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="7a9c0-152">Desinstalação – Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="7a9c0-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="7a9c0-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="7a9c0-154">Foi adicionado suporte para o Ubuntu 18.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="7a9c0-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="7a9c0-155">Instalação por meio do repositório de pacotes – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="7a9c0-156">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7a9c0-157">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-157">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7a9c0-158">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="7a9c0-159">Instalação por meio de download direto – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="7a9c0-160">Baixe o pacote Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7a9c0-161">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7a9c0-162">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="7a9c0-163">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="7a9c0-164">Desinstalação – Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="7a9c0-164">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="7a9c0-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="7a9c0-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="7a9c0-166">Instalação por meio do repositório de pacotes – Debian 8</span><span class="sxs-lookup"><span data-stu-id="7a9c0-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="7a9c0-167">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7a9c0-168">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-168">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7a9c0-169">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="7a9c0-170">Instalação por meio de download direto – Debian 8</span><span class="sxs-lookup"><span data-stu-id="7a9c0-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="7a9c0-171">Baixe o pacote Debian `powershell_6.0.2-1.debian.8_amd64.deb` da página [versões][] no computador Debian.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="7a9c0-172">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7a9c0-173">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="7a9c0-174">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="7a9c0-175">Desinstalação – Debian 8</span><span class="sxs-lookup"><span data-stu-id="7a9c0-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="7a9c0-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="7a9c0-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="7a9c0-177">Instalação por meio do repositório de pacotes – Debian 9</span><span class="sxs-lookup"><span data-stu-id="7a9c0-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="7a9c0-178">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7a9c0-179">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-179">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7a9c0-180">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="7a9c0-181">Instalação por meio de download direto – Debian 9</span><span class="sxs-lookup"><span data-stu-id="7a9c0-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="7a9c0-182">Baixe o pacote Debian `powershell_6.0.2-1.debian.9_amd64.deb` da página [versões][] no computador Debian.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="7a9c0-183">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="7a9c0-184">Desinstalação – Debian 9</span><span class="sxs-lookup"><span data-stu-id="7a9c0-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="7a9c0-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="7a9c0-186">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="7a9c0-187">Instalação por meio do repositório de pacotes (preferencial) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="7a9c0-188">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7a9c0-189">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="7a9c0-190">Instalação por meio de download direto – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="7a9c0-191">Usando o [CentOS 7][], baixe o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da página [versões][] no computador CentOS.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="7a9c0-192">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7a9c0-193">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="7a9c0-194">Desinstalação – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7a9c0-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7a9c0-197">Instalação por meio do repositório de pacotes (preferencial) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7a9c0-198">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7a9c0-199">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7a9c0-200">Instalação por meio de download direto – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7a9c0-201">Baixe o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da página [versões][] no computador Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="7a9c0-202">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7a9c0-203">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7a9c0-204">Desinstalação – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="7a9c0-205">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7a9c0-205">OpenSUSE 42.2</span></span>

<span data-ttu-id="7a9c0-206">Durante a instalação do PowerShell Core, o `zypper` pode relatar o erro a seguir:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="7a9c0-207">Nesse caso, verifique se uma biblioteca `libcurl` compatível está presente, conferindo se o comando a seguir mostra o pacote `libcurl4` como instalado:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="7a9c0-208">Em seguida, escolha a solução `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` ao instalar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="7a9c0-209">Instalação por meio do repositório de pacotes (preferencial) – OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7a9c0-209">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="7a9c0-210">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="7a9c0-211">Instalação por meio de download direto – OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7a9c0-211">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="7a9c0-212">Baixe o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da página [versões][] no computador OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7a9c0-213">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="7a9c0-214">Desinstalação – OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7a9c0-214">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="7a9c0-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="7a9c0-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="7a9c0-216">O Fedora 28 é compatível apenas com o PowerShell Core 6.1 e mais recentes.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="7a9c0-217">Instalação por meio do repositório de pacotes (preferencial) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7a9c0-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="7a9c0-218">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="7a9c0-219">Instalação por meio de download direto – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7a9c0-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="7a9c0-220">Baixe o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da página [versões][] no computador Fedora.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="7a9c0-221">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7a9c0-222">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="7a9c0-223">Desinstalação – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7a9c0-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="7a9c0-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="7a9c0-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="7a9c0-225">O suporte para o Arch é experimental.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-225">Arch support is experimental.</span></span>

<span data-ttu-id="7a9c0-226">O PowerShell está disponível no AUR (Repositório de Usuários do [Arch Linux][]).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="7a9c0-227">Ele pode ser compilado com a [versão marcada mais recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="7a9c0-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="7a9c0-228">Ele pode ser compilado na [confirmação mais recente com mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="7a9c0-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="7a9c0-229">Ele pode ser instalado usando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="7a9c0-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="7a9c0-230">Pacotes no AUR são mantidos pela comunidade – não há suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="7a9c0-231">Para obter mais informações sobre a instalação de pacotes usando o AUR, veja a [wiki do Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou a comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="7a9c0-233">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="7a9c0-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="7a9c0-234">O suporte para o AppImage é experimental</span><span class="sxs-lookup"><span data-stu-id="7a9c0-234">AppImage support is experimental</span></span>

<span data-ttu-id="7a9c0-235">Usando uma distribuição Linux recente, baixe a AppImage `powershell-6.0.1-x86_64.AppImage` da página [versões][] no computador Linux.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="7a9c0-236">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="7a9c0-237">A [AppImage][] permite executar o PowerShell sem instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="7a9c0-238">É um aplicativo portátil que inclui o PowerShell e suas dependências (incluindo dependências do sistema do .NET Core) em um pacote coeso.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="7a9c0-239">Esse pacote é um binário único que funciona independentemente da distribuição Linux do usuário.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-239">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="7a9c0-241">Kali</span><span class="sxs-lookup"><span data-stu-id="7a9c0-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="7a9c0-242">O suporte para o Kali é experimental.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="7a9c0-243">Instalação</span><span class="sxs-lookup"><span data-stu-id="7a9c0-243">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="7a9c0-244">Executar o PowerShell no Kali mais recente (Kali GNU/Linux Rolling) sem instalá-lo</span><span class="sxs-lookup"><span data-stu-id="7a9c0-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="7a9c0-245">Desinstalação – Kali</span><span class="sxs-lookup"><span data-stu-id="7a9c0-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="7a9c0-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="7a9c0-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="7a9c0-247">O suporte para o Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="7a9c0-248">Atualmente, o PowerShell tem suporte apenas no Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="7a9c0-249">Além disso, o CoreCLR (e, portanto, o PowerShell Core) funcionará apenas em dispositivos Pi 2 e Pi 3, pois outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), têm um processador sem suporte.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="7a9c0-250">Faça o download do [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga as [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para instalá-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="7a9c0-251">Instalação</span><span class="sxs-lookup"><span data-stu-id="7a9c0-251">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="7a9c0-252">Opcionalmente, você pode criar um link simbólico para poder iniciar o PowerShell sem especificar o caminho até o binário "pwsh"</span><span class="sxs-lookup"><span data-stu-id="7a9c0-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="7a9c0-253">Desinstalação – Raspbian</span><span class="sxs-lookup"><span data-stu-id="7a9c0-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="7a9c0-254">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="7a9c0-254">Binary Archives</span></span>

<span data-ttu-id="7a9c0-255">Os arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas Linux a fim de habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="7a9c0-256">Dependências</span><span class="sxs-lookup"><span data-stu-id="7a9c0-256">Dependencies</span></span>

<span data-ttu-id="7a9c0-257">O PowerShell cria binários portáteis para todas as distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="7a9c0-258">Porém, o tempo de execução do .NET Core exige dependências diferentes em diferentes distribuições e, portanto, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="7a9c0-259">O gráfico a seguir mostra as dependências do .NET Core 2.0 com suporte oficial em diferentes distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="7a9c0-260">SO</span><span class="sxs-lookup"><span data-stu-id="7a9c0-260">OS</span></span>                 | <span data-ttu-id="7a9c0-261">Dependências</span><span class="sxs-lookup"><span data-stu-id="7a9c0-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="7a9c0-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="7a9c0-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7a9c0-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a9c0-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="7a9c0-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="7a9c0-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="7a9c0-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7a9c0-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a9c0-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="7a9c0-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="7a9c0-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="7a9c0-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="7a9c0-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7a9c0-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a9c0-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="7a9c0-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="7a9c0-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7a9c0-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="7a9c0-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7a9c0-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a9c0-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="7a9c0-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="7a9c0-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="7a9c0-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="7a9c0-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7a9c0-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a9c0-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="7a9c0-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="7a9c0-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="7a9c0-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="7a9c0-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="7a9c0-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a9c0-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="7a9c0-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="7a9c0-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-280">CentOS 7</span></span> <br> <span data-ttu-id="7a9c0-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="7a9c0-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="7a9c0-282">RHEL 7</span></span> <br> <span data-ttu-id="7a9c0-283">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="7a9c0-283">OpenSUSE 42.2</span></span> | <span data-ttu-id="7a9c0-284">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="7a9c0-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="7a9c0-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="7a9c0-285">Fedora 27</span></span> <br> <span data-ttu-id="7a9c0-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7a9c0-286">Fedora 28</span></span> | <span data-ttu-id="7a9c0-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="7a9c0-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="7a9c0-288">Para implantar binários do PowerShell em distribuições Linux que sem suporte oficial, instale as dependências necessárias para o sistema operacional de destino em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="7a9c0-289">Por exemplo, nosso [dockerfile Amazon Linux][amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o arquivo `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="7a9c0-290">Instalação – Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="7a9c0-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="7a9c0-291">Linux</span><span class="sxs-lookup"><span data-stu-id="7a9c0-291">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="7a9c0-292">Desinstalação de arquivos binários</span><span class="sxs-lookup"><span data-stu-id="7a9c0-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="7a9c0-293">Caminhos</span><span class="sxs-lookup"><span data-stu-id="7a9c0-293">Paths</span></span>

* <span data-ttu-id="7a9c0-294">`$PSHOME` é `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="7a9c0-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="7a9c0-295">Perfis de usuário serão lidos de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7a9c0-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="7a9c0-296">Perfis padrão serão lidos de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7a9c0-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="7a9c0-297">Módulos de usuário serão lidos de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7a9c0-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7a9c0-298">Módulos compartilhados serão lidos de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7a9c0-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7a9c0-299">Módulos padrão serão lidos de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="7a9c0-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="7a9c0-300">Histórico de PSReadline será gravado em `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="7a9c0-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="7a9c0-301">Os perfis respeitam a configuração por host do PowerShell. Assim, os perfis específicos do host padrão existem em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="7a9c0-302">O PowerShell respeita a [Especificação de Diretório Base XDG][xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
