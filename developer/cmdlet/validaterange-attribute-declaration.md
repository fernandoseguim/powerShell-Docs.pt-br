---
title: Declaração de atributo ValidateRange | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857032"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="d45d3-102">Declaração de atributo ValidateRange</span><span class="sxs-lookup"><span data-stu-id="d45d3-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="d45d3-103">O atributo ValidateRange Especifica os valores mínimos e máximo (o intervalo) para o argumento do parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d45d3-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="d45d3-104">Esse atributo também pode ser usado por funções do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d45d3-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="d45d3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d45d3-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="d45d3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d45d3-106">Parameters</span></span>

<span data-ttu-id="d45d3-107">`MinRange` ([System. Object](/dotnet/api/system.object)) necessário.</span><span class="sxs-lookup"><span data-stu-id="d45d3-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="d45d3-108">Especifica o valor mínimo permitido.</span><span class="sxs-lookup"><span data-stu-id="d45d3-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="d45d3-109">`MaxRange` ([System. Object](/dotnet/api/system.object)) necessário.</span><span class="sxs-lookup"><span data-stu-id="d45d3-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="d45d3-110">Especifica o valor máximo permitido.</span><span class="sxs-lookup"><span data-stu-id="d45d3-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="d45d3-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d45d3-111">Remarks</span></span>

- <span data-ttu-id="d45d3-112">O tempo de execução do Windows PowerShell gera um erro de construção quando o valor da `MinRange` parâmetro é maior que o valor da `MaxRange` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d45d3-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="d45d3-113">O tempo de execução do Windows PowerShell gera um erro de validação nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="d45d3-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="d45d3-114">Quando o valor do argumento for menor do que o `MinRange` limite ou maior que o `MaxRange` limite.</span><span class="sxs-lookup"><span data-stu-id="d45d3-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="d45d3-115">Quando o argumento não é do mesmo tipo que o `MinRange` e o `MaxRange` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d45d3-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="d45d3-116">O atributo ValidateRange é definido pela [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="d45d3-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d45d3-117">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d45d3-117">See Also</span></span>

[<span data-ttu-id="d45d3-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="d45d3-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

<span data-ttu-id="d45d3-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="d45d3-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
