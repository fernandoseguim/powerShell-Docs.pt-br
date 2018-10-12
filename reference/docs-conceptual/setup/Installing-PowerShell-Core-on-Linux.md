---
title: Instalar o PowerShell Core no Linux
description: Informações sobre a instalação do PowerShell Core em diversas distribuições Linux
ms.date: 08/06/2018
ms.openlocfilehash: d60e1d5a89b6907b67c19b8cfcde969be156bd60
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851282"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="35ac6-103">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="35ac6-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="35ac6-104">É compatível com [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="35ac6-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="35ac6-105">Em distribuições Linux sem suporte oficial, tente usar o [Pacote Snap do PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="35ac6-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="35ac6-106">Além disso, tente implantar binários do PowerShell diretamente usando o arquivo [`tar.gz` do Linux][tar], mas você precisaria configurar as dependências necessárias com base no sistema operacional em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="35ac6-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="35ac6-107">Todos os pacotes estão disponíveis na nossa página [lançamentos][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="35ac6-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="35ac6-108">Depois de instalar o pacote, execute `pwsh` em um terminal.</span><span class="sxs-lookup"><span data-stu-id="35ac6-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="35ac6-109">Instalando versões prévias</span><span class="sxs-lookup"><span data-stu-id="35ac6-109">Installing Preview Releases</span></span>

<span data-ttu-id="35ac6-110">Ao instalar uma versão prévia do PowerShell Core para Linux por meio de um Repositório de Pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="35ac6-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="35ac6-111">A instalação por meio de download direito não é alterada, somente o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="35ac6-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="35ac6-112">Aqui está uma tabela dos comandos para instalar os pacotes estáveis e de versão prévia usando vários gerenciadores de pacotes:</span><span class="sxs-lookup"><span data-stu-id="35ac6-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="35ac6-113">Distribuições</span><span class="sxs-lookup"><span data-stu-id="35ac6-113">Distribution(s)</span></span>|<span data-ttu-id="35ac6-114">Comando estável</span><span class="sxs-lookup"><span data-stu-id="35ac6-114">Stable Command</span></span> | <span data-ttu-id="35ac6-115">Comando de versão prévia</span><span class="sxs-lookup"><span data-stu-id="35ac6-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="35ac6-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="35ac6-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="35ac6-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="35ac6-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="35ac6-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="35ac6-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="35ac6-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="35ac6-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="35ac6-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="35ac6-121">Instalação por meio do repositório de pacotes – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="35ac6-122">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="35ac6-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="35ac6-123">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="35ac6-123">This is the preferred method.</span></span>

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

<span data-ttu-id="35ac6-124">Como superusuário, registre o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="35ac6-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="35ac6-125">Daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="35ac6-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="35ac6-126">Instalação por meio de download direto – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="35ac6-127">Baixe o pacote Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="35ac6-127">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="35ac6-128">da página [lançamentos][] no computador com Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="35ac6-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="35ac6-129">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="35ac6-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="35ac6-130">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="35ac6-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="35ac6-131">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35ac6-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="35ac6-132">Desinstalação – Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="35ac6-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="35ac6-134">Instalação por meio do repositório de pacotes – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="35ac6-135">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="35ac6-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="35ac6-136">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="35ac6-136">This is the preferred method.</span></span>

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

<span data-ttu-id="35ac6-137">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="35ac6-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="35ac6-138">Instalação por meio de download direto – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="35ac6-139">Baixe o pacote Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="35ac6-139">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="35ac6-140">da página [lançamentos][] no computador com Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="35ac6-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="35ac6-141">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="35ac6-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="35ac6-142">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="35ac6-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="35ac6-143">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35ac6-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="35ac6-144">Desinstalação – Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="35ac6-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="35ac6-146">Foi adicionado suporte para o Ubuntu 18.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="35ac6-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="35ac6-147">Instalação por meio do repositório de pacotes – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="35ac6-148">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="35ac6-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="35ac6-149">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="35ac6-149">This is the preferred method.</span></span>

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

<span data-ttu-id="35ac6-150">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="35ac6-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="35ac6-151">Instalação por meio de download direto – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="35ac6-152">Baixe o pacote Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="35ac6-152">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="35ac6-153">da página [lançamentos][] no computador com Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="35ac6-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="35ac6-154">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="35ac6-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="35ac6-155">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="35ac6-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="35ac6-156">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35ac6-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="35ac6-157">Desinstalação – Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="35ac6-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="35ac6-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="35ac6-159">Foi adicionado suporte para o Ubuntu 18.10 após `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="35ac6-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="35ac6-160">Como o 18.10 é um build diário, ele tem suporte apenas pela comunidade.</span><span class="sxs-lookup"><span data-stu-id="35ac6-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="35ac6-161">A instalação no 18.10 é compatível por meio do `snapd`.</span><span class="sxs-lookup"><span data-stu-id="35ac6-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="35ac6-162">Veja [Pacote Snap][snap] para obter instruções completas;</span><span class="sxs-lookup"><span data-stu-id="35ac6-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="35ac6-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="35ac6-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="35ac6-164">Instalação por meio do repositório de pacotes – Debian 8</span><span class="sxs-lookup"><span data-stu-id="35ac6-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="35ac6-165">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="35ac6-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="35ac6-166">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="35ac6-166">This is the preferred method.</span></span>

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

<span data-ttu-id="35ac6-167">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="35ac6-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="35ac6-168">Instalação por meio de download direto – Debian 8</span><span class="sxs-lookup"><span data-stu-id="35ac6-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="35ac6-169">Baixe o pacote Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="35ac6-169">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="35ac6-170">da página [lançamentos][] no computador com Debian.</span><span class="sxs-lookup"><span data-stu-id="35ac6-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="35ac6-171">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="35ac6-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="35ac6-172">O comando `dpkg -i` falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="35ac6-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="35ac6-173">O próximo comando, `apt-get install -f`, resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35ac6-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="35ac6-174">Desinstalação – Debian 8</span><span class="sxs-lookup"><span data-stu-id="35ac6-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="35ac6-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="35ac6-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="35ac6-176">Instalação por meio do repositório de pacotes – Debian 9</span><span class="sxs-lookup"><span data-stu-id="35ac6-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="35ac6-177">O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="35ac6-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="35ac6-178">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="35ac6-178">This is the preferred method.</span></span>

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

<span data-ttu-id="35ac6-179">Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="35ac6-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="35ac6-180">Instalação por meio de download direto – Debian 9</span><span class="sxs-lookup"><span data-stu-id="35ac6-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="35ac6-181">Baixe o pacote Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="35ac6-181">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="35ac6-182">da página [lançamentos][] no computador com Debian.</span><span class="sxs-lookup"><span data-stu-id="35ac6-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="35ac6-183">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="35ac6-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="35ac6-184">Desinstalação – Debian 9</span><span class="sxs-lookup"><span data-stu-id="35ac6-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="35ac6-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="35ac6-186">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="35ac6-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="35ac6-187">Instalação por meio do repositório de pacotes (preferencial) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="35ac6-188">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="35ac6-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="35ac6-189">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35ac6-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="35ac6-190">Instalação por meio de download direto – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="35ac6-191">Usando o [CentOS 7][], baixe o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="35ac6-191">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="35ac6-192">da página [lançamentos][] no computador com CentOS.</span><span class="sxs-lookup"><span data-stu-id="35ac6-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="35ac6-193">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="35ac6-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="35ac6-194">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="35ac6-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="35ac6-195">Desinstalação – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="35ac6-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="35ac6-198">Instalação por meio do repositório de pacotes (preferencial) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="35ac6-199">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="35ac6-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="35ac6-200">Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35ac6-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="35ac6-201">Instalação por meio de download direto – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="35ac6-202">Baixe o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="35ac6-202">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="35ac6-203">da página de [lançamentos][] no computador com Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="35ac6-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="35ac6-204">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="35ac6-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="35ac6-205">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="35ac6-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="35ac6-206">Desinstalação – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="35ac6-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="35ac6-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="35ac6-208">Durante a instalação do PowerShell Core, o `zypper` pode relatar o erro a seguir:</span><span class="sxs-lookup"><span data-stu-id="35ac6-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.1.0-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.1.0-1.rhel.7.x86_64
 Solution 2: break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="35ac6-209">Nesse caso, verifique se uma biblioteca `libcurl` compatível está presente, conferindo se o comando a seguir mostra o pacote `libcurl4` como instalado:</span><span class="sxs-lookup"><span data-stu-id="35ac6-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="35ac6-210">Em seguida, escolha a solução `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` ao instalar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35ac6-210">Then choose the `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="35ac6-211">Instalação por meio do repositório de pacotes (preferencial) – OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="35ac6-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="35ac6-212">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="35ac6-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="35ac6-213">Instalação por meio de download direto – OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="35ac6-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="35ac6-214">Baixe o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm` da página [lançamentos][] no computador OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="35ac6-214">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="35ac6-215">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="35ac6-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="35ac6-216">Desinstalação – OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="35ac6-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="35ac6-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="35ac6-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="35ac6-218">O Fedora 28 é compatível apenas com o PowerShell Core 6.1 e mais recentes.</span><span class="sxs-lookup"><span data-stu-id="35ac6-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="35ac6-219">Instalação por meio do repositório de pacotes (preferencial) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="35ac6-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="35ac6-220">O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="35ac6-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="35ac6-221">Instalação por meio de download direto – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="35ac6-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="35ac6-222">Baixe o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="35ac6-222">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="35ac6-223">da página [lançamentos][] no computador com Fedora.</span><span class="sxs-lookup"><span data-stu-id="35ac6-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="35ac6-224">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="35ac6-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="35ac6-225">Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="35ac6-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="35ac6-226">Desinstalação – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="35ac6-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="35ac6-227">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="35ac6-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="35ac6-228">O suporte para o Arch é experimental.</span><span class="sxs-lookup"><span data-stu-id="35ac6-228">Arch support is experimental.</span></span>

<span data-ttu-id="35ac6-229">O PowerShell está disponível no AUR (Repositório de Usuários do [Arch Linux][]).</span><span class="sxs-lookup"><span data-stu-id="35ac6-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="35ac6-230">Ele pode ser compilado com a [versão marcada mais recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="35ac6-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="35ac6-231">Ele pode ser compilado na [confirmação mais recente com mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="35ac6-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="35ac6-232">Ele pode ser instalado usando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="35ac6-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="35ac6-233">Pacotes no AUR são mantidos pela comunidade – não há suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="35ac6-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="35ac6-234">Para obter mais informações sobre a instalação de pacotes usando o AUR, veja a [wiki do Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou a comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="35ac6-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="35ac6-236">Pacote Snap</span><span class="sxs-lookup"><span data-stu-id="35ac6-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="35ac6-237">Usando o Snap</span><span class="sxs-lookup"><span data-stu-id="35ac6-237">Getting snapd</span></span>

<span data-ttu-id="35ac6-238">O `snapd` é necessário para executar snaps.</span><span class="sxs-lookup"><span data-stu-id="35ac6-238">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="35ac6-239">Use [estas instruções](https://docs.snapcraft.io/core/install) para garantir que você tem o `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="35ac6-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="35ac6-240">Instalação por meio do Snap</span><span class="sxs-lookup"><span data-stu-id="35ac6-240">Installation via Snap</span></span>

<span data-ttu-id="35ac6-241">O PowerShell Core para Linux é publicado na [Snap Store](https://snapcraft.io/store) para facilitar a instalação (e as atualizações).</span><span class="sxs-lookup"><span data-stu-id="35ac6-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="35ac6-242">Essa é a opção preferencial.</span><span class="sxs-lookup"><span data-stu-id="35ac6-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="35ac6-243">Depois de instalado o Snap atualizará automaticamente, mas você poderá disparar uma atualização usando `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="35ac6-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="35ac6-244">Desinstalação</span><span class="sxs-lookup"><span data-stu-id="35ac6-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="35ac6-245">Kali</span><span class="sxs-lookup"><span data-stu-id="35ac6-245">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="35ac6-246">Instalação</span><span class="sxs-lookup"><span data-stu-id="35ac6-246">Installation</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="35ac6-247">Desinstalação – Kali</span><span class="sxs-lookup"><span data-stu-id="35ac6-247">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="35ac6-248">Raspbian</span><span class="sxs-lookup"><span data-stu-id="35ac6-248">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="35ac6-249">O suporte para o Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="35ac6-249">Raspbian support is experimental.</span></span>

<span data-ttu-id="35ac6-250">Atualmente, o PowerShell tem suporte apenas no Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="35ac6-250">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="35ac6-251">Além disso, o CoreCLR (e, portanto, o PowerShell Core) funcionará apenas em dispositivos Pi 2 e Pi 3, pois outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), têm um processador sem suporte.</span><span class="sxs-lookup"><span data-stu-id="35ac6-251">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="35ac6-252">Faça o download do [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga as [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para instalá-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="35ac6-252">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="35ac6-253">Instalação</span><span class="sxs-lookup"><span data-stu-id="35ac6-253">Installation</span></span>

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

<span data-ttu-id="35ac6-254">Opcionalmente, você pode criar um link simbólico para poder iniciar o PowerShell sem especificar o caminho até o binário "pwsh"</span><span class="sxs-lookup"><span data-stu-id="35ac6-254">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="35ac6-255">Desinstalação – Raspbian</span><span class="sxs-lookup"><span data-stu-id="35ac6-255">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="35ac6-256">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="35ac6-256">Binary Archives</span></span>

<span data-ttu-id="35ac6-257">Os arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas Linux a fim de habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="35ac6-257">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="35ac6-258">Dependências</span><span class="sxs-lookup"><span data-stu-id="35ac6-258">Dependencies</span></span>

<span data-ttu-id="35ac6-259">O PowerShell cria binários portáteis para todas as distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="35ac6-259">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="35ac6-260">Porém, o tempo de execução do .NET Core exige dependências diferentes em diferentes distribuições e, portanto, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="35ac6-260">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="35ac6-261">O gráfico a seguir mostra as dependências do .NET Core 2.0 com suporte oficial em diferentes distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="35ac6-261">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="35ac6-262">SO</span><span class="sxs-lookup"><span data-stu-id="35ac6-262">OS</span></span>                 | <span data-ttu-id="35ac6-263">Dependências</span><span class="sxs-lookup"><span data-stu-id="35ac6-263">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="35ac6-264">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-264">Ubuntu 14.04</span></span>       | <span data-ttu-id="35ac6-265">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="35ac6-265">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="35ac6-266">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="35ac6-266">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="35ac6-267">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-267">Ubuntu 16.04</span></span>       | <span data-ttu-id="35ac6-268">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="35ac6-268">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="35ac6-269">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="35ac6-269">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="35ac6-270">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="35ac6-270">Ubuntu 17.10</span></span>       | <span data-ttu-id="35ac6-271">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="35ac6-271">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="35ac6-272">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="35ac6-272">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="35ac6-273">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="35ac6-273">Ubuntu 18.04</span></span>       | <span data-ttu-id="35ac6-274">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="35ac6-274">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="35ac6-275">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="35ac6-275">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="35ac6-276">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="35ac6-276">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="35ac6-277">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="35ac6-277">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="35ac6-278">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="35ac6-278">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="35ac6-279">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="35ac6-279">Debian 9 (Stretch)</span></span> | <span data-ttu-id="35ac6-280">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="35ac6-280">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="35ac6-281">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="35ac6-281">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="35ac6-282">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-282">CentOS 7</span></span> <br> <span data-ttu-id="35ac6-283">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-283">Oracle Linux 7</span></span> <br> <span data-ttu-id="35ac6-284">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="35ac6-284">RHEL 7</span></span> <br> <span data-ttu-id="35ac6-285">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="35ac6-285">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="35ac6-286">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="35ac6-286">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="35ac6-287">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="35ac6-287">Fedora 27</span></span> <br> <span data-ttu-id="35ac6-288">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="35ac6-288">Fedora 28</span></span> | <span data-ttu-id="35ac6-289">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="35ac6-289">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="35ac6-290">Para implantar binários do PowerShell em distribuições Linux que sem suporte oficial, instale as dependências necessárias para o sistema operacional de destino em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="35ac6-290">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="35ac6-291">Por exemplo, nosso [dockerfile Amazon Linux][amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o arquivo `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="35ac6-291">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="35ac6-292">Instalação – Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="35ac6-292">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="35ac6-293">Linux</span><span class="sxs-lookup"><span data-stu-id="35ac6-293">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="35ac6-294">Desinstalação de arquivos binários</span><span class="sxs-lookup"><span data-stu-id="35ac6-294">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="35ac6-295">Caminhos</span><span class="sxs-lookup"><span data-stu-id="35ac6-295">Paths</span></span>

* <span data-ttu-id="35ac6-296">`$PSHOME` é `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="35ac6-296">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="35ac6-297">Perfis de usuário serão lidos de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="35ac6-297">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="35ac6-298">Perfis padrão serão lidos de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="35ac6-298">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="35ac6-299">Módulos de usuário serão lidos de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="35ac6-299">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="35ac6-300">Módulos compartilhados serão lidos de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="35ac6-300">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="35ac6-301">Módulos padrão serão lidos de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="35ac6-301">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="35ac6-302">Histórico de PSReadline será gravado em `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="35ac6-302">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="35ac6-303">Os perfis respeitam a configuração por host do PowerShell. Assim, os perfis específicos do host padrão existem em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="35ac6-303">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="35ac6-304">O PowerShell respeita a [Especificação de Diretório Base XDG][xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="35ac6-304">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[lançamentos]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
