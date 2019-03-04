---
title: Declaração de atributo ValidateSet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861202"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="41565-102">Declaração de atributo ValidateSet</span><span class="sxs-lookup"><span data-stu-id="41565-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="41565-103">O atributo ValidateSetAttribute Especifica um conjunto de valores possíveis para um argumento de parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41565-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="41565-104">Esse atributo também pode ser usado por funções do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41565-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="41565-105">Quando esse atributo for especificado, o tempo de execução do Windows PowerShell determina se o argumento fornecido para o parâmetro de cmdlet corresponde a um elemento no conjunto de elemento fornecido.</span><span class="sxs-lookup"><span data-stu-id="41565-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="41565-106">O cmdlet é executado apenas se o argumento do parâmetro com um elemento no conjunto.</span><span class="sxs-lookup"><span data-stu-id="41565-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="41565-107">Se nenhuma correspondência for encontrada, um erro será gerado pelo tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41565-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="41565-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41565-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="41565-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41565-109">Parameters</span></span>

<span data-ttu-id="41565-110">`ValidValues` ([System. String](/dotnet/api/System.String)) necessário.</span><span class="sxs-lookup"><span data-stu-id="41565-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="41565-111">Especifica os valores de elemento de parâmetro válido.</span><span class="sxs-lookup"><span data-stu-id="41565-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="41565-112">O exemplo a seguir mostra como especificar um elemento ou em vários elementos.</span><span class="sxs-lookup"><span data-stu-id="41565-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="41565-113">`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional.</span><span class="sxs-lookup"><span data-stu-id="41565-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="41565-114">O valor padrão de `true` indica que o caso é ignorado.</span><span class="sxs-lookup"><span data-stu-id="41565-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="41565-115">Um valor de `false` faz com que o cmdlet diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="41565-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="41565-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="41565-116">Remarks</span></span>

- <span data-ttu-id="41565-117">Esse atributo pode ser usado apenas uma vez por parâmetro.</span><span class="sxs-lookup"><span data-stu-id="41565-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="41565-118">Se o valor do parâmetro for uma matriz, cada elemento da matriz deve corresponder a um elemento do conjunto de atributos.</span><span class="sxs-lookup"><span data-stu-id="41565-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="41565-119">O atributo ValidateSetAttribute é definido pela [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="41565-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="41565-120">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="41565-120">See Also</span></span>

[<span data-ttu-id="41565-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="41565-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

<span data-ttu-id="41565-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="41565-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
