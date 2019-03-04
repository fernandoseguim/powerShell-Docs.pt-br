---
title: Elemento SelectionSetName para SelectionCondition para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862762"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="b7e6b-102">Elemento SelectionSetName para SelectionCondition para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="b7e6b-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="b7e6b-103">Especifica o conjunto de tipos do .NET que disparam a condição.</span><span class="sxs-lookup"><span data-stu-id="b7e6b-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b7e6b-104">Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando o controle.</span><span class="sxs-lookup"><span data-stu-id="b7e6b-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="b7e6b-105">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="b7e6b-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b7e6b-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b7e6b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7e6b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7e6b-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7e6b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7e6b-108">Attributes and Elements</span></span>

<span data-ttu-id="b7e6b-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7e6b-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7e6b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7e6b-110">Attributes</span></span>

<span data-ttu-id="b7e6b-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b7e6b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7e6b-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="b7e6b-112">Child Elements</span></span>

<span data-ttu-id="b7e6b-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b7e6b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b7e6b-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="b7e6b-114">Parent Elements</span></span>

|<span data-ttu-id="b7e6b-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7e6b-115">Element</span></span>|<span data-ttu-id="b7e6b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e6b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7e6b-117">Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b7e6b-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="b7e6b-118">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="b7e6b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b7e6b-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b7e6b-119">Text Value</span></span>

<span data-ttu-id="b7e6b-120">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="b7e6b-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7e6b-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7e6b-121">Remarks</span></span>

<span data-ttu-id="b7e6b-122">Conjuntos de seleção são grupos comuns de objetos .NET que podem ser usados por qualquer exibição que define o arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="b7e6b-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b7e6b-123">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b7e6b-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b7e6b-124">A condição de seleção pode especificar um conjunto de seleção ou um tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b7e6b-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b7e6b-125">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b7e6b-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b7e6b-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b7e6b-126">See Also</span></span>

[<span data-ttu-id="b7e6b-127">Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b7e6b-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="b7e6b-128">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="b7e6b-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b7e6b-129">Definindo conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="b7e6b-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b7e6b-130">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7e6b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
