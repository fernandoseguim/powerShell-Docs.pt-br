---
title: Elemento SelectionCondition para EntrySelectedBy para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854112"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="ab77d-102">Elemento SelectionCondition para EntrySelectedBy para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="ab77d-103">Define a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ab77d-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ab77d-104">Não há nenhum limite para o número de condições de seleção que pode ser especificado para uma definição ampla de entrada.</span><span class="sxs-lookup"><span data-stu-id="ab77d-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="ab77d-105">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition WideEntry (formato) EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab77d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab77d-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab77d-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ab77d-107">Attributes and Elements</span></span>

<span data-ttu-id="ab77d-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="ab77d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="ab77d-109">Você deve especificar um único `PropertyName` ou `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="ab77d-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="ab77d-110">O `SelectionSetName` e `TypeName` elementos são opcionais.</span><span class="sxs-lookup"><span data-stu-id="ab77d-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="ab77d-111">Você pode especificar um dos qualquer elemento.</span><span class="sxs-lookup"><span data-stu-id="ab77d-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab77d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ab77d-112">Attributes</span></span>

<span data-ttu-id="ab77d-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ab77d-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab77d-114">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="ab77d-114">Child Elements</span></span>

|<span data-ttu-id="ab77d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab77d-115">Element</span></span>|<span data-ttu-id="ab77d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab77d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab77d-117">Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="ab77d-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ab77d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ab77d-119">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="ab77d-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ab77d-120">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ab77d-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ab77d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ab77d-122">Especifica o bloco de script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="ab77d-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="ab77d-123">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="ab77d-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ab77d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="ab77d-125">Especifica o conjunto de tipos do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="ab77d-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="ab77d-126">Elemento TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ab77d-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ab77d-127">Optional element.</span></span><br /><br /> <span data-ttu-id="ab77d-128">Especifica um tipo .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="ab77d-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ab77d-129">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="ab77d-129">Parent Elements</span></span>

|<span data-ttu-id="ab77d-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab77d-130">Element</span></span>|<span data-ttu-id="ab77d-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab77d-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab77d-132">Elemento EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="ab77d-133">Define os tipos de .NET que usam essa entrada ampla ou a condição que deve existir para essa entrada a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ab77d-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ab77d-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab77d-134">Remarks</span></span>

<span data-ttu-id="ab77d-135">Cada entrada ampla deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.</span><span class="sxs-lookup"><span data-stu-id="ab77d-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ab77d-136">Quando você estiver definindo uma condição de seleção, os seguintes requisitos se aplicam:</span><span class="sxs-lookup"><span data-stu-id="ab77d-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="ab77d-137">A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="ab77d-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="ab77d-138">Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="ab77d-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="ab77d-139">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ab77d-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ab77d-140">Para obter mais informações sobre outros componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ab77d-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab77d-141">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ab77d-141">See Also</span></span>

[<span data-ttu-id="ab77d-142">Criando uma exibição ampla</span><span class="sxs-lookup"><span data-stu-id="ab77d-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ab77d-143">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="ab77d-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ab77d-144">Elemento EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="ab77d-145">Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="ab77d-146">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ab77d-147">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="ab77d-148">Elemento TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ab77d-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ab77d-149">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab77d-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
