---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220335"
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="99bf0-102">PULL sob demanda de configurações DSC</span><span class="sxs-lookup"><span data-stu-id="99bf0-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="99bf0-103">O novo cmdlet Update-DscConfiguration dispara um pull do(s) servidor(es) de recepção definido(s) na metaconfiguração.</span><span class="sxs-lookup"><span data-stu-id="99bf0-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="99bf0-104">Em geral, esse comportamento é conhecido como “Pull agora”.</span><span class="sxs-lookup"><span data-stu-id="99bf0-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="99bf0-105">Depois de disparado, o pull se comporta exatamente como faria quando disparado durante a frequência regular:</span><span class="sxs-lookup"><span data-stu-id="99bf0-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="99bf0-106">A soma de verificação da configuração atual é comparada com a soma de verificação da configuração no servidor de recepção.</span><span class="sxs-lookup"><span data-stu-id="99bf0-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="99bf0-107">Se elas forem iguais, ele será concluído com êxito sem aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="99bf0-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="99bf0-108">Se forem diferentes, a configuração será movida para baixo do servidor de recepção e aplicada.</span><span class="sxs-lookup"><span data-stu-id="99bf0-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="99bf0-109">**Observação:** se RefreshMode = “Push” da Metaconfiguração, um erro será retornado por este cmdlet; portanto, esse cmdlet nunca executará nenhuma ação quando um nó de destino estiver no modo “Push”.</span><span class="sxs-lookup"><span data-stu-id="99bf0-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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
