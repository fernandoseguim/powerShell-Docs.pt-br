---
title: Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858282"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="16589-102">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="16589-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="16589-103">Define a condição que deve existir para expandir os objetos da coleção desta definição.</span><span class="sxs-lookup"><span data-stu-id="16589-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="16589-104">Elemento (formato) elemento DefaultSettings (formato) elemento EnumerableExpansions (formato) elemento EnumerableExpansion (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition EnumerableExpansion (formato) EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="16589-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="16589-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16589-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="16589-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="16589-106">Attributes and Elements</span></span>

<span data-ttu-id="16589-107">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="16589-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="16589-108">Você deve especificar um único `PropertyName` ou `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="16589-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="16589-109">O `SelectionSetName` e `TypeName` elementos são opcionais.</span><span class="sxs-lookup"><span data-stu-id="16589-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="16589-110">Você pode especificar um dos qualquer elemento.</span><span class="sxs-lookup"><span data-stu-id="16589-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="16589-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="16589-111">Attributes</span></span>

<span data-ttu-id="16589-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="16589-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="16589-113">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="16589-113">Child Elements</span></span>

|<span data-ttu-id="16589-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="16589-114">Element</span></span>|<span data-ttu-id="16589-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="16589-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16589-116">Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="16589-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="16589-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="16589-117">Optional element.</span></span><br /><br /> <span data-ttu-id="16589-118">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="16589-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="16589-119">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="16589-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="16589-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="16589-120">Optional element.</span></span><br /><br /> <span data-ttu-id="16589-121">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="16589-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="16589-122">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="16589-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="16589-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="16589-123">Optional element.</span></span><br /><br /> <span data-ttu-id="16589-124">Especifica o conjunto de tipos do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="16589-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="16589-125">Elemento TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="16589-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="16589-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="16589-126">Optional element.</span></span><br /><br /> <span data-ttu-id="16589-127">Especifica um tipo .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="16589-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="16589-128">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="16589-128">Parent Elements</span></span>

|<span data-ttu-id="16589-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="16589-129">Element</span></span>|<span data-ttu-id="16589-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="16589-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16589-131">Elemento EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="16589-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="16589-132">Define quais objetos de coleção do .NET são expandidos por essa definição.</span><span class="sxs-lookup"><span data-stu-id="16589-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="16589-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="16589-133">Remarks</span></span>

<span data-ttu-id="16589-134">Cada definição deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.</span><span class="sxs-lookup"><span data-stu-id="16589-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="16589-135">Quando você estiver definindo uma condição de seleção, os seguintes requisitos se aplicam:</span><span class="sxs-lookup"><span data-stu-id="16589-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="16589-136">A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="16589-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="16589-137">Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="16589-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="16589-138">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para dados Diplaying](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="16589-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="16589-139">Para obter mais informações sobre outros componentes de uma exibição ampla, consulte [exibição ampla](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="16589-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="16589-140">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="16589-140">See Also</span></span>

[<span data-ttu-id="16589-141">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="16589-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="16589-142">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="16589-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
