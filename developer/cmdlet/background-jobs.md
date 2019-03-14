---
title: Trabalhos em segundo plano | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794698"
---
# <a name="background-jobs"></a>Trabalhos em segundo plano

Cmdlets pode executar sua ação internamente ou como um Windows PowerShell*trabalho em segundo plano*. Quando um cmdlet é executado como um trabalho em segundo plano, o trabalho é feito de forma assíncrona em seu próprio thread separado do thread do pipeline que usa o cmdlet. Da perspectiva do usuário, quando um cmdlet é executado como um trabalho em segundo plano, o prompt de comando retorna imediatamente, mesmo se o trabalho leva um longo período de tempo para ser concluída e o usuário pode continuar sem interrupções enquanto o trabalho é executado.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Trabalhos em segundo plano, trabalhos filhos e o repositório de trabalho

O objeto de trabalho que é retornado pelos cmdlets que oferecem suporte a trabalhos em segundo plano define o trabalho. (O [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet também retorna um objeto de trabalho.) O nome do trabalho, um identificador que é usado para especificar o trabalho, as informações de estado e os trabalhos filhos são incluídos nessa definição. O trabalho não realiza o trabalho. Cada trabalho em segundo plano tem pelo menos um trabalho filho, porque o trabalho filho executa o trabalho real. Quando você executar um cmdlet, para que o trabalho é executado como um trabalho em segundo plano, o cmdlet deve adicionar o trabalho e os trabalhos filho para um repositório comum, conhecido como o *repositório de trabalho*.

Para obter mais informações sobre como os trabalhos em segundo plano são tratados na linha de comando, consulte o seguinte:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Escrevendo um Cmdlet que é executado como um trabalho em segundo plano

Para gravar um cmdlet que pode ser executado como um trabalho em segundo plano, você deve concluir as seguintes tarefas:

- Definir um `asJob` Troque o parâmetro para que o usuário pode decidir se deseja executar o cmdlet como um trabalho em segundo plano.

- Criar um objeto que deriva de [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) classe. Esse objeto pode ser um objeto de trabalho personalizado ou um objeto de trabalho fornecida pelo Windows PowerShell, tal como uma [pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objeto.

- Em um método de processamento de registro, adicione um `if` instrução que detecta se o cmdlet deve ser executado como um trabalho em segundo plano.

- Para objetos de trabalho personalizado, implemente a classe de trabalho.

- Retorne os objetos apropriados, dependendo se o cmdlet é executado como um trabalho em segundo plano.

Para obter um exemplo de código, consulte [como suporte a trabalhos](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>APIs de relacionados ao trabalho em segundo plano

As seguintes APIs são fornecidas pelo Windows PowerShell para gerenciar trabalhos em segundo plano.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) deriva objetos de trabalho personalizado. Esta é uma classe abstrata.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gerencia e fornece informações sobre os trabalhos em segundo plano ativo atual.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) define o estado do trabalho em segundo plano. Os estados incluem iniciado, em execução e parado.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) fornece informações sobre o estado de um trabalho em segundo plano e, se o estado da última alteração foi causado por um erro, o motivo pelo qual o trabalho entrou no seu estado atual.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fornece os argumentos para um evento que é gerado quando um trabalho de plano de fundo muda de estado.

## <a name="windows-powershell-job-cmdlets"></a>Cmdlets de trabalho do PowerShell do Windows

Os cmdlets a seguir são fornecidos pelo Windows PowerShell para gerenciar trabalhos em segundo plano.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Obtém trabalhos em segundo plano do Windows PowerShell que estão em execução na sessão atual.

[Receive-Job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Obtém os resultados dos trabalhos de plano de fundo do Windows PowerShell na sessão atual.

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Exclui um trabalho em plano de fundo do Windows PowerShell.

[Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Inicia um trabalho em segundo plano do Windows PowerShell.

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Interrompe um trabalho em plano de fundo do Windows PowerShell.

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Suprime o prompt de comando até que um ou todos os trabalhos em segundo plano do Windows PowerShell executados na sessão sejam concluídos.

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
