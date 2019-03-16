---
title: Erros não fatais | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054350"
---
# <a name="non-terminating-errors"></a>Erros de não encerramento

Este tópico aborda o método usado para relatar erros de não finalização. Ele também aborda como chamar o método a partir do cmdlet.

Quando ocorre um erro de finalização, o cmdlet deve relatar este erro chamando o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método. Quando o cmdlet relata um erro de finalização, o cmdlet pode continuar a operar nesse objeto de entrada e na entrada mais objetos do pipeline. Se o cmdlet chama o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método, o cmdlet pode gravar um registro de erro que descreve a condição que causou o erro não fatal. Para obter mais informações sobre os registros de erro, consulte [registros de erros do Windows PowerShell](./windows-powershell-error-records.md).

Cmdlets pode chamar [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) conforme necessário de dentro de seu métodos de processamento de entrada. No entanto, os cmdlets pode chamar [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) somente do thread que chamou o [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) o método de processamento de entrada. Não chame [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) de outro thread. Em vez disso, se comunicar erros de volta para o thread principal.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Registros de erro do PowerShell do Windows](./windows-powershell-error-records.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
