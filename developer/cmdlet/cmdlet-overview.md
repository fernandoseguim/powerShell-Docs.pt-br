---
title: Visão geral de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: f8a8c9300d1ac811c7fbbf7050dd24f78306db8f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056661"
---
# <a name="cmdlet-overview"></a>Visão geral do cmdlet

Um cmdlet é um comando simples que é usado no ambiente do Windows PowerShell. O tempo de execução do Windows PowerShell invoca esses cmdlets dentro do contexto de scripts de automação que são fornecidos na linha de comando. O tempo de execução do Windows PowerShell também invoca-los programaticamente por meio de APIs do Windows PowerShell.

## <a name="cmdlets"></a>Cmdlets

Cmdlets de executar uma ação e normalmente retornam um objeto do Microsoft .NET Framework para o próximo comando no pipeline. Para gravar um cmdlet, você deve implementar uma classe cmdlet que é derivada de uma das duas classes base do cmdlet especializado. A classe derivada deve:

- Declara um atributo que identifica a classe derivada como um cmdlet.

- Defina as propriedades públicas que são decoradas com atributos que identificam as propriedades públicas como parâmetros de cmdlet.

- Substitua um ou mais dos métodos para processar os registros de processamento de entrada.

Você pode carregar o assembly que contém a classe diretamente usando o [Import-Module](/powershell/module/microsoft.powershell.core/import-module) cmdlet, ou você pode criar um aplicativo host que carrega o assembly usando o [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API. Os dois métodos fornecem acesso programático e de linha de comando para a funcionalidade do cmdlet.

## <a name="cmdlet-terms"></a>Termos de cmdlet

Os seguintes termos são usados com frequência na documentação de cmdlet do Windows PowerShell:

- **Atributo de cmdlet**: Um atributo do .NET Framework que é usado para declarar uma classe cmdlet como um cmdlet. Embora o Windows PowerShell usa vários outros atributos que são opcionais, o atributo de Cmdlet é obrigatório. Para obter mais informações sobre esse atributo, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

- **Parâmetro de cmdlet**: As propriedades públicas que definem os parâmetros que estão disponíveis para o usuário ou para o aplicativo que está executando o cmdlet. Cmdlets pode ter exigido, nomeada e posicionais, e *alternar* parâmetros. Parâmetros de opção permitem que você defina os parâmetros que são avaliados apenas se os parâmetros são especificados na chamada. Para obter mais informações sobre os diferentes tipos de parâmetros, consulte [parâmetros de Cmdlet](./cmdlet-parameters.md).

- **Conjunto de parâmetros**: Um grupo de parâmetros que podem ser usados no mesmo comando para executar uma ação específica. Um cmdlet pode ter vários conjuntos de parâmetros, mas cada conjunto de parâmetros deve ter pelo menos um parâmetro que seja exclusivo. Cmdlet bom design fortemente sugere que o parâmetro unique também ser um parâmetro obrigatório. Para obter mais informações sobre conjuntos de parâmetros, consulte [conjuntos de parâmetros do Cmdlet](./cmdlet-parameter-sets.md).

- **Parâmetro dinâmico**: Um parâmetro que é adicionado ao cmdlet em tempo de execução. Normalmente, os parâmetros dinâmicos são adicionados ao cmdlet quando outro parâmetro é definido como um valor específico. Para obter mais informações sobre parâmetros dinâmicos, consulte [parâmetros de Cmdlet dinâmicos](./cmdlet-dynamic-parameters.md).

- **Método de processamento de entrada**: Um método que um cmdlet pode usar para processar os registros que ele recebe como entrada. Os métodos de processamento de entrada incluem o [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método, o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, o [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método e o [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) método. Quando você implementa um cmdlet, você deve substituir pelo menos um dos [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)e [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) métodos. Normalmente, o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) é o método que você substituir porque ele é chamado para cada registro que o cmdlet processa. Em contraste, o [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método e o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método são chamados uma vez para executar Pré-processando ou pós-processamento dos registros. Para obter mais informações sobre esses métodos, consulte [métodos de processamento de entrada](./cmdlet-input-processing-methods.md).

- **Recurso ShouldProcess**: Windows PowerShell permite que você crie cmdlets que solicita ao usuário comentários antes que o cmdlet faz uma alteração no sistema. Para usar esse recurso, o cmdlet deve declarar que ele suporta o recurso de ShouldProcess, quando você declarar o atributo de Cmdlet, e o cmdlet deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos de dentro de um método de processamento de entrada. Para obter mais informações sobre como dar suporte a funcionalidade de ShouldProcess, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).

- **Transação**: Um grupo lógico de comandos que são tratados como uma única tarefa. Automaticamente, a tarefa falhará se qualquer comando no grupo falha e o usuário tem a opção de aceitar ou rejeitar as ações executadas na transação. Para participar de uma transação, o cmdlet deve declarar que ele oferece suporte a transações quando o atributo do Cmdlet é declarado. Suporte para transações foi introduzido no Windows PowerShell 2.0. Para obter mais informações sobre transações, consulte [Windows PowerShell transações](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710).

## <a name="how-cmdlets-differ-from-commands"></a>Como os Cmdlets diferem dos comandos

Cmdlets diferem dos comandos em outros ambientes shell de comando das seguintes maneiras:

- Os cmdlets são instâncias de classes do .NET Framework; eles não são executáveis autônomos.

- Cmdlets podem ser criados de apenas uma dúzia de linhas de código.

- Cmdlets geralmente fazer seus próprios de análise, apresentação de erro ou a formatação de saída. Análise, apresentação de erro e formatação de saída são manipuladas pelo tempo de execução do Windows PowerShell.

- Objetos do pipeline em vez de fluxos de texto de entrada do processo de cmdlets e cmdlets normalmente passar os objetos como saída para o pipeline.

- Os cmdlets são orientados a registros porque eles processam um único objeto por vez.

## <a name="cmdlet-base-classes"></a>Classes Base do cmdlet

Windows PowerShell dá suporte a cmdlets derivados de duas classes base.

- A maioria dos cmdlets são baseados nas classes do .NET Framework que derivam de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe base. Derivar desta classe permite que um cmdlet para usar o conjunto mínimo de dependências em tempo de execução do Windows PowerShell. Isso tem dois benefícios. A primeira vantagem é que os objetos de cmdlet são menores, e você é menos prováveis de ser afetado por alterações no tempo de execução do Windows PowerShell. A segunda vantagem é que, se for necessário, você pode criar diretamente uma instância do objeto de cmdlet e, em seguida, invocá-lo diretamente, em vez de invocá-lo por meio de runtime do Windows PowerShell.

- Os cmdlets mais complexos são baseados em classes do .NET Framework que derivam de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base. Derivar desta classe oferece muito mais acesso ao tempo de execução do Windows PowerShell. Esse acesso permite que seu cmdlet chamar scripts, para acessar provedores e para acessar o estado de sessão atual. (Para acessar o estado da sessão atual, você obter e definir variáveis de sessão e preferências.) No entanto, derivar desta classe aumenta o tamanho do objeto de cmdlet, e isso significa que seu cmdlet é mais estreitamente ligado para a versão atual do tempo de execução do Windows PowerShell.

Em geral, a menos que você precisa ter o acesso estendido para o tempo de execução do Windows PowerShell, você deve derivar do [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. No entanto, o tempo de execução do Windows PowerShell tem recursos de registro em log extensivo para a execução de cmdlets. Se seu modelo de auditoria depende esse registro em log, você pode impedir a execução do cmdlet de dentro de outro cmdlet derivando de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.

## <a name="input-processing-methods"></a>Métodos de processamento de entrada

O [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fornece os seguintes métodos virtuais que são usados para processar registros. Todas as classes de cmdlets derivados devem substituir um ou mais dos três primeiros métodos:

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Usado para fornecer funcionalidade opcional única de pré-processamento para o cmdlet.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Usado para fornecer funcionalidade de processamento de registro por registro para o cmdlet. O [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método pode ser chamado qualquer número de vezes ou, de forma alguma, dependendo da entrada do cmdlet.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Usado para fornecer funcionalidade opcional única de pós-processamento para o cmdlet.

- [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Usado para parar o processamento quando o usuário para o cmdlet de forma assíncrona (por exemplo, pressionando CTRL + C).

Para obter mais informações sobre esses métodos, consulte [métodos de processamento de entrada do Cmdlet](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Atributos de cmdlet

Windows PowerShell define vários atributos do .NET Framework que são usados para gerenciar os cmdlets e para especificar a funcionalidade comum que é fornecido pelo Windows PowerShell e que podem ser necessárias pelo cmdlet. Por exemplo, os atributos são usados para designar uma classe como um cmdlet, para especificar os parâmetros do cmdlet e solicitar a validação de entrada para que os desenvolvedores do cmdlet não é necessário implementar essa funcionalidade em seu código do cmdlet. Para obter mais informações sobre atributos, consulte [atributos do Windows PowerShell](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Nomes dos cmdlets

Windows PowerShell usa um par de nome do verbo e substantivo para cmdlets de nome. Por exemplo, o `Get-Command` cmdlet incluído no Windows PowerShell é usado para obter todos os cmdlets que estão registrados no shell de comando. O verbo identifica a ação que executa o cmdlet e o substantivo identifica o recurso no qual o cmdlet executa sua ação.

Esses nomes são especificados quando a classe do .NET Framework é declarada como um cmdlet. Para obter mais informações sobre como declarar uma classe do .NET Framework como um cmdlet, consulte [declaração de atributo do Cmdlet](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Escrevendo código do Cmdlet

Este documento fornece duas maneiras de descobrir como o código do cmdlet é gravado. Se você preferir ver o código sem muita explicação, consulte [exemplos de código do Cmdlet](./examples-of-cmdlet-code.md). Se você preferir obter mais explicações sobre o código, consulte o [GetProc Tutorial](./getproc-tutorial.md), [StopProc Tutorial](./stopproc-tutorial.md), ou [SelectStr Tutorial](./selectstr-tutorial.md) tópicos.

Para obter mais informações sobre as diretrizes para gravar cmdlets, consulte [diretrizes de desenvolvimento do Cmdlet](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Consulte Também

[Conceitos de Cmdlet do PowerShell do Windows](./windows-powershell-cmdlet-concepts.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
