# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="9d55e-101">Instalar o PowerShell Core no Windows</span><span class="sxs-lookup"><span data-stu-id="9d55e-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="9d55e-102">MSI</span><span class="sxs-lookup"><span data-stu-id="9d55e-102">MSI</span></span>

<span data-ttu-id="9d55e-103">Para instalar o PowerShell em um cliente do Windows ou Windows Server (funciona no Windows 7 SP1, no Server 2008 R2 e posterior), baixe o pacote MSI da nossa página [versões][] do GitHub.</span><span class="sxs-lookup"><span data-stu-id="9d55e-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="9d55e-104">O arquivo MSI tem esta aparência – `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="9d55e-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="9d55e-105">Após o download, clique duas vezes no instalador e siga os prompts.</span><span class="sxs-lookup"><span data-stu-id="9d55e-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="9d55e-106">Há um atalho colocado no Menu Iniciar após a instalação.</span><span class="sxs-lookup"><span data-stu-id="9d55e-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="9d55e-107">Por padrão, o pacote é instalado em `$env:ProgramFiles\PowerShell\`</span><span class="sxs-lookup"><span data-stu-id="9d55e-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
- <span data-ttu-id="9d55e-108">Você pode iniciar o PowerShell por meio do Menu Iniciar ou `$env:ProgramFiles\PowerShell\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="9d55e-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9d55e-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9d55e-109">Prerequisites</span></span>

<span data-ttu-id="9d55e-110">Para habilitar a comunicação remota do PowerShell pelo WSMan, os pré-requisitos a seguir precisam ser atendidos:</span><span class="sxs-lookup"><span data-stu-id="9d55e-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="9d55e-111">Instale o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) em versões do Windows antes do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9d55e-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="9d55e-112">Ele está disponível por meio do Windows Update ou de download direto.</span><span class="sxs-lookup"><span data-stu-id="9d55e-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="9d55e-113">Sistemas operacionais com suporte totalmente corrigidos (incluindo pacotes opcionais) já o terão instalado.</span><span class="sxs-lookup"><span data-stu-id="9d55e-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="9d55e-114">Instale o Windows Management Framework (WMF) 4.0 ou mais recente no Windows 7 e no Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="9d55e-114">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="9d55e-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="9d55e-115">ZIP</span></span>

