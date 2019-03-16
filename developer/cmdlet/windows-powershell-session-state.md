---
title: Estado de sessão do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059534"
---
# <a name="windows-powershell-session-state"></a>Estado de sessão do Windows PowerShell

Estado de sessão refere-se à configuração atual de uma sessão do Windows PowerShell ou o módulo. Uma sessão do Windows PowerShell é o ambiente operacional que é usado interativamente pelo usuário de linha de comando ou por um aplicativo host de forma programática. O estado de sessão para uma sessão é conhecido como o estado de sessão global.

Da perspectiva do desenvolvedor, uma sessão do Windows PowerShell refere-se para o tempo entre quando um aplicativo host é aberto em um espaço de execução do Windows PowerShell e quando ele fecha o espaço de execução. Examinamos outra maneira, a sessão é o tempo de vida de uma instância do mecanismo do Windows PowerShell que é chamado enquanto o runspace existe.

## <a name="module-session-state"></a>Estado de sessão do módulo

Estados de sessão do módulo são criados sempre que o módulo ou um de seus módulos aninhados é importado para a sessão. Quando um módulo exporta um elemento como um cmdlet, função ou script, uma referência a esse elemento é adicionada para o estado de sessão global da sessão. No entanto, quando o elemento é executado, ele é executado dentro do módulo, o estado de sessão.

## <a name="session-state-data"></a>Dados de estado de sessão

Dados de estado de sessão podem ser público ou privado. Dados públicos estão disponíveis para chamadas de fora o estado de sessão, enquanto dados particulares estão disponíveis somente para chamadas a partir de estado da sessão. Por exemplo, um módulo pode ter uma função privada que pode ser chamada somente pelo módulo ou apenas internamente por um elemento público que foi exportado. Isso é semelhante para os membros públicos e privados de um tipo .NET Framework.

Dados de estado de sessão são armazenados pela instância atual do mecanismo de execução dentro do contexto da sessão atual do Windows PowerShell. Dados de estado de sessão consistem dos seguintes itens:

- Informações de caminho

- Informações da unidade

- Informações do provedor do Windows PowerShell

- Informações sobre os módulos importados e referências para os elementos de módulo (como cmdlets, funções e scripts) que são exportadas pelo módulo. Essas informações e essas referências são para apenas o estado da sessão global.

- Informações de variável de estado de sessão

## <a name="accessing-session-state-data-within-cmdlets"></a>Acessando dados de estado de sessão dentro de Cmdlets

Cmdlets podem acessar os dados de estado de sessão ou indiretamente por meio de [System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) propriedade de classe do cmdlet ou diretamente por meio de [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe. O [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe fornece propriedades que podem ser usadas para investigar os diferentes tipos de dados de estado de sessão.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Cmdlets do Windows PowerShell](./cmdlet-overview.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[Shell do Windows PowerShell do SDK](../windows-powershell-reference.md)
