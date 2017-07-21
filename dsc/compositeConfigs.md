---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Aninhar configurações"
ms.openlocfilehash: 4de53b94056df46d74923dda56e02841cfac2cd1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="32c57-103">Aninhar configurações do DSC</span><span class="sxs-lookup"><span data-stu-id="32c57-103">Nesting DSC configurations</span></span>

<span data-ttu-id="32c57-104">Uma configuração aninhada (também chamada de configuração composta) é uma configuração chamada de dentro de outra configuração, como se fosse um recurso.</span><span class="sxs-lookup"><span data-stu-id="32c57-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="32c57-105">Ambas as configurações devem ser definidas no mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="32c57-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="32c57-106">Vejamos um exemplo simples:</span><span class="sxs-lookup"><span data-stu-id="32c57-106">Let's look at a simple example:</span></span>

```powershell
Configuration FileConfig 
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }
    
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

<span data-ttu-id="32c57-107">Neste exemplo, `FileConfig` usa dois parâmetros obrigatórios: **CopyFrom** e **CopyTo**, que são utilizados como valores para as propriedades **SourcePath** e **DestinationPath** no bloco de recursos `File`.</span><span class="sxs-lookup"><span data-stu-id="32c57-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="32c57-108">A configuração `NestedConfig` chama `FileConfig` como se fosse um recurso.</span><span class="sxs-lookup"><span data-stu-id="32c57-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="32c57-109">As propriedades do bloco de recursos `NestedConfig` (**CopyFrom** e **CopyTo**) são os parâmetros da configuração `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="32c57-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="32c57-110">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="32c57-110">See Also</span></span>

- [<span data-ttu-id="32c57-111">Recursos de composição: usando uma configuração DSC como um recurso</span><span class="sxs-lookup"><span data-stu-id="32c57-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)

