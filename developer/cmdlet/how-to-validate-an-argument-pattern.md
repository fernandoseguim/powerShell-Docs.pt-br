---
title: Como validar um padrão de argumento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855062"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="26007-102">Como validar um padrão de argumentos</span><span class="sxs-lookup"><span data-stu-id="26007-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="26007-103">Este exemplo mostra como especificar uma regra de validação que o tempo de execução do Windows PowerShell pode usar para verificar o padrão de caracteres do argumento de parâmetro antes que o cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="26007-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="26007-104">Você pode definir essa regra de validação ao declarar o atributo ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="26007-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="26007-105">Para obter mais informações sobre a classe que define esse atributo, consulte [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="26007-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="26007-106">Para validar um padrão de argumento</span><span class="sxs-lookup"><span data-stu-id="26007-106">To validate an argument pattern</span></span>

- <span data-ttu-id="26007-107">Adicione o atributo de validação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="26007-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="26007-108">Este exemplo especifica um padrão de quatro dígitos, onde cada dígito tem um valor de 0 a 9.</span><span class="sxs-lookup"><span data-stu-id="26007-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

<span data-ttu-id="26007-109">Para obter mais informações sobre como declarar esse atributo, consulte [declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="26007-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26007-110">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="26007-110">See Also</span></span>

[<span data-ttu-id="26007-111">Declaração de atributo ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="26007-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

<span data-ttu-id="26007-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="26007-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
