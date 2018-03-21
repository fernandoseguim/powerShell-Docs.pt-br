# <a name="installing-powershell-core-on-macos-and-linux"></a>Instalar o PowerShell Core no macOS e Linux

Dá suporte a [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch] e [macOS 10.12][mac].

Em distribuições Linux sem suporte oficial, tente usar o [PowerShell AppImage][lai]. Além disso, tente implantar binários do PowerShell diretamente usando o arquivo [`tar.gz` do Linux][tar], mas você precisaria configurar as dependências necessárias com base no sistema operacional em etapas separadas.

Todos os pacotes estão disponíveis na nossa página [versões][] do GitHub. Depois de instalar o pacote, execute `pwsh` em um terminal.

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

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Instalação por meio do repositório de pacotes – Ubuntu 14.04

O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações). Essa é a opção preferencial.

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

Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Instalação por meio de download direto – Ubuntu 14.04

Baixe o pacote Debian `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` da página [versões][] no computador Ubuntu.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.

### <a name="uninstallation---ubuntu-1404"></a>Desinstalação – Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Instalação por meio do repositório de pacotes – Ubuntu 16.04

O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).
Essa é a opção preferencial.

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

Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalação por meio de download direto – Ubuntu 16.04

Baixe o pacote Debian `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` da página [versões][] no computador Ubuntu:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Desinstalação – Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a>Ubuntu 17.04

### <a name="installation-via-package-repository---ubuntu-1704"></a>Instalação por meio do repositório de pacotes – Ubuntu 17.04

O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).
Essa é a opção preferencial.

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

Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.

### <a name="installation-via-direct-download---ubuntu-1704"></a>Instalação por meio de download direto – Ubuntu 17.04

Baixe o pacote Debian `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` da página [versões][] no computador Ubuntu:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.

### <a name="uninstallation---ubuntu-1704"></a>Desinstalação – Ubuntu 17.04

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Instalação por meio do repositório de pacotes – Debian 8

O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).
Essa é a opção preferencial.

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

Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.

### <a name="installation-via-direct-download---debian-8"></a>Instalação por meio de download direto – Debian 8

Baixe o pacote Debian `powershell_6.0.0-1.debian.8_amd64.deb` da página [versões][] no computador Debian:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.

### <a name="uninstallation---debian-8"></a>Desinstalação – Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Instalação por meio do repositório de pacotes – Debian 9

O PowerShell Core para Linux é publicado nos repositórios de pacote para facilitar a instalação (e as atualizações).
Essa é a opção preferencial.

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

Depois de registrar o repositório Microsoft uma vez como superusuário, daí em diante, você só precisa usar `sudo apt-get upgrade powershell` para atualizá-lo.

### <a name="installation-via-direct-download---debian-9"></a>Instalação por meio de download direto – Debian 9

Baixe o pacote Debian `powershell_6.0.0-1.debian.9_amd64.deb` da página [versões][] no computador Debian:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> Observe que `dpkg -i` falhará com dependências não atendidas; o próximo comando, `apt-get install -f`, resolve isso e, em seguida, conclui a configuração do pacote do PowerShell.

### <a name="uninstallation---debian-9"></a>Desinstalação – Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> Este pacote também funciona no Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Instalação por meio do repositório de pacotes (preferencial) – CentOS 7

O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>Instalação por meio de download direto – CentOS 7

Usando o [CentOS 7][], baixe o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` da página [versões][] no computador CentOS:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Em seguida, execute o seguinte no terminal:

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Desinstalação – CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Instalação por meio do repositório de pacotes (preferencial) – Red Hat Enterprise Linux (RHEL) 7

O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Depois de registrar o repositório da Microsoft uma vez como superusuário, você só precisa usar `sudo yum update powershell` para atualizar o PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Instalação por meio de download direto – Red Hat Enterprise Linux (RHEL) 7

Baixe o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` da página de [versões][] no computador Red Hat Enterprise Linux:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Desinstalação – Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> **Observação:** durante a instalação do PowerShell Core, o `zypper` pode relatar o erro a seguir:
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> Nesse caso, verifique se uma biblioteca `libcurl` compatível está presente, conferindo se o comando a seguir mostra o pacote `libcurl4` como instalado:
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> Em seguida, escolha a solução `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` ao instalar o pacote `powershell`.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Instalação por meio do repositório de pacotes (preferencial) – OpenSUSE 42.2

O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>Instalação por meio de download direto – OpenSUSE 42.2

Baixe o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` da página [versões][] no computador OpenSUSE:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Desinstalação – OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a>Fedora 25

### <a name="installation-via-package-repository-preferred---fedora-25"></a>Instalação por meio do repositório de pacotes (preferencial) – Fedora 25

O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).

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

### <a name="installation-via-direct-download---fedora-25"></a>Instalação por meio de download direto – Fedora 25

Baixe o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` da página [versões][] no computador Fedora:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>Desinstalação – Fedora 25

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a>Fedora 26

### <a name="installation-via-package-repository-preferred---fedora-26"></a>Instalação por meio do repositório de pacotes (preferencial) – Fedora 26

O PowerShell Core para Linux é publicado nos repositórios oficiais da Microsoft para facilitar a instalação (e as atualizações).

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

### <a name="installation-via-direct-download---fedora-26"></a>Instalação por meio de download direto – Fedora 26

