---
title: Instalar o PowerShell Core no Linux
description: Informações sobre a instalação do PowerShell Core em diversas distribuições Linux
ms.date: 08/06/2018
ms.openlocfilehash: 06194550f4e73f9dd38f8cdc25f6c7f698cafce2
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293326"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="618f7-103">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="618f7-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="618f7-104">É compatível com [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="618f7-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="618f7-105">Em distribuições Linux sem suporte oficial, tente usar o [Pacote Snap do PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="618f7-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="618f7-106">Além disso, tente implantar binários do PowerShell diretamente usando o arquivo [`tar.gz` do Linux][tar], mas você precisaria configurar as dependências necessárias com base no sistema operacional em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="618f7-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="618f7-107">Todos os pacotes estão disponíveis na nossa página [lançamentos][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="618f7-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="618f7-108">Depois de instalar o pacote, execute `pwsh` em um terminal.</span><span class="sxs-lookup"><span data-stu-id="618f7-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="618f7-109">Instalando versões prévias</span><span class="sxs-lookup"><span data-stu-id="618f7-109">Installing Preview Releases</span></span>

<span data-ttu-id="618f7-110">Ao instalar uma versão prévia do PowerShell Core para Linux por meio de um Repositório de Pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="618f7-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="618f7-111">A instalação por meio de download direito não é alterada, somente o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="618f7-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="618f7-112">Aqui está uma tabela dos comandos para instalar os pacotes estáveis e de versão prévia usando vários gerenciadores de pacotes:</span><span class="sxs-lookup"><span data-stu-id="618f7-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="618f7-113">Distribuições</span><span class="sxs-lookup"><span data-stu-id="618f7-113">Distribution(s)</span></span>|<span data-ttu-id="618f7-114">Comando estável</span><span class="sxs-lookup"><span data-stu-id="618f7-114">Stable Command</span></span> | <span data-ttu-id="618f7-115">Comando de versão prévia</span><span class="sxs-lookup"><span data-stu-id="618f7-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="618f7-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="618f7-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="618f7-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="618f7-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="618f7-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="618f7-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="618f7-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="618f7-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="618f7-120">Instalação por meio do repositório de pacotes – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="618f7-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="618f7-121">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="618f7-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="618f7-122">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="618f7-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="618f7-123">Como superusuário, registre o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="618f7-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="618f7-124">Daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="618f7-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="618f7-125">Instalação por meio de download direto – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="618f7-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="618f7-126">Baixar o pacote Debian</span><span class="sxs-lookup"><span data-stu-id="618f7-126">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.14.04_amd64.deb`
<span data-ttu-id="618f7-127">da página [lançamentos][] no computador com Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="618f7-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="618f7-128">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="618f7-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="618f7-129">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="618f7-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="618f7-130">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="618f7-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="618f7-131">Desinstalação – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="618f7-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="618f7-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="618f7-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="618f7-133">Instalação por meio do repositório de pacotes – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="618f7-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="618f7-134">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="618f7-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="618f7-135">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="618f7-135">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="618f7-136">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="618f7-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="618f7-137">Instalação por meio de download direto – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="618f7-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="618f7-138">Baixar o pacote Debian</span><span class="sxs-lookup"><span data-stu-id="618f7-138">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.16.04_amd64.deb`
<span data-ttu-id="618f7-139">da página [lançamentos][] no computador com Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="618f7-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="618f7-140">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="618f7-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="618f7-141">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="618f7-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="618f7-142">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="618f7-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="618f7-143">Desinstalação – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="618f7-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="618f7-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="618f7-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="618f7-145">Instalação por meio do repositório de pacotes – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="618f7-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="618f7-146">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="618f7-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="618f7-147">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="618f7-147">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="618f7-148">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="618f7-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="618f7-149">Instalação por meio de download direto – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="618f7-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="618f7-150">Baixar o pacote Debian</span><span class="sxs-lookup"><span data-stu-id="618f7-150">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.18.04_amd64.deb`
<span data-ttu-id="618f7-151">da página [lançamentos][] no computador com Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="618f7-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="618f7-152">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="618f7-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="618f7-153">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="618f7-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="618f7-154">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="618f7-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="618f7-155">Desinstalação – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="618f7-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="618f7-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="618f7-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="618f7-157">Como a versão 18.10 é uma [versão provisória](https://www.ubuntu.com/about/release-cycle), ela tem apenas [suporte da comunidade](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="618f7-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="618f7-158">A instalação no 18.10 é compatível por meio do `snapd`.</span><span class="sxs-lookup"><span data-stu-id="618f7-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="618f7-159">Veja [Pacote Snap][snap] para obter instruções completas;</span><span class="sxs-lookup"><span data-stu-id="618f7-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="618f7-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="618f7-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="618f7-161">Instalação por meio do repositório de pacotes – Debian 8</span><span class="sxs-lookup"><span data-stu-id="618f7-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="618f7-162">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="618f7-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="618f7-163">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="618f7-163">This is the preferred method.</span></span>

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

<span data-ttu-id="618f7-164">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="618f7-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="618f7-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="618f7-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="618f7-166">Instalação por meio do repositório de pacotes – Debian 9</span><span class="sxs-lookup"><span data-stu-id="618f7-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="618f7-167">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="618f7-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="618f7-168">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="618f7-168">This is the preferred method.</span></span>

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

<span data-ttu-id="618f7-169">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="618f7-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="618f7-170">Instalação por meio de download direto – Debian 9</span><span class="sxs-lookup"><span data-stu-id="618f7-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="618f7-171">Baixar o pacote Debian</span><span class="sxs-lookup"><span data-stu-id="618f7-171">Download the Debian package</span></span>
`powershell_6.2.0-1.debian.9_amd64.deb`
<span data-ttu-id="618f7-172">da página [lançamentos][] no computador com Debian.</span><span class="sxs-lookup"><span data-stu-id="618f7-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="618f7-173">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="618f7-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="618f7-174">Desinstalação – Debian 9</span><span class="sxs-lookup"><span data-stu-id="618f7-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="618f7-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="618f7-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="618f7-176">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="618f7-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="618f7-177">Instalação por meio do repositório de pacotes (preferencial) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="618f7-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="618f7-178">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="618f7-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="618f7-179">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="618f7-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="618f7-180">Instalação por meio de download direto – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="618f7-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="618f7-181">Usando o [CentOS 7][], baixe o pacote RPM</span><span class="sxs-lookup"><span data-stu-id="618f7-181">Using [CentOS 7][], download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="618f7-182">da página [lançamentos][] no computador com CentOS.</span><span class="sxs-lookup"><span data-stu-id="618f7-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="618f7-183">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="618f7-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="618f7-184">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="618f7-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="618f7-185">Desinstalação – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="618f7-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[<span data-ttu-id="618f7-186">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="618f7-186">CentOS 7</span></span>]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="618f7-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="618f7-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="618f7-188">Instalação por meio do repositório de pacotes (preferencial) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="618f7-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="618f7-189">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="618f7-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="618f7-190">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="618f7-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="618f7-191">Instalação por meio de download direto – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="618f7-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="618f7-192">Baixar o pacote RPM</span><span class="sxs-lookup"><span data-stu-id="618f7-192">Download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="618f7-193">da página de [lançamentos][] no computador com Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="618f7-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="618f7-194">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="618f7-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="618f7-195">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="618f7-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="618f7-196">Desinstalação – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="618f7-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="618f7-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="618f7-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="618f7-198">Instalação – openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="618f7-198">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="618f7-199">Instalação – openSUSE 42.3 Leap 15</span><span class="sxs-lookup"><span data-stu-id="618f7-199">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="618f7-200">Desinstalação – openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="618f7-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="618f7-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="618f7-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="618f7-202">O Fedora 28 é compatível apenas com o PowerShell Core 6.1 e mais recentes.</span><span class="sxs-lookup"><span data-stu-id="618f7-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="618f7-203">Instalação por meio do repositório de pacotes (preferencial) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="618f7-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="618f7-204">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="618f7-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="618f7-205">Instalação por meio de download direto – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="618f7-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="618f7-206">Baixar o pacote RPM</span><span class="sxs-lookup"><span data-stu-id="618f7-206">Download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="618f7-207">da página [lançamentos][] no computador com Fedora.</span><span class="sxs-lookup"><span data-stu-id="618f7-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="618f7-208">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="618f7-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="618f7-209">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="618f7-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="618f7-210">Desinstalação – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="618f7-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="618f7-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="618f7-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="618f7-212">O suporte para o Arch é experimental.</span><span class="sxs-lookup"><span data-stu-id="618f7-212">Arch support is experimental.</span></span>

<span data-ttu-id="618f7-213">O PowerShell está disponível no AUR (Repositório de Usuários do [Arch Linux][]).</span><span class="sxs-lookup"><span data-stu-id="618f7-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="618f7-214">Ele pode ser compilado com a [versão marcada mais recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="618f7-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="618f7-215">Ele pode ser compilado na [confirmação mais recente com mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="618f7-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="618f7-216">Ele pode ser instalado usando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="618f7-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="618f7-217">Pacotes no AUR são mantidos pela comunidade – não há suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="618f7-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="618f7-218">Para obter mais informações sobre a instalação de pacotes usando o AUR, veja a [wiki do Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou a comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="618f7-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[<span data-ttu-id="618f7-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="618f7-219">Arch Linux</span></span>]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="618f7-220">Pacote Snap</span><span class="sxs-lookup"><span data-stu-id="618f7-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="618f7-221">Usando o Snap</span><span class="sxs-lookup"><span data-stu-id="618f7-221">Getting snapd</span></span>

`snapd` <span data-ttu-id="618f7-222">é necessário para executar snaps.</span><span class="sxs-lookup"><span data-stu-id="618f7-222">is required to run snaps.</span></span>
<span data-ttu-id="618f7-223">Use [estas instruções](https://docs.snapcraft.io/core/install) para garantir que você tem o `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="618f7-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="618f7-224">Instalação por meio do Snap</span><span class="sxs-lookup"><span data-stu-id="618f7-224">Installation via Snap</span></span>

<span data-ttu-id="618f7-225">O PowerShell Core para Linux é publicado na [Snap Store](https://snapcraft.io/store) para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="618f7-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="618f7-226">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="618f7-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="618f7-227">Se você quiser instalar a versão prévia, use o método a seguir.</span><span class="sxs-lookup"><span data-stu-id="618f7-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="618f7-228">Depois de instalado, o Snap atualizará automaticamente, mas você poderá disparar uma atualização usando `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="618f7-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="618f7-229">Desinstalação</span><span class="sxs-lookup"><span data-stu-id="618f7-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="618f7-230">ou</span><span class="sxs-lookup"><span data-stu-id="618f7-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="618f7-231">Kali</span><span class="sxs-lookup"><span data-stu-id="618f7-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="618f7-232">Instalação – Kali</span><span class="sxs-lookup"><span data-stu-id="618f7-232">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="618f7-233">Desinstalação – Kali</span><span class="sxs-lookup"><span data-stu-id="618f7-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="618f7-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="618f7-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="618f7-235">O suporte para o Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="618f7-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="618f7-236">Atualmente, o PowerShell tem suporte apenas no Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="618f7-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="618f7-237">Além disso, o CoreCLR (e, portanto, o PowerShell Core) funcionará apenas em dispositivos Pi 2 e Pi 3, pois outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), têm um processador sem suporte.</span><span class="sxs-lookup"><span data-stu-id="618f7-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="618f7-238">Faça o download do [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga as [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para instalá-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="618f7-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="618f7-239">Instalação – Raspbian</span><span class="sxs-lookup"><span data-stu-id="618f7-239">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="618f7-240">Opcionalmente, você pode criar um link simbólico para poder iniciar o PowerShell sem especificar o caminho até o binário "pwsh"</span><span class="sxs-lookup"><span data-stu-id="618f7-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="618f7-241">Desinstalação – Raspbian</span><span class="sxs-lookup"><span data-stu-id="618f7-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="618f7-242">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="618f7-242">Binary Archives</span></span>

<span data-ttu-id="618f7-243">Os arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas Linux a fim de habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="618f7-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="618f7-244">Dependências</span><span class="sxs-lookup"><span data-stu-id="618f7-244">Dependencies</span></span>

<span data-ttu-id="618f7-245">O PowerShell cria binários portáteis para todas as distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="618f7-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="618f7-246">Porém, o tempo de execução do .NET Core exige dependências diferentes em diferentes distribuições e, portanto, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="618f7-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="618f7-247">O gráfico a seguir mostra as dependências do .NET Core 2.0 com suporte oficial em diferentes distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="618f7-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="618f7-248">SO</span><span class="sxs-lookup"><span data-stu-id="618f7-248">OS</span></span>                 | <span data-ttu-id="618f7-249">Dependências</span><span class="sxs-lookup"><span data-stu-id="618f7-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="618f7-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="618f7-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="618f7-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="618f7-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="618f7-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="618f7-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="618f7-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="618f7-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="618f7-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="618f7-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="618f7-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="618f7-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="618f7-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="618f7-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="618f7-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="618f7-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="618f7-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="618f7-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="618f7-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="618f7-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="618f7-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="618f7-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="618f7-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="618f7-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="618f7-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="618f7-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="618f7-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="618f7-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="618f7-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="618f7-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="618f7-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="618f7-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="618f7-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="618f7-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="618f7-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="618f7-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="618f7-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="618f7-268">CentOS 7</span></span> <br> <span data-ttu-id="618f7-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="618f7-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="618f7-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="618f7-270">RHEL 7</span></span> | <span data-ttu-id="618f7-271">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="618f7-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="618f7-272">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="618f7-272">openSUSE 42.3</span></span> | <span data-ttu-id="618f7-273">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="618f7-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="618f7-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="618f7-274">openSUSE Leap 15</span></span> | <span data-ttu-id="618f7-275">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="618f7-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="618f7-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="618f7-276">Fedora 27</span></span> <br> <span data-ttu-id="618f7-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="618f7-277">Fedora 28</span></span> | <span data-ttu-id="618f7-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="618f7-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="618f7-279">Para implantar binários do PowerShell em distribuições Linux que sem suporte oficial, instale as dependências necessárias para o sistema operacional de destino em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="618f7-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="618f7-280">Por exemplo, nosso [dockerfile Amazon Linux][amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o arquivo `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="618f7-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="618f7-281">Instalação – Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="618f7-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="618f7-282">Linux</span><span class="sxs-lookup"><span data-stu-id="618f7-282">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="618f7-283">Desinstalação de arquivos binários</span><span class="sxs-lookup"><span data-stu-id="618f7-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="618f7-284">Caminhos</span><span class="sxs-lookup"><span data-stu-id="618f7-284">Paths</span></span>

* `$PSHOME` <span data-ttu-id="618f7-285">é</span><span class="sxs-lookup"><span data-stu-id="618f7-285">is</span></span> `/opt/microsoft/powershell/6.2.0/`
* <span data-ttu-id="618f7-286">Perfis de usuário serão lidos de</span><span class="sxs-lookup"><span data-stu-id="618f7-286">User profiles will be read from</span></span> `~/.config/powershell/profile.ps1`
* <span data-ttu-id="618f7-287">Perfis padrão serão lidos de</span><span class="sxs-lookup"><span data-stu-id="618f7-287">Default profiles will be read from</span></span> `$PSHOME/profile.ps1`
* <span data-ttu-id="618f7-288">Módulos de usuário serão lidos de</span><span class="sxs-lookup"><span data-stu-id="618f7-288">User modules will be read from</span></span> `~/.local/share/powershell/Modules`
* <span data-ttu-id="618f7-289">Módulos compartilhados serão lidos de</span><span class="sxs-lookup"><span data-stu-id="618f7-289">Shared modules will be read from</span></span> `/usr/local/share/powershell/Modules`
* <span data-ttu-id="618f7-290">Módulos padrão serão lidos de</span><span class="sxs-lookup"><span data-stu-id="618f7-290">Default modules will be read from</span></span> `$PSHOME/Modules`
* <span data-ttu-id="618f7-291">Histórico de PSReadline será gravado em</span><span class="sxs-lookup"><span data-stu-id="618f7-291">PSReadline history will be recorded to</span></span> `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

<span data-ttu-id="618f7-292">Os perfis respeitam a configuração por host do PowerShell. Assim, os perfis específicos do host padrão existem em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="618f7-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="618f7-293">O PowerShell respeita a [Especificação de Diretório Base XDG][xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="618f7-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[<span data-ttu-id="618f7-294">lançamentos</span><span class="sxs-lookup"><span data-stu-id="618f7-294">releases</span></span>]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
