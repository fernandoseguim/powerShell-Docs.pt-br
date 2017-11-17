---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="eae21-102">Informações detalhadas sobre o estado do LCM</span><span class="sxs-lookup"><span data-stu-id="eae21-102">Detailed information about LCM state</span></span>

<span data-ttu-id="eae21-103">Fizemos melhorias na exposição de detalhes sobre o estado do LCM.</span><span class="sxs-lookup"><span data-stu-id="eae21-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="eae21-104">O LCMState retornado por Get-DscLocalConfigurationManager agora pode conter os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="eae21-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="eae21-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="eae21-105">**Idle**</span></span>
* <span data-ttu-id="eae21-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="eae21-106">**Busy**</span></span>
* <span data-ttu-id="eae21-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="eae21-107">**PendingReboot**</span></span>
* <span data-ttu-id="eae21-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="eae21-108">**PendingConfiguration**</span></span>

<span data-ttu-id="eae21-109">Também adicionamos uma propriedade de LCMStateDetail que contém mais informações sobre o estado.</span><span class="sxs-lookup"><span data-stu-id="eae21-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

