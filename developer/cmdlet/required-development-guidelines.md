---
title: Diretrizes de desenvolvimento obrigatórias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: a4b228be91bba27670b26fe21e765ae942afe968
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860712"
---
# <a name="required-development-guidelines"></a>Diretrizes para desenvolvimento necessárias

As diretrizes a seguir devem ser seguidas ao escrever seus cmdlets. Eles são separados em diretrizes para criação de cmdlets e diretrizes para escrever seu código do cmdlet. Se você não seguir essas diretrizes, seus cmdlets pode falhar e os usuários podem ter uma experiência ruim quando eles usam seus cmdlets.

## <a name="in-this-topic"></a>Neste tópico

### <a name="design-guidelines"></a>Diretrizes de design

- [Usar somente aprovados verbos (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Nomes de cmdlet: Caracteres que não podem ser usados (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Nomes de parâmetros que não podem ser usados (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Suporte a solicitações de confirmação (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Suporte a parâmetro Force para sessões interativas (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Objetos de documento de saída (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Diretrizes de código

- [Derivar do Cmdlet ou Classes de PSCmdlet (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Especificar o atributo de Cmdlet (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Substituir uma método (RC03) de processamento de entrada](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Especificar o atributo OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Não manterá os identificadores de objetos de saída (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Tratar erros robusto (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Usar um módulo do Windows PowerShell para implantar seus Cmdlets (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Diretrizes de design

As diretrizes a seguir devem ser seguidas durante a criação de cmdlets para garantir uma experiência de usuário consistente entre o uso de seus cmdlets e outros cmdlets. Quando você encontrar uma diretriz de Design que se aplica à sua situação, certifique-se de examinar as diretrizes de código para obter diretrizes semelhantes.

### <a name="use-only-approved-verbs-rd01"></a>Usar somente aprovados verbos (RD01)

O verbo especificado no atributo Cmdlet deve vir do reconhecido conjunto de verbos fornecidos pelo Windows PowerShell. Ele não deve ser um dos sinônimos proibidos. Use as cadeias de caracteres constante que são definidas pelas enumerações a seguir para especificar os verbos de cmdlet:

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Para obter mais informações sobre os nomes de verbos aprovados, consulte [verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Os usuários precisam de um conjunto de nomes de cmdlet detectáveis e esperado. Use o verbo apropriado para que o usuário possa fazer uma avaliação rápida do que um cmdlet faz e descubram facilmente os recursos do sistema. Por exemplo, a linha de comando a seguir obtém uma lista de todos os comandos do sistema cujos nomes começam com "start": `get-command start-*`. Use substantivos nos seus cmdlets para diferenciar seus cmdlets de outros cmdlets. O substantivo indica o recurso no qual a operação será executada. A operação em si é representada pelo verbo.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Nomes de cmdlet: Caracteres que não podem ser usados (RD02)

Ao nomear cmdlets, não use nenhum dos seguintes caracteres especiais.

|Caractere|Nome|
|---------------|----------|
|#|sinal de número|
|,|comma|
|()|Parênteses|
|{}|chaves|
|[]|colchetes|
|&|e comercial|
|-|hífen **Observação:**  O hífen pode ser usado para separar o verbo de substantivo, mas não pode ser usado dentro do substantivo ou dentro do verbo.|
|/|marca de barra|
|\|barra invertida|
|$|Sinal de cifrão|
|^|Sinal de interpolação|
|;|Ponto e vírgula|
|:|Dois-pontos|
|"|aspas duplas|
|'|marca de aspas simples|
|<>|colchetes angulares|
|&#124;|barra vertical|
|?|ponto de interrogação|
|@|sinal de arroba|
|' | fazer escala (acento grave)|
|*|Asterisco|
|%|Sinal de porcentagem|
|+|Sinal de adição|
|=|Sinal de igual|
|~|tilda|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Nomes de parâmetros que não podem ser usados (RD03)

Windows PowerShell fornece um conjunto comum de parâmetros para todos os cmdlets e parâmetros adicionais que são adicionados em situações específicas. Ao criar seus próprios cmdlets, você não pode usar os seguintes nomes: Confirmar, Debug, ErrorAction, ErrorVariable, OutBuffer, OutVariable, WarningAction, WarningVariable, WhatIf e UseTransaction e detalhado. Para obter mais informações sobre esses parâmetros, consulte [nomes de parâmetro comuns](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Suporte a solicitações de confirmação (RD04)

Para cmdlets que executam uma operação que modifique o sistema, eles devem chamar o [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método solicitar uma confirmação e, em casos especiais, chamar o [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método. (O [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método deve ser chamado somente depois da [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método é chamado.)

Para fazer essas chamadas que o cmdlet deve especificar que ele oferece suporte a solicitações de confirmação, definindo o `SupportsShouldProcess` palavra-chave do atributo Cmdlet. Para obter mais informações sobre como definir esse atributo, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Se o atributo de Cmdlet de classe do cmdlet indica que o cmdlet oferece suporte a chamadas para o [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método e o cmdlet não conseguir fazer a chamada para o [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, o usuário pode modificar o sistema inesperadamente.

Use o [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para qualquer modificação do sistema. Uma preferência do usuário e o `Whatif` controle de parâmetro de [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. Em contraste, o [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) chamada executa uma verificação adicional para modificações potencialmente perigosas. Esse método não é controlado por nenhuma preferência do usuário ou o `Whatif` parâmetro. Se seu cmdlet chama o [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método, ele deve ter um `Force` parâmetro que ignora as chamadas para esses dois métodos e que continua com a operação. Isso é importante porque permite que o cmdlet a ser usado em scripts não interativo e hosts.

Se seus cmdlets do dão suporte a essas chamadas, o usuário pode determinar se a ação realmente deve ser executada. Por exemplo, o [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) cmdlet chamadas a [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método antes de parar um conjunto de processos críticos, incluindo o sistema, o Winlogon, e Spoolsrv processos.

Para obter mais informações sobre o suporte a esses métodos, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Suporte a parâmetro Force para sessões interativas (RD05)

Se seu cmdlet é usado interativamente, sempre forneça um parâmetro Force para substituir as ações interativas, como prompts ou a leitura de linhas de entrada). Isso é importante porque permite que o cmdlet a ser usado em scripts não interativo e hosts. Os métodos a seguir podem ser implementados por um host interativo.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Objetos de documento de saída (RD06)

Windows PowerShell usa os objetos que são escritos para o pipeline. Em ordem para que os usuários podem aproveitar os objetos que são retornados por cada cmdlet, você deve documentar os objetos que são retornados e você deve documentar o que os membros desses objetos retornados são usados para.

## <a name="code-guidelines"></a>Diretrizes de código

As diretrizes a seguir devem ser seguidas ao escrever o código do cmdlet. Quando você encontrar uma diretriz de código que se aplica à sua situação, certifique-se de examinar as diretrizes de Design para obter diretrizes semelhantes.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Derivar do Cmdlet ou Classes de PSCmdlet (RC01)

Um cmdlet deve derivar do [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) ou [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base. Os cmdlets que derivam de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe não dependem do tempo de execução do Windows PowerShell. Eles podem ser chamados diretamente de qualquer linguagem do Microsoft .NET Framework. Os cmdlets que derivam de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe dependem do tempo de execução do Windows PowerShell. Portanto, eles são executadas dentro de um espaço de execução.

Todas as classes de cmdlet que você implementar devem ser classes públicas. Para obter mais informações sobre essas classes de cmdlet, consulte [visão geral de Cmdlet](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Especificar o atributo de Cmdlet (RC02)

Para um cmdlet seja reconhecida pelo Windows PowerShell, sua classe do .NET Framework deve ser decorada com o atributo de Cmdlet. Esse atributo especifica os seguintes recursos do cmdlet.

- O par do verbo e substantivo que identifica o cmdlet.

- O conjunto de parâmetros padrão que é usado quando vários conjuntos de parâmetros são especificados. O conjunto de parâmetros padrão é usado quando o Windows PowerShell não tem informações suficientes para determinar qual parâmetro definido para usar.

- Indica se o cmdlet oferece suporte a chamadas para o [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. Esse método exibe uma mensagem de confirmação para o usuário antes que o cmdlet faz uma alteração no sistema. Para obter mais informações sobre como as solicitações de confirmação são feitas, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).

- Indica o nível de impacto (ou severidade) da ação associada com a mensagem de confirmação. Na maioria dos casos, o valor padrão de médio deve ser usado. Para obter mais informações sobre como o nível de impacto afeta as solicitações de confirmação são exibidas ao usuário, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).

Para obter mais informações sobre como declarar o atributo de cmdlet, consulte [declaração CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Substituir uma método (RC03) de processamento de entrada

Para o cmdlet participar do ambiente do Windows PowerShell, ele deve substituir pelo menos um dos seguintes *métodos de processamento de entrada*.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) esse método é chamado uma vez, e ele é usado para fornecer a funcionalidade de pré-processamento.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) esse método é chamado várias vezes, e ele é usado para fornecer a funcionalidade de registro por registro.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) esse método é chamado uma vez, e ele é usado para fornecer funcionalidade de pós-processamento.

### <a name="specify-the-outputtype-attribute-rc04"></a>Especificar o atributo OutputType (RC04)

O atributo OutputType (introduzido no Windows PowerShell 2.0) Especifica o tipo do .NET Framework que seu cmdlet retorna para o pipeline. Especifica o tipo de saída de seus cmdlets faz com os objetos retornados pelo cmdlet mais detectáveis por outros cmdlets. Para obter mais informações sobre a decoração de classe do cmdlet com esse atributo, consulte [declaração de atributo OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Não manterá os identificadores de objetos de saída (RC05)

O cmdlet não deve reter os identificadores para os objetos que são passados para o [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Esses objetos são passados para o próximo cmdlet no pipeline, ou eles são usados por um script. Se você mantiver os identificadores de objetos, duas entidades possuirá cada objeto, o que causa erros.

### <a name="handle-errors-robustly-rc06"></a>Tratar erros robusto (RC06)

Um ambiente de administração inerentemente detecta e faz as alterações importantes no sistema que você está administrando. Portanto, é vital que cmdlets tratar erros corretamente. Para obter mais informações sobre os registros de erro, consulte [relatório de erros do Windows PowerShell](./error-reporting-concepts.md).

- Quando um erro impede que um cmdlet continua a processar qualquer mais registros, ele é um erro de encerramento. O cmdlet deve chamar o [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método que faz referência a um [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto. Se uma exceção não é detectada pelo cmdlet, o tempo de execução do Windows PowerShell em si gera um erro de encerramento que contém menos informações.

- Para um erro de finalização que não interrompe na próxima operação de registro que é proveniente de pipeline (por exemplo, um registro produzido por um processo diferente), o cmdlet deve chamar o [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método faz referência a um [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto. Um exemplo de um erro de finalização é o erro que ocorre se um determinado processo falha ao parar. Chamar o [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método permite que o usuário para executar consistentemente as ações solicitadas e reter as informações de determinadas ações que falham. O cmdlet deve tratar cada registro independentemente do quanto possível.

- O [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) que é referenciado pelo objeto de [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) e [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) métodos requer uma exceção em seu núcleo. Siga as diretrizes de design do .NET Framework ao determinar a exceção a usar. Se o erro semanticamente é o mesmo que uma exceção existente, use essa exceção ou derivam dessa exceção. Caso contrário, derive uma nova exceção ou hierarquia de exceções diretamente a partir de [System. Exception](/dotnet/api/System.Exception) tipo.

Uma [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto também requer uma categoria de erro que agrupa os erros do usuário. O usuário pode exibir os erros com base na categoria, definindo o valor da `$ErrorView` variável do shell para CategoryView. As categorias possíveis são definidas pela [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeração.

- Se um cmdlet cria um novo thread, e se o código que está em execução nesse thread gera uma exceção sem tratamento, o Windows PowerShell não irá capturar o erro e encerrará o processo.

- Se um objeto tiver um código em seu destruidor que faz com que uma exceção sem tratamento, o Windows PowerShell não irá capturar o erro e encerrará o processo. Isso também ocorre se um objeto chama métodos Dispose que causam uma exceção sem tratamento.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Usar um módulo do Windows PowerShell para implantar seus Cmdlets (RC07)

Crie um módulo do Windows PowerShell para empacotar e implantar seus cmdlets. Suporte para módulos é introduzido no Windows PowerShell 2.0. Você pode usar os assemblies que contêm suas classes de cmdlet diretamente como arquivos de módulo binário (Isso é muito útil ao testar seus cmdlets), ou você pode criar um manifesto de módulo que faz referência os assemblies de cmdlet. (Você também pode adicionar snap-in de assemblies existentes ao usar módulos.) Para obter mais informações sobre os módulos, consulte [escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Consulte Também

[Diretrizes de desenvolvimento altamente incentivados](./strongly-encouraged-development-guidelines.md)

[Diretrizes de desenvolvimento de consultoria](./advisory-development-guidelines.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
