---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Recurso de DSC WaitForAny
ms.openlocfilehash: 3d73c16397d9a18805184e6a5bb8561483144898
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-waitforany-resource"></a>Recurso de DSC WaitForAny

> Aplica-se a: Windows PowerShell 5.1 e posterior

O recurso de DSC (Desired State Configuration) **WaitForSome** pode ser usado dentro de um bloco de nó em uma [configuração DSC](configurations.md) para especificar dependências de configurações em outros nós.

Esse recurso terá êxito se o recurso especificado pela propriedade **ResourceName** estiver no estado desejado em qualquer nó de destino definido na propriedade **NodeName**.


## <a name="syntax"></a>Sintaxe

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| ResourceName| O nome do recurso do qual dependerá. Se esse recurso pertence a uma configuração diferente, formate o nome como "[__TipoDoRecurso__]__NomeDoRecurso__::[__NomeDaConfiguração__]::[__NomeDaConfiguração__]"|
| NodeName| Os nós de destino do recurso do qual dependerá.|
| RetryIntervalSec| O número de segundos antes de tentar novamente. O mínimo é 1.|
| RetryCount| O número máximo de tentativas.|
| ThrottleLimit| O número de máquinas para conectar-se simultaneamente. O padrão é new-cimsession padrão.|
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Exemplo

Para obter um exemplo de como usar esse recurso, consulte [Especificando dependências de nó cruzado](crossNodeDependencies.md)