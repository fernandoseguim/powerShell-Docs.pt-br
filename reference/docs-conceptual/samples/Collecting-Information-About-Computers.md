---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Coletando informações sobre computadores
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: 99125ef701705c20d4e955c79eaa3469ce4d58fb
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400156"
---
# <a name="collecting-information-about-computers"></a>Coletando informações sobre computadores

Os cmdlets do módulo **CimCmdlets** são os cmdlets mais importantes para tarefas de gerenciamento geral do sistema.
Todas as configurações do subsistema críticas são expostas por meio do WMI.
Além disso, o WMI trata dados como objetos que são coleções de um ou mais itens.
Como o Windows PowerShell também funciona com objetos e tem um pipeline que permite tratar objetos únicos ou vários objetos da mesma forma, o acesso ao WMI genérico permite executar algumas tarefas avançadas com pouquíssimo trabalho.

Os exemplos a seguir demonstram como coletar informações específicas usando `Get-CimInstance` em um computador arbitrário.
Especificamos o parâmetro **ComputerName** com o valor de ponto (**.**), que representa o computador local.
É possível especificar um nome ou endereço IP associado a qualquer computador que você pode acessar por meio do WMI.
Para recuperar as informações sobre o computador local, você pode omitir o parâmetro **ComputerName**.

### <a name="listing-desktop-settings"></a>Listar Configurações de Área de Trabalho

Vamos começar com um comando que coleta informações sobre as áreas de trabalho no computador local.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Isso retorna informações para todos os desktops, independentemente de estarem em uso ou não.

> [!NOTE]
> Informações retornadas por algumas classes WMI podem ser muito detalhadas e geralmente incluem metadados sobre a classe WMI.
Como a maioria dessas propriedades de metadados tem nomes que começam com **Cim**, é possível filtrar as propriedades usando `Select-Object`.
Especifique o parâmetro **-ExcludeProperty** com "Cim*" como o valor.
Por exemplo:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Para filtrar os metadados, use um operador de pipeline (|) para enviar os resultados do comando `Get-CimInstance` para `Select-Object -ExcludeProperty "CIM*"`.

### <a name="listing-bios-information"></a>Listando informações de BIOS

A classe WMI **Win32_BIOS** retorna informações bastante compactas e completas sobre o BIOS do sistema no computador local:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Listar informações do processador

Você pode recuperar informações gerais do processador por meio da classe **Win32_Processor** do WMI, embora provavelmente você preferirá filtrar as informações:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Para ver uma cadeia de caracteres de descrição genérica da família do processador, basta retornar a propriedade **SystemType**:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Listar o modelo e o fabricante do computador

As informações de modelo do computador também estão disponíveis no **Win32_ComputerSystem**.
A saída padrão exibida não precisará de filtragem para fornecer dados de OEM:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

A saída de comandos como este, que retornam informações diretamente de alguns dispositivos de hardware, é válida na mesma medida que os dados que você tem.
Algumas informações não são configuradas corretamente pelos fabricantes de hardware e, portanto, podem estar indisponíveis.

### <a name="listing-installed-hotfixes"></a>Listar os hotfixes instalados

Você pode listar os hotfixes instalados usando **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Essa classe retorna uma lista de hotfixes que tem esta aparência:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Para uma saída mais sucinta, pode ser útil excluir algumas propriedades.
Embora você possa usar o parâmetro **Property** de `Get-CimInstance` para escolher somente a **HotFixID**, fazer isso, na verdade, retornará mais informações, pois todos os metadados são exibidos por padrão:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Os dados adicionais são retornados, pois o parâmetro Property no `Get-CimInstance` restringe as propriedades retornadas de instâncias da classe WMI, não o objeto retornado para o Windows PowerShell.
Para reduzir a saída, use `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a>Listar informações de versão do sistema operacional

As propriedades da classe **Win32_OperatingSystem** incluem informações sobre versão e service pack.
Você pode selecionar apenas essas propriedades para obter um resumo das informações de versão de **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Você também pode usar caracteres curinga com o parâmetro **Property** de `Select-Object`.
Como todas as propriedades que começam com **Build** ou **ServicePack** são importantes para usar aqui, podemos reduzir isso para a seguinte forma:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Listar proprietário e usuários locais

Informações gerais de usuário local – o número de usuários licenciados, número de usuários atuais e nome do proprietário – podem ser encontradas com uma seleção das propriedades da classe **Win32_OperatingSystem**.
Você pode selecionar as propriedades a serem exibidas desta forma:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Uma versão mais sucinta usando caracteres curinga seria:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Obter o espaço em disco disponível

Para ver o espaço em disco e o espaço livre para as unidades locais, você pode usar a classe WMI Win32_LogicalDisk.
Você precisa ver apenas as instâncias com um DriveType de 3 – o valor que o WMI usa para discos rígidos fixos.

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a>Obter informações de sessão de logon

Você pode obter informações gerais sobre as sessões de logon associadas aos usuários por meio da classe WMI **Win32_LogonSession**:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Obter o usuário conectado a um computador

Você pode exibir o usuário conectado a um sistema de computador específico usando Win32_ComputerSystem.
Esse comando retorna somente o usuário conectado à área de trabalho do sistema:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Obter a hora local de um computador

Você pode recuperar a hora local atual em um computador específico usando a classe WMI **Win32_LocalTime**.

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

### <a name="displaying-service-status"></a>Exibir o status do serviço

Para exibir o status de todos os serviços em um computador específico, você pode usar o cmdlet `Get-Service` localmente.
Para sistemas remotos, você pode usar a classe WMI **Win32_Service**.
Se você também usar `Select-Object` para filtrar os resultados para **Status**, **Nome** e **DisplayName**, o formato de saída será praticamente idêntico ao de `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Para permitir a exibição completa de nomes para os serviços ocasionais com nomes muito longos, pode ser útil usar `Format-Table` com os parâmetros **AutoSize** e **Wrap** para otimizar a largura da coluna e permitir o encapsulamento de nomes longos em vez do truncamento:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
