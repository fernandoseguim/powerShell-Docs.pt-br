---
title: Expanda o elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858572"
---
# <a name="expand-element-format"></a><span data-ttu-id="347c7-102">Elemento Expand (formato)</span><span class="sxs-lookup"><span data-stu-id="347c7-102">Expand Element (Format)</span></span>

<span data-ttu-id="347c7-103">Especifica como o objeto de coleção é expandido para esta definição.</span><span class="sxs-lookup"><span data-stu-id="347c7-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="347c7-104">Configuração (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) EnumerableExpansion elemento (formato) expanda elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="347c7-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="347c7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="347c7-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="347c7-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="347c7-106">Attributes and Elements</span></span>

<span data-ttu-id="347c7-107">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Expand` elemento.</span><span class="sxs-lookup"><span data-stu-id="347c7-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="347c7-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="347c7-108">Attributes</span></span>

<span data-ttu-id="347c7-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="347c7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="347c7-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="347c7-110">Child Elements</span></span>

<span data-ttu-id="347c7-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="347c7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="347c7-112">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="347c7-112">Parent Elements</span></span>

|<span data-ttu-id="347c7-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="347c7-113">Element</span></span>|<span data-ttu-id="347c7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="347c7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="347c7-115">Elemento EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="347c7-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="347c7-116">Define os objetos são expandidos quando eles são exibidos em uma exibição de coleção de .NET como específica.</span><span class="sxs-lookup"><span data-stu-id="347c7-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="347c7-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="347c7-117">Text Value</span></span>

<span data-ttu-id="347c7-118">Especifique um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="347c7-118">Specify one of the following values:</span></span>

- <span data-ttu-id="347c7-119">EnumOnly: Exibe somente as propriedades dos objetos na coleção.</span><span class="sxs-lookup"><span data-stu-id="347c7-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="347c7-120">CoreOnly: Exibe apenas as propriedades do objeto da coleção.</span><span class="sxs-lookup"><span data-stu-id="347c7-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="347c7-121">Ambos: Exibe as propriedades dos objetos na coleção e as propriedades do objeto da coleção.</span><span class="sxs-lookup"><span data-stu-id="347c7-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="347c7-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="347c7-122">Remarks</span></span>

<span data-ttu-id="347c7-123">Esse elemento é usado para definir como os objetos de coleção e os objetos na coleção são exibidos.</span><span class="sxs-lookup"><span data-stu-id="347c7-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="347c7-124">Nesse caso, um objeto de coleção refere-se a qualquer objeto que dá suporte a **System.Collections.ICollection** interface.</span><span class="sxs-lookup"><span data-stu-id="347c7-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="347c7-125">O comportamento padrão é exibir somente as propriedades dos objetos na coleção.</span><span class="sxs-lookup"><span data-stu-id="347c7-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="347c7-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="347c7-126">See Also</span></span>

[<span data-ttu-id="347c7-127">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="347c7-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
