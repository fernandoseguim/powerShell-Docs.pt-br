---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Executando tarefas de rede
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 64c57c95a70bc4cad4b695a59d96673ed18afdf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954119"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="d1cd8-103">Executando tarefas de rede</span><span class="sxs-lookup"><span data-stu-id="d1cd8-103">Performing Networking Tasks</span></span>

<span data-ttu-id="d1cd8-104">Como TCP/IP é o protocolo de rede mais frequentemente usado, a maioria das tarefas de administração de protocolo de rede de baixo nível envolve TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="d1cd8-105">Nesta seção, usamos o Windows PowerShell e o WMI para realizar essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

### <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="d1cd8-106">Listando de endereços IP para um computador</span><span class="sxs-lookup"><span data-stu-id="d1cd8-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="d1cd8-107">Para obter todos os endereços IP em uso no computador local, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="d1cd8-108">A saída desse comando é diferente da maioria das listas de propriedades, porque os valores são colocados entre chaves:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="d1cd8-109">Para entender por que as chaves são exibidas, use o cmdlet Get-Member para examinar a propriedade **IPAddress**:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="d1cd8-110">A propriedade IPAddress para cada adaptador de rede na verdade é uma matriz.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="d1cd8-111">As chaves na definição indicam que **IPAddress** não é um valor de **System.String**, mas sim uma matriz de valores **System.String**.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

### <a name="listing-ip-configuration-data"></a><span data-ttu-id="d1cd8-112">Listando dados de configuração de IP</span><span class="sxs-lookup"><span data-stu-id="d1cd8-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="d1cd8-113">Para exibir dados detalhados de configuração de IP de cada adaptador de rede, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="d1cd8-114">A exibição padrão para o objeto de configuração do adaptador de rede é um conjunto muito reduzido das informações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="d1cd8-115">Para inspeção profunda e solução de problemas, use Select-Object ou um cmdlet de formatação, como Format-List, para especificar as propriedades a serem exibidas.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="d1cd8-116">Se não estiver interessado nas propriedades IPX ou WINS (que provavelmente será o caso em uma rede TCP/IP moderna), você poderá usar o parâmetro ExcludeProperty do Select-Object para ocultar propriedades com nomes que começam com "WINS" ou "IPX":</span><span class="sxs-lookup"><span data-stu-id="d1cd8-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="d1cd8-117">Esse comando retorna informações detalhadas sobre o DHCP, DNS, roteamento e outras propriedades de configuração de IP secundárias.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

### <a name="pinging-computers"></a><span data-ttu-id="d1cd8-118">Executando ping em computadores</span><span class="sxs-lookup"><span data-stu-id="d1cd8-118">Pinging Computers</span></span>

