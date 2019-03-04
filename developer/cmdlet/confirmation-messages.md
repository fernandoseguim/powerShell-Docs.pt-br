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
# <a name="confirmation-messages"></a><span data-ttu-id="f5570-102">Mensagens de confirmação</span><span class="sxs-lookup"><span data-stu-id="f5570-102">Confirmation Messages</span></span>

<span data-ttu-id="f5570-103">Aqui estão as mensagens de confirmação diferentes que podem ser exibidas, dependendo das variantes do [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos que são chamados.</span><span class="sxs-lookup"><span data-stu-id="f5570-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5570-104">Para o código de exemplo que mostra como solicitar confirmações, consulte [como a solicitação de confirmações](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="f5570-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="f5570-105">Especificação do recurso</span><span class="sxs-lookup"><span data-stu-id="f5570-105">Specifying the Resource</span></span>

<span data-ttu-id="f5570-106">Você pode especificar o recurso que está prestes a ser alterado ao chamar o [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="f5570-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="f5570-107">Nesse caso, você fornecer o recurso usando o `target` parâmetro do método e a operação é adicionado pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5570-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="f5570-108">Na seguinte mensagem, o texto "MyResource" é o recurso agiu e a operação é o nome do comando que faz a chamada.</span><span class="sxs-lookup"><span data-stu-id="f5570-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="f5570-109">Se o usuário seleciona **Yes** ou **Sim para tudo** para a confirmação da solicitação (conforme mostrado no exemplo a seguir), uma chamada para o [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é feito, o que faz com que uma segunda mensagem de confirmação a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="f5570-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="f5570-110">Especifica a operação e o recurso</span><span class="sxs-lookup"><span data-stu-id="f5570-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="f5570-111">Você pode especificar o recurso que está prestes a ser alterado e a operação que o comando está prestes a realizar chamando o [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="f5570-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="f5570-112">Nesse caso, você fornecer o recurso usando o `target` parâmetro e a operação usando o `target` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f5570-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="f5570-113">Na seguinte mensagem, o texto "MyResource" é o recurso agiu e "MyAction" é a operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="f5570-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="f5570-114">Se o usuário seleciona **Yes** ou **Sim para tudo** para a mensagem anterior, uma chamada para o [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é feita, o que faz com que um segunda mensagem de confirmação a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="f5570-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="f5570-115">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f5570-115">See Also</span></span>

<span data-ttu-id="f5570-116">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="f5570-116">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
