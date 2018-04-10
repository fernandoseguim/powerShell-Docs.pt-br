# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="c2c48-101">Instalar o PowerShell Core no Windows</span><span class="sxs-lookup"><span data-stu-id="c2c48-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="c2c48-102">MSI</span><span class="sxs-lookup"><span data-stu-id="c2c48-102">MSI</span></span>

<span data-ttu-id="c2c48-103">Para instalar o PowerShell em um cliente do Windows ou Windows Server (funciona no Windows 7 SP1, no Server 2008 R2 e posterior), baixe o pacote MSI da nossa página [versões][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="c2c48-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="c2c48-104">O arquivo MSI tem esta aparência – `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="c2c48-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="c2c48-105">Após o download, clique duas vezes no instalador e siga os prompts.</span><span class="sxs-lookup"><span data-stu-id="c2c48-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="c2c48-106">Há um atalho colocado no Menu Iniciar após a instalação.</span><span class="sxs-lookup"><span data-stu-id="c2c48-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

* <span data-ttu-id="c2c48-107">Por padrão, o pacote é instalado em `$env:ProgramFiles\PowerShell\`</span><span class="sxs-lookup"><span data-stu-id="c2c48-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
* <span data-ttu-id="c2c48-108">Você pode iniciar o PowerShell por meio do Menu Iniciar ou `$env:ProgramFiles\PowerShell\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="c2c48-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c2c48-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c2c48-109">Prerequisites</span></span>

<span data-ttu-id="c2c48-110">Para habilitar a comunicação remota do PowerShell pelo WSMan, os pré-requisitos a seguir precisam ser atendidos:</span><span class="sxs-lookup"><span data-stu-id="c2c48-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

* <span data-ttu-id="c2c48-111">Instale o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) em versões do Windows antes do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c2c48-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="c2c48-112">Ele está disponível por meio do Windows Update ou de download direto.</span><span class="sxs-lookup"><span data-stu-id="c2c48-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="c2c48-113">Sistemas operacionais com suporte totalmente corrigidos (incluindo pacotes opcionais) já o terão instalado.</span><span class="sxs-lookup"><span data-stu-id="c2c48-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
* <span data-ttu-id="c2c48-114">Instale o Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) ou mais recente ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) no Windows 7 e no Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="c2c48-114">Install the Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) or newer ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="c2c48-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="c2c48-115">ZIP</span></span>

