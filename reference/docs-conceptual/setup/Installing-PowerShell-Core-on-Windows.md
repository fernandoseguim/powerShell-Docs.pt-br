---
title: Instalar o PowerShell Core no Windows
description: Informações sobre a instalação do PowerShell Core no Windows
ms.date: 08/06/2018
ms.openlocfilehash: ba159a69df7e117e90e21dd26228b61146260475
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320884"
---
# <a name="installing-powershell-core-on-windows"></a>Instalar o PowerShell Core no Windows

## <a name="msi"></a>MSI

Para instalar o PowerShell em um cliente do Windows ou Windows Server (funciona no Windows 7 SP1, no Server 2008 R2 e posterior), baixe o pacote MSI da nossa página [versões][] do GitHub.

O arquivo MSI tem esta aparência – `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Após o download, clique duas vezes no instalador e siga os prompts.

Há um atalho colocado no Menu Iniciar após a instalação.

- Por padrão, o pacote é instalado em `$env:ProgramFiles\PowerShell\<version>`
- Você pode iniciar o PowerShell por meio do Menu Iniciar ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Pré-requisitos

Para habilitar a comunicação remota do PowerShell pelo WSMan, os pré-requisitos a seguir precisam ser atendidos:

- Instale o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) em versões do Windows antes do Windows 10.
  Ele está disponível por meio do Windows Update ou de download direto.
  Sistemas operacionais com suporte totalmente corrigidos (incluindo pacotes opcionais) já o terão instalado.
- Instale o Windows Management Framework (WMF) 4.0 ou mais recente no Windows 7 e no Windows Server 2008 R2.

## <a name="zip"></a>ZIP

Arquivos binários de ZIP do PowerShell são fornecidos para habilitar cenários de implantação avançada.
Observe que, ao usar o arquivo ZIP, você não obtém a verificação de pré-requisitos, como ocorre no pacote MSI.
Para que a comunicação remota pelo WSMan funcione corretamente em versões do Windows antes do Windows 10, é necessário garantir que os [pré-requisitos](#prerequisites) sejam atendidos.

## <a name="deploying-on-windows-iot"></a>Implantar no Windows IoT

O Windows IoT já é fornecido com o Windows PowerShell, o qual usaremos para implantar o PowerShell Core 6.

1. Crie `PSSession` no dispositivo de destino

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Copie o pacote ZIP no dispositivo

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Conecte-se ao dispositivo e expanda o arquivo

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. Configuração de comunicação remota no PowerShell Core 6

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Conecte-se ao ponto de extremidade do PowerShell Core 6 no dispositivo

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a>Implantação no Nano Server

Estas instruções pressupõem que uma versão do PowerShell já está em execução na imagem do Nano Server e que ela foi gerada pelo [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).
Nano Server é um sistema operacional "sem periféricos". Os principais binários podem ser implantados usando dois métodos diferentes.

1. Offline – monte o VHD do Nano Server e descompacte o conteúdo do arquivo zip para o local escolhido na imagem montada.
2. Online – transfira o arquivo zip em uma sessão do PowerShell e descompacte-o em seu local escolhido.

Em ambos os casos, você precisa do pacote da versão ZIP do Windows 10 x64 e precisa executar os comandos em uma instância "Administrador" do PowerShell.

### <a name="offline-deployment-of-powershell-core"></a>Implantação offline do PowerShell Core

1. Use o utilitário zip favorito para descompactar o pacote para um diretório na imagem montada do Nano Server.
2. Desmonte a imagem e inicialize-a.
3. Conecte-se à instância da caixa de entrada do Windows PowerShell.
4. Siga as instruções para criar um ponto de extremidade de comunicação remota usando a ["outra técnica de instância"](../core-powershell/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Implantação online do PowerShell Core

As etapas a seguir servem de orientação para a implantação do PowerShell Core em uma instância em execução do Nano Server, e a configuração do seu ponto de extremidade de comunicação remota.

- Conectar-se à instância da caixa de entrada do Windows PowerShell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Copiar o arquivo para a instância do Nano Server

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Entrar na sessão

  ```powershell
  Enter-PSSession $session
  ```

- Extrair o arquivo ZIP

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Se você deseja comunicação remota baseada no WSMan, siga as instruções para criar um ponto de extremidade de comunicação remota usando a ["outra técnica de instância"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instruções para criar um ponto de extremidade de comunicação remota

O PowerShell Core dá suporte ao protocolo PSRP (comunicação remota do PowerShell) por WSMan e SSH.
Para obter mais informações, consulte:

- [Comunicação remota do SSH no PowerShell Core][ssh-remoting]
- [Comunicação remota do WSMan no PowerShell Core][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Instruções de instalação do artefato

Publicamos um arquivo com os bits de CoreCLR em cada build de CI com [AppVeyor][].

Para instalar o PowerShell Core do artefato CoreCLR:

1. Baixe o pacote ZIP da guia **artefatos** do build particular.
2. Desbloqueie o arquivo ZIP: clique com o botão direito em Explorador de Arquivos -> Propriedades -> marque a caixa "Desbloquear" -> aplicar
3. Extraia o arquivo zip para o diretório `bin`
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[versões]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
