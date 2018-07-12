---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.topic: conceptual
contributor: vaibch
title: Falha de cmdlets do Gerenciador de Comutador de Rede
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893147"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="374af-103">Falha de cmdlets do Gerenciador de Comutador de Rede</span><span class="sxs-lookup"><span data-stu-id="374af-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="374af-104">Os cmdlets do Gerenciador de Comutador de Rede podem ser usados para gerenciar os comutadores de rede em WSMAN.</span><span class="sxs-lookup"><span data-stu-id="374af-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="374af-105">Alguns cmdlets do módulo são capazes de aceitar valores de pipelines.</span><span class="sxs-lookup"><span data-stu-id="374af-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="374af-106">Na Preview do 5.1 WMF, os cmdlets que podem aceitar o valor de pipeline não poderão ser executados quando os valores não forem passados pelos pipelines.</span><span class="sxs-lookup"><span data-stu-id="374af-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="374af-107">Se o parâmetro "InputObject" não for usado, o cmdlet deverá continuar a execução sem falhas.</span><span class="sxs-lookup"><span data-stu-id="374af-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="374af-108">Aqui está a lista dos cmdlets afetados, ou seja, esses cmdlets pode aceitar o valor para o parâmetro "InputObject" de pipeline.</span><span class="sxs-lookup"><span data-stu-id="374af-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="374af-109">Se esse valor não for passado do pipeline, a execução do cmdlet falhará.</span><span class="sxs-lookup"><span data-stu-id="374af-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="374af-110">Disable-NetworkSwitchEthernetPo</span><span class="sxs-lookup"><span data-stu-id="374af-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="374af-111">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="374af-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="374af-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="374af-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="374af-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="374af-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="374af-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="374af-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="374af-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="374af-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="374af-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="374af-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="374af-117">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="374af-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="374af-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="374af-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="374af-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="374af-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="374af-120">Resolução</span><span class="sxs-lookup"><span data-stu-id="374af-120">Resolution</span></span>

<span data-ttu-id="374af-121">Os cmdlets funcionam bem quando o valor do parâmetro InputObject é passado pelo pipeline.</span><span class="sxs-lookup"><span data-stu-id="374af-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="374af-122">Alguns exemplos que funcionam para os cmdlets acima são:</span><span class="sxs-lookup"><span data-stu-id="374af-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```