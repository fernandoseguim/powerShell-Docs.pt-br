---
title: Executando comandos remotos
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
translationtype: Human Translation
ms.sourcegitcommit: 593f0c2ca72e00f19c395c1dae31798d5a5f652d
ms.openlocfilehash: 75d41569b18e61342809eebcc76b7899ec6363fa

---

# Executando comandos remotos
Você pode executar comandos em uma ou centenas de computadores com um único comando do Windows PowerShell. O Windows PowerShell dá suporte à computação remota usando diversas tecnologias, incluindo WMI, RPC e WS\-Management.

## Comunicação remota sem configuração
Muitos cmdlets do Windows PowerShell tem um parâmetro ComputerName que permite coletar dados e alterar as configurações remotas de um ou mais computadores. Eles usam uma variedade de tecnologias de comunicação e muitos funcionam em todos os sistemas operacionais Windows que oferecem suporte ao Windows PowerShell sem qualquer configuração especial.

Esses cmdlets incluem:

-   [Restart-Computer](https://technet.microsoft.com/en-us/library/dd315301.aspx)

-   [Test-Connection](https://technet.microsoft.com/en-us/library/dd315259.aspx)

-   [Clear-EventLog](https://technet.microsoft.com/en-us/library/dd347552.aspx)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/dd315250.aspx)

-   [Get-Hotfix](https://technet.microsoft.com/en-us/library/e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-Process](https://technet.microsoft.com/en-us/library/dd347630.aspx)

-   [Get-Service](https://technet.microsoft.com/en-us/library/dd347591.aspx)

-   [Set-Service](https://technet.microsoft.com/en-us/library/dd315324.aspx)

-   [Get-WinEvent](https://technet.microsoft.com/en-us/library/dd315358.aspx)

-   [Get-WmiObject](https://technet.microsoft.com/en-us/library/dd315295.aspx)

Normalmente, os cmdlets que oferecem suporte à comunicação remota sem configuração especial possuem um parâmetro ComputerName e não um parâmetro Session. Para localizar esses cmdlets em sua sessão, digite:

```
get-command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## Comunicação remota do Windows PowerShell
A comunicação remota do Windows PowerShell, que usa o protocolo WS\-Management, permite executar qualquer comando do Windows PowerShell em um ou vários computadores remotos. Ela permite estabelecer conexões persistentes, iniciar sessões interativas 1:1 e executar scripts em vários computadores.

Para usar a comunicação remota do Windows PowerShell, o computador remoto deve ser configurado para gerenciamento remoto. Para obter mas informações, incluindo instruções consulte [Sobre requisitos remotos](https://technet.microsoft.com/en-us/library/dd315349.aspx).

Depois de configurar a comunicação remota do Windows PowerShell, muitas estratégias de comunicação remota estão disponíveis para você. O restante deste documento lista apenas algumas delas. Para obter mais informações, confira [about_Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) e [Perguntas frequentes sobre about_Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx).

### Iniciar uma sessão interativa
Para iniciar uma sessão interativa com um único computador remoto, use o cmdlet [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx). Por exemplo, para iniciar uma sessão interativa com o computador remoto Server01, digite:

```
enter-pssession Server01
```

O prompt de comando muda para exibir o nome do computador ao qual você está conectado. Daí em diante, os comandos digitados no prompt são executados no computador remoto e os resultados são exibidos no computador local.

Para encerrar a sessão interativa, digite:

```
exit-pssession
```

Para obter mais informações sobre os cmdlets Enter\-PSSession e Exit\-PSSession cmdlets, consulte [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) e [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx).

### Executar um comando remoto
Para executar qualquer comando em um ou vários computadores remotos, use o cmdlet [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).
Por exemplo, para executar um comando [Get-UICulture](https://technet.microsoft.com/en-us/library/dd347742.aspx) nos computadores remotos Server01 e Server02, digite:

```
invoke-command -computername Server01, Server02 {get-UICulture}
```

O resultado é retornado no seu computador.

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

Para obter mais informações sobre o cmdlet Invoke\-Command, consulte [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462).

### Executar um script
Para executar um script em um ou vários computadores remotos, use o parâmetro FilePath do cmdlet Invoke\-Command. O script deve estar ativado ou acessível para o computador local. Os resultados são retornados no computador local.

Por exemplo, o comando a seguir executa o script DiskCollect.ps1 nos computadores remotos Server01 e Server02.

```
invoke-command -computername Server01, Server02 -filepath c:\Scripts\DiskCollect.ps1
```

Para obter mais informações sobre o cmdlet Invoke\-Command, consulte [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).

### Estabelecer uma conexão persistente
Para executar uma série de comandos relacionados que compartilham dados, crie uma sessão no computador remoto e, em seguida, use o cmdlet Invoke\-Command para executar comandos na sessão que você criou. Para criar uma sessão remota, use o cmdlet New\-PSSession.

Por exemplo, o comando a seguir cria uma sessão remota no computador Server01 e outra sessão remota no computador Server02. Ele salva os objetos da sessão na variável $s.

```
$s = new-pssession -computername Server01, Server02
```

Agora que as sessões foram estabelecidas, você pode executar qualquer comando nelas. E como as sessões são persistentes, você pode coletar dados em um comando e usá-los em um comando subsequente.

Por exemplo, o comando a seguir executa um comando Get\-Hotfix em sessões na variável $s e salva os resultados na variável $h. A variável $h é criada em cada uma das sessões em $s, mas não existe na sessão local.

```
invoke-command -session $s {$h = get-hotfix}
```

Agora você pode usar os dados na variável $h em comandos subsequentes, como mostrado a seguir. Os resultados são exibidos no computador local.

```
invoke-command -session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"} }
```

### Comunicação remota avançada
O gerenciamento remoto do Windows PowerShell começa aqui. Usando os cmdlets instalados com o Windows PowerShell, você pode estabelecer e configurar sessões remotas tanto de extremidades locais quanto remotas, criar sessões personalizadas e restritas, permitir que os usuários importem os comandos de uma sessão remota executado implicitamente na própria sessão remota, configurar a segurança de uma sessão remota e muito mais.

Para facilitar a configuração remota, o Windows PowerShell inclui um provedor WSMan. A unidade WSMAN: criada pelo provedor permite navegar por uma hierarquia de definições de configuração no computador local e nos computadores remotos.
Para saber mais sobre o provedor WSMan, confira [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) e   [about-WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx) ou, no console do Windows PowerShell, digite "get\-help wsman".

Para obter mais informações, consulte:
- [Perguntas frequentes sobre comunicação remota](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/dd819496.aspx)
- [Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx). 

Para obter ajuda com erros de comunicação remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).

## Consulte Também
- [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
- [Import-PSSession](https://technet.microsoft.com/en-us/library/048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
- [New-PSSession](https://technet.microsoft.com/en-us/library/59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
- [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/af68867a-d201-4b19-a1de-594015ed8a25)
- [Provedor WSMan](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)




<!--HONumber=Jun16_HO4-->


