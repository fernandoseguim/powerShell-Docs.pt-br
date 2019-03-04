---
title: Como validar um conjunto de argumentos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861362"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="0cc3c-102">Como validar um conjunto de argumentos</span><span class="sxs-lookup"><span data-stu-id="0cc3c-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="0cc3c-103">Este exemplo mostra como especificar uma regra de validação que o tempo de execução do Windows PowerShell pode usar para verificar o argumento do parâmetro antes que o cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="0cc3c-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="0cc3c-104">Essa regra de validação fornece um conjunto de valores válidos para o argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0cc3c-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="0cc3c-105">Para obter mais informações sobre a classe que define esse atributo, consulte [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="0cc3c-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="0cc3c-106">Para validar um conjunto de argumentos</span><span class="sxs-lookup"><span data-stu-id="0cc3c-106">To validate an argument set</span></span>

- <span data-ttu-id="0cc3c-107">Adicione o atributo ValidateSet conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cc3c-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="0cc3c-108">Este exemplo especifica um conjunto de três valores possíveis para o `UserName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0cc3c-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

<span data-ttu-id="0cc3c-109">Para obter mais informações sobre como declarar esse atributo, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0cc3c-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0cc3c-110">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0cc3c-110">See Also</span></span>

[<span data-ttu-id="0cc3c-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="0cc3c-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="0cc3c-112">Declaração de atributo ValidateSet</span><span class="sxs-lookup"><span data-stu-id="0cc3c-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

<span data-ttu-id="0cc3c-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="0cc3c-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
