---
title: Falha de cmdlets do Gerenciador de Comutador de Rede
contributor: vaibch
ms.openlocfilehash: 8495d79aec54d93f94e745e2efccb5116ad5d944
ms.sourcegitcommit: a3966253a165d193a42b43b9430a4dc76988f82f
ms.translationtype: HT
ms.contentlocale: pt-BR
---
<span data-ttu-id="5a79e-102">Os cmdlets do Gerenciador de Comutador de Rede podem ser usados para gerenciar os comutadores de rede em WSMAN.</span><span class="sxs-lookup"><span data-stu-id="5a79e-102">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span> <span data-ttu-id="5a79e-103">Alguns cmdlets do módulo são capazes de aceitar valores de pipelines.</span><span class="sxs-lookup"><span data-stu-id="5a79e-103">A few cmdlets of this module are capable of accepting values from pipelines.</span></span> <span data-ttu-id="5a79e-104">Na Preview do 5.1 WMF, os cmdlets que podem aceitar o valor de pipeline não poderão ser executados quando os valores não forem passados pelos pipelines.</span><span class="sxs-lookup"><span data-stu-id="5a79e-104">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="5a79e-105">Se o parâmetro "InputObject" não for usado, o cmdlet deverá continuar a execução sem falhas.</span><span class="sxs-lookup"><span data-stu-id="5a79e-105">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="5a79e-106">Aqui está a lista dos cmdlets afetados, ou seja, esses cmdlets pode aceitar o valor para o parâmetro "InputObject" de pipeline.</span><span class="sxs-lookup"><span data-stu-id="5a79e-106">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span> <span data-ttu-id="5a79e-107">Se esse valor não for passado do pipeline, a execução do cmdlet falhará.</span><span class="sxs-lookup"><span data-stu-id="5a79e-107">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="5a79e-108">Disable-NetworkSwitchEthernetPo</span><span class="sxs-lookup"><span data-stu-id="5a79e-108">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="5a79e-109">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="5a79e-109">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="5a79e-110">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5a79e-110">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="5a79e-111">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5a79e-111">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="5a79e-112">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="5a79e-112">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="5a79e-113">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="5a79e-113">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="5a79e-114">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5a79e-114">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="5a79e-115">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5a79e-115">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="5a79e-116">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="5a79e-116">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="5a79e-117">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="5a79e-117">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="5a79e-118">Resolução</span><span class="sxs-lookup"><span data-stu-id="5a79e-118">Resolution</span></span>
<span data-ttu-id="5a79e-119">Os cmdlets funcionam bem quando o valor do parâmetro InputObject é passado pelo pipeline.</span><span class="sxs-lookup"><span data-stu-id="5a79e-119">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="5a79e-120">Alguns exemplos que funcionam para os cmdlets acima são:</span><span class="sxs-lookup"><span data-stu-id="5a79e-120">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="5a79e-121">Disable-NetworkSwitchEthernetPo</span><span class="sxs-lookup"><span data-stu-id="5a79e-121">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="5a79e-122">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="5a79e-122">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="5a79e-123">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5a79e-123">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="5a79e-124">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5a79e-124">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="5a79e-125">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="5a79e-125">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="5a79e-126">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5a79e-126">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="5a79e-127">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5a79e-127">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="5a79e-128">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="5a79e-128">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
