---
title: Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858012"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="891e1-102">Elemento SelectionCondition para EntrySelectedBy para Controls para View (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="891e1-103">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="891e1-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="891e1-104">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="891e1-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="891e1-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para controles para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) EntrySelectedBy CustomEntry para controles para elemento de exibição (formato) SelectionCondition EntrySelectedBy para controles para exibição ( Formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="891e1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="891e1-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="891e1-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="891e1-107">Attributes and Elements</span></span>

<span data-ttu-id="891e1-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="891e1-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="891e1-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="891e1-109">Attributes</span></span>

<span data-ttu-id="891e1-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="891e1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="891e1-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="891e1-111">Child Elements</span></span>

|<span data-ttu-id="891e1-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="891e1-112">Element</span></span>|<span data-ttu-id="891e1-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="891e1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="891e1-114">Elemento PropertyName para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="891e1-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="891e1-115">Optional element.</span></span><br /><br /> <span data-ttu-id="891e1-116">Especifica uma propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="891e1-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="891e1-117">Elemento ScriptBlock para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="891e1-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="891e1-118">Optional element.</span></span><br /><br /> <span data-ttu-id="891e1-119">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="891e1-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="891e1-120">Elemento SelectionSetName para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="891e1-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="891e1-121">Optional element.</span></span><br /><br /> <span data-ttu-id="891e1-122">Especifica o conjunto de tipos do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="891e1-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="891e1-123">Elemento TypeName para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="891e1-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="891e1-124">Optional element.</span></span><br /><br /> <span data-ttu-id="891e1-125">Especifica um tipo .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="891e1-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="891e1-126">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="891e1-126">Parent Elements</span></span>

|<span data-ttu-id="891e1-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="891e1-127">Element</span></span>|<span data-ttu-id="891e1-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="891e1-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="891e1-129">Elemento EntrySelectedBy para CustomEntry controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="891e1-130">Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="891e1-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="891e1-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="891e1-131">Remarks</span></span>

<span data-ttu-id="891e1-132">Quando você estiver definindo uma condição de seleção, os seguintes requisitos se aplicam:</span><span class="sxs-lookup"><span data-stu-id="891e1-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="891e1-133">A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="891e1-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="891e1-134">Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="891e1-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="891e1-135">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="891e1-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="891e1-136">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="891e1-136">See Also</span></span>

[<span data-ttu-id="891e1-137">Elemento PropertyName para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="891e1-138">Elemento ScriptBlock para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="891e1-139">Elemento SelectionSetName para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="891e1-140">Elemento TypeName para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="891e1-141">Elemento EntrySelectedBy para CustomEntry controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="891e1-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="891e1-142">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="891e1-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
