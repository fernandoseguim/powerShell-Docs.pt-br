---
title: Obtendo objetos WMI (Get-WmiObject)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
---
# Obtendo objetos WMI (Get-WmiObject)

## Obtendo objetos WMI (Get-WmiObject)
O WMI (Instrumentação de Gerenciamento do Windows) é uma das principais tecnologias para a administração do sistema, pois ela expõe uma grande variedade de informações de maneira uniforme. Devido a quanto o WMI possibilita, o cmdlet do Windows PowerShell para acessar objetos WMI, **Get-WmiObject**, é um dos mais úteis para fazer o trabalho real. Vamos discutir como usar Get-WmiObject para acessar objetos WMI e como usar objetos WMI para fazer coisas específicas.

### Listar classes WMI
O primeiro problema que a maioria dos usuários do WMI encontram é tentar descobrir o que pode ser feito com o WMI. As classes WMI descrevem os recursos que podem ser gerenciados. Há centenas de classes WMI, algumas das quais contêm dezenas de propriedades.

O **Get-WmiObject** cuida desse problema, possibilitando que o WMI possa ser descoberto. Você pode obter uma lista das classes WMI disponíveis no computador local digitando:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Você pode recuperar as mesmas informações de um computador remoto usando o parâmetro ComputerName, especificando um nome do computador ou endereço IP:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

A listagem de classe retornada por computadores remotos pode variar por sistema operacional específico que o computador está executando e as extensões WMI específicas adicionadas por aplicativos instalados.

> [!NOTE]
> Ao usar Get-WmiObject para se conectar a um computador remoto, o computador remoto deve estar executando o WMI e, sob a configuração padrão, a conta que você está usando deve estar no grupo Administradores local no computador remoto. O sistema remoto não precisa ter o Windows PowerShell. instalado. Isso permite administrar sistemas operacionais que não executam o Windows PowerShell, mas que têm WMI disponível.

Você pode até mesmo incluir o ComputerName ao se conectar ao sistema local. Você pode usar o nome do computador local, seu endereço IP (ou o endereço de loopback 127.0.0.1), ou ‘.’ em estilo WMI como o nome do computador. Se você estiver executando o Windows PowerShell em um computador chamado Admin01 com endereço IP 192.168.1.90, os comandos a seguir retornarão a listagem da classe WMI para o computador:

```
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject usa o namespace root/cimv2 por padrão. Se você desejar especificar outro namespace de WMI, use o parâmetro **Namespace** e especifique o caminho do namespace correspondente:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### Exibir detalhes da classe WMI
Se você já souber o nome de uma classe WMI, poderá usá-la para obter informações imediatamente. Por exemplo, uma das classes WMI geralmente usadas para recuperar informações sobre um computador é **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Embora mostremos todos os parâmetros, o comando pode ser expresso de forma mais sucinta. O parâmetro **ComputerName** não é necessário ao se conectar ao sistema local. Vamos mostrá-lo para demonstrar o caso mais geral e lembrá-lo sobre o parâmetro. O **Namespace** assume o padrão de root/cimv2 e também pode ser omitido. Por fim, a maioria dos cmdlets permitem omitir o nome dos parâmetros comuns. Com Get-WmiObject, se nenhum nome for especificado para o primeiro parâmetro, o Windows PowerShell o tratará como o parâmetro **Class**. Isso significa que o último comando pode ter sido emitido digitando:

```
Get-WmiObject Win32_OperatingSystem
```

A classe **Win32_OperatingSystem** tem muitos mais propriedades do que as exibidas aqui. Você pode usar Get-Member para ver todas as propriedades. As propriedades de uma classe WMI ficam automaticamente disponíveis assim como outras propriedades de objeto:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### Exibir propriedades não padrão com cmdlets Format
Se desejar ver as informações contidas na classe **Win32_OperatingSystem** que não são exibidas por padrão, você poderá exibi-las usando os cmdlets **Format**. Por exemplo, se você deseja exibir dados de memória disponível, digite:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMem FreePhysicalMem FreeVirtualMemo FreeSpaceInPagi
                              ory              ry         ngFiles
--------------- --------------- --------------- --------------- ---------------
        2097024          785904          305808         2056724         1558232
```

> [!NOTE]
> Curingas funcionam com nomes de propriedade no **Format-Table**, portanto, o elemento final do pipeline pode ser reduzido para **Format-Table -Property TotalV, *Free***

Os dados da memória podem ficar mais legíveis se você formatá-los como uma lista digitando:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```



<!--HONumber=Apr16_HO1-->


