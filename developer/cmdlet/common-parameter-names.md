---
title: Os nomes de parâmetro comuns | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059653"
---
# <a name="common-parameter-names"></a>Nomes de parâmetro comuns

Os parâmetros descritos neste tópico são denominados *parâmetros comuns de*. Eles são adicionados aos cmdlets pelo tempo de execução do Windows PowerShell e não podem ser declarados pelo cmdlet.

> [!NOTE]
> Esses parâmetros também são adicionados aos cmdlets do provedor e a funções que são decoradas com o `CmdletBinding` atributo.

## <a name="general-common-parameters"></a>Parâmetros gerais comuns

Os seguintes parâmetros são adicionados a todos os cmdlets e podem ser acessados sempre que o cmdlet é executado. Esses parâmetros são definidos pela [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) classe.

### <a name="debug-alias-db"></a>Depurar (alias: banco de dados)

Tipo de dados: SwitchParameter

Esse parâmetro especifica se depuração no nível do programador de mensagens que podem ser exibidos na linha de comando. Essas mensagens destinam-se para a operação do cmdlet de solução de problemas e são geradas por chamadas para o [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método. Mensagens de depuração não precisam ser localizada.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias: ea)

Tipo de dados: Enumeração

Esse parâmetro especifica a ação que deve ocorrer quando ocorre um erro. Os valores possíveis para esse parâmetro são definidos pela [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) enumeração.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: ev)

Tipo de dados: Cadeia de caracteres

Esse parâmetro especifica a variável na qual colocar os objetos quando ocorre um erro. Para acrescentar a essa variável, use +*varname* em vez de limpar e definir a variável.

### <a name="outvariable-alias-ov"></a>OutVariable (alias: ov)

Tipo de dados: Cadeia de caracteres

Esse parâmetro especifica a variável na qual colocar todos os objetos gerados pelo cmdlet de saída. Para acrescentar a essa variável, use +*varname* em vez de limpar e definir a variável.

### <a name="outbuffer-alias-ob"></a>OutBuffer (alias: ob)

Tipo de dados: Int32

Esse parâmetro define o número de objetos a serem armazenados no buffer de saída antes de todos os objetos passados pelo pipeline. Por padrão, os objetos são passados imediatamente pelo pipeline.

### <a name="verbose-alias-vb"></a>Detalhado (alias: vb)

Tipo de dados: SwitchParameter

Esse parâmetro especifica se o cmdlet grava mensagens explicativas que podem ser exibidas na linha de comando. Essas mensagens são o objetivo de fornecer ajuda adicional para o usuário e são geradas por chamadas para o [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método.

### <a name="warningaction-alias-wa"></a>WarningAction (alias: wa)

Tipo de dados: Enumeração

Esse parâmetro especifica a ação que deve ocorrer quando o cmdlet grava uma mensagem de aviso. Os valores possíveis para esse parâmetro são definidos pela [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) enumeração.

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: wv)

Tipo de dados: Cadeia de caracteres

Esse parâmetro especifica a variável na qual as mensagens de aviso podem ser salvo. Para acrescentar a essa variável, use +*varname* em vez de limpar e definir a variável.

## <a name="risk-mitigation-parameters"></a>Parâmetros de mitigação de risco

Os seguintes parâmetros são adicionados aos cmdlets que solicita confirmação antes de realizar sua ação. Para obter mais informações sobre solicitações de confirmação, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md). Esses parâmetros são definidos pela [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) classe.

### <a name="confirm-alias-cf"></a>Confirmar (alias: cf)

Tipo de dados: SwitchParameter

Esse parâmetro especifica se o cmdlet exibirá um prompt perguntando se o usuário tem certeza de que deseja continuar.

### <a name="whatif-alias-wi"></a>WhatIf (alias: wi)

Tipo de dados: SwitchParameter

Esse parâmetro especifica se o cmdlet grava uma mensagem que descreve os efeitos da execução do cmdlet sem realmente executar qualquer ação.

## <a name="transaction-parameters"></a>Parâmetros de transação

O parâmetro a seguir é adicionado aos cmdlets que oferecem suporte a transações. Esses parâmetros são definidos pela [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) classe.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias: usetx)

Tipo de dados: SwitchParameter

Esse parâmetro especifica se o cmdlet usará a transação atual para executar sua ação.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
