---
title: Elemento SelectionCondition para EntrySelectedBy para CustomControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858822"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="07484-102">Elemento SelectionCondition para EntrySelectedBy para CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="07484-103">Define uma condição que deve existir para uma definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="07484-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="07484-104">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="07484-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="07484-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento de configuração para elemento de exibição (formato) CustomEntries CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para CustomControl para exibição ( Elemento de CustomItem Format) para CustomEntry para CustomControl para elemento de exibição (formato) EntrySelectedBy CustomEntry para CustomControl para elemento de exibição (formato) SelectionCondition EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07484-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07484-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07484-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="07484-107">Attributes and Elements</span></span>

<span data-ttu-id="07484-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="07484-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="07484-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="07484-109">Attributes</span></span>

<span data-ttu-id="07484-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="07484-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07484-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="07484-111">Child Elements</span></span>

|<span data-ttu-id="07484-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="07484-112">Element</span></span>|<span data-ttu-id="07484-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="07484-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07484-114">Elemento PropertyName para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="07484-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="07484-115">Optional element.</span></span><br /><br /> <span data-ttu-id="07484-116">Especifica uma propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="07484-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="07484-117">Elemento ScriptBlock para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="07484-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="07484-118">Optional element.</span></span><br /><br /> <span data-ttu-id="07484-119">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="07484-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="07484-120">Elemento SelectionSetName para SelectionCondition para um controle personalizado para o modo de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="07484-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="07484-121">Optional element.</span></span><br /><br /> <span data-ttu-id="07484-122">Especifica o conjunto de tipos do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="07484-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="07484-123">Elemento TypeName para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="07484-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="07484-124">Optional element.</span></span><br /><br /> <span data-ttu-id="07484-125">Especifica um tipo .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="07484-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="07484-126">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="07484-126">Parent Elements</span></span>

|<span data-ttu-id="07484-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="07484-127">Element</span></span>|<span data-ttu-id="07484-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="07484-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07484-129">Elemento EntrySelectedBy para CustomEntry para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="07484-130">Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="07484-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="07484-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="07484-131">Remarks</span></span>

<span data-ttu-id="07484-132">Quando você estiver definindo uma condição de seleção, os seguintes requisitos se aplicam:</span><span class="sxs-lookup"><span data-stu-id="07484-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="07484-133">A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="07484-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="07484-134">Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="07484-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="07484-135">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="07484-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07484-136">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="07484-136">See Also</span></span>

[<span data-ttu-id="07484-137">Elemento PropertyName para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="07484-138">Elemento ScriptBlock para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="07484-139">Elemento SelectionSetName para SelectionCondition para um controle personalizado para o modo de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="07484-140">Elemento TypeName para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="07484-141">Elemento EntrySelectedBy para CustomEntry para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="07484-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="07484-142">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="07484-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
