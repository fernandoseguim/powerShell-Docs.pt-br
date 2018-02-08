# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="fbb4a-101">Instalar o PowerShell Core no macOS e Linux</span><span class="sxs-lookup"><span data-stu-id="fbb4a-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="fbb4a-102">Dá suporte a [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch] e [macOS 10.12][mac].</span><span class="sxs-lookup"><span data-stu-id="fbb4a-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="fbb4a-103">Em distribuições Linux sem suporte oficial, tente usar o [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="fbb4a-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span> <span data-ttu-id="fbb4a-104">Além disso, tente implantar binários do PowerShell diretamente usando o arquivo [`tar.gz` do Linux][tar], mas você precisaria configurar as dependências necessárias com base no sistema operacional em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="fbb4a-105">Todos os pacotes estão disponíveis na nossa página [versões][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="fbb4a-106">Depois de instalar o pacote, execute `pwsh` em um terminal.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="fbb4a-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="fbb4a-108">Instalação por meio do repositório de pacotes – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="fbb4a-109">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span> <span data-ttu-id="fbb4a-110">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-110">This is the preferred method.</span></span>

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

<span data-ttu-id="fbb4a-111">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="fbb4a-112">Instalação por meio de download direto – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="fbb4a-113">Baixe o pacote Debian `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-113">Download the Debian package `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

<span data-ttu-id="fbb4a-114">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="fbb4a-115">Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="fbb4a-116">Desinstalação – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="fbb4a-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="fbb4a-118">Instalação por meio do repositório de pacotes – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="fbb4a-119">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fbb4a-120">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-120">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="fbb4a-121">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="fbb4a-122">Instalação por meio de download direto – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="fbb4a-123">Baixe o pacote Debian `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` da página [versões][] no computador Ubuntu:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-123">Download the Debian package `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

<span data-ttu-id="fbb4a-124">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="fbb4a-125">Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="fbb4a-126">Desinstalação – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="fbb4a-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="fbb4a-128">Instalação por meio do repositório de pacotes – Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="fbb4a-129">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fbb4a-130">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-130">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="fbb4a-131">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="fbb4a-132">Instalação por meio de download direto – Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="fbb4a-133">Baixe o pacote Debian `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` da página [versões][] no computador Ubuntu:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-133">Download the Debian package `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

<span data-ttu-id="fbb4a-134">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="fbb4a-135">Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="fbb4a-136">Desinstalação – Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="fbb4a-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="fbb4a-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="fbb4a-138">Instalação por meio do repositório de pacotes – Debian 8</span><span class="sxs-lookup"><span data-stu-id="fbb4a-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="fbb4a-139">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fbb4a-140">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-140">This is the preferred method.</span></span>

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

<span data-ttu-id="fbb4a-141">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="fbb4a-142">Instalação por meio de download direto – Debian 8</span><span class="sxs-lookup"><span data-stu-id="fbb4a-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="fbb4a-143">Baixe o pacote Debian `powershell_6.0.0-1.debian.8_amd64.deb` da página [versões][] no computador Debian:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-143">Download the Debian package `powershell_6.0.0-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

<span data-ttu-id="fbb4a-144">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="fbb4a-145">Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="fbb4a-146">Desinstalação – Debian 8</span><span class="sxs-lookup"><span data-stu-id="fbb4a-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="fbb4a-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="fbb4a-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="fbb4a-148">Instalação por meio do repositório de pacotes – Debian 9</span><span class="sxs-lookup"><span data-stu-id="fbb4a-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="fbb4a-149">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="fbb4a-150">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-150">This is the preferred method.</span></span>

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

<span data-ttu-id="fbb4a-151">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="fbb4a-152">Instalação por meio de download direto – Debian 9</span><span class="sxs-lookup"><span data-stu-id="fbb4a-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="fbb4a-153">Baixe o pacote Debian `powershell_6.0.0-1.debian.9_amd64.deb` da página [versões][] no computador Debian:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-153">Download the Debian package `powershell_6.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="fbb4a-154">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="fbb4a-155">Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="fbb4a-156">Desinstalação – Debian 9</span><span class="sxs-lookup"><span data-stu-id="fbb4a-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="fbb4a-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-157">CentOS 7</span></span>

