---
title: Executando comandos remotos
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
---
# Executando comandos remotos
Você pode executar comandos em uma ou centenas de computadores com um único comando do Windows PowerShell. O Windows PowerShell dá suporte à computação remota usando diversas tecnologias, incluindo WMI, RPC e WS-Management.

## Comunicação remota sem configuração
Muitos cmdlets do Windows PowerShell tem um parâmetro ComputerName que permite coletar dados e alterar as configurações remotas de um ou mais computadores. Eles usam uma variedade de tecnologias de comunicação e muitos funcionam em todos os sistemas operacionais Windows que oferecem suporte ao Windows PowerShell sem qualquer configuração especial.

Esses cmdlets incluem:

-   [Restart-Computer](assetId:///bd52bcf6-80ee-4866-9320-04ee1d1dca4a)

-   [Test-Connection](assetId:///87d293e5-10e2-489b-b0a9-922d77c05f3f)

-   [Clear-EventLog](assetId:///05d0de31-3c9d-4cd6-8e1a-dac19835464c)

-   [Get-EventLog [m2]](assetId:///a4372a60-b7d9-4b1c-a268-aa5240300141)

-   [Get-Hotfix](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-Process [m2]](assetId:///27a05dbd-4b69-48a3-8d55-b295f6225f15)

-   [Get-Service [m2]](assetId:///0a09cb22-0a1c-4a79-9851-4e53075f9cf6)

-   [Set-Service [m2]](assetId:///b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

-   [Get-WinEvent](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-WmiObject [m2]](assetId:///a4c499fa-deec-4c4b-b3fb-6e195d48a396)

Normalmente, os cmdlets que oferecem suporte à comunicação remota sem configuração especial possuem um parâmetro ComputerName e não um parâmetro Session. Para localizar esses cmdlets em sua sessão, digite:

```
get-command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## Comunicação remota do Windows PowerShell
A comunicação remota do Windows PowerShell, que usa o protocolo WS-Management, permite executar qualquer comando do Windows PowerShell em um ou vários computadores remotos. Ela permite estabelecer conexões persistentes, iniciar sessões interativas 1:1 e executar scripts em vários computadores.

Para usar a comunicação remota do Windows PowerShell, o computador remoto deve ser configurado para gerenciamento remoto. Para obter mas informações, incluindo instruções consulte [about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd).

Depois de configurar a comunicação remota do Windows PowerShell, muitas estratégias de comunicação remota estão disponíveis para você. O restante deste documento lista apenas algumas delas. Para obter mais informações, consulte [about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970) e [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42).

### Iniciar uma sessão interativa
Para iniciar uma sessão interativa com um único computador remoto, use o cmdlet [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c). Por exemplo, para iniciar uma sessão interativa com o computador remoto Server01, digite:

```
enter-pssession Server01
```

O prompt de comando muda para exibir o nome do computador ao qual você está conectado. Daí em diante, os comandos digitados no prompt são executados no computador remoto e os resultados são exibidos no computador local.

Para encerrar a sessão interativa, digite:

```
exit-pssession
```

Para obter mais informações sobre os cmdlets Enter-PSSession e Exit-PSSession cmdlets, consulte [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c) e [Exit-PSSession](assetId:///b6daa1ce-48a5-41a3-ac4b-b64dbe03465d).

### Executar um comando remoto
Para executar qualquer comando em um ou vários computadores remotos, use o cmdlet [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462). Por exemplo, para executar um comando [Get-UICulture [m2]](assetId:///99175c2e-e856-4208-970e-3dd2f6bac5b8) nos computadores remotos Server01 e Server02, digite:

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

Para obter mais informações sobre o cmdlet Invoke-Command, consulte [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462).

### Executar um script
Para executar um script em um ou vários computadores remotos, use o parâmetro FilePath do cmdlet Invoke-Command. O script deve estar ativado ou acessível para o computador local. Os resultados são retornados no computador local.

Por exemplo, o comando a seguir executa o script DiskCollect.ps1 nos computadores remotos Server01 e Server02.

```
invoke-command -computername Server01, Server02 -filepath c:\Scripts\DiskCollect.ps1
```

Para obter mais informações sobre o cmdlet Invoke-Command, consulte [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462).

### Estabelecer uma conexão persistente
Para executar uma série de comandos relacionados que compartilham dados, crie uma sessão no computador remoto e, em seguida, use o cmdlet Invoke-Command para executar comandos na sessão que você criou. Para criar uma sessão remota, use o cmdlet New-PSSession.

Por exemplo, o comando a seguir cria uma sessão remota no computador Server01 e outra sessão remota no computador Server02. Ele salva os objetos da sessão na variável $s.

```
$s = new-pssession -computername Server01, Server02
```

Agora que as sessões foram estabelecidas, você pode executar qualquer comando nelas. E como as sessões são persistentes, você pode coletar dados em um comando e usá-los em um comando subsequente.

Por exemplo, o comando a seguir executa um comando Get-Hotfix em sessões na variável $s e salva os resultados na variável $h. A variável $h é criada em cada uma das sessões em $s, mas não existe na sessão local.

```
invoke-command -session $s {$h = get-hotfix}
```

Agora você pode usar os dados na variável $h em comandos subsequentes, como mostrado a seguir. Os resultados são exibidos no computador local.

```
invoke-command -session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"
```

### Comunicação remota avançada
O gerenciamento remoto do Windows PowerShell começa aqui. Usando os cmdlets instalados com o Windows PowerShell, você pode estabelecer e configurar sessões remotas tanto de extremidades locais quanto remotas, criar sessões personalizadas e restritas, permitir que os usuários importem os comandos de uma sessão remota executado implicitamente na própria sessão remota, configurar a segurança de uma sessão remota e muito mais.

Para facilitar a configuração remota, o Windows PowerShell inclui um provedor WSMan. A unidade WSMAN: criada pelo provedor permite navegar por uma hierarquia de definições de configuração no computador local e nos computadores remotos. Para obter mais informações sobre o provedor WSMan, consulte [Provedor WSMan](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735) e [about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed), ou então, no console do Windows PowerShell, digite "get-help wsman".

Para obter mais informações, consulte [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42), [Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25) e [Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d). Para obter ajuda com erros de comunicação remota, consulte [about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317).

## Consulte Também
[about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
[about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42)
[about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd)
[about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317)
[about_PSSessions](assetId:///7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
[about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed)
[Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)
[Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
[New-PSSession](assetId:///59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
[Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25)
[Provedor WSMan](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735)



<!--HONumber=Apr16_HO1-->


