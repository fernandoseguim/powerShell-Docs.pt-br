---
title: Tipos de saída do Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853922"
---
# <a name="types-of-cmdlet-output"></a>Tipos de saída do cmdlet

O PowerShell fornece vários métodos que podem ser chamados pelos cmdlets para gerar a saída. Esses métodos usam uma operação específica para escrever a saída para um fluxo de dados específicos, como o fluxo de dados de sucesso ou o fluxo de dados de erro. Este artigo descreve os tipos de saída e os métodos usados para gerá-los.

## <a name="types-of-output"></a>Tipos de saída

### <a name="success-output"></a>Saída de êxito

Cmdlets pode relatar êxito, retornando um objeto que pode ser processado pelo comando Avançar no pipeline. Depois que o cmdlet executou com êxito sua ação, o cmdlet chama o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. É recomendável que você chame esse método em vez do [WriteLine](/dotnet/api/System.Console.WriteLine) ou [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) métodos.

Você pode fornecer um **PassThru** Troque o parâmetro para os cmdlets que normalmente não retornam objetos.
Quando o **PassThru** parâmetro de opção é especificado na linha de comando, é solicitado que o cmdlet para retornar um objeto. Para obter um exemplo de um cmdlet que tem um **PassThru** parâmetro, consulte [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Saída de erro

Cmdlets podem relatar erros. Quando ocorre um erro de terminação, o cmdlet gera uma exceção. Quando ocorre um erro de finalização, o cmdlet chama o [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método para enviar um registro de erro para o fluxo de dados de erro. Para obter mais informações sobre relatórios de erros, consulte [conceitos do Reporting erro](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Saída detalhada

Cmdlets podem fornecer informações úteis para você, enquanto o cmdlet corretamente está processando registros chamando o [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método. O método gera mensagens detalhadas que indicam como a ação continuar.

Por padrão, as mensagens detalhadas não são exibidas. Você pode especificar o **Verbose** parâmetro quando o cmdlet é executado para exibir essas mensagens. **Verbose** é um parâmetro comum que está disponível para todos os cmdlets.

### <a name="progress-output"></a>Saída de progresso

Cmdlets pode fornecer informações de progresso para você quando o cmdlet estiver executando tarefas que levam muito tempo para ser concluído, como copiar um diretório, recursivamente. Para exibir informações sobre o andamento do cmdlet chama o [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.

### <a name="debug-output"></a>Saída de depuração

Cmdlets pode fornecer mensagens de depuração que são úteis quando o código do cmdlet de solução de problemas. Para exibir informações de depuração do cmdlet chama o [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método.

Por padrão, as mensagens de depuração não são exibidas. Você pode especificar o **depurar** parâmetro quando o cmdlet é executado para exibir essas mensagens. **Depurar** é um parâmetro comum que está disponível para todos os cmdlets.

### <a name="warning-output"></a>Saída de aviso

Cmdlets pode exibir mensagens de aviso com a chamada a [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método.

Por padrão, as mensagens de aviso são exibidas. No entanto, você pode configurar mensagens de aviso usando o `$WarningPreference` variável ou usando o **Verbose** e **depurar** parâmetros quando o cmdlet for chamado.

## <a name="displaying-output"></a>Exibindo saída

Para todas as chamadas de método de gravação, a exibição de conteúdo é determinada pelas variáveis de tempo de execução específico. A exceção é o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Usando essas variáveis, você pode fazer apropriado escrever chamada no local correto em seu código e não se preocupar sobre quando ou se a saída deve ser exibida.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Acessar a funcionalidade de saída de um aplicativo host

Você também pode criar um cmdlet para acessar diretamente a funcionalidade de saída de um aplicativo host por meio do tempo de execução do PowerShell. Usando o APIs fornecidas pelo PowerShell, em vez de host [System. console](/dotnet/api/System.Console) ou [Forms](/dotnet/api/System.Windows.Forms) garante que seu cmdlet funcionará com uma variedade de hosts. Por exemplo: o **powershell.exe** host de console, o **powershell_ise.exe** host gráfico, o host de comunicação remota do PowerShell e hosts de terceiros.

## <a name="see-also"></a>Consulte também

[Conceitos de relatórios de erro](./error-reporting-concepts.md)

[Visão geral de cmdlet](./cmdlet-overview.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)