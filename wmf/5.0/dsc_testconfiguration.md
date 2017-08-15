---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: ce60b240045acf538edae1a08007971e538588ca
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2017
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>O cmdlet Test-DscConfiguration dá suporte a configurações de referência

O cmdlet Test-DscConfiguration foi atualizado para permitir o teste do estado de configuração desejado de um ou mais nós de destino, especificando um documento de configuração de referência para comparação.

Os novos conjuntos de parâmetros a seguir usam configurações DSC no caminho especificado para apenas testar e nunca aplicar cada configuração no(s) nó(s) de destino especificado(s). Assim como acontece com Start-DscConfiguration e outros cmdlets do DSC, o nome de cada MOF é usado para determinar em qual nó de destino a configuração deverá ser testada. 

```powershell
Test-DscConfiguration   [-Path] <string> 
                        [[-ComputerName] <string[]>] 
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

Os novos conjuntos de parâmetros a seguir usam uma única configuração DSC para apenas testar e nunca aplicar a configuração no(s) nó(s) de destino especificado(s). 

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string> 
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

