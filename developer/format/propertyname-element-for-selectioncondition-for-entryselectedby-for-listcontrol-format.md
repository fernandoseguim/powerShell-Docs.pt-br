---
title: Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: f857f5944b9e971215a06d6f5c39f7c22c6cf99f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853292"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="f1ad0-102">Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f1ad0-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="f1ad0-103">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="f1ad0-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f1ad0-104">Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a entrada da lista é usada.</span><span class="sxs-lookup"><span data-stu-id="f1ad0-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="f1ad0-105">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento ListControl (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition ListEntry (formato) EntrySelectedBy para elemento de PropertyName ListEntry (formato) SelectionCondition para EmtrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f1ad0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f1ad0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1ad0-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f1ad0-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f1ad0-107">Attributes and Elements</span></span>

<span data-ttu-id="f1ad0-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="f1ad0-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f1ad0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f1ad0-109">Attributes</span></span>

<span data-ttu-id="f1ad0-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f1ad0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f1ad0-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="f1ad0-111">Child Elements</span></span>

<span data-ttu-id="f1ad0-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f1ad0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f1ad0-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="f1ad0-113">Parent Elements</span></span>

|<span data-ttu-id="f1ad0-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1ad0-114">Element</span></span>|<span data-ttu-id="f1ad0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1ad0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f1ad0-116">Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f1ad0-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f1ad0-117">Define a condição que deve existir para essa entrada de lista a ser usado.</span><span class="sxs-lookup"><span data-stu-id="f1ad0-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f1ad0-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f1ad0-118">Text Value</span></span>

<span data-ttu-id="f1ad0-119">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="f1ad0-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1ad0-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1ad0-120">Remarks</span></span>

<span data-ttu-id="f1ad0-121">A condição de seleção deve especificar pelo menos um nome de propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f1ad0-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="f1ad0-122">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f1ad0-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f1ad0-123">Para obter mais informações sobre outros componentes de uma exibição de lista, consulte [criação de exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f1ad0-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1ad0-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f1ad0-124">See Also</span></span>

[<span data-ttu-id="f1ad0-125">Criando uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="f1ad0-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f1ad0-126">Definir condições para quando os dados é exibida.</span><span class="sxs-lookup"><span data-stu-id="f1ad0-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f1ad0-127">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f1ad0-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f1ad0-128">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f1ad0-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f1ad0-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1ad0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
