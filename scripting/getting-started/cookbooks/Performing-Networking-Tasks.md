---
title: Executando tarefas de rede
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 6d878b89a4cd49948cb465525e74e92db819c192

---

# Executando tarefas de rede
Como TCP\/IP é o protocolo de rede mais usado em geral, a maioria das tarefas de administração de protocolo de rede de baixo nível envolvem TCP\/IP. Nesta seção, usamos o Windows PowerShell e o WMI para realizar essas tarefas.

### Listando de endereços IP para um computador
Para obter todos os endereços IP em uso no computador local, use o seguinte comando:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Format-Table -Property IPAddress
```

A saída desse comando é diferente da maioria das listas de propriedades, porque os valores são colocados entre chaves:

<pre>IPAddress
---------
{192.168.1.80} {192.168.148.1} {192.168.171.1} {0.0.0.0}</pre>

Para entender por que as chaves são exibidas, use o cmdlet Get\-Member para examinar a propriedade **IPAddress**:

<pre>PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Get-Member -Name IPAddress TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapter Configuration Name      MemberType Definition ----      ---------- ---------- IPAddress Property   System.String[] IPAddress {get;}</pre>

A propriedade IPAddress para cada adaptador de rede na verdade é uma matriz. As chaves na definição indicam que **IPAddress** não é um valor de **System.String**, mas sim uma matriz de valores **System.String**.

### Listando dados de configuração de IP
Para exibir dados detalhados de configuração de IP de cada adaptador de rede, use o seguinte comando:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName .
```

A exibição padrão para o objeto de configuração do adaptador de rede é um conjunto muito reduzido das informações disponíveis. Para obter uma inspeção e solução de problemas profundas, use Select\-Object ou um cmdlet de formatação, como Format\-List, para especificar as propriedades a serem exibidas.

Se você não estiver interessado nas propriedades IPX ou WINS – que provavelmente será o caso em uma rede TCP\/IP moderna –, poderá usar o parâmetro ExcludeProperty de Select\-Object para ocultar propriedades com nomes que começam com “WINS” ou “IPX”:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Esse comando retorna informações detalhadas sobre o DHCP, DNS, roteamento e outras propriedades de configuração de IP secundárias.

### Executando ping em computadores
Você pode executar um ping simples em um computador usando **Win32\_PingStatus**. O comando a seguir executa o ping, mas retorna uma saída longa:

```
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Uma forma mais útil de resumir as informações é exibir as propriedades Address, ResponseTime e StatusCode geradas pelo comando a seguir. O parâmetro Autosize de Format\-Table redimensiona as colunas da tabela para que elas sejam exibidas corretamente no Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
A status code of 0 indicates a successful ping.
```

Você pode usar uma matriz para executar o ping de vários computadores com um único comando. Como há mais de um endereço, use **ForEach\-Object** para executar ping em cada endereço separadamente:

```
"127.0.0.1","localhost","research.microsoft.com" | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Você pode usar o mesmo formato de comando para executar o ping de todos os computadores em uma sub-rede, como uma rede privada que usa o número da rede 192.168.1.0 e uma máscara de sub-rede de classe C padrão (255.255.255.0)., somente os endereços no intervalo de 192.168.1.1 a 192.168.1.254 são endereços locais legítimos (0 é sempre reservado para o número da rede e 255 é um endereço de difusão de sub-rede).

Para representar uma matriz de números de 1 a 254 no Windows PowerShell, use a instrução **1..254.** Um ping de sub-rede completa pode ser executado, gerando a matriz e adicionando os valores a um endereço parcial na instrução do ping:

```
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Observe que essa técnica para a geração de um intervalo de endereços também pode ser usada em outro local. Você pode gerar um conjunto completo de endereços dessa forma:

`$ips = 1..254 | ForEach-Object -Process {"192.168.1." + $_}`

### Recuperando propriedades do adaptador de rede
Mencionamos anteriormente neste guia do usuário que é possível recuperar propriedades de configuração geral usando **Win32\_NetworkAdapterConfiguration**. Embora não sejam estritamente informações de TCP/\/IP, informações do adaptador de rede, como endereços MAC e tipos de adaptador, podem ser úteis para entender o que está acontecendo com um computador. Para obter um resumo dessas informações, use o seguinte comando:

```
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### Atribuindo o domínio DNS a um adaptador de rede
Para atribuir o domínio DNS à resolução de nomes automática, use o método **Win32\_NetworkAdapterConfiguration SetDNSDomain**. Como você atribui o domínio DNS a cada configuração de adaptador de rede de modo independente, é necessário usar uma instrução **ForEach\-Object** para atribuir o domínio a cada adaptador:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain("fabrikam.com") }
```

A instrução de filtragem “IPEnabled\=true” é necessária porque, mesmo em uma rede que usa apenas TCP/\/IP, várias das configurações de adaptador de rede em um computador não são adaptadores reais de TCP/\/IP; eles são elementos de software geral com suporte a RAS, PPTP, QoS e outros serviços para todos os adaptadores, não tendo assim um endereço próprio.

