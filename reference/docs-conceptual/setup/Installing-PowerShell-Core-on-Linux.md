# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="0bf26-101">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="0bf26-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="0bf26-102">Oferece suporte a [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="0bf26-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], and [Arch Linux][arch].</span></span>

<span data-ttu-id="0bf26-103">Em distribuições Linux sem suporte oficial, tente usar o [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="0bf26-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="0bf26-104">Além disso, tente implantar binários do PowerShell diretamente usando o arquivo [`tar.gz` do Linux][tar], mas você precisaria configurar as dependências necessárias com base no sistema operacional em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="0bf26-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="0bf26-105">Todos os pacotes estão disponíveis na nossa página [versões][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="0bf26-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="0bf26-106">Depois de instalar o pacote, execute `pwsh` em um terminal.</span><span class="sxs-lookup"><span data-stu-id="0bf26-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="0bf26-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="0bf26-108">Instalação por meio do repositório de pacotes – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="0bf26-109">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="0bf26-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0bf26-110">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="0bf26-110">This is the preferred method.</span></span>

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

<span data-ttu-id="0bf26-111">Como superusuário, registre o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0bf26-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="0bf26-112">Daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="0bf26-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="0bf26-113">Instalação por meio de download direto – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="0bf26-114">Baixe o pacote Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="0bf26-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0bf26-115">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="0bf26-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="0bf26-116">Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bf26-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="0bf26-117">Desinstalação – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="0bf26-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="0bf26-119">Instalação por meio do repositório de pacotes – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="0bf26-120">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="0bf26-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0bf26-121">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="0bf26-121">This is the preferred method.</span></span>

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

<span data-ttu-id="0bf26-122">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="0bf26-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="0bf26-123">Instalação por meio de download direto – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="0bf26-124">Baixe o pacote Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="0bf26-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0bf26-125">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="0bf26-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="0bf26-126">Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bf26-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="0bf26-127">Desinstalação – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="0bf26-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="0bf26-129">Instalação por meio do repositório de pacotes – Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="0bf26-130">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="0bf26-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0bf26-131">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="0bf26-131">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0bf26-132">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="0bf26-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="0bf26-133">Instalação por meio de download direto – Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="0bf26-134">Baixe o pacote Debian `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="0bf26-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0bf26-135">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="0bf26-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="0bf26-136">Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bf26-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="0bf26-137">Desinstalação – Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="0bf26-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="0bf26-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="0bf26-139">Instalação por meio do repositório de pacotes – Debian 8</span><span class="sxs-lookup"><span data-stu-id="0bf26-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="0bf26-140">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="0bf26-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0bf26-141">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="0bf26-141">This is the preferred method.</span></span>

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

<span data-ttu-id="0bf26-142">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="0bf26-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="0bf26-143">Instalação por meio de download direto – Debian 8</span><span class="sxs-lookup"><span data-stu-id="0bf26-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="0bf26-144">Baixe o pacote Debian `powershell_6.0.2-1.debian.8_amd64.deb` da página [versões][] no computador Debian.</span><span class="sxs-lookup"><span data-stu-id="0bf26-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="0bf26-145">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="0bf26-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0bf26-146">Observe que `dpkg -i` falhará com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="0bf26-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="0bf26-147">O próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bf26-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="0bf26-148">Desinstalação – Debian 8</span><span class="sxs-lookup"><span data-stu-id="0bf26-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="0bf26-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="0bf26-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="0bf26-150">Instalação por meio do repositório de pacotes – Debian 9</span><span class="sxs-lookup"><span data-stu-id="0bf26-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="0bf26-151">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="0bf26-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="0bf26-152">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="0bf26-152">This is the preferred method.</span></span>

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

<span data-ttu-id="0bf26-153">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="0bf26-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="0bf26-154">Instalação por meio de download direto – Debian 9</span><span class="sxs-lookup"><span data-stu-id="0bf26-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="0bf26-155">Baixe o pacote Debian `powershell_6.0.2-1.debian.9_amd64.deb` da página [versões][] no computador Debian.</span><span class="sxs-lookup"><span data-stu-id="0bf26-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="0bf26-156">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="0bf26-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0bf26-157">Observe que `dpkg -i` falhará com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="0bf26-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="0bf26-158">O próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bf26-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="0bf26-159">Desinstalação – Debian 9</span><span class="sxs-lookup"><span data-stu-id="0bf26-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="0bf26-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-160">CentOS 7</span></span>

> <span data-ttu-id="0bf26-161">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="0bf26-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="0bf26-162">Instalação por meio do repositório de pacotes (preferencial) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="0bf26-163">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="0bf26-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0bf26-164">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bf26-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="0bf26-165">Instalação por meio de download direto – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="0bf26-166">Usando o [CentOS 7][], baixe o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da página [versões][] no computador CentOS.</span><span class="sxs-lookup"><span data-stu-id="0bf26-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="0bf26-167">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="0bf26-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0bf26-168">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="0bf26-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="0bf26-169">Desinstalação – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0bf26-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0bf26-172">Instalação por meio do repositório de pacotes (preferencial) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="0bf26-173">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="0bf26-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0bf26-174">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bf26-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0bf26-175">Instalação por meio de download direto – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="0bf26-176">Baixe o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da página [versões][] no computador Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="0bf26-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="0bf26-177">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="0bf26-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0bf26-178">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="0bf26-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0bf26-179">Desinstalação – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="0bf26-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="0bf26-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="0bf26-181">Durante a instalação do PowerShell Core, o `zypper` pode relatar o erro a seguir:</span><span class="sxs-lookup"><span data-stu-id="0bf26-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="0bf26-182">Nesse caso, verifique se uma biblioteca `libcurl` compatível está presente, conferindo se o comando a seguir mostra o pacote `libcurl4` como instalado:</span><span class="sxs-lookup"><span data-stu-id="0bf26-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="0bf26-183">Em seguida, escolha a solução `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` ao instalar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bf26-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="0bf26-184">Instalação por meio do repositório de pacotes (preferencial) – OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="0bf26-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="0bf26-185">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="0bf26-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="0bf26-186">Instalação por meio de download direto – OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="0bf26-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="0bf26-187">Baixe o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da página [versões][] no computador OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="0bf26-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0bf26-188">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="0bf26-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="0bf26-189">Desinstalação – OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="0bf26-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="0bf26-190">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="0bf26-190">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="0bf26-191">Instalação por meio do repositório de pacotes (preferencial) – Fedora 25</span><span class="sxs-lookup"><span data-stu-id="0bf26-191">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="0bf26-192">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="0bf26-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="0bf26-193">Instalação por meio de download direto – Fedora 25</span><span class="sxs-lookup"><span data-stu-id="0bf26-193">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="0bf26-194">Baixe o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da página [versões][] no computador Fedora.</span><span class="sxs-lookup"><span data-stu-id="0bf26-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0bf26-195">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="0bf26-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0bf26-196">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="0bf26-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="0bf26-197">Desinstalação – Fedora 25</span><span class="sxs-lookup"><span data-stu-id="0bf26-197">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="0bf26-198">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="0bf26-198">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="0bf26-199">Instalação por meio do repositório de pacotes (preferencial) – Fedora 26</span><span class="sxs-lookup"><span data-stu-id="0bf26-199">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="0bf26-200">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="0bf26-200">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="0bf26-201">Instalação por meio de download direto – Fedora 26</span><span class="sxs-lookup"><span data-stu-id="0bf26-201">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="0bf26-202">Baixe o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da página [versões][] no computador Fedora.</span><span class="sxs-lookup"><span data-stu-id="0bf26-202">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="0bf26-203">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="0bf26-203">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0bf26-204">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="0bf26-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="0bf26-205">Desinstalação – Fedora 26</span><span class="sxs-lookup"><span data-stu-id="0bf26-205">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="0bf26-206">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="0bf26-206">Arch Linux</span></span>

<span data-ttu-id="0bf26-207">O PowerShell está disponível no AUR (Repositório de Usuários do [Arch Linux][]).</span><span class="sxs-lookup"><span data-stu-id="0bf26-207">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="0bf26-208">Ele pode ser compilado com a [versão marcada mais recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="0bf26-208">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="0bf26-209">Ele pode ser compilado na [confirmação mais recente com mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="0bf26-209">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="0bf26-210">Ele pode ser instalado usando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="0bf26-210">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="0bf26-211">Pacotes no AUR são mantidos pela comunidade – não há suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="0bf26-211">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="0bf26-212">Para obter mais informações sobre a instalação de pacotes usando o AUR, veja a [wiki do Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou a comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="0bf26-212">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="0bf26-214">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="0bf26-214">Linux AppImage</span></span>

<span data-ttu-id="0bf26-215">Usando uma distribuição Linux recente, baixe a AppImage `powershell-6.0.1-x86_64.AppImage` da página [versões][] no computador Linux.</span><span class="sxs-lookup"><span data-stu-id="0bf26-215">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="0bf26-216">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="0bf26-216">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="0bf26-217">A [AppImage][] permite executar o PowerShell sem instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="0bf26-217">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="0bf26-218">É um aplicativo portátil que inclui o PowerShell e suas dependências (incluindo dependências do sistema do .NET Core) em um pacote coeso.</span><span class="sxs-lookup"><span data-stu-id="0bf26-218">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="0bf26-219">Esse pacote é um binário único que funciona independentemente da distribuição Linux do usuário.</span><span class="sxs-lookup"><span data-stu-id="0bf26-219">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="0bf26-221">Kali</span><span class="sxs-lookup"><span data-stu-id="0bf26-221">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="0bf26-222">Instalação</span><span class="sxs-lookup"><span data-stu-id="0bf26-222">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="0bf26-223">Executar o PowerShell no Kali mais recente (Kali GNU/Linux Rolling) sem instalá-lo</span><span class="sxs-lookup"><span data-stu-id="0bf26-223">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="0bf26-224">Desinstalação – Kali</span><span class="sxs-lookup"><span data-stu-id="0bf26-224">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="0bf26-225">Raspbian</span><span class="sxs-lookup"><span data-stu-id="0bf26-225">Raspbian</span></span>

<span data-ttu-id="0bf26-226">Atualmente, o PowerShell tem suporte apenas no Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="0bf26-226">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="0bf26-227">Além disso, o CoreCLR (e, portanto, o PowerShell Core) funcionará apenas em dispositivos Pi 2 e Pi 3, pois outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), têm um processador sem suporte.</span><span class="sxs-lookup"><span data-stu-id="0bf26-227">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="0bf26-228">Faça o download do [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga as [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para instalá-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="0bf26-228">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="0bf26-229">Instalação</span><span class="sxs-lookup"><span data-stu-id="0bf26-229">Installation</span></span>

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

<span data-ttu-id="0bf26-230">Opcionalmente, você pode criar um link simbólico para poder iniciar o PowerShell sem especificar o caminho até o binário "pwsh"</span><span class="sxs-lookup"><span data-stu-id="0bf26-230">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="0bf26-231">Desinstalação – Raspbian</span><span class="sxs-lookup"><span data-stu-id="0bf26-231">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="0bf26-232">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="0bf26-232">Binary Archives</span></span>

<span data-ttu-id="0bf26-233">Os arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas Linux a fim de habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="0bf26-233">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="0bf26-234">Dependências</span><span class="sxs-lookup"><span data-stu-id="0bf26-234">Dependencies</span></span>

<span data-ttu-id="0bf26-235">O PowerShell cria binários portáteis para todas as distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="0bf26-235">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="0bf26-236">Porém, o tempo de execução do .NET Core exige dependências diferentes em diferentes distribuições e, portanto, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="0bf26-236">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="0bf26-237">O gráfico a seguir mostra as dependências do .NET Core 2.0 com suporte oficial em diferentes distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="0bf26-237">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="0bf26-238">SO</span><span class="sxs-lookup"><span data-stu-id="0bf26-238">OS</span></span>                 | <span data-ttu-id="0bf26-239">Dependências</span><span class="sxs-lookup"><span data-stu-id="0bf26-239">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="0bf26-240">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-240">Ubuntu 14.04</span></span>       | <span data-ttu-id="0bf26-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0bf26-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0bf26-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="0bf26-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="0bf26-243">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-243">Ubuntu 16.04</span></span>       | <span data-ttu-id="0bf26-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0bf26-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0bf26-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="0bf26-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="0bf26-246">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="0bf26-246">Ubuntu 17.04</span></span>       | <span data-ttu-id="0bf26-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0bf26-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0bf26-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="0bf26-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="0bf26-249">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="0bf26-249">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="0bf26-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0bf26-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0bf26-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="0bf26-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="0bf26-252">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="0bf26-252">Debian 9 (Stretch)</span></span> | <span data-ttu-id="0bf26-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="0bf26-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0bf26-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="0bf26-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="0bf26-255">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-255">CentOS 7</span></span> <br> <span data-ttu-id="0bf26-256">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-256">Oracle Linux 7</span></span> <br> <span data-ttu-id="0bf26-257">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="0bf26-257">RHEL 7</span></span> <br> <span data-ttu-id="0bf26-258">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="0bf26-258">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="0bf26-259">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="0bf26-259">Fedora 25</span></span> | <span data-ttu-id="0bf26-260">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="0bf26-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="0bf26-261">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="0bf26-261">Fedora 26</span></span>          | <span data-ttu-id="0bf26-262">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="0bf26-262">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="0bf26-263">Para implantar binários do PowerShell em distribuições Linux que sem suporte oficial, instale as dependências necessárias para o sistema operacional de destino em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="0bf26-263">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="0bf26-264">Por exemplo, nosso [dockerfile Amazon Linux][amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o arquivo `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="0bf26-264">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="0bf26-265">Instalação – Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="0bf26-265">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="0bf26-266">Linux</span><span class="sxs-lookup"><span data-stu-id="0bf26-266">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="0bf26-267">Desinstalação de arquivos binários</span><span class="sxs-lookup"><span data-stu-id="0bf26-267">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="0bf26-268">Caminhos</span><span class="sxs-lookup"><span data-stu-id="0bf26-268">Paths</span></span>

* <span data-ttu-id="0bf26-269">`$PSHOME` é `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="0bf26-269">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="0bf26-270">Perfis de usuário serão lidos de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0bf26-270">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="0bf26-271">Perfis padrão serão lidos de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0bf26-271">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="0bf26-272">Módulos de usuário serão lidos de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0bf26-272">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0bf26-273">Módulos compartilhados serão lidos de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0bf26-273">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0bf26-274">Módulos padrão serão lidos de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="0bf26-274">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="0bf26-275">Histórico de PSReadline será gravado em `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="0bf26-275">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="0bf26-276">Os perfis respeitam a configuração por host do PowerShell. Assim, os perfis específicos do host padrão existem em `Microsoft.PowerShell_profile.ps1` nas mesmas localizações.</span><span class="sxs-lookup"><span data-stu-id="0bf26-276">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="0bf26-277">O PowerShell respeita a [Especificação de Diretório Base XDG][xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="0bf26-277">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
