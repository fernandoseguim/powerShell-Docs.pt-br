---
title: Elemento SelectionCondition para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861232"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="40303-102">Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="40303-103">Define a condição que deve existir para usar para esta definição da exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="40303-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="40303-104">Não há nenhum limite para o número de condições de seleção que pode ser especificado para uma definição de tabela.</span><span class="sxs-lookup"><span data-stu-id="40303-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="40303-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="40303-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40303-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40303-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="40303-107">Attributes and Elements</span></span>

<span data-ttu-id="40303-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do elemento SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="40303-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="40303-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="40303-109">Attributes</span></span>

<span data-ttu-id="40303-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="40303-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="40303-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="40303-111">Child Elements</span></span>

|<span data-ttu-id="40303-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="40303-112">Element</span></span>|<span data-ttu-id="40303-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="40303-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40303-114">Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="40303-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="40303-115">Optional element.</span></span><br /><br /> <span data-ttu-id="40303-116">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="40303-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="40303-117">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="40303-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="40303-118">Optional element.</span></span><br /><br /> <span data-ttu-id="40303-119">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="40303-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="40303-120">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="40303-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="40303-121">Optional element.</span></span><br /><br /> <span data-ttu-id="40303-122">Especifica o conjunto de tipos do .NET que disparam a condição.</span><span class="sxs-lookup"><span data-stu-id="40303-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="40303-123">Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="40303-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="40303-124">Optional element.</span></span><br /><br /> <span data-ttu-id="40303-125">Especifica um tipo .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="40303-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="40303-126">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="40303-126">Parent Elements</span></span>

|<span data-ttu-id="40303-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="40303-127">Element</span></span>|<span data-ttu-id="40303-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="40303-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40303-129">Elemento EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="40303-130">Define os tipos de .NET que usam essa entrada de tabela ou a condição que deve existir para essa entrada a ser usado.</span><span class="sxs-lookup"><span data-stu-id="40303-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="40303-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="40303-131">Remarks</span></span>

<span data-ttu-id="40303-132">Cada entrada da lista deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.</span><span class="sxs-lookup"><span data-stu-id="40303-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="40303-133">Quando você estiver definindo uma condição de seleção, os seguintes requisitos se aplicam:</span><span class="sxs-lookup"><span data-stu-id="40303-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="40303-134">A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="40303-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="40303-135">Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="40303-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="40303-136">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="40303-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="40303-137">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="40303-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40303-138">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="40303-138">See Also</span></span>

[<span data-ttu-id="40303-139">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="40303-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="40303-140">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="40303-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="40303-141">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="40303-142">Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="40303-143">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="40303-144">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="40303-145">Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="40303-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="40303-146">Escrevendo um formatação do Windows PowerShell e tipos de arquivo</span><span class="sxs-lookup"><span data-stu-id="40303-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
