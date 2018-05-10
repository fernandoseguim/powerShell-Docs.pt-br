# <a name="powershell-remoting-over-ssh"></a>Comunicação remota do PowerShell por SSH

## <a name="overview"></a>Visão geral

Normalmente, a comunicação remota do PowerShell usa WinRM para negociação de conexão e transporte de dados.
SSH foi escolhido para esta implementação de comunicação remota porque ele está disponível para plataformas Linux e Windows e permite a verdadeira comunicação remota multiplataforma do PowerShell.
No entanto, o WinRM também fornece um modelo de hospedagem robusto para sessões remotas do PowerShell que essa implementação ainda não faz.
Isso significa que a configuração de ponto de extremidade remoto do PowerShell e a JEA (Just Enough Administration) ainda não tem suporte nesta implementação.

A comunicação remota do PowerShell SSH permite que você faça a comunicação remota de sessão básica do PowerShell entre máquinas Windows e Linux.
Isso é feito por meio da criação de um processo de hospedagem do PowerShell no computador de destino como um subsistema de SSH.
Por fim, isso será alterado para um modelo de hospedagem mais geral semelhante ao funcionamento do WinRM para dar suporte à configuração de ponto de extremidade e JEA.

Agora, os cmdlets New-PSSession, Enter-PSSession e Invoke-Command têm um novo parâmetro definido para facilitar essa nova conexão de comunicação remota

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Esse novo conjunto de parâmetros provavelmente será alterado, mas, por enquanto, permite que você crie SSH PSSessions com as quais você pode interagir na linha de comando ou invocar comandos e scripts.
Especifique o computador de destino com o parâmetro HostName e forneça o nome de usuário com UserName.
Ao executar os cmdlets interativamente na linha de comando do PowerShell, você será solicitado a fornecer uma senha.
Porém, você também tem a opção de usar a autenticação de chave SSH e fornecer um caminho de arquivo de chave privada com o parâmetro KeyFilePath.

## <a name="general-setup-information"></a>Informações gerais de configuração

SSH deve ser instalado em todos os computadores.
Você deve instalar o cliente (ssh.exe) e o servidor (sshd.exe) para que possa fazer experiências com a comunicação remota de e para os computadores.
No Windows, será necessário instalar [OpenSSH Win32 do GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
No Linux, você precisará instalar o SSH (incluindo sshd server) apropriado à sua plataforma.
Você também precisará de um build recente do PowerShell ou um pacote do GitHub com o recurso de comunicação remota do SSH.
Subsistemas SSH são usados para estabelecer um processo do PowerShell no computador remoto e o servidor SSH precisará ser configurado para isso.
Além disso, você precisará habilitar a autenticação de senha e autenticação baseada em chave opcionalmente.

## <a name="setup-on-windows-machine"></a>Instalação no computador Windows

1. Instale a versão mais recente do [PowerShell Core para Windows]
    - Você saberá se ele tem o suporte de comunicação remota do SSH examinando os conjuntos de parâmetros para New-PSSession

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. Instalar o build mais recente [OpenSSH Win32] do GitHub usando as instruções de [instalação]
1. Edite o arquivo sshd_config no local em que você instalou OpenSSH Win32
    - Verifique se a autenticação de senha está habilitada

    ```
    PasswordAuthentication yes
    ```

    - Adicione uma entrada de subsistema PowerShell, substitua `c:/program files/powershell/6.0.0/pwsh.exe` pelo caminho correto para a versão que você deseja usar

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - Como alternativa, habilite a autenticação de chave

    ```
    PubkeyAuthentication yes
    ```

1. Reinicie o serviço sshd

    ```powershell
    Restart-Service sshd
    ```

1. Adicione o caminho em que OpenSSH está instalado à sua variável Path Env
    - Isso deve ser feito juntamente com as linhas de `C:\Program Files\OpenSSH\`
    - Isso permite que ssh.exe seja localizado

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Instalação no computador Linux (Ubuntu 14.04)

1. Instale o build mais recente do [PowerShell para Linux] do GitHub
1. Instale o [Ubuntu SSH] conforme necessário

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. Edite o arquivo sshd_config no local /etc/ssh
    - Verifique se a autenticação de senha está habilitada

    ```
    PasswordAuthentication yes
    ```

    - Adicione uma entrada do subsistema PowerShell

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - Como alternativa, habilite a autenticação de chave

    ```
    PubkeyAuthentication yes
    ```

1. Reinicie o serviço sshd

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a>Instalação no computador MacOS

1. Instale o build mais recente do [PowerShell para MacOS]
    - Verifique se a comunicação remota do SSH está habilitada, seguindo estas etapas:
      - Abra `System Preferences`
      - Clique em `Sharing`
      - Verifique `Remote Login` – deve dizer `Remote Login: On`
      - Permita o acesso a usuários apropriados
1. Edite o arquivo `sshd_config` no local `/private/etc/ssh/sshd_config`
    - Usar seu editor favorito ou

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - Verifique se a autenticação de senha está habilitada

    ```
    PasswordAuthentication yes
    ```

    - Adicione uma entrada do subsistema PowerShell

    ```
    Subsystem powershell /usr/local/bin/powershell -sshs -NoLogo -NoProfile
    ```

    - Como alternativa, habilite a autenticação de chave

    ```
    PubkeyAuthentication yes
    ```

1. Reinicie o serviço sshd

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a>Exemplo de comunicação remota do PowerShell

A maneira mais fácil de testar a comunicação remota é experimentá-la em um único computador.
Aqui, criarei uma sessão remota para o mesmo computador em uma caixa de Linux.
Observe que estou usando cmdlets do PowerShell em um prompt de comando para que possamos ver avisos do SSH para confirmar o computador host, bem como prompts de senha.
Você pode usar o mesmo procedimento em um computador Windows para garantir que a comunicação remota está funcionando nele e alternar entre os computadores simplesmente alterando o nome do host.

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
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

### <a name="known-issues"></a>Problemas conhecidos

1. O comando sudo não funciona em uma sessão remota para computador Linux.

[PowerShell Core para Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[OpenSSH Win32]: https://github.com/PowerShell/Win32-OpenSSH/releases
[instalação]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[PowerShell para Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[PowerShell para MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012