<span data-ttu-id="d1cd8-119">Você pode executar um ping simples em um computador usando **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="d1cd8-120">O comando a seguir executa o ping, mas retorna uma saída longa:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="d1cd8-121">Uma forma mais útil de resumir as informações é exibir as propriedades Address, ResponseTime e StatusCode geradas pelo comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="d1cd8-122">O parâmetro Autosize de Format-Table redimensiona as colunas da tabela para que elas sejam exibidas corretamente no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="d1cd8-123">Um StatusCode de 0 indica um ping bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="d1cd8-124">Você pode usar uma matriz para executar o ping de vários computadores com um único comando.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="d1cd8-125">Como há mais de um endereço, use o **ForEach-Object** para executar o ping em cada endereço separadamente:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="d1cd8-126">Você pode usar o mesmo formato de comando para executar o ping de todos os computadores em uma sub-rede, como uma rede privada que usa o número da rede 192.168.1.0 e uma máscara de sub-rede de classe C padrão (255.255.255.0)., somente os endereços no intervalo de 192.168.1.1 a 192.168.1.254 são endereços locais legítimos (0 é sempre reservado para o número da rede e 255 é um endereço de difusão de sub-rede).</span><span class="sxs-lookup"><span data-stu-id="d1cd8-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="d1cd8-127">Para representar uma matriz de números de 1 a 254 no Windows PowerShell, use a instrução **1..254.**</span><span class="sxs-lookup"><span data-stu-id="d1cd8-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="d1cd8-128">Um ping de sub-rede completa pode ser executado, gerando a matriz e adicionando os valores a um endereço parcial na instrução do ping:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="d1cd8-129">Observe que essa técnica para a geração de um intervalo de endereços também pode ser usada em outro local.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="d1cd8-130">Você pode gerar um conjunto completo de endereços dessa forma:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="d1cd8-131">Recuperando propriedades do adaptador de rede</span><span class="sxs-lookup"><span data-stu-id="d1cd8-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="d1cd8-132">Mencionamos anteriormente neste guia do usuário que você pode recuperar propriedades de configuração geral usando **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="d1cd8-133">Embora não sejam estritamente informações TCP/IP, informações do adaptador de rede, como endereços MAC e tipos de adaptador podem ser úteis para entender o que está acontecendo com um computador.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="d1cd8-134">Para obter um resumo dessas informações, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="d1cd8-135">Atribuindo o domínio DNS a um adaptador de rede</span><span class="sxs-lookup"><span data-stu-id="d1cd8-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="d1cd8-136">Para atribuir o domínio DNS à resolução de nome automática, use o método **Win32_NetworkAdapterConfiguration SetDNSDomain**.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="d1cd8-137">Como você atribui o domínio DNS para cada configuração de adaptador de rede independentemente, é necessário usar uma instrução **ForEach-Object** para atribuir o domínio a cada adaptador:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="d1cd8-138">A instrução de filtragem "IPEnabled=$true" é necessária porque, mesmo em uma rede que usa apenas TCP/IP, várias das configurações de adaptador de rede em um computador não são adaptadores verdadeiros de TCP/IP. Eles são elementos de software comuns compatíveis com RAS, PPTP, QoS e outros serviços para todos os adaptadores, não tendo assim um endereço próprio.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="d1cd8-139">Você pode filtrar o comando usando o cmdlet **Where-Object** em vez de usar o filtro **Get-WmiObject**.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="d1cd8-140">Executar tarefas de configuração de DHCP</span><span class="sxs-lookup"><span data-stu-id="d1cd8-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="d1cd8-141">Modificar os detalhes de DHCP envolve trabalhar com um conjunto de adaptadores de rede, assim como na configuração do DNS.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="d1cd8-142">Existem várias ações diferentes que você pode executar usando o WMI, e abordaremos algumas delas.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

#### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="d1cd8-143">Determinação dos adaptadores habilitados para DHCP</span><span class="sxs-lookup"><span data-stu-id="d1cd8-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="d1cd8-144">Para localizar os adaptadores habilitados para DHCP em um computador, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="d1cd8-145">Para excluir adaptadores com problemas de configuração de IP, você pode recuperar apenas adaptadores habilitados para IP:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="d1cd8-146">Recuperando propriedades de DHCP</span><span class="sxs-lookup"><span data-stu-id="d1cd8-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="d1cd8-147">Como as propriedades relacionadas a DHCP para um adaptador geralmente começam com "DHCP", você pode usar o parâmetro de propriedade de Format-Table para exibir somente as propriedades:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="d1cd8-148">Habilitando o DHCP em cada adaptador</span><span class="sxs-lookup"><span data-stu-id="d1cd8-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="d1cd8-149">Para habilitar o DHCP em todos os adaptadores, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="d1cd8-150">Você pode usar a instrução **Filter** "IPEnabled=$true e DHCPEnabled=$false" para evitar habilitar o DHCP onde ele já estiver habilitado. No entanto, omitir essa etapa não causará erros.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="d1cd8-151">Liberar e renovar concessões de DHCP nos adaptadores específicos</span><span class="sxs-lookup"><span data-stu-id="d1cd8-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="d1cd8-152">A classe **Win32_NetworkAdapterConfiguration** tem os métodos **ReleaseDHCPLease** e **RenewDHCPLease**.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="d1cd8-153">Ambos são usados da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-153">Both are used in the same way.</span></span> <span data-ttu-id="d1cd8-154">Em geral, use esses métodos se você só precisar liberar ou renovar endereços para um adaptador em uma sub-rede específica.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="d1cd8-155">A maneira mais fácil de filtrar os adaptadores em uma sub-rede é escolher apenas as configurações de adaptador que usam o gateway para essa sub-rede.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="d1cd8-156">Por exemplo, o comando a seguir libera todas as concessões DHCP nos adaptadores no computador local que estão obtendo concessões de DHCP do 192.168.1.254:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="d1cd8-157">A única alteração para renovar uma concessão de DHCP é usar o método **RenewDHCPLease** em vez do **ReleaseDHCPLease**:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="d1cd8-158">Ao usar esses métodos em um computador remoto, lembre-se de que você poderá perder o acesso ao sistema remoto se estiver conectado a ele por meio do adaptador com a concessão liberada ou renovada.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="d1cd8-159">Liberar e renovar concessões de DHCP em todos os adaptadores</span><span class="sxs-lookup"><span data-stu-id="d1cd8-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="d1cd8-160">Você pode executar liberações ou renovações de endereço DHCP globais em todos os adaptadores usando os métodos **Win32_NetworkAdapterConfiguration**, **ReleaseDHCPLeaseAll** e **RenewDHCPLeaseAll**.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="d1cd8-161">No entanto, o comando deve ser aplicado à classe WMI, em vez de um adaptador específico, pois liberações e renovações de concessões globais são executada na classe, não em um adaptador específico.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="d1cd8-162">Você pode obter uma referência a uma classe WMI, em vez de instâncias de classe, listando todas as classes WMI e selecionando somente a classe desejada por nome.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="d1cd8-163">Por exemplo, o comando a seguir retorna a classe Win32_NetworkAdapterConfiguration:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="d1cd8-164">Você pode tratar o comando inteiro como a classe e, em seguida, invocar o método **ReleaseDHCPAdapterLease**.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="d1cd8-165">No comando a seguir, os parênteses que cercam os elementos de pipeline **Get-WmiObject** e **Where-Object** direcionam o Windows PowerShell para avaliá-los primeiro:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="d1cd8-166">Você pode usar o mesmo formato de comando para invocar o método **RenewDHCPLeaseAll**:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a><span data-ttu-id="d1cd8-167">Criando um compartilhamento de rede</span><span class="sxs-lookup"><span data-stu-id="d1cd8-167">Creating a Network Share</span></span>

<span data-ttu-id="d1cd8-168">Para criar um compartilhamento de rede, use o método **Win32_Share Create**:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="d1cd8-169">Você também pode criar o compartilhamento usando **net share** no Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a><span data-ttu-id="d1cd8-170">Removendo um compartilhamento de rede</span><span class="sxs-lookup"><span data-stu-id="d1cd8-170">Removing a Network Share</span></span>

<span data-ttu-id="d1cd8-171">É possível remover um compartilhamento de rede com o **Win32_Share**, mas o processo é ligeiramente diferente da criação de um compartilhamento, pois você precisa recuperar o compartilhamento específico a ser removido em vez da classe **Win32_Share**.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="d1cd8-172">A instrução a seguir exclui o compartilhamento "TempShare":</span><span class="sxs-lookup"><span data-stu-id="d1cd8-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="d1cd8-173">**Net share** também funciona:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="d1cd8-174">Conectando-se a uma unidade de rede acessível do Windows</span><span class="sxs-lookup"><span data-stu-id="d1cd8-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="d1cd8-175">Os novos cmdlets **New-PSDrive** criam uma unidade do Windows PowerShell, porém unidades criadas dessa forma estão disponíveis somente para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="d1cd8-176">Para criar uma nova unidade em rede, você pode usar o objeto COM **WScript.Network**.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="d1cd8-177">O comando a seguir mapeia o compartilhamento \\\\FPS01\\users para a unidade B local:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="d1cd8-178">O comando **net use** também funciona:</span><span class="sxs-lookup"><span data-stu-id="d1cd8-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="d1cd8-179">Unidades mapeadas com um **WScript.Network** ou net use ficam disponíveis imediatamente para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1cd8-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>