---
title: Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861212"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="b14ac-102">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="b14ac-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="b14ac-103">Especifica o conjunto de tipos do .NET que disparam a condição.</span><span class="sxs-lookup"><span data-stu-id="b14ac-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b14ac-104">Quando qualquer um dos tipos neste conjunto estiver presente, a condição for atendida.</span><span class="sxs-lookup"><span data-stu-id="b14ac-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="b14ac-105">Elemento DefaultSettings elemento (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansions (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition EnumerableExpansion (formato) EntrySelectedBy para Elemento de SelectionSetName EnumerableExpansion (formato) para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="b14ac-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b14ac-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b14ac-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b14ac-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b14ac-107">Attributes and Elements</span></span>

<span data-ttu-id="b14ac-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="b14ac-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b14ac-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b14ac-109">Attributes</span></span>

<span data-ttu-id="b14ac-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b14ac-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b14ac-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="b14ac-111">Child Elements</span></span>

<span data-ttu-id="b14ac-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b14ac-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b14ac-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="b14ac-113">Parent Elements</span></span>

|<span data-ttu-id="b14ac-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b14ac-114">Element</span></span>|<span data-ttu-id="b14ac-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b14ac-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b14ac-116">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="b14ac-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b14ac-117">Define a condição que deve existir para expandir os objetos da coleção desta definição.</span><span class="sxs-lookup"><span data-stu-id="b14ac-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b14ac-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b14ac-118">Text Value</span></span>

<span data-ttu-id="b14ac-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="b14ac-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b14ac-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="b14ac-120">Remarks</span></span>

<span data-ttu-id="b14ac-121">A condição de seleção pode especificar um conjunto de seleção ou um tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b14ac-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b14ac-122">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b14ac-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b14ac-123">Conjuntos de seleção são grupos comuns de objetos .NET que podem ser usados por qualquer exibição que define o arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="b14ac-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b14ac-124">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b14ac-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b14ac-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b14ac-125">See Also</span></span>

[<span data-ttu-id="b14ac-126">Definindo conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="b14ac-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b14ac-127">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="b14ac-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="b14ac-128">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b14ac-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
