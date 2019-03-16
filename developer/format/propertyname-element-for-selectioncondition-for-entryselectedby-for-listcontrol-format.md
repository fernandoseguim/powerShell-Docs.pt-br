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
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059007"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="3fc64-102">Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3fc64-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="3fc64-103">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="3fc64-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="3fc64-104">Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a entrada da lista é usada.</span><span class="sxs-lookup"><span data-stu-id="3fc64-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="3fc64-105">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento ListControl (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition ListEntry (formato) EntrySelectedBy para elemento de PropertyName ListEntry (formato) SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3fc64-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3fc64-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fc64-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3fc64-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3fc64-107">Attributes and Elements</span></span>

<span data-ttu-id="3fc64-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="3fc64-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3fc64-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3fc64-109">Attributes</span></span>

<span data-ttu-id="3fc64-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3fc64-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3fc64-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="3fc64-111">Child Elements</span></span>

<span data-ttu-id="3fc64-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3fc64-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3fc64-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="3fc64-113">Parent Elements</span></span>

|<span data-ttu-id="3fc64-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="3fc64-114">Element</span></span>|<span data-ttu-id="3fc64-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fc64-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3fc64-116">Elemento SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3fc64-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="3fc64-117">Define a condição que deve existir para essa entrada de lista a ser usado.</span><span class="sxs-lookup"><span data-stu-id="3fc64-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3fc64-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="3fc64-118">Text Value</span></span>

<span data-ttu-id="3fc64-119">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="3fc64-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="3fc64-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fc64-120">Remarks</span></span>

<span data-ttu-id="3fc64-121">A condição de seleção deve especificar pelo menos um nome de propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="3fc64-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="3fc64-122">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3fc64-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3fc64-123">Para obter mais informações sobre outros componentes de uma exibição de lista, consulte [criação de exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="3fc64-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3fc64-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="3fc64-124">See Also</span></span>

[<span data-ttu-id="3fc64-125">Criando uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="3fc64-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3fc64-126">Definir condições para quando os dados é exibida.</span><span class="sxs-lookup"><span data-stu-id="3fc64-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3fc64-127">Elemento ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3fc64-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="3fc64-128">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3fc64-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="3fc64-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fc64-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
