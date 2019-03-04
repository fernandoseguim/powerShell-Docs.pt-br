---
title: Elemento EntrySelectedBy para CustomEntry para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862812"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="78753-102">Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78753-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="78753-103">Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="78753-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="78753-104">Esse elemento é usado ao definir como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="78753-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="78753-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) EntrySelectedBy CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78753-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="78753-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78753-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="78753-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="78753-107">Attributes and Elements</span></span>

<span data-ttu-id="78753-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="78753-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="78753-109">Você deve especificar pelo menos um critério de seleção para uma definição de, conjunto de seleção ou tipo.</span><span class="sxs-lookup"><span data-stu-id="78753-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="78753-110">Não há nenhum limite máximo ao número de elementos filho que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="78753-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="78753-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="78753-111">Attributes</span></span>

<span data-ttu-id="78753-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="78753-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="78753-113">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="78753-113">Child Elements</span></span>

|<span data-ttu-id="78753-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="78753-114">Element</span></span>|<span data-ttu-id="78753-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="78753-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78753-116">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78753-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="78753-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="78753-117">Optional element.</span></span><br /><br /> <span data-ttu-id="78753-118">Define a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="78753-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="78753-119">Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78753-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="78753-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="78753-120">Optional element.</span></span><br /><br /> <span data-ttu-id="78753-121">Especifica um conjunto de tipos do .NET que usam essa definição do controle.</span><span class="sxs-lookup"><span data-stu-id="78753-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="78753-122">Elemento TypeName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78753-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="78753-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="78753-123">Optional element.</span></span><br /><br /> <span data-ttu-id="78753-124">Especifica um tipo .NET que usa essa definição do controle.</span><span class="sxs-lookup"><span data-stu-id="78753-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="78753-125">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="78753-125">Parent Elements</span></span>

|<span data-ttu-id="78753-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="78753-126">Element</span></span>|<span data-ttu-id="78753-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="78753-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78753-128">Elemento CustomEntry para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78753-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="78753-129">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="78753-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="78753-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="78753-130">Remarks</span></span>

<span data-ttu-id="78753-131">Condições de seleção são usadas para definir uma condição que deve existir para a definição a ser usado, como quando um objeto tem uma propriedade específica ou quando um valor de propriedade específica ou script avalia para `true`.</span><span class="sxs-lookup"><span data-stu-id="78753-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="78753-132">Para obter mais informações sobre condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="78753-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="78753-133">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="78753-133">See Also</span></span>

[<span data-ttu-id="78753-134">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78753-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="78753-135">Elemento SelectionSetName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78753-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="78753-136">Elemento TypeName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78753-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="78753-137">Elemento CustomEntry para CustomEntries controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="78753-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="78753-138">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="78753-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
