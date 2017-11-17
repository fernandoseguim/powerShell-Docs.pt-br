---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="e5000-102">As frequências de RefreshMode e ConfigurationMode não precisam ser múltiplos um do outro</span><span class="sxs-lookup"><span data-stu-id="e5000-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="e5000-103">Na versão anterior do DSC, o LCM trataria `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` como múltiplos um do outro.</span><span class="sxs-lookup"><span data-stu-id="e5000-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="e5000-104">No WMF 5.0 RTM, essas propriedades são processadas de forma independente uma da outra.</span><span class="sxs-lookup"><span data-stu-id="e5000-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span> 

<span data-ttu-id="e5000-105">Para obter mais informações, veja [Configurando o Gerenciador de Configurações Local](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="e5000-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>

