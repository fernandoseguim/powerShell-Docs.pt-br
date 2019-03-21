---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso de DSC WaitForSome
ms.openlocfilehash: 888da1810f0a9233579bad5eef8d5dd556947c61
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059449"
---
# <a name="dsc-waitforsome-resource"></a>Recurso de DSC WaitForSome

> Aplica-se a: Windows PowerShell 5.0 e posterior

O recurso de DSC (Desired State Configuration) **WaitForSome** pode ser usado dentro de um bloco de nó em uma [configuração DSC](../../../configurations/configurations.md) para especificar dependências de configurações em outros nós.

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
| ResourceName| O nome do recurso do qual dependerá. Se esse recurso pertence a uma configuração diferente, formate o nome como "[__TipoDoRecurso__]__NomeDoRecurso__::[__NomeDaConfiguração__]::[__NomeDaConfiguração__]"|
| RetryIntervalSec| O número de segundos antes de tentar novamente. O mínimo é 1.|
| RetryCount| O número máximo de tentativas.|
| ThrottleLimit| O número de máquinas para conectar-se simultaneamente. O padrão é new-cimsession padrão.|
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Confira [Usar DSC com credenciais do usuário](https://docs.microsoft.com/powershell/dsc/runasuser) |

## <a name="example"></a>Exemplo

Para obter um exemplo de como usar esse recurso, consulte [Especificando dependências de nó cruzado](../../../configurations/crossNodeDependencies.md)
