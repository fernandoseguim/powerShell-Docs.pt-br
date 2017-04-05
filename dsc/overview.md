---
title: "Visão Geral da Configuração de Estado Desejado do Windows PowerShell"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: ec773688540a3f4a2f128f66d311926fd5b9a935
ms.sourcegitcommit: 6d27d6db5ab0e2d5b6c7229e2e2d2e57915ea22d
translationtype: HT
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Visão Geral da Configuração de Estado Desejado do Windows PowerShell 

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

A DSC é uma plataforma de gerenciamento no PowerShell que permite que você gerencie sua infraestrutura de desenvolvimento e TI com configuração como código.

- Para obter uma visão geral dos benefícios comerciais de usar a DSC, confira [Visão Geral da Configuração do Estado Desejado para Tomadores de Decisão](decisionMaker.md).
- Para obter uma visão geral dos benefícios de engenharia ao usar a DSC, confira [Visão Geral da Configuração do Estado Desejado para Engenheiros](DscForEngineers.md).
- Para começar a usar a DSC rapidamente, veja [Início rápido da DSC](quickStart.md).

## <a name="key-concepts"></a>Conceitos Principais

A DSC é uma plataforma declarativa usada para configuração, implantação e gerenciamento de sistemas. Consiste em três componentes principais:

- [Configurações](configurations.md) são scripts declarativos do PowerShell que definem e configuram instâncias de recursos.
    Após executar a configuração, a DSC (e os recursos que estão sendo chamados pela configuração) vai simplesmente “realizar”, garantindo que o sistema exista no estado disposto pela configuração. 
    As configurações da DSC também são idempotentes: o Gerenciador de Configurações Local (LCM) continuará garantindo que os computadores sejam configurados no estado declarado pela configuração.
- Os recursos são a parte de "realização" da DSC. Eles contêm o código que definem e mantêm o destino de uma configuração no estado especificado. 
    Os recursos residem dentro de módulos do PowerShell e podem ser escritos para modelar algo tão genérico quanto um arquivo ou um processo do Windows ou tão específico quanto um servidor IIS ou em uma VM em execução no Azure.
- O Gerenciador de Configurações Local (LCM) é o mecanismo pelo qual a DSC facilita a interação entre recursos e configurações. 
    Regularmente, o LCM sonda o sistema usando o fluxo de controle implementado pelos recursos para garantir que o estado definido por uma Configuração seja mantido. 
    Se o sistema estiver sem estado, o LCM faz chamadas para o código nos recursos para “realizar”, de acordo com a configuração. 

## <a name="see-also"></a>Consulte Também

- [Configurações DSC](configurations.md)
- [Recursos de DSC](resources.md)
- [Configurando o Gerenciador de Configurações Local](metaConfig.md)

