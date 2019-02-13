---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 31fde15e644455dbe77f68bca713bf026544fdc7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676445"
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="c3b16-102">PULL sob demanda de configurações DSC</span><span class="sxs-lookup"><span data-stu-id="c3b16-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="c3b16-103">O novo cmdlet Update-DscConfiguration dispara um pull do(s) servidor(es) de recepção definido(s) na metaconfiguração.</span><span class="sxs-lookup"><span data-stu-id="c3b16-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="c3b16-104">Em geral, esse comportamento é conhecido como “Pull agora”.</span><span class="sxs-lookup"><span data-stu-id="c3b16-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="c3b16-105">Depois de disparado, o pull se comporta exatamente como faria quando disparado durante a frequência regular:</span><span class="sxs-lookup"><span data-stu-id="c3b16-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="c3b16-106">A soma de verificação da configuração atual é comparada com a soma de verificação da configuração no servidor de recepção.</span><span class="sxs-lookup"><span data-stu-id="c3b16-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="c3b16-107">Se elas forem iguais, ele será concluído com êxito sem aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="c3b16-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="c3b16-108">Se forem diferentes, a configuração será movida para baixo do servidor de recepção e aplicada.</span><span class="sxs-lookup"><span data-stu-id="c3b16-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="c3b16-109">**Observação:** se RefreshMode = “Push” da Metaconfiguração, um erro será retornado por este cmdlet; portanto, esse cmdlet nunca executará nenhuma ação quando um nó de destino estiver no modo “Push”.</span><span class="sxs-lookup"><span data-stu-id="c3b16-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
