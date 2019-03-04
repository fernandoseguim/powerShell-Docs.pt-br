---
title: Exemplo de código RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 1a09cfee3bb317de6c1ca4dde86a87d72a498e6e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858602"
---
# <a name="runspace08-code-sample"></a>Exemplo de código RunSpace08

Aqui está o código-fonte para o exemplo Runspace08 descrito [criando um aplicativo que adiciona parâmetros do Console a um comando](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Este aplicativo de exemplo cria um espaço de execução, cria um pipeline, adiciona dois comandos ao pipeline, adiciona dois parâmetros para o segundo comando e, em seguida, executa o pipeline. Os comandos que são adicionados ao pipeline são as `Get-Process` e `Sort-Object` cmdlets.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Consulte Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)