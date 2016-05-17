---
title:  Coletando informações sobre computadores
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
---

# Coletando informações sobre computadores
**Get-WmiObject** é o cmdlet mais importante para as tarefas gerais de gerenciamento do sistema. Todas as configurações do subsistema críticas são expostas por meio do WMI. Além disso, o WMI trata dados como objetos que são coleções de um ou mais itens. Como o Windows PowerShell também funciona com objetos e tem um pipeline que permite tratar objetos únicos ou vários objetos da mesma forma, o acesso ao WMI genérico permite executar algumas tarefas avançadas com pouquíssimo trabalho.

Os exemplos a seguir demonstram como coletar informações específicas usando **Get-WmiObject** em um computador arbitrário. Especificamos o parâmetro **ComputerName** com o valor de ponto (**.**), que representa o computador local. É possível especificar um nome ou endereço IP associado a qualquer computador que você pode acessar por meio do WMI. Para recuperar as informações sobre o computador local, você pode omitir o **-ComputerName.**

### Listar Configurações de Área de Trabalho
Vamos começar com um comando que coleta informações sobre as áreas de trabalho no computador local.

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

Isso retorna informações para todos os desktops, independentemente de estarem em uso ou não.

> [!NOTE]
> Informações retornadas por algumas classes WMI podem ser muito detalhadas e geralmente incluem metadados sobre a classe WMI. Como a maioria dessas propriedades de metadados têm nomes que começam com um sublinhado duplo, você pode filtrar as propriedades usando Select-Object. Especifique apenas as propriedades que começam com caracteres alfabéticos usando **[a-z]&42;** como o valor da propriedade. Por exemplo:

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

Para filtrar os metadados, use um operador de pipeline (|) para enviar os resultados do comando Get-WmiObject para **Select-Object -Property [a-z]&#42;**.

### Listando informações de BIOS
A classe WMI Win32_BIOS retorna informações bastante compactas e completas sobre a BIOS do sistema no computador local:

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### Listar informações do processador
Você pode recuperar informações gerais do processador por meio da classe **Win32_Processor** do WMI, embora provavelmente seja recomendável filtrar as informações:

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

Para ver uma cadeia de caracteres de descrição genérica da família do processador, você pode simplesmente retornar a propriedade **Win32_ComputerSystemSystemType**:

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### Listar o modelo e o fabricante do computador
As informações de modelo do computador também estão disponíveis no **Win32_ComputerSystem**. A saída padrão exibida não precisará de filtragem para fornecer dados de OEM:

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

A saída de comandos como este, que retornam informações diretamente de alguns dispositivos de hardware, é válida na mesma medida que os dados que você tem. Algumas informações não são configuradas corretamente pelos fabricantes de hardware e, portanto, podem estar indisponíveis.

### Listar os hotfixes instalados
Você pode listar os hotfixes instalados usando **Win32_QuickFixEngineering**:

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

Essa classe retorna uma lista de hotfixes que tem esta aparência:

```
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

Para uma saída mais sucinta, pode ser útil excluir algumas propriedades. Embora você possa usar o parâmetro **Get-WmiObject Property** para escolher somente a **HotFixID**, fazer isso na verdade retornará mais informações, pois todos os metadados são exibido por padrão:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId
HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

Os dados adicionais são retornados porque o parâmetro Property no **Get-WmiObject** restringe as propriedades retornadas de instâncias da classe WMI, não o objeto retornado para o Windows PowerShell. Para reduzir a saída, use **Select-Object**:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### Listar informações de versão do sistema operacional
As propriedades da classe **Win32_OperatingSystem** incluem informações sobre versão e service pack. Você pode selecionar apenas essas propriedades para obter um resumo das informações de versão de **Win32_OperatingSystem**:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Você também pode usar caracteres curinga com o parâmetro **Select-Object Property**. Como todas as propriedades que começam com **Build** ou **ServicePack** são importantes para usar aqui, podemos reduzir isso para a seguinte forma:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### Listar proprietário e usuários locais
Informações gerais de usuário local (número de usuários licenciados, número de usuários atuais e nome do proprietário) podem ser encontradas com uma seleção das propriedades de **Win32_OperatingSystem**. Você pode selecionar as propriedades a serem exibidas desta forma:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Uma versão mais sucinta usando caracteres curinga seria:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### Obter o espaço em disco disponível
Para ver o espaço em disco e o espaço livre para as unidades locais, você pode usar a classe WMI Win32_LogicalDisk. Você precisa ver apenas as instâncias com DriveType 3, o valor que o WMI usa para discos rígidos fixos.

```
Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### Obter informações de sessão de logon
Você pode obter informações gerais sobre as sessões de logon associadas aos usuários por meio da classe WMI Win32_LogonSession:

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### Obter o usuário conectado a um computador
Você pode exibir o usuário conectado a um sistema de computador específico usando Win32_ComputerSystem. Esse comando retorna somente o usuário conectado à área de trabalho do sistema:

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### Obter a hora local de um computador
Você pode recuperar a hora local atual em um computador específico usando a classe WMI Win32_LocalTime. Como essa classe exibe por padrão todos os metadados, pode ser útil filtrá-los usando **Select-Object**:

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### Exibir o status do serviço
Para exibir o status de todos os serviços em um computador específico, você pode usar localmente o cmdlet **Get-Service** conforme mencionado anteriormente. Para sistemas remotos, você pode usar a classe WMI Win32_Service. Se você também usar **Select-Object** para filtrar os resultados para **Status**, **Name** e **DisplayName**, o formato de saída será praticamente idêntico ao do **Get-Service**:

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Para permitir a exibição completa de nomes para os serviços ocasionais com nomes muito longos, pode ser útil usar **Format-Table** com os parâmetros **AutoSize** e **Wrap** para otimizar a largura da coluna e permitir o encapsulamento de nomes longos em vez do truncamento:

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```



<!--HONumber=May16_HO2-->


