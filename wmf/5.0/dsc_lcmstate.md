---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="4d9f2-102">Informações detalhadas sobre o estado do LCM</span><span class="sxs-lookup"><span data-stu-id="4d9f2-102">Detailed information about LCM state</span></span>

<span data-ttu-id="4d9f2-103">Fizemos melhorias na exposição de detalhes sobre o estado do LCM.</span><span class="sxs-lookup"><span data-stu-id="4d9f2-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="4d9f2-104">O LCMState retornado por Get-DscLocalConfigurationManager agora pode conter os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="4d9f2-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="4d9f2-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="4d9f2-105">**Idle**</span></span>
* <span data-ttu-id="4d9f2-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="4d9f2-106">**Busy**</span></span>
* <span data-ttu-id="4d9f2-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="4d9f2-107">**PendingReboot**</span></span>
* <span data-ttu-id="4d9f2-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="4d9f2-108">**PendingConfiguration**</span></span>

<span data-ttu-id="4d9f2-109">Também adicionamos uma propriedade de LCMStateDetail que contém mais informações sobre o estado.</span><span class="sxs-lookup"><span data-stu-id="4d9f2-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