<span data-ttu-id="9d55e-116">Arquivos binários de ZIP do PowerShell são fornecidos para habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="9d55e-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="9d55e-117">Observe que, ao usar o arquivo ZIP, você não obtém a verificação de pré-requisitos, como ocorre no pacote MSI.</span><span class="sxs-lookup"><span data-stu-id="9d55e-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="9d55e-118">Para que a comunicação remota pelo WSMan funcione corretamente em versões do Windows antes do Windows 10, é necessário garantir que os [pré-requisitos](#prerequisites) sejam atendidos.</span><span class="sxs-lookup"><span data-stu-id="9d55e-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="9d55e-119">Implantar no Windows IoT</span><span class="sxs-lookup"><span data-stu-id="9d55e-119">Deploying on Windows IoT</span></span>

<span data-ttu-id="9d55e-120">O Windows IoT já é fornecido com o Windows PowerShell, o qual usaremos para implantar o PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="9d55e-120">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="9d55e-121">Crie `PSSession` no dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="9d55e-121">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="9d55e-122">Copie o pacote ZIP no dispositivo</span><span class="sxs-lookup"><span data-stu-id="9d55e-122">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="9d55e-123">Conecte-se ao dispositivo e expanda o arquivo</span><span class="sxs-lookup"><span data-stu-id="9d55e-123">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. <span data-ttu-id="9d55e-124">Configuração de comunicação remota no PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="9d55e-124">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="9d55e-125">Conecte-se ao ponto de extremidade do PowerShell Core 6 no dispositivo</span><span class="sxs-lookup"><span data-stu-id="9d55e-125">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="9d55e-126">Implantação no Nano Server</span><span class="sxs-lookup"><span data-stu-id="9d55e-126">Deploying on Nano Server</span></span>

<span data-ttu-id="9d55e-127">Estas instruções pressupõem que uma versão do PowerShell já está em execução na imagem do Nano Server e que ela foi gerada pelo [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="9d55e-127">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="9d55e-128">Nano Server é um sistema operacional "sem periféricos".</span><span class="sxs-lookup"><span data-stu-id="9d55e-128">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="9d55e-129">Os principais binários podem ser implantados usando dois métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="9d55e-129">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="9d55e-130">Offline – monte o VHD do Nano Server e descompacte o conteúdo do arquivo zip para a localização escolhida na imagem montada.</span><span class="sxs-lookup"><span data-stu-id="9d55e-130">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="9d55e-131">Online – transfira o arquivo zip em uma sessão do PowerShell e descompacte-o em sua localização escolhida.</span><span class="sxs-lookup"><span data-stu-id="9d55e-131">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="9d55e-132">Em ambos os casos, você precisa do pacote da versão ZIP do Windows 10 x64 e precisa executar os comandos em uma instância "Administrador" do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d55e-132">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="9d55e-133">Implantação offline do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9d55e-133">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="9d55e-134">Use o utilitário zip favorito para descompactar o pacote para um diretório na imagem montada do Nano Server.</span><span class="sxs-lookup"><span data-stu-id="9d55e-134">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="9d55e-135">Desmonte a imagem e inicialize-a.</span><span class="sxs-lookup"><span data-stu-id="9d55e-135">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="9d55e-136">Conecte-se à instância da caixa de entrada do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d55e-136">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="9d55e-137">Siga as instruções para criar um ponto de extremidade de comunicação remota usando a ["outra técnica de instância"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="9d55e-137">Follow the instructions to create a remoting endpoint using the ["another instance technique"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="9d55e-138">Implantação online do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9d55e-138">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="9d55e-139">As etapas a seguir servem de orientação para a implantação do PowerShell Core em uma instância em execução do Nano Server, e a configuração do seu ponto de extremidade de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="9d55e-139">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="9d55e-140">Conectar-se à instância da caixa de entrada do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d55e-140">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="9d55e-141">Copiar o arquivo para a instância do Nano Server</span><span class="sxs-lookup"><span data-stu-id="9d55e-141">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="9d55e-142">Entrar na sessão</span><span class="sxs-lookup"><span data-stu-id="9d55e-142">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="9d55e-143">Extrair o arquivo ZIP</span><span class="sxs-lookup"><span data-stu-id="9d55e-143">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="9d55e-144">Se você deseja comunicação remota baseada no WSMan, siga as instruções para criar um ponto de extremidade de comunicação remota usando a ["outra técnica de instância"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="9d55e-144">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="9d55e-145">Instruções para criar um ponto de extremidade de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="9d55e-145">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="9d55e-146">O PowerShell Core dá suporte ao protocolo PSRP (comunicação remota do PowerShell) por WSMan e SSH.</span><span class="sxs-lookup"><span data-stu-id="9d55e-146">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="9d55e-147">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="9d55e-147">For more information, see:</span></span>

- <span data-ttu-id="9d55e-148">[Comunicação remota do SSH no PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="9d55e-148">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="9d55e-149">[Comunicação remota do WSMan no PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="9d55e-149">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="9d55e-150">Instruções de instalação do artefato</span><span class="sxs-lookup"><span data-stu-id="9d55e-150">Artifact Installation Instructions</span></span>

<span data-ttu-id="9d55e-151">Publicamos um arquivo com os bits de CoreCLR em cada build de CI com [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="9d55e-151">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="9d55e-152">Para instalar o PowerShell Core do artefato CoreCLR:</span><span class="sxs-lookup"><span data-stu-id="9d55e-152">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="9d55e-153">Baixe o pacote ZIP da guia **artefatos** do build particular.</span><span class="sxs-lookup"><span data-stu-id="9d55e-153">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="9d55e-154">Desbloqueie o arquivo ZIP: clique com o botão direito em Explorador de Arquivos -> Propriedades -> marque a caixa "Desbloquear" -> aplicar</span><span class="sxs-lookup"><span data-stu-id="9d55e-154">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="9d55e-155">Extraia o arquivo zip para o diretório `bin`</span><span class="sxs-lookup"><span data-stu-id="9d55e-155">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[versões]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell