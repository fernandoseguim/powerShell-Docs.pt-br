---
title: Gerenciando processos com os Cmdlets de processo
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 6857cf5e73252f646e563fa12a8252b4bdc2e1e5

---

# Gerenciando processos com os Cmdlets de processo
Você pode usar os cmdlets de processo do Windows PowerShell para gerenciar processos locais e remotos no Windows PowerShell.

## Obtendo processos (Get\-Process)
Para obter os processos em execução no computador local, execute um **Get\-Process** sem parâmetros.

Você pode obter processos específicos definindo seus nomes de processo ou IDs de processo. O comando a seguir obtém o processo Idle:

```
PS> Get-Process -id 0
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Embora seja normal que os cmdlets não retornem dados em algumas situações, quando você especificar um processo por seu ProcessId, **Get\-Process** gerará um erro se ele não encontrar correspondências, pois o objetivo comum é recuperar um processo em execução conhecido. Caso não haja nenhum processo com essa ID, é provável que a ID esteja incorreta ou que o processo do seu interesse já tenha terminado:

```
PS> Get-Process -Id 99
Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Você pode usar o parâmetro Name do cmdlet Get\-Process para especificar um subconjunto de processos com base no nome do processo. O parâmetro Name pode ter vários nomes em uma lista separada por vírgula e dá suporte ao uso de curingas para que você possa digitar padrões de nome.

Por exemplo, o comando a seguir obtém o processo cujos nomes começam com "ex".

```
PS> Get-Process -Name ex*
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Como a classe .NET System.Diagnostics.Process é a base de processos do Windows PowerShell, ele segue algumas as convenções usadas pelo System.Diagnostics.Process. Uma dessas convenções é que o nome do processo para um executável nunca inclui ".exe" ao final do nome do executável.

**Get\-Process** também aceita vários valores para o parâmetro Name.

```
PS> Get-Process -Name exp*,power* 
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Você pode usar o parâmetro ComputerName de Get\-Process para obter os processos em computadores remotos. Por exemplo, o comando a seguir obtém os processos do PowerShell no computador local (representado por "localhost") e em dois computadores remotos.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Os nomes de computador não são evidentes nessa exibição, mas são armazenados na propriedade MachineName dos objetos de processo retornados por Get\-Process. O comando a seguir usa o cmdlet Format\-Table para exibir a ID do processo, as propriedades ProcessName e MachineName (ComputerName) dos objetos de processo.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName
  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Esse comando mais complexo adiciona a propriedade MachineName à exibição padrão de Get\-Process. O acento grave (\`)(ASCII 96) é o caractere de continuação do Windows PowerShell.

```
get-process powershell -computername localhost, Server01, Server02 | format-table -property Handles, `
                    @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}}, `
                    @{Label="PM(K)";Expression={[int]($_.PM/1024)}}, `
                    @{Label="WS(K)";Expression={[int]($_.WS/1024)}}, `
                    @{Label="VM(M)";Expression={[int]($_.VM/1MB)}}, `
                    @{Label="CPU(s)";Expression={if ($_.CPU -ne $()` 
                    {$_.CPU.ToString("N")}}}, `                                                                         
                    Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## Interrompendo processos (Stop\-Process)
O Windows PowerShell oferece flexibilidade para listar processos, mas como podemos interromper um processo?

O cmdlet **Stop\-Process** usa um Nome ou uma ID para especificar um processo que você deseja interromper. A capacidade de parar os processos depende das suas permissões. Alguns processos não podem ser interrompidos. Por exemplo, se você tentar interromper o processo ocioso, você receberá um erro:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

Você também pode forçar um prompt com o parâmetro **Confirm**. Esse parâmetro será especialmente útil se você usar um caractere curinga ao especificar o nome do processo, pois você poderá corresponder acidentalmente alguns processos que não deseja interromper:

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

A manipulação complexa de processos é possível usando alguns cmdlets de filtragem de objetos. Como um objeto Process tem uma propriedade Responding que é verdadeira quando ele não está respondendo, você pode interromper todos os aplicativos sem resposta com o seguinte comando:

```
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

Você pode usar a mesma abordagem em outras situações. Por exemplo, suponha que um aplicativo de área de notificação secundário é executado automaticamente quando os usuários iniciam o outro aplicativo. Você pode achar que isso não funciona corretamente em sessões de Serviços de Terminal, mas você ainda deseja mantê-lo em sessões que são executadas no console do computador físico. Sessões conectadas à área de trabalho do computador físico sempre têm uma ID de sessão 0 e, portanto, é possível interromper todas as instâncias do processo que estão em outras sessões usando **Where\-Object** e o processo, com **SessionId**:

```
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

O cmdlet Stop\-Process não tem um parâmetro ComputerName. Portanto, para executar um comando de interrupção do processo em um computador remoto, é necessário usar o cmdlet Invoke\-Command. Por exemplo, para parar o processo do PowerShell no computador remoto Server01, digite:

```
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## Parar todas as outras sessões do Windows PowerShell
Ocasionalmente, pode ser útil poder parar a execução de todas as sessões do Windows PowerShell que não sejam a sessão atual. Se uma sessão usar muitos recursos ou estiver inacessível (ela pode estar em execução remotamente ou em outra sessão de área de trabalho), poderá não ser possível pará-la diretamente. Se você tentar interromper todas as sessões, no entanto, a sessão atual talvez seja encerrada.

Cada sessão do Windows PowerShell tem uma variável de ambiente PID que contém a ID do processo do Windows PowerShell. Você pode verificar o $PID com a ID de cada sessão e encerrar somente sessões do Windows PowerShell que têm uma ID diferente. O comando de pipeline a seguir faz isso e retorna a lista de sessões finalizadas (devido ao uso do parâmetro **PassThru**):

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -
PassThru
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## Iniciando, depuração e aguardando a processos
O Windows PowerShell também inclui cmdlets para iniciar (ou reiniciar), depurar um processo e aguardar a conclusão de um processo antes de executar um comando. Para obter informações sobre esses cmdlets, consulte o tópico de Ajuda do cmdlet para cada cmdlet.

## Consulte Também
[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
[Start-Process](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
[Wait-Process](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
[Debug-Process](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
[Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)




<!--HONumber=Jun16_HO4-->


