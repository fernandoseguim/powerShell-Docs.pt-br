---
title: Mensagens de confirmação | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861412"
---
# <a name="confirmation-messages"></a>Mensagens de confirmação

Aqui estão as mensagens de confirmação diferentes que podem ser exibidas, dependendo das variantes do [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos que são chamados.

> [!IMPORTANT]
> Para o código de exemplo que mostra como solicitar confirmações, consulte [como a solicitação de confirmações](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Especificação do recurso

Você pode especificar o recurso que está prestes a ser alterado ao chamar o [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método. Nesse caso, você fornecer o recurso usando o `target` parâmetro do método e a operação é adicionado pelo Windows PowerShell. Na seguinte mensagem, o texto "MyResource" é o recurso agiu e a operação é o nome do comando que faz a chamada.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Se o usuário seleciona **Yes** ou **Sim para tudo** para a confirmação da solicitação (conforme mostrado no exemplo a seguir), uma chamada para o [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é feito, o que faz com que uma segunda mensagem de confirmação a ser exibido.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Especifica a operação e o recurso

Você pode especificar o recurso que está prestes a ser alterado e a operação que o comando está prestes a realizar chamando o [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método. Nesse caso, você fornecer o recurso usando o `target` parâmetro e a operação usando o `target` parâmetro. Na seguinte mensagem, o texto "MyResource" é o recurso agiu e "MyAction" é a operação a ser executada.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Se o usuário seleciona **Yes** ou **Sim para tudo** para a mensagem anterior, uma chamada para o [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é feita, o que faz com que um segunda mensagem de confirmação a ser exibido.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
