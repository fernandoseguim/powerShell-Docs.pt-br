---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso de DSC WaitForAll
ms.openlocfilehash: 1e891f1aecbdbe641973669f71f22664ad8ea16c
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047024"
---
# <a name="dsc-waitforall-resource"></a>Recurso de DSC WaitForAll

> Aplica-se a: Windows PowerShell 5.0 e posterior

O recurso de DSC (Desired State Configuration) **WaitForAll** pode ser usado dentro de um bloco de nó em uma [configuração DSC](../../../configurations/configurations.md) para especificar dependências em configurações em outros nós.

Esse recurso terá êxito se o recurso especificado pela propriedade **ResourceName** estiver no estado desejado em todos os nós de destino definidos na propriedade **NodeName**.

## <a name="syntax"></a>Sintaxe

```
WaitForAll [string] #ResourceName
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

Para obter um exemplo de como usar esse recurso, consulte [Especificando dependências de nó cruzado](../../../configurations/crossNodeDependencies.md)
