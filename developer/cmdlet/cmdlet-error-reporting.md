---
title: Relatório de erros do cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057936"
---
# <a name="cmdlet-error-reporting"></a>Relatório de erros do cmdlet

Cmdlets deve relatar erros de forma diferente dependendo se os erros são erros de finalização ou erros sem encerramento. Erros de encerramento são erros que fazem com que o pipeline a ser encerrado imediatamente ou erros que ocorrem quando há nenhum motivo para continuar o processamento. Erros sem encerramento são os erros que relatam uma condição de erro atual, mas o cmdlet pode continuar a processar objetos de entrada. Com erros sem encerramento, normalmente, o usuário é notificado do problema, mas o cmdlet continua a processar o próximo objeto de entrada.

## <a name="terminating-and-nonterminating-errors"></a>Erros de finalização e sem encerramento

As diretrizes a seguir podem ser usadas para determinar se uma condição de erro é um erro de terminação ou um erro sem encerramento.

- A condição de erro impede a seu cmdlet processamento bem-sucedido de todos os objetos ainda mais a entrada? Nesse caso, isso é um erro de encerramento.

- A condição de erro está relacionada a um objeto de entrada específico ou um subconjunto de objetos de entrada? Nesse caso, esse é um erro sem encerramento.

- O cmdlet aceita vários objetos de entrada, tal que o processamento pode ter êxito em outro objeto de entrada? Nesse caso, esse é um erro sem encerramento.

- Cmdlets que podem aceitar vários objetos de entrada devem decidir entre o que está encerrando e erros sem encerramento, mesmo quando uma determinada situação se aplica a um único objeto de entrada.

- Cmdlets pode receber qualquer número de objetos de entrada e enviar qualquer número de objetos de sucesso ou erro antes de lançar uma exceção de terminação. Não há nenhuma relação entre o número de objetos de entrada recebidos e o número de objetos de êxito e erro enviadas.

- Cmdlets que pode aceitar somente 0-1 objetos de entrada e gerar 0-1 apenas de saída objetos devem tratar erros como erros de finalização e geram exceções de encerramento.

## <a name="reporting-nonterminating-errors"></a>Relatando erros sem encerramento

O relatório de um erro sem encerramento sempre deve ser feito dentro da implementação do cmdlet do [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método, o [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, ou o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Esses tipos de erros são relatados por meio da chamada a [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método que por sua vez envia um registro de erro para o fluxo de erro.

## <a name="reporting-terminating-errors"></a>Relatório de erros de finalização

Erros de encerramento são relatados ao lançar exceções ou chamando o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método. Lembre-se de que cmdlets também pode capturar e relançar exceções, como OutOfMemory, no entanto, eles não são necessários para gerar novamente as exceções, como o tempo de execução do Windows PowerShell irá capturá-las também.

Você também pode definir suas próprias exceções para questões específicas à sua situação ou adicionar informações adicionais em uma exceção existente usando o seu registro de erro.

## <a name="error-records"></a>Registros de erro

Windows PowerShell descreve uma condição de erro sem encerramento através do uso do [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objetos. Cada [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto fornece informações de categoria de erro, um objeto de destino opcionais e detalhes sobre a condição de erro.

### <a name="error-identifiers"></a>Identificadores de erro

O identificador de erro é uma simple cadeia de caracteres que identifica a condição de erro dentro do cmdlet. Windows PowerShell combina esse identificador com um identificador de cmdlet para criar um identificador de erro totalmente qualificado que pode ser usado mais tarde, ao filtrar fluxos de erro ou o log de erros ao responder a erros específicos, ou com outras atividades específicas do usuário.

As diretrizes a seguir devem ser seguidas ao especificar identificadores de erro.

- Atribua identificadores de erro diferente, altamente específico, para caminhos de código diferentes. Cada caminho de código que chama [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) deve ter seu próprio identificador de erro.

- Identificadores de erro devem ser exclusivos para os tipos de exceção do CLR para erros de finalização e sem encerramento.

- Não altere a semântica de um identificador de erro entre as versões do seu cmdlet ou o provedor do Windows PowerShell. Depois que a semântica de um identificador de erro é estabelecida, ela deve permanecer constante ao longo do ciclo de vida de seu cmdlet.

- Para erros de finalização, use um identificador de erro exclusivo para um determinado tipo de exceção do CLR. Se o tipo de exceção for alterado, use um novo identificador de erro.

- Para erros sem encerramento, use um identificador de erro específico para um objeto de entrada específico.

- Escolha o texto para o identificador de tersely corresponde ao erro que está sendo relatado. Não use espaço em branco ou pontuação.

- Não gere identificadores de erro que não são reproduzíveis. Por exemplo, não geram identificadores que incluem um identificador de processo. Identificadores de erro são úteis apenas quando eles correspondem aos identificadores que são vistos por outros usuários que estão tendo o mesmo problema.

### <a name="error-categories"></a>Categorias de erro

Categorias de erro são usadas para agrupar erros para o usuário final. Windows PowerShell define essas categorias e cmdlets e provedores do Windows PowerShell devem escolher entre elas durante a geração de registro de erro.

Para obter uma descrição das categorias de erro que estão disponíveis, consulte o [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeração. Em geral, você deve evitar usar NoError, UndefinedError e erro genérico sempre que possível.

Os usuários podem exibir erros com base na categoria quando eles definem "`$ErrorView`" para "CategoryView".

## <a name="see-also"></a>Consulte Também

[Cmdlets do Windows PowerShell](./cmdlet-overview.md)

[Saída do cmdlet](./types-of-cmdlet-output.md)

[Shell do Windows PowerShell do SDK](../windows-powershell-reference.md)
