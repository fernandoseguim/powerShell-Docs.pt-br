---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.topic: conceptual
contributor: vaibch
title: Falha de cmdlets do Gerenciador de Comutador de Rede
ms.openlocfilehash: 197a25411a82e5d256a9420706535d5411991f1b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
<span data-ttu-id="b3124-103">Os cmdlets do Gerenciador de Comutador de Rede podem ser usados para gerenciar os comutadores de rede em WSMAN.</span><span class="sxs-lookup"><span data-stu-id="b3124-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="b3124-104">Alguns cmdlets do módulo são capazes de aceitar valores de pipelines.</span><span class="sxs-lookup"><span data-stu-id="b3124-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="b3124-105">Na Preview do 5.1 WMF, os cmdlets que podem aceitar o valor de pipeline não poderão ser executados quando os valores não forem passados pelos pipelines.</span><span class="sxs-lookup"><span data-stu-id="b3124-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="b3124-106">Se o parâmetro "InputObject" não for usado, o cmdlet deverá continuar a execução sem falhas.</span><span class="sxs-lookup"><span data-stu-id="b3124-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="b3124-107">Aqui está a lista dos cmdlets afetados, ou seja, esses cmdlets pode aceitar o valor para o parâmetro "InputObject" de pipeline.</span><span class="sxs-lookup"><span data-stu-id="b3124-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="b3124-108">Se esse valor não for passado do pipeline, a execução do cmdlet falhará.</span><span class="sxs-lookup"><span data-stu-id="b3124-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="b3124-109">Disable-NetworkSwitchEthernetPo</span><span class="sxs-lookup"><span data-stu-id="b3124-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="b3124-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="b3124-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="b3124-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="b3124-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="b3124-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="b3124-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="b3124-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="b3124-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="b3124-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="b3124-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="b3124-115">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="b3124-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="b3124-116">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="b3124-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="b3124-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="b3124-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="b3124-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="b3124-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="b3124-119">Resolução</span><span class="sxs-lookup"><span data-stu-id="b3124-119">Resolution</span></span>
<span data-ttu-id="b3124-120">Os cmdlets funcionam bem quando o valor do parâmetro InputObject é passado pelo pipeline.</span><span class="sxs-lookup"><span data-stu-id="b3124-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="b3124-121">Alguns exemplos que funcionam para os cmdlets acima são:</span><span class="sxs-lookup"><span data-stu-id="b3124-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="b3124-122">Disable-NetworkSwitchEthernetPo</span><span class="sxs-lookup"><span data-stu-id="b3124-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="b3124-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="b3124-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="b3124-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="b3124-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="b3124-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="b3124-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="b3124-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="b3124-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="b3124-127">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="b3124-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="b3124-128">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="b3124-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="b3124-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="b3124-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
