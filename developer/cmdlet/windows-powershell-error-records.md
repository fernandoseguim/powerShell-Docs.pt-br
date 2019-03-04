---
title: Erro do Windows PowerShell registra | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: bbe04a8fb556f0f6807bc0eae6634e3cf505759e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861972"
---
# <a name="windows-powershell-error-records"></a>Registros de erros do Windows PowerShell

Cmdlets deve passar uma [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto que identifica a condição de erro para erros de finalização e finalização.

O [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto contém as seguintes informações:

- A exceção que descreve o erro. Geralmente, isso é uma exceção que o cmdlet capturados e convertido em um registro de erro. Todos os registros de erro devem conter uma exceção.

Se o cmdlet não capturar uma exceção, ele deve criar uma nova exceção e escolher a classe de exceção que melhor descreve a condição de erro. No entanto, não é necessário lançar a exceção, pois ele pode ser acessado por meio de [System.Management.Automation.Errorrecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) propriedade do [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto.

- Um identificador de erro que fornece um designador de destino que pode ser usado para fins de diagnóstico e por scripts do Windows PowerShell para lidar com condições de erro específicas com manipuladores de erro específico. Todos os registros de erro devem conter um identificador de erro (consulte o identificador do erro).

- Uma categoria de erro que fornece um designador geral que pode ser usado para fins de diagnóstico. Todos os registros de erro devem especificar uma categoria de erro (consulte a categoria de erro).

- Uma mensagem de erro de substituição opcionais e uma ação recomendada (consulte a mensagem de erro de substituição).

- Informações de chamada opcional sobre o cmdlet que gerou o erro. Essas informações são especificadas pelo Windows PowerShell (consulte a mensagem de invocação).

- O objeto de destino que estava sendo processado quando o erro ocorreu. Isso pode ser o objeto de entrada, ou pode ser outro objeto que estava processando a seu cmdlet. Por exemplo, para o comando `remove-item -recurse c:\somedirectory`, o erro pode ser uma instância de um objeto FileInfo para "c:\somedirectory\lockedfile". As informações de objeto de destino são opcionais.

## <a name="error-identifier"></a>Identificador do erro

Quando você cria um registro de erro, especifique um identificador que designa a condição de erro dentro do seu cmdlet. Windows PowerShell combina o identificador de destino com o nome do seu cmdlet para criar um identificador de erro totalmente qualificado. O identificador totalmente qualificado de erro pode ser acessado por meio de [System.Management.Automation.Errorrecord.Fullyqualifiederrorid*](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) propriedade do [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)objeto. O identificador de erro não está disponível por si só. Ele está disponível apenas como parte do identificador de erro totalmente qualificado.

Use as diretrizes a seguir para gerar identificadores de erro quando você cria registros de erro:

- Use identificadores de erro específicas a uma condição de erro. Os identificadores de erro de destino para fins de diagnóstico e de scripts que lidar com condições de erro específicas com manipuladores de erro específico. Um usuário deve ser capaz de usar o identificador de erro para identificar o erro e sua origem. Identificadores de erro também habilitar o relatório para condições de erro específico de exceções existentes para que o novo subclasses de exceção não são necessárias.

- Em geral, atribua identificadores de erro diferentes para diferentes caminhos de código. O usuário final se beneficia da identificadores específicos. Geralmente, cada caminho de código que chama [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) tem seu próprio identificador. Como regra, defina um novo identificador quando você define uma nova cadeia de caracteres de modelo para a mensagem de erro e vice-versa. Não use a mensagem de erro como um identificador.

- Quando você publica o código usando um identificador de erro específica, você estabelece que a semântica de erros com esse identificador para o seu produto completo do ciclo de vida de suporte. Não reutilize-lo em um contexto que é semanticamente diferente do contexto original. Se alterar a semântica desse erro, crie e, em seguida, use um novo identificador.

- Em geral, você deve usar um identificador de erro específica somente para exceções de um determinado tipo CLR. Se o tipo da exceção ou o tipo do objeto de destino for alterada, criar e, em seguida, usar um novo identificador.

- Escolha o texto para o identificador de erro concisa corresponde ao erro que você está relatando. Use as convenções de nomenclatura e capitalização do padrão do .NET Framework. Não use espaço em branco ou pontuação. Não localize os identificadores de erro.

- Não gere dinamicamente os identificadores de erro de forma não reproduzíveis. Por exemplo, não incorporam informações de erro, como uma ID de processo. Identificadores de erro são úteis apenas se eles correspondem aos identificadores de erro vistos por outros usuários que estão tendo a mesma condição de erro.

## <a name="error-category"></a>Categoria de erro

Quando você cria um registro de erro, especifique a categoria do erro usando uma das constantes definidas pelo [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeração. Windows PowerShell usa a categoria de erro para exibir informações de erro quando os usuários definir as `$ErrorView` variável para `"CategoryView"`.

Evite usar o [System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified) constante. Se você tiver quaisquer informações sobre o erro ou sobre a operação que causou o erro, escolha a categoria que melhor descreve o erro ou a operação, mesmo se a categoria não é uma correspondência perfeita.

As informações exibidas pelo Windows PowerShell são conhecidas como a cadeia de caracteres de exibição de categoria e baseia-se nas propriedades do [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) classe. (Essa classe é acessada por meio de erro [System.Management.Automation.Errorrecord.Categoryinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) propriedade.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

A lista a seguir descreve as informações exibidas:

- Categoria: Windows PowerShell-definido [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) constante.

- TargetName: Por padrão, o nome do objeto o cmdlet estava processando quando ocorreu o erro. Ou outra cadeia de caracteres definida pelo cmdlet.

- TargetType: Por padrão, o tipo de objeto de destino. Ou outra cadeia de caracteres definida pelo cmdlet.

- Atividade: Por padrão, o nome do cmdlet que criou o registro de erro. Ou alguns outra cadeia definida pelo cmdlet.

- Motivo: Por padrão, o tipo de exceção. Ou outra cadeia de caracteres definida pelo cmdlet.

## <a name="replacement-error-message"></a>Mensagem de erro de substituição

Quando você desenvolve um registro de erro para um cmdlet, a mensagem de erro padrão para o erro é proveniente do texto da mensagem padrão na [System.Exception.Message](/dotnet/api/System.Exception.Message) propriedade. Esta é uma propriedade de somente leitura cujo texto da mensagem destina-se apenas para fins de depuração (de acordo com as diretrizes do .NET Framework). É recomendável que você crie uma mensagem de erro que substitui ou amplia o texto da mensagem padrão. Verifique a mensagem mais fácil de usar e mais específicas para o cmdlet.

A mensagem de substituição é fornecida por um [System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails) objeto. Use um dos construtores a seguir deste objeto, pois elas fornecem informações de localização adicional que podem ser usadas pelo Windows PowerShell.

- [ErrorDetails.ErrorDetails (Cmdlet, a cadeia de caracteres, cadeia de caracteres, objeto\[System.Management.Automation.Errordetails.%23Ctor%28System.Management.Automation.Cmdlet%2Csystem.String%2Csystem.String%2Csystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Use esse construtor, se sua cadeia de caracteres de modelo é uma cadeia de caracteres de recurso no mesmo assembly no qual o cmdlet é implementado ou se você deseja carregar a cadeia de caracteres de modelo por meio de uma substituição do [System.Management.Automation.Cmdlet.Getresourcestring* ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) método.

- [ErrorDetails.ErrorDetails (Assembly, a cadeia de caracteres, a cadeia de caracteres, objeto\[System.Management.Automation.Errordetails.%23Ctor%28System.Reflection.Assembly%2Csystem.String%2Csystem.String%2Csystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Use esse construtor, se a cadeia de caracteres de modelo está em outro assembly, e você não carregá-la por meio de uma substituição de [System.Management.Automation.Cmdlet.Getresourcestring*](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

A mensagem de substituição deve estar de acordo com as diretrizes de design do .NET Framework para gravar mensagens de exceção com uma pequena diferença. O estado de diretrizes que mensagens de exceção devem ser escritas para desenvolvedores. Essas mensagens de substituição devem ser escritas para o usuário do cmdlet.

A mensagem de erro de substituição deve ser adicionada antes do [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) são chamados de métodos . Para adicionar uma mensagem de substituição, defina as [System.Management.Automation.Errorrecord.Errordetails*](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) propriedade do registro de erro. Quando essa propriedade é definida, o Windows PowerShell exibe a [System.Management.Automation.Errordetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) propriedade em vez do texto da mensagem padrão.

## <a name="recommended-action-information"></a>Recomendado de informações sobre a ação

O [System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails) objeto também pode fornecer informações sobre quais ações são recomendadas quando ocorrer o erro.

## <a name="invocation-information"></a>Informações de invocação

Quando usa um cmdlet [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) para relatar um registro de erro, o Windows PowerShell adiciona automaticamente as informações que descrevem o comando que foi invocado quando o erro ocorreu. Essas informações são fornecidas por um [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) objeto que contém o nome do cmdlet que foi invocado pelo comando, o comando em si e as informações sobre o pipeline ou script. Essa propriedade é somente leitura.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Relatório de erros do Windows PowerShell](./error-reporting-concepts.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
