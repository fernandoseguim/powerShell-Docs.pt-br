---
title: Elemento SelectionSetName para SelectionCondition controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855112"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="7aaaf-102">Elemento SelectionSetName para SelectionCondition para Controls para View (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaaf-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="7aaaf-103">Especifica o conjunto de tipos do .NET que disparam a condição.</span><span class="sxs-lookup"><span data-stu-id="7aaaf-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="7aaaf-104">Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando o controle.</span><span class="sxs-lookup"><span data-stu-id="7aaaf-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="7aaaf-105">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="7aaaf-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="7aaaf-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para controles para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) EntrySelectedBy CustomEntry para controles para elemento de exibição (formato) SelectionCondition EntrySelectedBy para controles para exibição ( Elemento de SelectionSetName Format) para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaaf-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7aaaf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7aaaf-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7aaaf-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7aaaf-108">Attributes and Elements</span></span>

<span data-ttu-id="7aaaf-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="7aaaf-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7aaaf-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="7aaaf-110">Attributes</span></span>

<span data-ttu-id="7aaaf-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7aaaf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7aaaf-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="7aaaf-112">Child Elements</span></span>

<span data-ttu-id="7aaaf-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7aaaf-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7aaaf-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="7aaaf-114">Parent Elements</span></span>

|<span data-ttu-id="7aaaf-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="7aaaf-115">Element</span></span>|<span data-ttu-id="7aaaf-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7aaaf-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7aaaf-117">Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaaf-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="7aaaf-118">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="7aaaf-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7aaaf-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="7aaaf-119">Text Value</span></span>

<span data-ttu-id="7aaaf-120">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="7aaaf-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7aaaf-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="7aaaf-121">Remarks</span></span>

<span data-ttu-id="7aaaf-122">Conjuntos de seleção são grupos comuns de objetos .NET que podem ser usados por qualquer exibição que define o arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="7aaaf-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="7aaaf-123">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7aaaf-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="7aaaf-124">A condição de seleção pode especificar um conjunto de seleção ou um tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="7aaaf-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="7aaaf-125">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7aaaf-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7aaaf-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="7aaaf-126">See Also</span></span>

[<span data-ttu-id="7aaaf-127">Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaaf-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="7aaaf-128">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="7aaaf-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7aaaf-129">Definindo conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="7aaaf-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7aaaf-130">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7aaaf-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
