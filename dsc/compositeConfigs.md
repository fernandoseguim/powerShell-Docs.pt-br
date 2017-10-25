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
# <a name="nesting-dsc-configurations"></a>Aninhar configurações do DSC

Uma configuração aninhada (também chamada de configuração composta) é uma configuração chamada de dentro de outra configuração, como se fosse um recurso.
Ambas as configurações devem ser definidas no mesmo arquivo.

Vejamos um exemplo simples:

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

Neste exemplo, `FileConfig` usa dois parâmetros obrigatórios: **CopyFrom** e **CopyTo**, que são utilizados como valores para as propriedades **SourcePath** e **DestinationPath** no bloco de recursos `File`. A configuração `NestedConfig` chama `FileConfig` como se fosse um recurso.
As propriedades do bloco de recursos `NestedConfig` (**CopyFrom** e **CopyTo**) são os parâmetros da configuração `FileConfig`.

## <a name="see-also"></a>Consulte Também

- [Recursos de composição: usando uma configuração DSC como um recurso](authoringResourceComposite.md)