<span data-ttu-id="c2c48-116">Arquivos binários de ZIP do PowerShell são fornecidos para habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="c2c48-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="c2c48-117">Observe que, ao usar o arquivo ZIP, você não obtém a verificação de pré-requisitos, como ocorre no pacote MSI.</span><span class="sxs-lookup"><span data-stu-id="c2c48-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="c2c48-118">Para que a comunicação remota pelo WSMan funcione corretamente em versões do Windows antes do Windows 10, é necessário garantir que os [pré-requisitos](#prerequisites) sejam atendidos.</span><span class="sxs-lookup"><span data-stu-id="c2c48-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="c2c48-119">Implantação no Nano Server</span><span class="sxs-lookup"><span data-stu-id="c2c48-119">Deploying on Nano Server</span></span>

<span data-ttu-id="c2c48-120">Estas instruções pressupõem que uma versão do PowerShell já está em execução na imagem do Nano Server e que ela foi gerada pelo [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="c2c48-120">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="c2c48-121">O Nano Server é um sistema operacional "sem periféricos" e a implantação dos binários do PowerShell Core pode ocorrer de duas maneiras diferentes:</span><span class="sxs-lookup"><span data-stu-id="c2c48-121">Nano Server is a "headless" OS and deployment of PowerShell Core binaries can happen in two different ways:</span></span>

1. <span data-ttu-id="c2c48-122">Offline – monte o VHD do Nano Server e descompacte o conteúdo do arquivo zip para o local escolhido na imagem montada.</span><span class="sxs-lookup"><span data-stu-id="c2c48-122">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="c2c48-123">Online – transfira o arquivo zip em uma sessão do PowerShell e descompacte-o em seu local escolhido.</span><span class="sxs-lookup"><span data-stu-id="c2c48-123">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="c2c48-124">Em ambos os casos, você precisa do pacote da versão Zip do Windows 10 x64 e precisa executar os comandos em uma instância "Administrador" do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2c48-124">In both cases, you will need the Windows 10 x64 Zip release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="c2c48-125">Implantação offline do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c2c48-125">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="c2c48-126">Use o utilitário zip favorito para descompactar o pacote para um diretório na imagem montada do Nano Server.</span><span class="sxs-lookup"><span data-stu-id="c2c48-126">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="c2c48-127">Desmonte a imagem e inicialize-a.</span><span class="sxs-lookup"><span data-stu-id="c2c48-127">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="c2c48-128">Conecte-se à instância da caixa de entrada do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2c48-128">Connect to the inbox instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="c2c48-129">Siga as instruções para criar um ponto de extremidade de comunicação remota usando a [outra técnica de instância](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="c2c48-129">Follow the instructions to create a remoting endpoint using the [another instance technique](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="c2c48-130">Implantação online do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c2c48-130">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="c2c48-131">As etapas a seguir orientam sobre a implantação do PowerShell Core a uma instância em execução do Nano Server e a configuração do seu ponto de extremidade de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="c2c48-131">The following steps will guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

* <span data-ttu-id="c2c48-132">Conectar-se à instância da caixa de entrada do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2c48-132">Connect to the inbox instance of Windows PowerShell</span></span>

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* <span data-ttu-id="c2c48-133">Copiar o arquivo para a instância do Nano Server</span><span class="sxs-lookup"><span data-stu-id="c2c48-133">Copy the file to the Nano Server instance</span></span>

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* <span data-ttu-id="c2c48-134">Entrar na sessão</span><span class="sxs-lookup"><span data-stu-id="c2c48-134">Enter the session</span></span>

```powershell
Enter-PSSession $session
```

* <span data-ttu-id="c2c48-135">Extrair o arquivo ZIP</span><span class="sxs-lookup"><span data-stu-id="c2c48-135">Extract the Zip file</span></span>

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* <span data-ttu-id="c2c48-136">Se você deseja comunicação remota baseada no WSMan, siga as instruções para criar um ponto de extremidade de comunicação remota usando a [outra técnica de instância](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="c2c48-136">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the [another instance technique](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="c2c48-137">Instruções para criar um ponto de extremidade de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="c2c48-137">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="c2c48-138">O PowerShell Core dá suporte ao protocolo PSRP (comunicação remota do PowerShell) por WSMan e SSH.</span><span class="sxs-lookup"><span data-stu-id="c2c48-138">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="c2c48-139">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="c2c48-139">For more information, see:</span></span>

* <span data-ttu-id="c2c48-140">[Comunicação remota do SSH no PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="c2c48-140">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="c2c48-141">[Comunicação remota do WSMan no PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="c2c48-141">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="c2c48-142">Instruções de instalação do artefato</span><span class="sxs-lookup"><span data-stu-id="c2c48-142">Artifact Installation Instructions</span></span>

<span data-ttu-id="c2c48-143">Publicamos um arquivo com os bits de CoreCLR em cada build de CI com [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="c2c48-143">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

## <a name="coreclr-artifacts"></a><span data-ttu-id="c2c48-144">Artefatos do CoreCLR</span><span class="sxs-lookup"><span data-stu-id="c2c48-144">CoreCLR Artifacts</span></span>

* <span data-ttu-id="c2c48-145">Baixe o pacote zip da guia **artefatos** do build particular.</span><span class="sxs-lookup"><span data-stu-id="c2c48-145">Download zip package from **artifacts** tab of the particular build.</span></span>
* <span data-ttu-id="c2c48-146">Desbloqueie o arquivo zip: clique com o botão direito do mouse em Explorador de Arquivos -> Propriedades -> marque a caixa "Desbloquear" -> aplique</span><span class="sxs-lookup"><span data-stu-id="c2c48-146">Unblock zip file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
* <span data-ttu-id="c2c48-147">Extraia o arquivo zip para o diretório `bin`</span><span class="sxs-lookup"><span data-stu-id="c2c48-147">Extract zip file to `bin` directory</span></span>
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[versões]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell