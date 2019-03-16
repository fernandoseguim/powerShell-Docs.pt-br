---
title: GetProc02 (C#) exemplos de código | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 2ac4aea2fdefdfe86349c14fe9b87cd8c41db090
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054553"
---
# <a name="getproc02-c-sample-code"></a>Código de exemplo GetProc02 (C#)

O código a seguir mostra a implementação de um `Get-Process` cmdlet que aceite entrada de linha de comando. Observe que essa implementação define uma `Name` parâmetro para permitir a entrada de linha de comando e ele usa o [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como a saída objetos do mecanismo de envio de saída para o pipeline.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a>Consulte Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)