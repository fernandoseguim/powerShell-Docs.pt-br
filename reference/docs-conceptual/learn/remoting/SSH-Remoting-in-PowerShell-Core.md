---
title: Comunicação remota do PowerShell por SSH
description: Comunicação remota no PowerShell Core usando SSH
ms.date: 08/14/2018
ms.openlocfilehash: 1d7bcb69c7e784bf745cb5c2633106ea53f6226a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58056525"
---
# <a name="powershell-remoting-over-ssh"></a>Comunicação remota do PowerShell por SSH

## <a name="overview"></a>Visão geral

Normalmente, a comunicação remota do PowerShell usa WinRM para negociação de conexão e transporte de dados. Agora, o SSH está disponível para plataformas Linux e Windows, e permite a verdadeira comunicação remota multiplataforma do PowerShell.

O WinRM fornece um modelo de hospedagem robusto para sessões remotas do PowerShell. No momento, a comunicação remota baseada em SSH não oferece suporte à configuração de ponto de extremidade remoto e JEA (Just Enough Administration).

A comunicação remota do SSH permite que você faça a comunicação remota de sessão básica do PowerShell entre máquinas Windows e Linux. A comunicação remota do SSH cria um processo de hospedagem do PowerShell no computador de destino como um subsistema de SSH.
Eventualmente, implementaremos um modelo de hospedagem geral, semelhante ao WinRM, para dar suporte à configuração de ponto de extremidade e JEA.

Agora, os cmdlets `New-PSSession`, `Enter-PSSession` e `Invoke-Command` têm um novo parâmetro definido para dar suporte a essa nova conexão de comunicação remota.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Para criar uma sessão remota, especifique o computador de destino com o parâmetro `HostName` e forneça o nome de usuário com `UserName`. Ao executar os cmdlets interativamente, você receberá uma solicitação de senha. Você também pode usar a autenticação de chave SSH usando um arquivo de chave privada com o parâmetro `KeyFilePath`.

## <a name="general-setup-information"></a>Informações gerais de configuração

O SSH deve ser instalado em todos os computadores. Instale o cliente SSH (`ssh.exe`) e o servidor (`sshd.exe`) para que possa fazer comunicação remota entre os computadores. Agora, o OpenSSH para Windows está disponível no build 1809 do Windows 10 e no Windows Server 2019. Para obter mais informações, confira [OpenSSH para Windows](/windows-server/administration/openssh/openssh_overview). No Linux, instale o SSH (incluindo sshd server) apropriado à sua plataforma. Você também precisará instalar o PowerShell Core no GitHub para obter o recurso de comunicação remota do SSH. O servidor SSH deve ser configurado para criar um subsistema de SSH para hospedar um processo do PowerShell no computador remoto. Você também deve configurar autenticação baseada em chave ou habilitação por senha.

## <a name="set-up-on-windows-machine"></a>Configuração no computador Windows

1. Instale a versão mais recente do [PowerShell Core para Windows](../../install/installing-powershell-core-on-windows.md#msi)

   - Você saberá se ele tem o suporte de comunicação remota do SSH examinando os conjuntos de parâmetros para `New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Instale o OpenSSH Win32 mais recente. Para obter instruções de instalação, confira [Instalação do OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).
3. Edite o arquivo `sshd_config` localizado em `$env:ProgramData\ssh`.

   - Verifique se a autenticação de senha está habilitada

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Há um bug no OpenSSH para Windows que impede que os espaços trabalhem em caminhos executáveis do subsistema. Saiba mais neste [tópico do GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Uma solução é criar um symlink para o diretório de instalação do PowerShell que não contenha espaços:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     e, em seguida, inseri-lo no subsistema:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Como alternativa, habilite a autenticação de chave

     ```
     PubkeyAuthentication yes
     ```

4. Reinicie o serviço sshd

   ```powershell
   Restart-Service sshd
   ```

5. Adicione o caminho no qual o OpenSSH está instalado à sua variável de ambiente Path. Por exemplo, `C:\Program Files\OpenSSH\`. Essa entrada permite que ssh.exe seja localizado.

## <a name="set-up-on-linux-ubuntu-1404-machine"></a>Configuração no computador com Linux (Ubuntu 14.04)

1. Instale o build mais recente do [PowerShell Core para Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) do GitHub
2. Instale o [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) conforme necessário

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Edite o arquivo sshd_config no local /etc/ssh

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

4. Reinicie o serviço sshd

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Configuração no computador MacOS

1. Instale o build mais recente do [PowerShell Core para MacOS](../../install/installing-powershell-core-on-macos.md)

   - Verifique se a comunicação remota do SSH está habilitada, seguindo estas etapas:
     - Abra `System Preferences`
     - Clique em `Sharing`
     - Verifique `Remote Login` – deve dizer `Remote Login: On`
     - Permita o acesso a usuários apropriados

2. Edite o arquivo `sshd_config` no local `/private/etc/ssh/sshd_config`

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
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Como alternativa, habilite a autenticação de chave

     ```
     PubkeyAuthentication yes
     ```

3. Reinicie o serviço sshd

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Autenticação

A comunicação remota do PowerShell por SSH depende da troca de autenticação entre o cliente do SSH e o serviço de SSH; ela própria não implementa nenhum esquema de autenticação.
Isso significa que os esquemas de autenticação configurada, incluindo a autenticação multifator, são manipulados por SSH e são independentes do PowerShell.
Por exemplo, você pode configurar o serviço SSH para exigir autenticação de chave pública, bem como uma senha única para aumentar a segurança.
A configuração da autenticação multifator está fora do escopo desta documentação.
Consulte a documentação para o SSH sobre como configurar a autenticação multifator corretamente e validar seu trabalho fora do PowerShell antes de tentar usá-la com a comunicação remota do PowerShell.

## <a name="powershell-remoting-example"></a>Exemplo de comunicação remota do PowerShell

A maneira mais fácil de testar a comunicação remota é experimentá-la em um único computador. Neste exemplo, criamos uma sessão remota para o mesmo computador com Linux. Estamos usando cmdlets do PowerShell de forma interativa para que possamos ver avisos do SSH para verificar o computador host, bem como solicitar uma senha. Você pode fazer a mesma coisa em um computador com Windows para garantir ao funcionamento da comunicação remota. Em seguida, realize a comunicação remota entre máquinas alterando o nome do host.

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
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
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

### <a name="known-issues"></a>Problemas conhecidos

O comando sudo não funciona em uma sessão remota para computador com Linux.

## <a name="see-also"></a>Consulte Também

[PowerShell Core para Windows](../../install/installing-powershell-core-on-windows.md#msi)

[PowerShell Core para Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404)

[PowerShell Core para MacOS](../../install/installing-powershell-core-on-macos.md)

[OpenSSH para Windows](/windows-server/administration/openssh/openssh_overview)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