> <span data-ttu-id="fbb4a-158">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="fbb4a-159">Instalação por meio do repositório de pacotes (preferencial) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="fbb4a-160">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="fbb4a-161">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="fbb4a-162">Instalação por meio de download direto – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="fbb4a-163">Usando o [CentOS 7][], baixe o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` da página [versões][] no computador CentOS:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fbb4a-164">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fbb4a-165">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="fbb4a-166">Desinstalação – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fbb4a-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fbb4a-169">Instalação por meio do repositório de pacotes (preferencial) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="fbb4a-170">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="fbb4a-171">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fbb4a-172">Instalação por meio de download direto – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="fbb4a-173">Baixe o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` da página de [versões][] no computador Red Hat Enterprise Linux:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-173">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="fbb4a-174">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fbb4a-175">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="fbb4a-176">Desinstalação – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="fbb4a-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="fbb4a-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="fbb4a-178">**Observação:** durante a instalação do PowerShell Core, o OpenSUSE pode reportar que nada fornece `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-178">**Note:** When installing PowerShell Core, OpenSUSE may report that nothing provides `libcurl`.</span></span>
<span data-ttu-id="fbb4a-179">`libcurl` já deve estar instalado em versões com suporte do OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-179">`libcurl` should already be installed on supported versions of OpenSUSE.</span></span>
<span data-ttu-id="fbb4a-180">Execute `zypper search libcurl` para confirmar.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-180">Run `zypper search libcurl` to confirm.</span></span>
<span data-ttu-id="fbb4a-181">O erro apresentará 2 "soluções".</span><span class="sxs-lookup"><span data-stu-id="fbb4a-181">The error will present 2 'solutions'.</span></span> <span data-ttu-id="fbb4a-182">Escolha a "Solução 2" para continuar a instalação do PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-182">Choose 'Solution 2' to continue installing PowerShell Core.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="fbb4a-183">Instalação por meio do repositório de pacotes (preferencial) – OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="fbb4a-183">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="fbb4a-184">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-184">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="fbb4a-185">Instalação por meio de download direto – OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="fbb4a-185">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="fbb4a-186">Baixe o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` da página [versões][] no computador OpenSUSE:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-186">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fbb4a-187">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-187">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="fbb4a-188">Desinstalação – OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="fbb4a-188">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="fbb4a-189">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="fbb4a-189">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="fbb4a-190">Instalação por meio do repositório de pacotes (preferencial) – Fedora 25</span><span class="sxs-lookup"><span data-stu-id="fbb4a-190">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="fbb4a-191">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-191">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="fbb4a-192">Instalação por meio de download direto – Fedora 25</span><span class="sxs-lookup"><span data-stu-id="fbb4a-192">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="fbb4a-193">Baixe o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` da página [versões][] no computador Fedora:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-193">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fbb4a-194">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-194">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fbb4a-195">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="fbb4a-196">Desinstalação – Fedora 25</span><span class="sxs-lookup"><span data-stu-id="fbb4a-196">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="fbb4a-197">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="fbb4a-197">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="fbb4a-198">Instalação por meio do repositório de pacotes (preferencial) – Fedora 26</span><span class="sxs-lookup"><span data-stu-id="fbb4a-198">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="fbb4a-199">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="fbb4a-200">Instalação por meio de download direto – Fedora 26</span><span class="sxs-lookup"><span data-stu-id="fbb4a-200">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="fbb4a-201">Baixe o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` da página [versões][] no computador Fedora:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-201">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fbb4a-202">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-202">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="fbb4a-203">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="fbb4a-204">Desinstalação – Fedora 26</span><span class="sxs-lookup"><span data-stu-id="fbb4a-204">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="fbb4a-205">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="fbb4a-205">Arch Linux</span></span>

