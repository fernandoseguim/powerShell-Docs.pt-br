---
title: Exemplo do Windows PowerShell02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861062"
---
# <a name="windows-powershell02-sample"></a>Amostra Windows PowerShell02

Este exemplo mostra como executar comandos de forma assíncrona usando os espaços de execução de um pool de Runspaces. O exemplo gera uma lista de comandos e, em seguida, executa esses comandos, enquanto o mecanismo Windows PowerShell abre um espaço de execução do pool quando ele for necessário.

## <a name="requirements"></a>Requisitos

- Este exemplo requer o Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demonstra

Este exemplo demonstra o seguinte:

- Criando um objeto RunspacePool com um número mínimo e máximo de espaços de execução pode estar aberto ao mesmo tempo.

- Criando uma lista de comandos.

- Executando os comandos de forma assíncrona.

- Chamar o [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) método para ver quantos espaços de execução são gratuitos.

- Capturar a saída do comando com o [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.

## <a name="example"></a>Exemplo

Este exemplo mostra como abrir os espaços de execução de um pool de Runspaces e como executar comandos assincronamente esses espaços de execução.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Consulte Também

[Escrevendo um aplicativo de Host do PowerShell do Windows](./writing-a-windows-powershell-host-application.md)