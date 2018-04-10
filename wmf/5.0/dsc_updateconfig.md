---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 27f8fab6a72e7f3a3f510f5a9e503bbfb8a8f618
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a>PULL sob demanda de configurações DSC

O novo cmdlet Update-DscConfiguration dispara um pull do(s) servidor(es) de recepção definido(s) na metaconfiguração. Em geral, esse comportamento é conhecido como “Pull agora”.


Depois de disparado, o pull se comporta exatamente como faria quando disparado durante a frequência regular:

1. A soma de verificação da configuração atual é comparada com a soma de verificação da configuração no servidor de recepção.
2. Se elas forem iguais, ele será concluído com êxito sem aplicar a configuração.
3. Se forem diferentes, a configuração será movida para baixo do servidor de recepção e aplicada.

**Observação:** se RefreshMode = “Push” da Metaconfiguração, um erro será retornado por este cmdlet; portanto, esse cmdlet nunca executará nenhuma ação quando um nó de destino estiver no modo “Push”.

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