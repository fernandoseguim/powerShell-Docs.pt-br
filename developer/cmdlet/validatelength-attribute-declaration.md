---
title: Declaração de atributo ValidateLength | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794324"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="eb71b-102">Declaração de atributo ValidateLength</span><span class="sxs-lookup"><span data-stu-id="eb71b-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="eb71b-103">O atributo ValidateLength Especifica o número mínimo e máximo de caracteres para um argumento de parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb71b-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="eb71b-104">Esse atributo também pode ser usado por funções do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb71b-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="eb71b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb71b-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="eb71b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb71b-106">Parameters</span></span>

<span data-ttu-id="eb71b-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span><span class="sxs-lookup"><span data-stu-id="eb71b-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="eb71b-108">Especifica o número mínimo de caracteres permitidos.</span><span class="sxs-lookup"><span data-stu-id="eb71b-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="eb71b-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span><span class="sxs-lookup"><span data-stu-id="eb71b-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="eb71b-110">Especifica o número máximo de caracteres permitidos.</span><span class="sxs-lookup"><span data-stu-id="eb71b-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb71b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb71b-111">Remarks</span></span>

- <span data-ttu-id="eb71b-112">Para obter mais informações sobre como declarar esse atributo, consulte [como regras de validação de entrada declarar](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="eb71b-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="eb71b-113">Quando esse atributo não for usado, o argumento do parâmetro correspondente pode ser de qualquer comprimento.</span><span class="sxs-lookup"><span data-stu-id="eb71b-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="eb71b-114">O tempo de execução do Windows PowerShell gera um erro sob as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="eb71b-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="eb71b-115">Quando o valor da `MaxLength` parâmetro de atributo é menor que o valor da `MinLength` parâmetro do atributo.</span><span class="sxs-lookup"><span data-stu-id="eb71b-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="eb71b-116">Quando o `MaxLength` parâmetro de atributo é definido como 0.</span><span class="sxs-lookup"><span data-stu-id="eb71b-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="eb71b-117">Quando o argumento não é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="eb71b-117">When the argument is not a string.</span></span>

- <span data-ttu-id="eb71b-118">O atributo ValidateLength é definido pela [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="eb71b-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb71b-119">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="eb71b-119">See Also</span></span>

[<span data-ttu-id="eb71b-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="eb71b-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

<span data-ttu-id="eb71b-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="eb71b-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
