
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="6ac1c-101">Comunicação remota do PowerShell por SSH</span><span class="sxs-lookup"><span data-stu-id="6ac1c-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="6ac1c-102">Visão geral</span><span class="sxs-lookup"><span data-stu-id="6ac1c-102">Overview</span></span>

<span data-ttu-id="6ac1c-103">Normalmente, a comunicação remota do PowerShell usa WinRM para negociação de conexão e transporte de dados.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="6ac1c-104">SSH foi escolhido para esta implementação de comunicação remota porque ele está disponível para plataformas Linux e Windows e permite a verdadeira comunicação remota multiplataforma do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="6ac1c-105">No entanto, o WinRM também fornece um modelo de hospedagem robusto para sessões remotas do PowerShell que essa implementação ainda não faz.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="6ac1c-106">Isso significa que a configuração de ponto de extremidade remoto do PowerShell e a JEA (Just Enough Administration) ainda não tem suporte nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="6ac1c-107">A comunicação remota do PowerShell SSH permite que você faça a comunicação remota de sessão básica do PowerShell entre máquinas Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="6ac1c-108">Isso é feito por meio da criação de um processo de hospedagem do PowerShell no computador de destino como um subsistema de SSH.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="6ac1c-109">Por fim, isso será alterado para um modelo de hospedagem mais geral semelhante ao funcionamento do WinRM para dar suporte à configuração de ponto de extremidade e JEA.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="6ac1c-110">Agora, os cmdlets `New-PSSession`, `Enter-PSSession` e `Invoke-Command` têm um novo parâmetro definido para facilitar essa nova conexão de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="6ac1c-110">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="6ac1c-111">Esse novo conjunto de parâmetros provavelmente será alterado, mas, por enquanto, permite que você crie SSH PSSessions com as quais você pode interagir na linha de comando ou invocar comandos e scripts.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="6ac1c-112">Especifique o computador de destino com o parâmetro HostName e forneça o nome de usuário com UserName.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="6ac1c-113">Ao executar os cmdlets interativamente na linha de comando do PowerShell, você será solicitado a fornecer uma senha.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="6ac1c-114">Porém, você também tem a opção de usar a autenticação de chave SSH e fornecer um caminho de arquivo de chave privada com o parâmetro KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="6ac1c-115">Informações gerais de configuração</span><span class="sxs-lookup"><span data-stu-id="6ac1c-115">General setup information</span></span>

<span data-ttu-id="6ac1c-116">SSH deve ser instalado em todos os computadores.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="6ac1c-117">Você deve instalar o cliente (`ssh.exe`) e o servidor (`sshd.exe`) para que possa fazer experiências com a comunicação remota de e para os computadores.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-117">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="6ac1c-118">No Windows, será necessário instalar [OpenSSH Win32 do GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="6ac1c-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="6ac1c-119">No Linux, você precisará instalar o SSH (incluindo sshd server) apropriado à sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="6ac1c-120">Você também precisará de um build recente do PowerShell ou um pacote do GitHub com o recurso de comunicação remota do SSH.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="6ac1c-121">Subsistemas SSH são usados para estabelecer um processo do PowerShell no computador remoto e o servidor SSH precisará ser configurado para isso.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="6ac1c-122">Além disso, você precisará habilitar a autenticação de senha e autenticação baseada em chave opcionalmente.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="6ac1c-123">Instalação no computador Windows</span><span class="sxs-lookup"><span data-stu-id="6ac1c-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="6ac1c-124">Instale a versão mais recente do [PowerShell Core para Windows]</span><span class="sxs-lookup"><span data-stu-id="6ac1c-124">Install the latest version of [PowerShell Core for Windows]</span></span>
   - <span data-ttu-id="6ac1c-125">Você saberá se ele tem o suporte de comunicação remota do SSH examinando os conjuntos de parâmetros para `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="6ac1c-125">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="6ac1c-126">Instalar o build mais recente [OpenSSH Win32] do GitHub usando as instruções de [instalação]</span><span class="sxs-lookup"><span data-stu-id="6ac1c-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
3. <span data-ttu-id="6ac1c-127">Edite o arquivo sshd_config no local em que você instalou OpenSSH Win32</span><span class="sxs-lookup"><span data-stu-id="6ac1c-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
   - <span data-ttu-id="6ac1c-128">Verifique se a autenticação de senha está habilitada</span><span class="sxs-lookup"><span data-stu-id="6ac1c-128">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    <span data-ttu-id="6ac1c-129">Há um bug no OpenSSH para Windows que impede que os espaços trabalhem em caminhos executáveis do subsistema.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-129">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
    <span data-ttu-id="6ac1c-130">Veja [esse problema no GitHub para obter mais informações](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="6ac1c-130">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

    <span data-ttu-id="6ac1c-131">Uma solução é criar um symlink que não contenha espaços, para o diretório de instalação do Powershell:</span><span class="sxs-lookup"><span data-stu-id="6ac1c-131">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    <span data-ttu-id="6ac1c-132">e, em seguida, inseri-lo no subsistema:</span><span class="sxs-lookup"><span data-stu-id="6ac1c-132">and then enter it in the subsystem:</span></span>

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="6ac1c-133">Como alternativa, habilite a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="6ac1c-133">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="6ac1c-134">Reinicie o serviço sshd</span><span class="sxs-lookup"><span data-stu-id="6ac1c-134">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="6ac1c-135">Adicione o caminho em que OpenSSH está instalado à sua variável Path Env</span><span class="sxs-lookup"><span data-stu-id="6ac1c-135">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
   - <span data-ttu-id="6ac1c-136">Isso deve ser feito juntamente com as linhas de `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="6ac1c-136">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="6ac1c-137">Isso permite que ssh.exe seja localizado</span><span class="sxs-lookup"><span data-stu-id="6ac1c-137">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="6ac1c-138">Instalação no computador Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="6ac1c-138">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="6ac1c-139">Instalar o build mais recente do [PowerShell Core para Linux] do GitHub</span><span class="sxs-lookup"><span data-stu-id="6ac1c-139">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
