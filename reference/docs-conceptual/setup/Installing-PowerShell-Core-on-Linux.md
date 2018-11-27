---
title: Instalar o PowerShell Core no Linux
description: Informações sobre a instalação do PowerShell Core em diversas distribuições Linux
ms.date: 08/06/2018
ms.openlocfilehash: afb11f053517af592fe42754d543f9f4a9966c5b
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321104"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="261aa-103">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="261aa-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="261aa-104">É compatível com [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="261aa-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="261aa-105">Em distribuições Linux sem suporte oficial, tente usar o [Pacote Snap do PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="261aa-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="261aa-106">Além disso, tente implantar binários do PowerShell diretamente usando o arquivo [`tar.gz` do Linux][tar], mas você precisaria configurar as dependências necessárias com base no sistema operacional em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="261aa-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="261aa-107">Todos os pacotes estão disponíveis na nossa página [lançamentos][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="261aa-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="261aa-108">Depois de instalar o pacote, execute `pwsh` em um terminal.</span><span class="sxs-lookup"><span data-stu-id="261aa-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="261aa-109">Instalando versões prévias</span><span class="sxs-lookup"><span data-stu-id="261aa-109">Installing Preview Releases</span></span>

<span data-ttu-id="261aa-110">Ao instalar uma versão prévia do PowerShell Core para Linux por meio de um Repositório de Pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="261aa-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="261aa-111">A instalação por meio de download direito não é alterada, somente o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="261aa-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="261aa-112">Aqui está uma tabela dos comandos para instalar os pacotes estáveis e de versão prévia usando vários gerenciadores de pacotes:</span><span class="sxs-lookup"><span data-stu-id="261aa-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="261aa-113">Distribuições</span><span class="sxs-lookup"><span data-stu-id="261aa-113">Distribution(s)</span></span>|<span data-ttu-id="261aa-114">Comando estável</span><span class="sxs-lookup"><span data-stu-id="261aa-114">Stable Command</span></span> | <span data-ttu-id="261aa-115">Comando de versão prévia</span><span class="sxs-lookup"><span data-stu-id="261aa-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="261aa-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="261aa-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="261aa-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="261aa-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="261aa-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="261aa-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="261aa-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="261aa-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="261aa-120">Instalação por meio do repositório de pacotes – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="261aa-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="261aa-121">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="261aa-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="261aa-122">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="261aa-122">This is the preferred method.</span></span>

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

<span data-ttu-id="261aa-123">Como superusuário, registre o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="261aa-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="261aa-124">Daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="261aa-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="261aa-125">Instalação por meio de download direto – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="261aa-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="261aa-126">Baixe o pacote Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="261aa-126">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="261aa-127">da página [lançamentos][] no computador com Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="261aa-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="261aa-128">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="261aa-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="261aa-129">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="261aa-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="261aa-130">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="261aa-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="261aa-131">Desinstalação – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="261aa-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="261aa-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="261aa-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="261aa-133">Instalação por meio do repositório de pacotes – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="261aa-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="261aa-134">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="261aa-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="261aa-135">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="261aa-135">This is the preferred method.</span></span>

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

<span data-ttu-id="261aa-136">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="261aa-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="261aa-137">Instalação por meio de download direto – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="261aa-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="261aa-138">Baixe o pacote Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="261aa-138">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="261aa-139">da página [lançamentos][] no computador com Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="261aa-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="261aa-140">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="261aa-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="261aa-141">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="261aa-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="261aa-142">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="261aa-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="261aa-143">Desinstalação – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="261aa-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="261aa-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="261aa-144">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="261aa-145">Foi adicionado suporte para o Ubuntu 18.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="261aa-145">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="261aa-146">Instalação por meio do repositório de pacotes – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="261aa-146">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="261aa-147">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="261aa-147">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="261aa-148">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="261aa-148">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="261aa-149">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="261aa-149">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="261aa-150">Instalação por meio de download direto – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="261aa-150">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="261aa-151">Baixe o pacote Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="261aa-151">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="261aa-152">da página [lançamentos][] no computador com Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="261aa-152">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="261aa-153">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="261aa-153">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="261aa-154">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="261aa-154">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="261aa-155">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="261aa-155">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="261aa-156">Desinstalação – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="261aa-156">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="261aa-157">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="261aa-157">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="261aa-158">Foi adicionado suporte para o Ubuntu 18.10 após `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="261aa-158">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="261aa-159">Como o 18.10 é um build diário, ele tem suporte apenas pela comunidade.</span><span class="sxs-lookup"><span data-stu-id="261aa-159">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="261aa-160">A instalação no 18.10 é compatível por meio do `snapd`.</span><span class="sxs-lookup"><span data-stu-id="261aa-160">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="261aa-161">Veja [Pacote Snap][snap] para obter instruções completas;</span><span class="sxs-lookup"><span data-stu-id="261aa-161">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="261aa-162">Debian 8</span><span class="sxs-lookup"><span data-stu-id="261aa-162">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="261aa-163">Instalação por meio do repositório de pacotes – Debian 8</span><span class="sxs-lookup"><span data-stu-id="261aa-163">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="261aa-164">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="261aa-164">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="261aa-165">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="261aa-165">This is the preferred method.</span></span>

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

<span data-ttu-id="261aa-166">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="261aa-166">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="261aa-167">Instalação por meio de download direto – Debian 8</span><span class="sxs-lookup"><span data-stu-id="261aa-167">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="261aa-168">Baixe o pacote Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="261aa-168">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="261aa-169">da página [lançamentos][] no computador com Debian.</span><span class="sxs-lookup"><span data-stu-id="261aa-169">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="261aa-170">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="261aa-170">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="261aa-171">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="261aa-171">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="261aa-172">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="261aa-172">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="261aa-173">Desinstalação – Debian 8</span><span class="sxs-lookup"><span data-stu-id="261aa-173">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="261aa-174">Debian 9</span><span class="sxs-lookup"><span data-stu-id="261aa-174">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="261aa-175">Instalação por meio do repositório de pacotes – Debian 9</span><span class="sxs-lookup"><span data-stu-id="261aa-175">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="261aa-176">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="261aa-176">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="261aa-177">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="261aa-177">This is the preferred method.</span></span>

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

<span data-ttu-id="261aa-178">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="261aa-178">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="261aa-179">Instalação por meio de download direto – Debian 9</span><span class="sxs-lookup"><span data-stu-id="261aa-179">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="261aa-180">Baixe o pacote Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="261aa-180">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="261aa-181">da página [lançamentos][] no computador com Debian.</span><span class="sxs-lookup"><span data-stu-id="261aa-181">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="261aa-182">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="261aa-182">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="261aa-183">Desinstalação – Debian 9</span><span class="sxs-lookup"><span data-stu-id="261aa-183">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="261aa-184">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="261aa-184">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="261aa-185">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="261aa-185">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="261aa-186">Instalação por meio do repositório de pacotes (preferencial) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="261aa-186">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="261aa-187">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="261aa-187">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="261aa-188">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="261aa-188">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="261aa-189">Instalação por meio de download direto – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="261aa-189">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="261aa-190">Usando o [CentOS 7][], baixe o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="261aa-190">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="261aa-191">da página [lançamentos][] no computador com CentOS.</span><span class="sxs-lookup"><span data-stu-id="261aa-191">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="261aa-192">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="261aa-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="261aa-193">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="261aa-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="261aa-194">Desinstalação – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="261aa-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="261aa-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="261aa-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="261aa-197">Instalação por meio do repositório de pacotes (preferencial) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="261aa-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="261aa-198">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="261aa-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="261aa-199">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="261aa-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="261aa-200">Instalação por meio de download direto – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="261aa-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="261aa-201">Baixe o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="261aa-201">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="261aa-202">da página de [lançamentos][] no computador com Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="261aa-202">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="261aa-203">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="261aa-203">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="261aa-204">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="261aa-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="261aa-205">Desinstalação – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="261aa-205">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="261aa-206">openSUSE</span><span class="sxs-lookup"><span data-stu-id="261aa-206">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="261aa-207">Instalação – openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="261aa-207">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="261aa-208">Instalação – openSUSE 42.3 Leap 15</span><span class="sxs-lookup"><span data-stu-id="261aa-208">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="261aa-209">Desinstalação – openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="261aa-209">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="261aa-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="261aa-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="261aa-211">O Fedora 28 é compatível apenas com o PowerShell Core 6.1 e mais recentes.</span><span class="sxs-lookup"><span data-stu-id="261aa-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="261aa-212">Instalação por meio do repositório de pacotes (preferencial) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="261aa-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="261aa-213">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="261aa-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="261aa-214">Instalação por meio de download direto – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="261aa-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="261aa-215">Baixe o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="261aa-215">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="261aa-216">da página [lançamentos][] no computador com Fedora.</span><span class="sxs-lookup"><span data-stu-id="261aa-216">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="261aa-217">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="261aa-217">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="261aa-218">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="261aa-218">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="261aa-219">Desinstalação – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="261aa-219">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="261aa-220">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="261aa-220">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="261aa-221">O suporte para o Arch é experimental.</span><span class="sxs-lookup"><span data-stu-id="261aa-221">Arch support is experimental.</span></span>

<span data-ttu-id="261aa-222">O PowerShell está disponível no AUR (Repositório de Usuários do [Arch Linux][]).</span><span class="sxs-lookup"><span data-stu-id="261aa-222">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="261aa-223">Ele pode ser compilado com a [versão marcada mais recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="261aa-223">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="261aa-224">Ele pode ser compilado na [confirmação mais recente com mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="261aa-224">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="261aa-225">Ele pode ser instalado usando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="261aa-225">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="261aa-226">Pacotes no AUR são mantidos pela comunidade – não há suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="261aa-226">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="261aa-227">Para obter mais informações sobre a instalação de pacotes usando o AUR, veja a [wiki do Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou a comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="261aa-227">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="261aa-229">Pacote Snap</span><span class="sxs-lookup"><span data-stu-id="261aa-229">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="261aa-230">Usando o Snap</span><span class="sxs-lookup"><span data-stu-id="261aa-230">Getting snapd</span></span>

<span data-ttu-id="261aa-231">O `snapd` é necessário para executar snaps.</span><span class="sxs-lookup"><span data-stu-id="261aa-231">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="261aa-232">Use [estas instruções](https://docs.snapcraft.io/core/install) para garantir que você tem o `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="261aa-232">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="261aa-233">Instalação por meio do Snap</span><span class="sxs-lookup"><span data-stu-id="261aa-233">Installation via Snap</span></span>

<span data-ttu-id="261aa-234">O PowerShell Core para Linux é publicado na [Snap Store](https://snapcraft.io/store) para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="261aa-234">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="261aa-235">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="261aa-235">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="261aa-236">Se você quiser instalar a versão prévia, use o método a seguir.</span><span class="sxs-lookup"><span data-stu-id="261aa-236">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="261aa-237">Depois de instalado, o Snap atualizará automaticamente, mas você poderá disparar uma atualização usando `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="261aa-237">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="261aa-238">Desinstalação</span><span class="sxs-lookup"><span data-stu-id="261aa-238">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="261aa-239">ou</span><span class="sxs-lookup"><span data-stu-id="261aa-239">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="261aa-240">Kali</span><span class="sxs-lookup"><span data-stu-id="261aa-240">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="261aa-241">Instalação – Kali</span><span class="sxs-lookup"><span data-stu-id="261aa-241">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="261aa-242">Desinstalação – Kali</span><span class="sxs-lookup"><span data-stu-id="261aa-242">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="261aa-243">Raspbian</span><span class="sxs-lookup"><span data-stu-id="261aa-243">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="261aa-244">O suporte para o Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="261aa-244">Raspbian support is experimental.</span></span>

<span data-ttu-id="261aa-245">Atualmente, o PowerShell tem suporte apenas no Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="261aa-245">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="261aa-246">Além disso, o CoreCLR (e, portanto, o PowerShell Core) funcionará apenas em dispositivos Pi 2 e Pi 3, pois outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), têm um processador sem suporte.</span><span class="sxs-lookup"><span data-stu-id="261aa-246">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="261aa-247">Faça o download do [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga as [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para instalá-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="261aa-247">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="261aa-248">Instalação – Raspbian</span><span class="sxs-lookup"><span data-stu-id="261aa-248">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="261aa-249">Opcionalmente, você pode criar um link simbólico para poder iniciar o PowerShell sem especificar o caminho até o binário "pwsh"</span><span class="sxs-lookup"><span data-stu-id="261aa-249">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="261aa-250">Desinstalação – Raspbian</span><span class="sxs-lookup"><span data-stu-id="261aa-250">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="261aa-251">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="261aa-251">Binary Archives</span></span>

<span data-ttu-id="261aa-252">Os arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas Linux a fim de habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="261aa-252">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="261aa-253">Dependências</span><span class="sxs-lookup"><span data-stu-id="261aa-253">Dependencies</span></span>

<span data-ttu-id="261aa-254">O PowerShell cria binários portáteis para todas as distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="261aa-254">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="261aa-255">Porém, o tempo de execução do .NET Core exige dependências diferentes em diferentes distribuições e, portanto, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="261aa-255">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="261aa-256">O gráfico a seguir mostra as dependências do .NET Core 2.0 com suporte oficial em diferentes distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="261aa-256">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="261aa-257">SO</span><span class="sxs-lookup"><span data-stu-id="261aa-257">OS</span></span>                 | <span data-ttu-id="261aa-258">Dependências</span><span class="sxs-lookup"><span data-stu-id="261aa-258">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="261aa-259">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="261aa-259">Ubuntu 14.04</span></span>       | <span data-ttu-id="261aa-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="261aa-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="261aa-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="261aa-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="261aa-262">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="261aa-262">Ubuntu 16.04</span></span>       | <span data-ttu-id="261aa-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="261aa-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="261aa-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="261aa-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="261aa-265">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="261aa-265">Ubuntu 17.10</span></span>       | <span data-ttu-id="261aa-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="261aa-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="261aa-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="261aa-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="261aa-268">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="261aa-268">Ubuntu 18.04</span></span>       | <span data-ttu-id="261aa-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="261aa-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="261aa-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="261aa-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="261aa-271">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="261aa-271">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="261aa-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="261aa-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="261aa-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="261aa-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="261aa-274">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="261aa-274">Debian 9 (Stretch)</span></span> | <span data-ttu-id="261aa-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="261aa-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="261aa-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="261aa-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="261aa-277">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="261aa-277">CentOS 7</span></span> <br> <span data-ttu-id="261aa-278">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="261aa-278">Oracle Linux 7</span></span> <br> <span data-ttu-id="261aa-279">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="261aa-279">RHEL 7</span></span> | <span data-ttu-id="261aa-280">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="261aa-280">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="261aa-281">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="261aa-281">openSUSE 42.3</span></span> | <span data-ttu-id="261aa-282">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="261aa-282">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="261aa-283">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="261aa-283">openSUSE Leap 15</span></span> | <span data-ttu-id="261aa-284">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="261aa-284">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="261aa-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="261aa-285">Fedora 27</span></span> <br> <span data-ttu-id="261aa-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="261aa-286">Fedora 28</span></span> | <span data-ttu-id="261aa-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="261aa-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="261aa-288">Para implantar binários do PowerShell em distribuições Linux que sem suporte oficial, instale as dependências necessárias para o sistema operacional de destino em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="261aa-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="261aa-289">Por exemplo, nosso [dockerfile Amazon Linux][amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o arquivo `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="261aa-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="261aa-290">Instalação – Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="261aa-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="261aa-291">Linux</span><span class="sxs-lookup"><span data-stu-id="261aa-291">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="261aa-292">Desinstalação de arquivos binários</span><span class="sxs-lookup"><span data-stu-id="261aa-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="261aa-293">Caminhos</span><span class="sxs-lookup"><span data-stu-id="261aa-293">Paths</span></span>

* <span data-ttu-id="261aa-294">`$PSHOME` é `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="261aa-294">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="261aa-295">Perfis de usuário serão lidos de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="261aa-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="261aa-296">Perfis padrão serão lidos de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="261aa-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="261aa-297">Módulos de usuário serão lidos de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="261aa-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="261aa-298">Módulos compartilhados serão lidos de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="261aa-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="261aa-299">Módulos padrão serão lidos de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="261aa-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="261aa-300">Histórico de PSReadline será gravado em `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="261aa-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="261aa-301">Os perfis respeitam a configuração por host do PowerShell. Assim, os perfis específicos do host padrão existem em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="261aa-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="261aa-302">O PowerShell respeita a [Especificação de Diretório Base XDG][xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="261aa-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[lançamentos]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
