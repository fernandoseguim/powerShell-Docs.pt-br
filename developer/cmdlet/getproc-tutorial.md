---
title: Tutorial de GetProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862452"
---
# <a name="getproc-tutorial"></a>Tutorial de GetProc

Esta seção fornece um tutorial para criação de um cmdlet Get-Proc é muito semelhante do [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet fornecido pelo Windows PowerShell. Este tutorial fornece uma explicação do código e fragmentos de código que ilustram como os cmdlets são implementados.

## <a name="topics-in-this-tutorial"></a>Tópicos neste tutorial

Os tópicos neste tutorial são criados para serem lidos em sequência, com cada tópico com base no que foi discutido no tópico anterior.

[Criação de um Cmdlet sem parâmetros](./creating-a-cmdlet-without-parameters.md) esta seção descreve como criar um cmdlet que recupera informações do computador local sem o uso de parâmetros e, em seguida, grava as informações para o pipeline.

[Adicionar parâmetros de entrada de linha de comando desse processo](./adding-parameters-that-process-command-line-input.md) esta seção descreve como adicionar um parâmetro para o cmdlet Get-Proc para que o cmdlet pode processar a entrada com base em objetos explícitos passados para o cmdlet. A implementação descrita aqui recupera processos com base em seu nome e, em seguida, grava as informações para o pipeline.

[Adicionando parâmetros de entrada do Pipeline esse processo](./adding-parameters-that-process-pipeline-input.md) esta seção descreve como adicionar um parâmetro para o cmdlet Get-Proc para que o cmdlet pode processar objetos passados para ele por meio do pipeline. O cmdlet de implementação descrito aqui recupera processos com base em objetos passados para o cmdlet e, em seguida, grava as informações para o pipeline.

[Adicionando o relatório de erros sem encerramento para o Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) esta seção descreve como adicionar relatórios a um cmdlet de erros sem encerramento. A implementação descrita aqui detecta erros de não encerramento que ocorrem durante o processamento de entrada e grava um registro de erro no fluxo de erro.

## <a name="see-also"></a>Consulte Também

[Criação de um Cmdlet sem parâmetros](./creating-a-cmdlet-without-parameters.md)

[Adicionar parâmetros que processam a entrada de linha de comando](./adding-parameters-that-process-command-line-input.md)

[Adicionar parâmetros de entrada do Pipeline de processo](./adding-parameters-that-process-pipeline-input.md)

[Adição do cmdlet de relatório de erros sem encerramento](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