É possível filtrar o comando usando o cmdlet **Where\-Object** em vez de usar o filtro **Get\-WmiObject**.

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain("fabrikam.com")}
```

### Executar tarefas de configuração de DHCP
Modificar os detalhes de DHCP envolve trabalhar com um conjunto de adaptadores de rede, assim como na configuração do DNS. Existem várias ações diferentes que você pode executar usando o WMI, e abordaremos algumas delas.

#### Determinando os adaptadores habilitados para DHCP
Para encontrar os adaptadores habilitados para DHCP em um computador, use o seguinte comando:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName .
```

Para excluir adaptadores com problemas de configuração de IP, é possível recuperar apenas adaptadores habilitados para IP:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName .
```

#### Recuperando propriedades de DHCP
Como as propriedades relacionadas a DHCP de um adaptador geralmente começam com “DHCP”, é possível usar o parâmetro Property de Format\-Table para exibir somente essas propriedades:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName . | Format-Table -Property DHCP*
```

#### Habilitando o DHCP em cada adaptador
Para habilitar o DHCP em todos os adaptadores, use o seguinte comando:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

É possível usar a instrução **Filter** “IPEnabled\=true” e “DHCPEnabled\=false” para evitar habilitar o DHCP nos locais em que ele já estiver habilitado, porém, omitir essa etapa não causará erros.

#### Liberar e renovar concessões de DHCP nos adaptadores específicos
A classe **Win32\_NetworkAdapterConfiguration** tem os métodos **ReleaseDHCPLease** e **RenewDHCPLease**. Ambos são usados da mesma maneira. Em geral, use esses métodos se você só precisar liberar ou renovar endereços para um adaptador em uma sub-rede específica. A maneira mais fácil de filtrar os adaptadores em uma sub-rede é escolher apenas as configurações de adaptador que usam o gateway para essa sub-rede. Por exemplo, o comando a seguir libera todas as concessões DHCP nos adaptadores no computador local que estão obtendo concessões de DHCP do 192.168.1.254:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

A única alteração para renovar uma concessão de DHCP é usar o método **RenewDHCPLease** em vez do **ReleaseDHCPLease**:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Ao usar esses métodos em um computador remoto, lembre-se de que você poderá perder o acesso ao sistema remoto se estiver conectado a ele por meio do adaptador com a concessão liberada ou renovada.

#### Liberar e renovar concessões de DHCP em todos os adaptadores
É possível executar liberações ou renovações de endereço DHCP globais em todos os adaptadores usando os métodos **Win32\_NetworkAdapterConfiguration**, **ReleaseDHCPLeaseAll** e **RenewDHCPLeaseAll**. No entanto, o comando deve ser aplicado à classe WMI, em vez de um adaptador específico, pois liberações e renovações de concessões globais são executada na classe, não em um adaptador específico.

Você pode obter uma referência a uma classe WMI, em vez de instâncias de classe, listando todas as classes WMI e selecionando somente a classe desejada por nome. Por exemplo, o comando a seguir retorna a classe Win32\_NetworkAdapterConfiguration:

```
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"}
```

Você pode tratar o comando inteiro como a classe e, em seguida, invocar o método **ReleaseDHCPAdapterLease**. No comando a seguir, os parênteses em torno dos elementos de pipeline **Get\-WmiObject** e **Where\-Object** direcionam o Windows PowerShell para avaliá-los primeiro:

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).ReleaseDHCPLeaseAll()
```

Você pode usar o mesmo formato de comando para invocar o método **RenewDHCPLeaseAll**:

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).RenewDHCPLeaseAll()
```

### Criando um compartilhamento de rede
Para criar um compartilhamento de rede, use o método **Win32\_Share Create**:

```
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Win32_Share"}).Create("C:\temp","TempShare",0,25,"test share of the temp folder")
```

Você também pode criar o compartilhamento usando **net share** no Windows PowerShell:

```
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### Removendo um compartilhamento de rede
É possível remover um compartilhamento de rede com **Win32\_Share**, mas o processo é ligeiramente diferente da criação de um compartilhamento, pois você precisa recuperar o compartilhamento específico a ser removido em vez da classe **Win32\_Share**. A instrução a seguir exclui o compartilhamento "TempShare":

```
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Net share** também funciona:

```
PS> net share tempshare /delete
tempshare was deleted successfully.
```

### Conectando-se a uma unidade de rede acessível do Windows
Os novos cmdlets **New\-PSDrive** criam uma unidade do Windows PowerShell, porém, as unidades criadas dessa forma estão disponíveis somente para o Windows PowerShell. Para criar uma nova unidade em rede, você pode usar o objeto COM **WScript.Network**. O comando a seguir mapeia o compartilhamento \\\\FPS01\\users para a unidade B local:

```
(New-Object -ComObject WScript.Network).MapNetworkDrive("B:", "\\FPS01\users")
```

O comando **net use** também funciona:

```
net use B: \\FPS01\users
```

Unidades mapeadas com um **WScript.Network** ou net use ficam disponíveis imediatamente para o Windows PowerShell.




<!--HONumber=Jun16_HO4-->