<span data-ttu-id="fbb4a-206">O PowerShell está disponível no AUR (Repositório de Usuários do [Arch Linux][]).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-206">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="fbb4a-207">Ele pode ser compilado com a [versão marcada mais recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="fbb4a-207">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="fbb4a-208">Ele pode ser compilado na [confirmação mais recente com mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="fbb4a-208">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="fbb4a-209">Ele pode ser instalado usando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="fbb4a-209">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="fbb4a-210">Pacotes no AUR são mantidos pela comunidade – não há suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-210">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="fbb4a-211">Para obter mais informações sobre a instalação de pacotes usando o AUR, veja a [wiki do Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou a comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="fbb4a-211">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="fbb4a-213">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="fbb4a-213">Linux AppImage</span></span>

<span data-ttu-id="fbb4a-214">Usando uma distribuição Linux recente, baixe a AppImage `powershell-6.0.0-x86_64.AppImage` da página [versões][] no computador Linux.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-214">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="fbb4a-215">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-215">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

<span data-ttu-id="fbb4a-216">A [AppImage][] permite executar o PowerShell sem instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-216">The [AppImage][] lets you run PowerShell without installing it.</span></span> <span data-ttu-id="fbb4a-217">É um aplicativo portátil que inclui o PowerShell e suas dependências (incluindo dependências do sistema do .NET Core) em um pacote coeso.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-217">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span> <span data-ttu-id="fbb4a-218">Esse pacote funciona independentemente da distribuição Linux do usuário e é um binário único.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-218">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="fbb4a-220">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="fbb4a-220">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="fbb4a-221">Instalação por meio do Homebrew (preferencial) – macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="fbb4a-221">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="fbb4a-222">[Homebrew][brew] é o gerenciador de pacotes ausentes para macOS.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-222">[Homebrew][brew] is the missing package manager for macOS.</span></span> <span data-ttu-id="fbb4a-223">Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="fbb4a-223">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="fbb4a-224">Depois da instalação do Homebrew, é fácil instalar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-224">Once you've installed Homebrew, installing PowerShell is easy.</span></span> <span data-ttu-id="fbb4a-225">Primeiro, instale o [Homebrew-Cask][cask], assim você pode instalar mais pacotes:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-225">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="fbb4a-226">Agora, você pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-226">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="fbb4a-227">Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-227">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="fbb4a-228">Observação: por causa [desse problema no Cask](https://github.com/caskroom/homebrew-cask/issues/29301), no momento, você deve fazer uma reinstalação para atualizar.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-228">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="fbb4a-229">Instalação por meio de download direto – macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="fbb4a-229">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="fbb4a-230">Usando o macOS 10.12, baixe o pacote PKG `powershell-6.0.0-osx.10.12-x64.pkg` da página [versões][] no computador macOS.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-230">Using macOS 10.12, download the PKG package `powershell-6.0.0-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="fbb4a-231">Clique duas vezes no arquivo e siga os prompts ou instale-o do terminal:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-231">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="fbb4a-232">Desinstalação – macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="fbb4a-232">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="fbb4a-233">Se você instalou o PowerShell com Homebrew, a desinstalação é fácil:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-233">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="fbb4a-234">Se você instalou o PowerShell por meio de download direto, o PowerShell deve ser removido manualmente:</span><span class="sxs-lookup"><span data-stu-id="fbb4a-234">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="fbb4a-235">Para desinstalar os caminhos do PowerShell adicionais (como o caminho de perfil do usuário), veja a seção [caminhos][paths] abaixo neste documento e remova os caminhos desejados com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-235">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span> <span data-ttu-id="fbb4a-236">(Observação: isso não é necessário se você instalou usando Homebrew.)</span><span class="sxs-lookup"><span data-stu-id="fbb4a-236">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="fbb4a-237">Kali</span><span class="sxs-lookup"><span data-stu-id="fbb4a-237">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="fbb4a-238">Instalação</span><span class="sxs-lookup"><span data-stu-id="fbb4a-238">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="fbb4a-239">Executar o PowerShell no Kali mais recente (Kali GNU/Linux Rolling) sem instalá-lo</span><span class="sxs-lookup"><span data-stu-id="fbb4a-239">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="fbb4a-240">Desinstalação – Kali</span><span class="sxs-lookup"><span data-stu-id="fbb4a-240">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a><span data-ttu-id="fbb4a-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="fbb4a-241">Raspbian</span></span>

<span data-ttu-id="fbb4a-242">Atualmente, o PowerShell tem suporte apenas no Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="fbb4a-243">Instalação</span><span class="sxs-lookup"><span data-stu-id="fbb4a-243">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="fbb4a-244">Desinstalação – Raspbian</span><span class="sxs-lookup"><span data-stu-id="fbb4a-244">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="fbb4a-245">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="fbb4a-245">Binary Archives</span></span>

<span data-ttu-id="fbb4a-246">Arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas macOS e Linux para habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-246">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="fbb4a-247">Dependências</span><span class="sxs-lookup"><span data-stu-id="fbb4a-247">Dependencies</span></span>

<span data-ttu-id="fbb4a-248">No Linux, o PowerShell cria binários portáteis para todas as distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-248">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="fbb4a-249">Porém, o tempo de execução do .NET Core exige dependências diferentes em diferentes distribuições e, portanto, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-249">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="fbb4a-250">O gráfico a seguir mostra as dependências do .NET Core 2.0 em diferentes distribuições Linux oficialmente com suporte.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-250">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="fbb4a-251">SO</span><span class="sxs-lookup"><span data-stu-id="fbb4a-251">OS</span></span>                 | <span data-ttu-id="fbb4a-252">Dependências</span><span class="sxs-lookup"><span data-stu-id="fbb4a-252">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="fbb4a-253">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-253">Ubuntu 14.04</span></span>       | <span data-ttu-id="fbb4a-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fbb4a-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fbb4a-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="fbb4a-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="fbb4a-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="fbb4a-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fbb4a-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fbb4a-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="fbb4a-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="fbb4a-259">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="fbb4a-259">Ubuntu 17.04</span></span>       | <span data-ttu-id="fbb4a-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fbb4a-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fbb4a-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="fbb4a-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="fbb4a-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="fbb4a-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="fbb4a-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fbb4a-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fbb4a-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="fbb4a-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="fbb4a-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="fbb4a-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="fbb4a-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="fbb4a-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="fbb4a-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="fbb4a-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="fbb4a-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-268">CentOS 7</span></span> <br> <span data-ttu-id="fbb4a-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="fbb4a-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="fbb4a-270">RHEL 7</span></span> <br> <span data-ttu-id="fbb4a-271">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="fbb4a-271">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="fbb4a-272">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="fbb4a-272">Fedora 25</span></span> | <span data-ttu-id="fbb4a-273">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="fbb4a-273">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="fbb4a-274">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="fbb4a-274">Fedora 26</span></span>          | <span data-ttu-id="fbb4a-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="fbb4a-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="fbb4a-276">Para implantar binários do PowerShell em distribuições Linux que sem suporte oficial, instale as dependências necessárias para o sistema operacional de destino em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-276">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="fbb4a-277">Por exemplo, nosso [dockerfile Amazon Linux][amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o arquivo `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-277">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="fbb4a-278">Instalação – Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="fbb4a-278">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="fbb4a-279">Linux</span><span class="sxs-lookup"><span data-stu-id="fbb4a-279">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="fbb4a-280">macOS</span><span class="sxs-lookup"><span data-stu-id="fbb4a-280">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="fbb4a-281">Desinstalação – Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="fbb4a-281">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="fbb4a-282">Linux</span><span class="sxs-lookup"><span data-stu-id="fbb4a-282">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="fbb4a-283">macOS</span><span class="sxs-lookup"><span data-stu-id="fbb4a-283">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="fbb4a-284">Caminhos</span><span class="sxs-lookup"><span data-stu-id="fbb4a-284">Paths</span></span>

* <span data-ttu-id="fbb4a-285">`$PSHOME` é `/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="fbb4a-285">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="fbb4a-286">Perfis de usuário serão lidos de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="fbb4a-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="fbb4a-287">Perfis padrão serão lidos de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="fbb4a-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="fbb4a-288">Módulos de usuário serão lidos de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="fbb4a-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="fbb4a-289">Módulos compartilhados serão lidos de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="fbb4a-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="fbb4a-290">Módulos padrão serão lidos de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="fbb4a-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="fbb4a-291">Histórico de PSReadline será gravado em `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="fbb4a-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="fbb4a-292">Os perfis respeitam a configuração por host do PowerShell. Assim, os perfis específicos do host padrão existem em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="fbb4a-293">No Linux e no macOS, a [especificação de diretório básico XDG] [ xdg-bds] é respeitada.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-293">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="fbb4a-294">Observe que, como macOS é uma derivação do BSD, em vez de `/opt`, o prefixo usado é `/usr/local`.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-294">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span> <span data-ttu-id="fbb4a-295">Portanto, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.0/`, e o symlink é colocado em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="fbb4a-295">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
