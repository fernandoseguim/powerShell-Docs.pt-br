---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Obtendo objetos WMI Get WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 67922426ae3f13ef5f4c70bc70bb3ce1594d3d05
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="f7abf-103">Obtendo objetos WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="f7abf-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="f7abf-104">Obtendo objetos WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="f7abf-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="f7abf-105">O WMI (Instrumentação de Gerenciamento do Windows) é uma das principais tecnologias para a administração do sistema, pois ela expõe uma grande variedade de informações de maneira uniforme.</span><span class="sxs-lookup"><span data-stu-id="f7abf-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="f7abf-106">Devido a quanto o WMI possibilita, o cmdlet do Windows PowerShell para acessar objetos WMI, **Get-WmiObject**, é um dos mais úteis para fazer o trabalho real.</span><span class="sxs-lookup"><span data-stu-id="f7abf-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="f7abf-107">Vamos discutir como usar Get-WmiObject para acessar objetos WMI e como usar objetos WMI para fazer coisas específicas.</span><span class="sxs-lookup"><span data-stu-id="f7abf-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="f7abf-108">Listar classes WMI</span><span class="sxs-lookup"><span data-stu-id="f7abf-108">Listing WMI Classes</span></span>

<span data-ttu-id="f7abf-109">O primeiro problema que a maioria dos usuários do WMI encontram é tentar descobrir o que pode ser feito com o WMI.</span><span class="sxs-lookup"><span data-stu-id="f7abf-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="f7abf-110">As classes WMI descrevem os recursos que podem ser gerenciados.</span><span class="sxs-lookup"><span data-stu-id="f7abf-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="f7abf-111">Há centenas de classes WMI, algumas das quais contêm dezenas de propriedades.</span><span class="sxs-lookup"><span data-stu-id="f7abf-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="f7abf-112">O **Get-WmiObject** cuida desse problema, possibilitando que o WMI possa ser descoberto.</span><span class="sxs-lookup"><span data-stu-id="f7abf-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="f7abf-113">Você pode obter uma lista das classes WMI disponíveis no computador local digitando:</span><span class="sxs-lookup"><span data-stu-id="f7abf-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="f7abf-114">Você pode recuperar as mesmas informações de um computador remoto usando o parâmetro ComputerName, especificando um nome do computador ou endereço IP:</span><span class="sxs-lookup"><span data-stu-id="f7abf-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="f7abf-115">A listagem de classe retornada por computadores remotos pode variar por sistema operacional específico que o computador está executando e as extensões WMI específicas adicionadas por aplicativos instalados.</span><span class="sxs-lookup"><span data-stu-id="f7abf-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="f7abf-116">Ao usar Get-WmiObject para se conectar a um computador remoto, o computador remoto deve estar executando o WMI e, sob a configuração padrão, a conta que você está usando deve estar no grupo Administradores local no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="f7abf-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="f7abf-117">O sistema remoto não precisa ter o Windows PowerShell. instalado.</span><span class="sxs-lookup"><span data-stu-id="f7abf-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="f7abf-118">Isso permite administrar sistemas operacionais que não executam o Windows PowerShell, mas que têm WMI disponível.</span><span class="sxs-lookup"><span data-stu-id="f7abf-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="f7abf-119">Você pode até mesmo incluir o ComputerName ao se conectar ao sistema local.</span><span class="sxs-lookup"><span data-stu-id="f7abf-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="f7abf-120">Você pode usar o nome do computador local, seu endereço IP (ou o endereço de loopback 127.0.0.1) ou '.' em estilo WMI como o nome do computador.</span><span class="sxs-lookup"><span data-stu-id="f7abf-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="f7abf-121">Se você estiver executando o Windows PowerShell em um computador chamado Admin01 com endereço IP 192.168.1.90, os comandos a seguir retornarão a listagem da classe WMI para o computador:</span><span class="sxs-lookup"><span data-stu-id="f7abf-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="f7abf-122">Get-WmiObject usa o namespace root/cimv2 por padrão.</span><span class="sxs-lookup"><span data-stu-id="f7abf-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="f7abf-123">Se você desejar especificar outro namespace de WMI, use o parâmetro **Namespace** e especifique o caminho do namespace correspondente:</span><span class="sxs-lookup"><span data-stu-id="f7abf-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="f7abf-124">Exibir detalhes da classe WMI</span><span class="sxs-lookup"><span data-stu-id="f7abf-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="f7abf-125">Se você já souber o nome de uma classe WMI, poderá usá-la para obter informações imediatamente.</span><span class="sxs-lookup"><span data-stu-id="f7abf-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="f7abf-126">Por exemplo, uma das classes WMI geralmente usadas para recuperar informações sobre um computador é **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="f7abf-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="f7abf-127">Embora mostremos todos os parâmetros, o comando pode ser expresso de forma mais sucinta.</span><span class="sxs-lookup"><span data-stu-id="f7abf-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="f7abf-128">O parâmetro **ComputerName** não é necessário ao se conectar ao sistema local.</span><span class="sxs-lookup"><span data-stu-id="f7abf-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="f7abf-129">Vamos mostrá-lo para demonstrar o caso mais geral e lembrá-lo sobre o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f7abf-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="f7abf-130">O **Namespace** assume o padrão de root/cimv2 e também pode ser omitido.</span><span class="sxs-lookup"><span data-stu-id="f7abf-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="f7abf-131">Por fim, a maioria dos cmdlets permitem omitir o nome dos parâmetros comuns.</span><span class="sxs-lookup"><span data-stu-id="f7abf-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="f7abf-132">Com Get-WmiObject, se nenhum nome for especificado para o primeiro parâmetro, o Windows PowerShell o tratará como o parâmetro **Class**.</span><span class="sxs-lookup"><span data-stu-id="f7abf-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="f7abf-133">Isso significa que o último comando pode ter sido emitido digitando:</span><span class="sxs-lookup"><span data-stu-id="f7abf-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="f7abf-134">A classe **Win32_OperatingSystem** tem muitos mais propriedades do que as exibidas aqui.</span><span class="sxs-lookup"><span data-stu-id="f7abf-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="f7abf-135">Você pode usar Get-Member para ver todas as propriedades.</span><span class="sxs-lookup"><span data-stu-id="f7abf-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="f7abf-136">As propriedades de uma classe WMI ficam automaticamente disponíveis assim como outras propriedades de objeto:</span><span class="sxs-lookup"><span data-stu-id="f7abf-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="f7abf-137">Exibindo propriedades não padrão com cmdlets Format</span><span class="sxs-lookup"><span data-stu-id="f7abf-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="f7abf-138">Se quiser ver as informações contidas na classe **Win32_OperatingSystem** que não são exibidas por padrão, você poderá exibi-las usando os cmdlets **Format**.</span><span class="sxs-lookup"><span data-stu-id="f7abf-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="f7abf-139">Por exemplo, se você deseja exibir dados de memória disponível, digite:</span><span class="sxs-lookup"><span data-stu-id="f7abf-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="f7abf-140">Os curingas funcionam com nomes de propriedade em **Format-Table**, portanto o elemento final do pipeline pode ser reduzido para **Format-Table -Property Total*,Free*</span><span class="sxs-lookup"><span data-stu-id="f7abf-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to **Format-Table -Property Total*,Free*</span></span>

<span data-ttu-id="f7abf-141">Os dados da memória podem ficar mais legíveis se você formatá-los como uma lista digitando:</span><span class="sxs-lookup"><span data-stu-id="f7abf-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```