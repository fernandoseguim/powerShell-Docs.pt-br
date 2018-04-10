---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Executando comandos remotos
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: eb9f0ce0102de13d4fcd1d51f0e9174e9d5c340c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="running-remote-commands"></a>Executando comandos remotos

Você pode executar comandos em uma ou centenas de computadores com um único comando do Windows PowerShell. O Windows PowerShell oferece suporte à computação remota usando diversas tecnologias, incluindo WMI, RPC e WS-Management.

## <a name="remoting-in-powershell-core"></a>Comunicação remota no PowerShell Core

O PowerShell Core, a edição mais recente do PowerShell no Windows, macOS e Linux, dá suporte ao WMI, WS-Management e à comunicação remota do SSH.
(Não há mais suporte para RPC.)

Para obter mais informações sobre como configurar isso, veja:

* [Comunicação remota do SSH no PowerShell Core][ssh-remoting]
* [Comunicação remota do WSMan no PowerShell Core][wsman-remoting]

## <a name="remoting-without-configuration"></a>Comunicação remota sem configuração

Muitos cmdlets do Windows PowerShell têm o parâmetro ComputerName que permite coletar dados e alterar as configurações de um ou mais computadores remotos. Eles usam uma variedade de tecnologias de comunicação e muitos funcionam em todos os sistemas operacionais Windows que oferecem suporte ao Windows PowerShell sem qualquer configuração especial.

Esses cmdlets incluem:

* [Restart-Computer](https://go.microsoft.com/fwlink/?LinkId=821625)
* [Test-Connection](https://go.microsoft.com/fwlink/?LinkId=821646)
* [Clear-EventLog](https://go.microsoft.com/fwlink/?LinkId=821568)
* [Get-EventLog](https://go.microsoft.com/fwlink/?LinkId=821585)
* [Get-HotFix](https://go.microsoft.com/fwlink/?LinkId=821586)
* [Get-Process](https://go.microsoft.com/fwlink/?linkid=821590)
* [Get-Service](https://go.microsoft.com/fwlink/?LinkId=821593)
* [Set-Service](https://go.microsoft.com/fwlink/?LinkId=821633)
* [Get-WinEvent](https://go.microsoft.com/fwlink/?linkid=821529)
* [Get-WmiObject](https://go.microsoft.com/fwlink/?LinkId=821595)

Normalmente, os cmdlets que dão suporte à comunicação remota sem configuração especial têm um parâmetro ComputerName, e não um parâmetro Session. Para localizar esses cmdlets em sua sessão, digite:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Comunicação remota do Windows PowerShell

A comunicação remota do Windows PowerShell, que usa o protocolo WS-Management, permite executar qualquer comando do Windows PowerShell em um ou vários computadores remotos. Ela permite estabelecer conexões persistentes, iniciar sessões interativas 1:1 e executar scripts em vários computadores.

Para usar a comunicação remota do Windows PowerShell, o computador remoto deve ser configurado para gerenciamento remoto. Para obter mas informações, incluindo instruções consulte [Sobre requisitos remotos](https://technet.microsoft.com/library/dd315349.aspx).

Depois de configurar a comunicação remota do Windows PowerShell, muitas estratégias de comunicação remota estão disponíveis para você. O restante deste documento lista apenas algumas delas. Para obter mais informações, confira [about_Remote](https://technet.microsoft.com/library/dd347744.aspx) e [Perguntas frequentes sobre about_Remote](https://technet.microsoft.com/library/dd347744.aspx).

### <a name="start-an-interactive-session"></a>Iniciar uma sessão interativa

Para iniciar uma sessão interativa com um único computador remoto, use o cmdlet [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477).
Por exemplo, para iniciar uma sessão interativa com o computador remoto Server01, digite:

```powershell
Enter-PSSession Server01
```

O prompt de comando muda para exibir o nome do computador ao qual você está conectado. Daí em diante, os comandos digitados no prompt são executados no computador remoto e os resultados são exibidos no computador local.

Para encerrar a sessão interativa, digite:

```powershell
Exit-PSSession
```

Para saber mais sobre os cmdlets Enter-PSSession e Exit-PSSession, confira [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) e [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).

### <a name="run-a-remote-command"></a>Executar um comando remoto

Para executar qualquer comando em um ou vários computadores remotos, use o cmdlet [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).
Por exemplo, para executar um comando [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) nos computadores remotos Server01 e Server02, digite:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

O resultado é retornado no seu computador.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

Para saber mais sobre o cmdlet Invoke-Command, confira [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="run-a-script"></a>Executar um script

Para executar um script em um ou vários computadores remotos, use o parâmetro FilePath do cmdlet Invoke-Command. O script deve estar ativado ou acessível para o computador local. Os resultados são retornados no computador local.

Por exemplo, o comando a seguir executa o script DiskCollect.ps1 nos computadores remotos Server01 e Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

Para saber mais sobre o cmdlet Invoke-Command, confira [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="establish-a-persistent-connection"></a>Estabelecer uma conexão persistente

Para executar uma série de comandos relacionados que compartilham dados, crie uma sessão no computador remoto e, em seguida, use o cmdlet Invoke-Command para executar comandos na sessão que você criou. Para criar uma sessão remota, use o cmdlet New-PSSession.

Por exemplo, o comando a seguir cria uma sessão remota no computador Server01 e outra sessão remota no computador Server02. Ele salva os objetos da sessão na variável $s.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Agora que as sessões foram estabelecidas, você pode executar qualquer comando nelas. E como as sessões são persistentes, você pode coletar dados em um comando e usá-los em um comando subsequente.

Por exemplo, o comando a seguir executa um comando Get-HotFix em sessões na variável $s e salva os resultados na variável $h. A variável $h é criada em cada uma das sessões em $s, mas não existe na sessão local.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Agora você pode usar os dados na variável $h em comandos subsequentes, como mostrado a seguir. Os resultados são exibidos no computador local.

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Comunicação remota avançada

O gerenciamento remoto do Windows PowerShell começa aqui. Usando os cmdlets instalados com o Windows PowerShell, você pode estabelecer e configurar sessões remotas tanto de extremidades locais quanto remotas, criar sessões personalizadas e restritas, permitir que os usuários importem os comandos de uma sessão remota executado implicitamente na própria sessão remota, configurar a segurança de uma sessão remota e muito mais.

Para facilitar a configuração remota, o Windows PowerShell inclui um provedor WSMan. A unidade WSMAN: criada pelo provedor permite navegar por uma hierarquia de definições de configuração no computador local e nos computadores remotos.
Para saber mais sobre o provedor WSMan, confira [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) e [about_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx) ou, no console do Windows PowerShell, digite "Get-Help wsman".

Para obter mais informações, consulte:

- [Perguntas frequentes sobre comunicação remota](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Para obter ajuda com erros de comunicação remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).

## <a name="see-also"></a>Consulte Também

- [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Provedor WSMan](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md