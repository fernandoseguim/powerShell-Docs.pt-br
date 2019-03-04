---
title: Elemento EntrySelectedBy para ListEntry para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 723619e67612b859d0acbab37eecd82141adf923
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854942"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="b16f0-102">Elemento EntrySelectedBy para ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b16f0-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="b16f0-103">Define os tipos de .NET que usam essa definição de exibição de lista ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="b16f0-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="b16f0-104">Na maioria dos casos, apenas uma definição é necessária para uma exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="b16f0-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="b16f0-105">No entanto, você pode fornecer várias definições para o modo de exibição de lista, se você quiser usar a mesma exibição de lista para exibir dados diferentes para objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="b16f0-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="b16f0-106">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para elemento de ListEntry ListControl (formato) ListEntry para elemento de EntrySelectedBy ListControl (formato) ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b16f0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b16f0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b16f0-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b16f0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b16f0-108">Attributes and Elements</span></span>

<span data-ttu-id="b16f0-109">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="b16f0-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b16f0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b16f0-110">Attributes</span></span>

<span data-ttu-id="b16f0-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b16f0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b16f0-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="b16f0-112">Child Elements</span></span>

|<span data-ttu-id="b16f0-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b16f0-113">Element</span></span>|<span data-ttu-id="b16f0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b16f0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b16f0-115">Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b16f0-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b16f0-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b16f0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b16f0-117">Define a condição que deve existir para essa definição de exibição de lista a ser usado.</span><span class="sxs-lookup"><span data-stu-id="b16f0-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="b16f0-118">Elemento SelectionSetName para EnrtySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b16f0-118">SelectionSetName Element for EnrtySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b16f0-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b16f0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b16f0-120">Especifica um conjunto de tipos do .NET que usam essa definição de exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="b16f0-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="b16f0-121">Elemento TypeName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b16f0-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b16f0-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b16f0-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b16f0-123">Especifica um tipo .NET que usa essa definição de exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="b16f0-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b16f0-124">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="b16f0-124">Parent Elements</span></span>

|<span data-ttu-id="b16f0-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b16f0-125">Element</span></span>|<span data-ttu-id="b16f0-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b16f0-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b16f0-127">Elemento ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b16f0-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="b16f0-128">Define como as linhas da lista são exibidas.</span><span class="sxs-lookup"><span data-stu-id="b16f0-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b16f0-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="b16f0-129">Remarks</span></span>

<span data-ttu-id="b16f0-130">Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para uma definição de exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="b16f0-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="b16f0-131">Não há nenhum limite máximo ao número de elementos filho que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="b16f0-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="b16f0-132">Condições de seleção são usadas para definir uma condição que deve existir para a definição a serem usadas, como quando um objeto tem uma propriedade específica ou um valor de propriedade específico ou um script que é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="b16f0-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="b16f0-133">Para obter mais informações sobre condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b16f0-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b16f0-134">Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b16f0-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b16f0-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b16f0-135">Example</span></span>

<span data-ttu-id="b16f0-136">O exemplo a seguir mostra como definir os objetos para uma exibição de lista usando seu nome de tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="b16f0-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="b16f0-137">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b16f0-137">See Also</span></span>

[<span data-ttu-id="b16f0-138">Elemento ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b16f0-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="b16f0-139">Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b16f0-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="b16f0-140">Elemento SelectionSetName para EnrtySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b16f0-140">SelectionSetName Element for EnrtySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="b16f0-141">Elemento TypeName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b16f0-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="b16f0-142">Criando uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="b16f0-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b16f0-143">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="b16f0-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b16f0-144">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b16f0-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
