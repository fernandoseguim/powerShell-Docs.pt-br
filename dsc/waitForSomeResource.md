---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso de DSC WaitForSome
ms.openlocfilehash: 3ea9dc51cbb00cf6158abf114fdb31fd91307df9
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2017
---
# <a name="dsc-waitforsome-resource"></a>Recurso de DSC WaitForSome

> Aplica-se a: Windows PowerShell 5.0 e posterior

O recurso de DSC (Desired State Configuration) **WaitForAny** pode ser usado dentro de um bloco de nó em uma [configuração DSC](configurations.md) para especificar dependências de configurações em outros nós.

O recurso terá êxito se o recurso especificado pela propriedade **ResourceName** estiver no estado desejado em um número mínimo de nós (especificado por **NodeCount**) definidos pela propriedade **NodeName**. 


## <a name="syntax"></a>Sintaxe

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| NodeCount| O número mínimo de nós que devem estar no estado desejado para que esse recurso tenha êxito.|
| NodeName| Os nós de destino do recurso do qual dependerá.| 
| ResourceName| O nome do recurso do qual dependerá.| 
| RetryIntervalSec| O número de segundos antes de tentar novamente. O mínimo é 1.| 
| RetryCount| O número máximo de tentativas.| 
| ThrottleLimit| O número de máquinas para conectar-se simultaneamente. O padrão é new-cimsession padrão.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Confira [Usar DSC com credenciais do usuário](https://docs.microsoft.com/en-us/powershell/dsc/runasuser) |


## <a name="example"></a>Exemplo

Para obter um exemplo de como usar esse recurso, consulte [Especificando dependências de nó cruzado](crossNodeDependencies.md)

