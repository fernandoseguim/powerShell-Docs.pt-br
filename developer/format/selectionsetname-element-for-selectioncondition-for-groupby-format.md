---
title: Elemento SelectionSetName para SelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856752"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="71c2b-102">Elemento SelectionSetName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="71c2b-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="71c2b-103">Especifica o conjunto de tipos do .NET que disparam a condição.</span><span class="sxs-lookup"><span data-stu-id="71c2b-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="71c2b-104">Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando esse controle.</span><span class="sxs-lookup"><span data-stu-id="71c2b-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="71c2b-105">Esse elemento é usado ao definir como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="71c2b-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="71c2b-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) EntrySelectedBy CustomEntry para elemento de GroupBy (formato) SelectionCondition EntrySelectedBy para elemento de GroupBy (formato) SelectionSetName SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="71c2b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="71c2b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71c2b-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="71c2b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="71c2b-108">Attributes and Elements</span></span>

<span data-ttu-id="71c2b-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="71c2b-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="71c2b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="71c2b-110">Attributes</span></span>

<span data-ttu-id="71c2b-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="71c2b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="71c2b-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="71c2b-112">Child Elements</span></span>

<span data-ttu-id="71c2b-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="71c2b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="71c2b-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="71c2b-114">Parent Elements</span></span>

|<span data-ttu-id="71c2b-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="71c2b-115">Element</span></span>|<span data-ttu-id="71c2b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="71c2b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71c2b-117">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="71c2b-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="71c2b-118">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="71c2b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="71c2b-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="71c2b-119">Text Value</span></span>

<span data-ttu-id="71c2b-120">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="71c2b-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="71c2b-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="71c2b-121">Remarks</span></span>

<span data-ttu-id="71c2b-122">Conjuntos de seleção são grupos comuns de objetos .NET que podem ser usados por qualquer exibição que define o arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="71c2b-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="71c2b-123">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="71c2b-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="71c2b-124">Quando esse elemento for especificado, é possível especificar o [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="71c2b-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="71c2b-125">Para obter mais informações sobre como definir as condições de seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="71c2b-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71c2b-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="71c2b-126">See Also</span></span>

[<span data-ttu-id="71c2b-127">Elemento TypeName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="71c2b-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="71c2b-128">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="71c2b-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="71c2b-129">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="71c2b-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="71c2b-130">Definindo conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="71c2b-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="71c2b-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c2b-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