Baixe o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` da página [versões][] no computador Fedora:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Você também pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>Desinstalação – Fedora 26

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

O PowerShell está disponível no AUR (Repositório de Usuários do [Arch Linux][]).

* Ele pode ser compilado com a [versão marcada mais recente][arch-release]
* Ele pode ser compilado na [confirmação mais recente com mestre][arch-git]
* Ele pode ser instalado usando o [binário da versão mais recente][arch-bin]

Pacotes no AUR são mantidos pela comunidade – não há suporte oficial.

Para obter mais informações sobre a instalação de pacotes usando o AUR, veja a [wiki do Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou a comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>Linux AppImage

Usando uma distribuição Linux recente, baixe a AppImage `powershell-6.0.0-x86_64.AppImage` da página [versões][] no computador Linux.

Em seguida, execute o seguinte no terminal:

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

A [AppImage][] permite executar o PowerShell sem instalá-lo. É um aplicativo portátil que inclui o PowerShell e suas dependências (incluindo dependências do sistema do .NET Core) em um pacote coeso. Esse pacote funciona independentemente da distribuição Linux do usuário e é um binário único.

[appimage]: http://appimage.org/

## <a name="macos-1012"></a>macOS 10.12

### <a name="installation-via-homebrew-preferred---macos-1012"></a>Instalação por meio do Homebrew (preferencial) – macOS 10.12

[Homebrew][brew] é o gerenciador de pacotes ausentes para macOS. Se o comando `brew` não for encontrado, será necessário instalar o Homebrew seguindo [as instruções][brew].

Depois da instalação do Homebrew, é fácil instalar o PowerShell. Primeiro, instale o [Homebrew-Cask][cask], assim você pode instalar mais pacotes:

```sh
brew tap caskroom/cask
```

Agora, você pode instalar o PowerShell:

```sh
brew cask install powershell
```

Quando são lançadas novas versões do PowerShell, basta atualizar fórmula do Homebrew e atualizar o PowerShell:

```sh
brew update
brew cask reinstall powershell
```

> Observação: por causa [desse problema no Cask](https://github.com/caskroom/homebrew-cask/issues/29301), no momento, você deve fazer uma reinstalação para atualizar.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a>Instalação por meio de download direto – macOS 10.12

Usando o macOS 10.12, baixe o pacote PKG `powershell-6.0.0-osx.10.12-x64.pkg` da página [versões][] no computador macOS.

Clique duas vezes no arquivo e siga os prompts ou instale-o do terminal:

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a>Desinstalação – macOS 10.12

Se você instalou o PowerShell com Homebrew, a desinstalação é fácil:

```sh
brew cask uninstall powershell
```

Se você instalou o PowerShell por meio de download direto, o PowerShell deve ser removido manualmente:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Para desinstalar os caminhos do PowerShell adicionais (como o caminho de perfil do usuário), veja a seção [caminhos][paths] abaixo neste documento e remova os caminhos desejados com `sudo rm`. (Observação: isso não é necessário se você instalou usando Homebrew.)

[paths]:#paths

## <a name="kali"></a>Kali

### <a name="installation"></a>Instalação

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Executar o PowerShell no Kali mais recente (Kali GNU/Linux Rolling) sem instalá-lo

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Desinstalação – Kali

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a>Raspbian

Atualmente, o PowerShell tem suporte apenas no Raspbian Stretch.

### <a name="installation"></a>Instalação

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

### <a name="uninstallation---raspbian"></a>Desinstalação – Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Arquivos binários

Arquivos binários `tar.gz` do PowerShell são fornecidos para plataformas macOS e Linux para habilitar cenários de implantação avançada.

### <a name="dependencies"></a>Dependências

No Linux, o PowerShell cria binários portáteis para todas as distribuições Linux.
Porém, o tempo de execução do .NET Core exige dependências diferentes em diferentes distribuições e, portanto, o PowerShell faz o mesmo.

O gráfico a seguir mostra as dependências do .NET Core 2.0 em diferentes distribuições Linux oficialmente com suporte.

| SO                 | Dependências |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 <br> Fedora 25 | libunwind, libcurl, openssl-libs, libicu |
| Fedora 26          | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Para implantar binários do PowerShell em distribuições Linux que sem suporte oficial, instale as dependências necessárias para o sistema operacional de destino em etapas separadas. Por exemplo, nosso [dockerfile Amazon Linux][amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o arquivo `tar.gz` Linux.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Instalação – Arquivos binários

#### <a name="linux"></a>Linux

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

#### <a name="macos"></a>macOS

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

### <a name="uninstallation---binary-archives"></a>Desinstalação – Arquivos binários

#### <a name="linux"></a>Linux

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a>macOS

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a>Caminhos

* `$PSHOME` é `/opt/microsoft/powershell/6.0.0/`
* Perfis de usuário serão lidos de `~/.config/powershell/profile.ps1`
* Perfis padrão serão lidos de `$PSHOME/profile.ps1`
* Módulos de usuário serão lidos de `~/.local/share/powershell/Modules`
* Módulos compartilhados serão lidos de `/usr/local/share/powershell/Modules`
* Módulos padrão serão lidos de `$PSHOME/Modules`
* Histórico de PSReadline será gravado em `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Os perfis respeitam a configuração por host do PowerShell. Assim, os perfis específicos do host padrão existem em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.

No Linux e no macOS, a [especificação de diretório básico XDG] [ xdg-bds] é respeitada.

Observe que, como macOS é uma derivação do BSD, em vez de `/opt`, o prefixo usado é `/usr/local`. Portanto, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.0/`, e o symlink é colocado em `/usr/local/bin/pwsh`.

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
