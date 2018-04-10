---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="c03fe-102">As frequências de RefreshMode e ConfigurationMode não precisam ser múltiplos um do outro</span><span class="sxs-lookup"><span data-stu-id="c03fe-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="c03fe-103">Na versão anterior do DSC, o LCM trataria `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` como múltiplos um do outro.</span><span class="sxs-lookup"><span data-stu-id="c03fe-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="c03fe-104">No WMF 5.0 RTM, essas propriedades são processadas de forma independente uma da outra.</span><span class="sxs-lookup"><span data-stu-id="c03fe-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="c03fe-105">Para obter mais informações, veja [Configurando o Gerenciador de Configurações Local](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="c03fe-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>