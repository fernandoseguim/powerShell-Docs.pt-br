---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="24692-102">Informações detalhadas sobre o estado do LCM</span><span class="sxs-lookup"><span data-stu-id="24692-102">Detailed information about LCM state</span></span>

<span data-ttu-id="24692-103">Fizemos melhorias na exposição de detalhes sobre o estado do LCM.</span><span class="sxs-lookup"><span data-stu-id="24692-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="24692-104">O LCMState retornado por Get-DscLocalConfigurationManager agora pode conter os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="24692-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="24692-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="24692-105">**Idle**</span></span>
* <span data-ttu-id="24692-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="24692-106">**Busy**</span></span>
* <span data-ttu-id="24692-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="24692-107">**PendingReboot**</span></span>
* <span data-ttu-id="24692-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="24692-108">**PendingConfiguration**</span></span>

<span data-ttu-id="24692-109">Também adicionamos uma propriedade de LCMStateDetail que contém mais informações sobre o estado.</span><span class="sxs-lookup"><span data-stu-id="24692-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>