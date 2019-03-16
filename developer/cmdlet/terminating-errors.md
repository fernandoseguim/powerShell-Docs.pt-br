---
title: Erros de finalização | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059228"
---
# <a name="terminating-errors"></a>Erros de encerramento

Este tópico aborda o método usado para relatório de erros de finalização. Ele também aborda como chamar o método a partir do cmdlet e ele discute as exceções que podem ser retornadas pelo tempo de execução do Windows PowerShell quando o método é chamado.

Quando uma terminação erro ocorrer, o cmdlet deve relatar o erro chamando o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método. Esse método permite que o cmdlet enviar um registro de erro que descreve a condição que causou o erro de terminação. Para obter mais informações sobre os registros de erro, consulte [registros de erros do Windows PowerShell](./windows-powershell-error-records.md).

Quando o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método é chamado, o tempo de execução do Windows PowerShell permanentemente interrompe a execução do pipeline e gera um [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exceção. Qualquer tentativa subsequente de chamar [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), ou várias outras APIs que faz com que essas chamadas para lançar um [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exceção.

O [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exceção também pode ocorrer se outro cmdlet no pipeline relata um erro de terminação, se o usuário solicitou parar o pipeline, ou se o pipeline foi interrompido antes da conclusão por qualquer motivo. O cmdlet não precisa capturar o [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exceção, a menos que ele deve abrir limpar recursos ou seu estado interno.

Cmdlets pode gravar qualquer número de objetos de saída ou erros de não finalização antes de relatar um erro de encerramento. No entanto, o erro de terminação permanentemente interrompe o pipeline e nenhuma saída adicional, encerrando erros, ou podem ser relatados erros de não finalização.

Cmdlets pode chamar [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) somente do thread que chamou o [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) o método de processamento de entrada. Não tente chamar [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ou [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) de outro thread. Em vez disso, os erros devem ser comunicados volta para o thread principal.

É possível que um cmdlet gerar uma exceção em sua implementação do [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Qualquer exceção gerada a partir desses métodos (com exceção de algumas condições de erro grave que interrompe o host do Windows PowerShell) é interpretada como um erro de encerramento que interrompe o pipeline, mas não o Windows PowerShell como um todo. (Isso se aplica somente ao thread principal do cmdlet. Exceções não identificadas em threads gerados pelo cmdlet, em geral, interrompem o host do Windows PowerShell.) É recomendável que você use [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) em vez de gerar uma exceção porque o registro de erro fornece informações adicionais sobre a condição de erro, que é útil para o usuário final. Cmdlets devem honrar a diretriz de código gerenciado contra capturando e manipulando todas as exceções (`catch (Exception e)`). Converta apenas exceções de tipos conhecidos e esperados em registros de erro.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Registros de erro do PowerShell do Windows](./windows-powershell-error-records.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