2. <span data-ttu-id="6ac1c-140">Instalar o [Ubuntu SSH] conforme necessário</span><span class="sxs-lookup"><span data-stu-id="6ac1c-140">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="6ac1c-141">Edite o arquivo sshd_config no local /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="6ac1c-141">Edit the sshd_config file at location /etc/ssh</span></span>
   - <span data-ttu-id="6ac1c-142">Verifique se a autenticação de senha está habilitada</span><span class="sxs-lookup"><span data-stu-id="6ac1c-142">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="6ac1c-143">Adicione uma entrada do subsistema PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ac1c-143">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="6ac1c-144">Como alternativa, habilite a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="6ac1c-144">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="6ac1c-145">Reinicie o serviço sshd</span><span class="sxs-lookup"><span data-stu-id="6ac1c-145">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="6ac1c-146">Instalação no computador MacOS</span><span class="sxs-lookup"><span data-stu-id="6ac1c-146">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="6ac1c-147">Instalar o build mais recente do [PowerShell Core para MacOS]</span><span class="sxs-lookup"><span data-stu-id="6ac1c-147">Install the latest [PowerShell Core for MacOS] build</span></span>
   - <span data-ttu-id="6ac1c-148">Verifique se a comunicação remota do SSH está habilitada, seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="6ac1c-148">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="6ac1c-149">Abra `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="6ac1c-149">Open `System Preferences`</span></span>
     - <span data-ttu-id="6ac1c-150">Clique em `Sharing`</span><span class="sxs-lookup"><span data-stu-id="6ac1c-150">Click on `Sharing`</span></span>
     - <span data-ttu-id="6ac1c-151">Verifique `Remote Login` – deve dizer `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="6ac1c-151">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="6ac1c-152">Permita o acesso a usuários apropriados</span><span class="sxs-lookup"><span data-stu-id="6ac1c-152">Allow access to appropriate users</span></span>
2. <span data-ttu-id="6ac1c-153">Edite o arquivo `sshd_config` no local `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="6ac1c-153">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
   - <span data-ttu-id="6ac1c-154">Usar seu editor favorito ou</span><span class="sxs-lookup"><span data-stu-id="6ac1c-154">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="6ac1c-155">Verifique se a autenticação de senha está habilitada</span><span class="sxs-lookup"><span data-stu-id="6ac1c-155">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="6ac1c-156">Adicione uma entrada do subsistema PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ac1c-156">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="6ac1c-157">Como alternativa, habilite a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="6ac1c-157">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="6ac1c-158">Reinicie o serviço sshd</span><span class="sxs-lookup"><span data-stu-id="6ac1c-158">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="6ac1c-159">Exemplo de comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ac1c-159">PowerShell Remoting Example</span></span>

<span data-ttu-id="6ac1c-160">A maneira mais fácil de testar a comunicação remota é experimentá-la em um único computador.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-160">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="6ac1c-161">Aqui, criarei uma sessão remota para o mesmo computador em uma caixa de Linux.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-161">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="6ac1c-162">Observe que estou usando cmdlets do PowerShell em um prompt de comando para que possamos ver avisos do SSH para confirmar o computador host, bem como prompts de senha.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-162">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="6ac1c-163">Você pode usar o mesmo procedimento em um computador Windows para garantir que a comunicação remota está funcionando nele e alternar entre os computadores simplesmente alterando o nome do host.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-163">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a><span data-ttu-id="6ac1c-164">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="6ac1c-164">Known Issues</span></span>

- <span data-ttu-id="6ac1c-165">O comando sudo não funciona em uma sessão remota para computador Linux.</span><span class="sxs-lookup"><span data-stu-id="6ac1c-165">sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ac1c-166">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="6ac1c-166">See Also</span></span>

[<span data-ttu-id="6ac1c-167">PowerShell Core para Windows</span><span class="sxs-lookup"><span data-stu-id="6ac1c-167">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="6ac1c-168">PowerShell Core para Linux</span><span class="sxs-lookup"><span data-stu-id="6ac1c-168">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="6ac1c-169">PowerShell Core para MacOS</span><span class="sxs-lookup"><span data-stu-id="6ac1c-169">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="6ac1c-170">OpenSSH Win32</span><span class="sxs-lookup"><span data-stu-id="6ac1c-170">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="6ac1c-171">instalação</span><span class="sxs-lookup"><span data-stu-id="6ac1c-171">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="6ac1c-172">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="6ac1c-172">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)