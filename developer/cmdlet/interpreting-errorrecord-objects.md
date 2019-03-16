---
title: Interpretando objetos ErrorRecord | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058769"
---
# <a name="interpreting-errorrecord-objects"></a>Interpretar objetos ErrorRecord

Na maioria dos casos, um [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto representa um erro não fatal gerado por um comando ou script. Erros de finalização também podem especificar as informações adicionais em um ErrorRecord por meio de [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) interface.

Se você quiser escrever um manipulador de erros em seu script ou um host para lidar com erros específicos que ocorrem durante a execução de comando ou script, você deve interpretar os [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto para determinar se ele representa a classe de erro que você deseja manipular.

Quando um cmdlet encontra uma terminação ou erro não fatal, ele deve criar um registro de erro que descreve a condição de erro. O aplicativo host deve investigar esses registros de erro e executar qualquer ação reduzirá o erro. O aplicativo host também deve investigar a registros de erro para erros de não encerramento que foram capazes de continuar, mas não conseguiu processar um registro, e ele deve investigar os registros de erro para erros de finalização que causou o pipeline parar.

> [!NOTE]
> Para erros de finalização, o cmdlet chamadas a [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método. Para erros de finalização, o cmdlet chama o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método.

## <a name="error-record-design"></a>Design de registros de erro

Registros de erro são projetados para fornecer informações de erro adicionais que não estão disponíveis em exceções, garantindo que as informações combinadas em cada registro de erro são exclusivas. Este exclusividade permite que o aplicativo de host inspecionar as diferentes partes do registro de erro para que ele pode identificar a condição de erro e a ação que o host deve executar.

## <a name="interpreting-error-records"></a>Interpretando os registros de erro

Você pode examinar as várias partes do registro de erro para identificar o erro. Essas partes incluem o seguinte:

- A categoria de erro

- A exceção de erro

- O identificador totalmente qualificado do erro (FQID)

- Outras informações

### <a name="the-error-category"></a>A categoria de erro

A categoria de erro do registro de erro é uma das constantes predefinidas fornecidas pelo [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeração. Essas informações estão disponíveis por meio de [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) propriedade da [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto.

O cmdlet pode especificar as categorias de CloseError, OpenError, InvalidType, ReadError e WriteError e outras categorias de erro. O aplicativo host pode usar a categoria de erro para capturar os grupos de erros.

### <a name="the-exception"></a>A exceção

A exceção incluída no registro de erro é fornecida pelo cmdlet e podem ser acessada por meio de [System.Management.Automation.ErrorRecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) propriedade do [ System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto.

Os aplicativos host podem usar o `is` palavra-chave para identificar que a exceção é de uma classe específica ou de uma classe derivada. É melhor para a ramificação no tipo de exceção, conforme mostrado no exemplo a seguir.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

Dessa forma, você capturar as classes derivadas. No entanto, há problemas se a exceção é desserializada.

### <a name="the-fqid"></a>O FQID

O FQID é a informação mais específica, que você pode usar para identificar o erro. É uma cadeia de caracteres que inclui um identificador definido pelo cmdlet, o nome da classe do cmdlet e a fonte que relatou o erro. Em geral, um registro de erro é análogo a um registro de evento de um log de eventos do Windows. O FQID é análogo à tupla a seguir, que identifica a classe do registro do evento: (*nome do log*, *fonte*, *ID do evento*).

O FQID foi projetado para ser inspecionado como uma única cadeia de caracteres. No entanto, os casos existem no qual o identificador de erro é projetado para ser analisado pelo aplicativo host. O exemplo a seguir é um identificador de erro totalmente qualificado bem formado.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

No exemplo anterior, o primeiro token é o identificador de erro, o que é seguido pelo nome da classe do cmdlet. O identificador de erro pode ser um único token, ou pode ser um identificador separado por ponto que permite a ramificação na inspeção do identificador. Não use espaço em branco ou pontuação no identificador de erro. É especialmente importante para não usar uma vírgula; uma vírgula é usada pelo Windows PowerShell para separar o identificador e o nome de classe do cmdlet.

### <a name="other-information"></a>Outras informações

O [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto também pode fornecer informações que descreve o ambiente no qual ocorreu o erro. Essas informações incluem itens como o objeto de destino que estava sendo processado quando o erro ocorreu, informações sobre invocação e detalhes do erro. Embora essas informações podem ser úteis para o aplicativo host, ele não é normalmente usado para identificar o erro. Essas informações estão disponíveis por meio das seguintes propriedades:

[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.ErrorRecord.InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.ErrorRecord.TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Adicionando relatórios de erros ao seu Cmdlet não fatal](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Relatório de erros do Windows PowerShell](./error-reporting-concepts.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
