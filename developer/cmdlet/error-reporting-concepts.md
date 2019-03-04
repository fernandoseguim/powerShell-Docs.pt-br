---
title: Conceitos de relatórios de erros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: aac6b7b6ac8a0fad15194b6d3f92c434524fabdb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855072"
---
# <a name="error-reporting-concepts"></a>Conceitos de relatórios de erro

Windows PowerShell fornece dois mecanismos para relatar erros: um mecanismo para a *erros de finalização* e um outro mecanismo para *erros não fatais*. É importante para seu cmdlet para relatar erros corretamente para que o aplicativo host que está executando seus cmdlets possa reagir de forma apropriada.

O cmdlet deve chamar o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método quando ocorre um erro que não tiver ou não deve permitir que o cmdlet a continuar a processar seus objetos de entrada. O cmdlet deve chamar o [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método para relatar erros de não finalização quando o cmdlet pode continuar a processar os objetos de entrada. Os dois métodos fornecem um registro de erro que o aplicativo host pode usar para investigar a causa do erro.

Use as diretrizes a seguir para determinar se um erro é uma terminação ou erro não fatal.

- Um erro é um erro de terminação, se ele impede que seu cmdlet continua a processar o objeto atual ou o processamento bem-sucedido de todos os objetos ainda mais a entrada, independentemente de seu conteúdo.

- Um erro é um erro de terminação, se você não quiser seu cmdlet continuar a processar o objeto atual ou qualquer objeto de entrada adicional, independentemente de seu conteúdo.

- Um erro é um erro de terminação, se ele ocorrer em um cmdlet que não aceitam ou retornam um objeto ou se ele ocorrer em um cmdlet que aceita ou retorna apenas um objeto.

- Um erro é um erro de finalização, se você deseja que seu cmdlet para continuar a processar o objeto atual e todos os objetos ainda mais a entrada.

- Um erro é um erro não fatal se ele está relacionado a um objeto de entrada específico ou um subconjunto de objetos de entrada.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Registros de erro do PowerShell do Windows](./windows-powershell-error-records.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
