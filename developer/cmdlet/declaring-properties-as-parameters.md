---
title: Declarando propriedades como parâmetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861372"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="7e49a-102">Declarar propriedades como parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e49a-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="7e49a-103">Este tópico fornece informações básicas, que você deve compreender antes de você declarar os parâmetros de um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7e49a-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="7e49a-104">Para declarar os parâmetros de um cmdlet em sua classe do cmdlet, definir as propriedades públicas que representam cada parâmetro e, em seguida, adicione um ou mais atributos de parâmetro para cada propriedade.</span><span class="sxs-lookup"><span data-stu-id="7e49a-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="7e49a-105">O tempo de execução do Windows PowerShell usa os atributos de parâmetro para identificar a propriedade como um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7e49a-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="7e49a-106">A sintaxe básica para declarar o atributo de parâmetro é `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="7e49a-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="7e49a-107">Aqui está um exemplo de uma propriedade definida como um parâmetro obrigatório.</span><span class="sxs-lookup"><span data-stu-id="7e49a-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="7e49a-108">Aqui estão algumas coisas a serem lembrados sobre parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7e49a-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="7e49a-109">Um parâmetro deve ser explicitamente marcado como público.</span><span class="sxs-lookup"><span data-stu-id="7e49a-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="7e49a-110">Parâmetros que não são marcados como padrão público para interno e não serão encontrados pelo tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e49a-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="7e49a-111">Parâmetros devem ser definidos como tipos do Microsoft .NET Framework para fornecer melhor validação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7e49a-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="7e49a-112">Por exemplo, os parâmetros que são restritos a um valor fora do conjunto de valores devem ser definidos como um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="7e49a-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="7e49a-113">Parâmetros que usam um valor de identificador de recurso uniforme (URI) devem ser do tipo [System. URI](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="7e49a-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="7e49a-114">Evite parâmetros de cadeias de caracteres básicas para propriedades de texto de forma tudo, exceto livre.</span><span class="sxs-lookup"><span data-stu-id="7e49a-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="7e49a-115">Você pode adicionar um parâmetro para qualquer número de conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7e49a-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="7e49a-116">Para obter mais informações sobre conjuntos de parâmetros, consulte [conjuntos de parâmetros do Cmdlet](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7e49a-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="7e49a-117">Windows PowerShell também fornece um conjunto de parâmetros comuns que ficam disponíveis automaticamente para cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7e49a-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="7e49a-118">Para obter mais informações sobre esses parâmetros e seus aliases, consulte [comum de parâmetros do Cmdlet](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="7e49a-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e49a-119">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="7e49a-119">See Also</span></span>

[<span data-ttu-id="7e49a-120">Parâmetros comuns de cmdlet</span><span class="sxs-lookup"><span data-stu-id="7e49a-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="7e49a-121">Tipos de parâmetro de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7e49a-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

<span data-ttu-id="7e49a-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="7e49a-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
