---
title: Exemplos de código do Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 39c0814faf72cdb4b24730acb2ae429a2f465b32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863122"
---
# <a name="examples-of-cmdlet-code"></a>Exemplos de código do cmdlet

Esta seção contém exemplos de código do cmdlet que você pode usar para começar a escrever seus próprios cmdlets.

> [!IMPORTANT]
> Se você quiser instruções passo a passo para gravar cmdlets, consulte [tutoriais para gravar Cmdlets](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>Nesta seção

[Como gravar um Cmdlet simples](./how-to-write-a-simple-cmdlet.md) Este exemplo mostra a estrutura básica do código do cmdlet.

[Como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md) Este exemplo mostra como declarar os diferentes tipos de parâmetros.

[Como declarar conjuntos de parâmetros](./how-to-declare-parameter-sets.md) Este exemplo mostra como declarar conjuntos de parâmetros que podem alterar a ação que executa um cmdlet.

[Como validar o parâmetro de entrada](./how-to-validate-parameter-input.md) estes exemplos mostram como validar a entrada de parâmetro.

[Como declarar parâmetros dinâmicos](./how-to-declare-dynamic-parameters.md) Este exemplo mostra como declarar um parâmetro que é adicionado em tempo de execução.

[Como invocar Scripts dentro de um Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) Este exemplo mostra como chamar um script que é fornecido para um cmdlet.

[Como substituir os métodos de processamento de entrada](./how-to-override-input-processing-methods.md) estes exemplos mostram a estrutura básica usada para substituir os métodos de BeginProcessing, ProcessRecord e EndProcessing.

[Como suporte a chamadas para ShouldProcess](./how-to-request-confirmations.md) Este exemplo mostra como o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)métodos devem ser chamados de dentro de um cmdlet.

[Como oferecem suporte a transações](./how-to-support-transactions.md) Este exemplo mostra como indicar que o cmdlet oferece suporte a transações e como implementar a ação que é executada quando o cmdlet é usado em uma transação.

[Como dar suporte a trabalhos](./how-to-support-jobs.md) Este exemplo mostra como dar suporte a trabalhos quando você escreve cmdlets.

[Como invocar um Cmdlet de dentro de um Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) Este exemplo mostra como chamar um cmdlet de dentro de outro cmdlet, que permite que você adicionar a funcionalidade do cmdlet invocado para o cmdlet que você está desenvolvendo.

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
