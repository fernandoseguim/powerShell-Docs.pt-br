---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso de DSC WaitForSome
ms.openlocfilehash: 5d67a9111f6358240590b651e627ffb96abc0896
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="dsc-waitforsome-resource" class="xliff"></a>
# Recurso de DSC WaitForSome

> Aplica-se a: Windows PowerShell 5.0 e posterior

O recurso de DSC (Desired State Configuration) **WaitForAny** pode ser usado dentro de um bloco de nó em uma [configuração DSC](configurations.md) para especificar dependências de configurações em outros nós.

O recurso terá êxito se o recurso especificado pela propriedade **ResourceName** estiver no estado desejado em um número mínimo de nós (especificado por **NodeCount**) definidos pela propriedade **NodeName**. 


<a id="syntax" class="xliff"></a>
## Sintaxe

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    NodeCount = [Uint32]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

<a id="properties" class="xliff"></a>
## Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| ResourceName| O nome do recurso do qual dependerá.| 
| NodeName| Os nós de destino do recurso do qual dependerá.| 
| NodeCount| O número mínimo de nós que devem estar no estado desejado para que esse recurso tenha êxito.|
| RetryIntervalSec| O número de segundos antes de tentar novamente. O mínimo é 1.| 
| RetryCount| O número máximo de tentativas.| 
| ThrottleLimit| O número de máquinas para conectar-se simultaneamente. O padrão é new-cimsession padrão.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.|


<a id="example" class="xliff"></a>
## Exemplo

Para obter um exemplo de como usar esse recurso, consulte [Especificando dependências de nó cruzado](crossNodeDependencies.md)

