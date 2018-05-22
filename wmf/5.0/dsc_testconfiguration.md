---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="36a20-102">O cmdlet Test-DscConfiguration dá suporte a configurações de referência</span><span class="sxs-lookup"><span data-stu-id="36a20-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="36a20-103">O cmdlet Test-DscConfiguration foi atualizado para permitir o teste do estado de configuração desejado de um ou mais nós de destino, especificando um documento de configuração de referência para comparação.</span><span class="sxs-lookup"><span data-stu-id="36a20-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="36a20-104">Os novos conjuntos de parâmetros a seguir usam configurações DSC no caminho especificado para apenas testar e nunca aplicar cada configuração no(s) nó(s) de destino especificado(s).</span><span class="sxs-lookup"><span data-stu-id="36a20-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="36a20-105">Assim como acontece com Start-DscConfiguration e outros cmdlets do DSC, o nome de cada MOF é usado para determinar em qual nó de destino a configuração deverá ser testada.</span><span class="sxs-lookup"><span data-stu-id="36a20-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

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

<span data-ttu-id="36a20-106">Os novos conjuntos de parâmetros a seguir usam uma única configuração DSC para apenas testar e nunca aplicar a configuração no(s) nó(s) de destino especificado(s).</span><span class="sxs-lookup"><span data-stu-id="36a20-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

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
