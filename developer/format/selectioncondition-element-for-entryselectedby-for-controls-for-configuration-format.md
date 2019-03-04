---
title: Elemento SelectionCondition para EntrySelectedBy para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854142"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="34bb4-102">Elemento SelectionCondition para EntrySelectedBy para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="34bb4-103">Define uma condição que deve existir para uma definição de controle comum a ser usado.</span><span class="sxs-lookup"><span data-stu-id="34bb4-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="34bb4-104">Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="34bb4-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="34bb4-105">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl controles para Elemento de configuração (formato) de CustomEntry para CustomControl controles para o elemento de configuração (formato) de EntrySelectedBy para CustomEntry controles para o elemento de configuração (formato) de SelectionCondition para EntrySelectedBy para CustomEntry para Configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34bb4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34bb4-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34bb4-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="34bb4-107">Attributes and Elements</span></span>

<span data-ttu-id="34bb4-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="34bb4-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34bb4-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="34bb4-109">Attributes</span></span>

<span data-ttu-id="34bb4-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="34bb4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34bb4-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="34bb4-111">Child Elements</span></span>

|<span data-ttu-id="34bb4-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="34bb4-112">Element</span></span>|<span data-ttu-id="34bb4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="34bb4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34bb4-114">Elemento PropertyName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="34bb4-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="34bb4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="34bb4-116">Especifica uma propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="34bb4-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="34bb4-117">Elemento ScriptBlock para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="34bb4-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="34bb4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="34bb4-119">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="34bb4-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="34bb4-120">Elemento SelectionSetName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="34bb4-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="34bb4-121">Optional element.</span></span><br /><br /> <span data-ttu-id="34bb4-122">Especifica o conjunto de tipos do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="34bb4-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="34bb4-123">Elemento TypeName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="34bb4-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="34bb4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="34bb4-125">Especifica um tipo .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="34bb4-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="34bb4-126">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="34bb4-126">Parent Elements</span></span>

|<span data-ttu-id="34bb4-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="34bb4-127">Element</span></span>|<span data-ttu-id="34bb4-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="34bb4-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34bb4-129">Elemento EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="34bb4-130">Define os tipos de .NET que usam essa entrada da definição de controle comuns.</span><span class="sxs-lookup"><span data-stu-id="34bb4-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="34bb4-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="34bb4-131">Remarks</span></span>

<span data-ttu-id="34bb4-132">As diretrizes a seguir devem ser seguidas ao definir uma condição de seleção:</span><span class="sxs-lookup"><span data-stu-id="34bb4-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="34bb4-133">A condição de seleção deve especificar um nome menos de uma propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="34bb4-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="34bb4-134">Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="34bb4-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="34bb4-135">Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="34bb4-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34bb4-136">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="34bb4-136">See Also</span></span>

[<span data-ttu-id="34bb4-137">Elemento PropertyName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="34bb4-138">Elemento ScriptBlock para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="34bb4-139">Elemento SelectionSetName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="34bb4-140">Elemento TypeName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="34bb4-141">Elemento EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="34bb4-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="34bb4-142">Escrevendo um formatação do Windows PowerShell e tipos de arquivo</span><span class="sxs-lookup"><span data-stu-id="34bb4-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
