---
title: Como solicitar confirmações | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 8cfbcacf93733667ffba63a252c86518c0919b57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863402"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="d9f76-102">Como solicitar confirmações</span><span class="sxs-lookup"><span data-stu-id="d9f76-102">How to Request Confirmations</span></span>

<span data-ttu-id="d9f76-103">Este exemplo mostra como chamar o [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para solicitar confirmações das usuário antes de uma ação é executada.</span><span class="sxs-lookup"><span data-stu-id="d9f76-103">This example shows how to call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9f76-104">Para obter mais informações sobre como o Windows PowerShell lida com essas solicitações, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="d9f76-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="d9f76-105">Para solicitar uma confirmação</span><span class="sxs-lookup"><span data-stu-id="d9f76-105">To request confirmation</span></span>

1. <span data-ttu-id="d9f76-106">Certifique-se de que o `SupportsShouldProcess` parâmetro do Cmdlet atributo for definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="d9f76-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="d9f76-107">(Para funções isso é um parâmetro do atributo CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="d9f76-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="d9f76-108">Adicionar um `Force` parâmetro ao cmdlet, para que o usuário pode substituir uma solicitação de confirmação.</span><span class="sxs-lookup"><span data-stu-id="d9f76-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="d9f76-109">Adicionar um `if` instrução que usa o valor de retorno de [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para determinar se o [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="d9f76-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="d9f76-110">Adicione um segundo `if` instrução que usa o valor de retorno de [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método e o valor da `Force` parâmetro para determinar se a operação deve ser executada.</span><span class="sxs-lookup"><span data-stu-id="d9f76-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="d9f76-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9f76-111">Example</span></span>

<span data-ttu-id="d9f76-112">No exemplo de código a seguir, o [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos são chamados de dentro do substituição do [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="d9f76-112">In the following code example, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="d9f76-113">No entanto, você também pode chamar esses métodos de outra métodos de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="d9f76-113">However, you can also call these methods from the other input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="d9f76-114">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d9f76-114">See Also</span></span>

<span data-ttu-id="d9f76-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="d9f76-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
