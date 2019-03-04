---
title: Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863272"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="b7042-102">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b7042-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="b7042-103">Especifica o conjunto de tipos do .NET que disparam a condição.</span><span class="sxs-lookup"><span data-stu-id="b7042-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b7042-104">Quando qualquer um dos tipos neste conjunto estiver presente, a condição é atendida e o objeto é exibido usando essa definição da exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="b7042-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="b7042-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para elemento de SelectionSetName TableRowEntry (formato) SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b7042-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7042-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7042-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7042-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7042-107">Attributes and Elements</span></span>

<span data-ttu-id="b7042-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7042-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7042-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7042-109">Attributes</span></span>

<span data-ttu-id="b7042-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b7042-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7042-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="b7042-111">Child Elements</span></span>

<span data-ttu-id="b7042-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b7042-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b7042-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="b7042-113">Parent Elements</span></span>

|<span data-ttu-id="b7042-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7042-114">Element</span></span>|<span data-ttu-id="b7042-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7042-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7042-116">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b7042-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b7042-117">Define a condição que deve existir para usar para esta definição da exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="b7042-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b7042-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b7042-118">Text Value</span></span>

<span data-ttu-id="b7042-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="b7042-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7042-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7042-120">Remarks</span></span>

<span data-ttu-id="b7042-121">A condição de seleção pode especificar um conjunto de seleção ou um tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b7042-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b7042-122">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b7042-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b7042-123">Conjuntos de seleção são grupos comuns de objetos .NET que podem ser usados por qualquer exibição que define o arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="b7042-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b7042-124">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b7042-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b7042-125">Para obter mais informações sobre outros componentes de uma exibição ampla, consulte [criando uma exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b7042-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b7042-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b7042-126">See Also</span></span>

[<span data-ttu-id="b7042-127">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="b7042-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b7042-128">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="b7042-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b7042-129">Elemento TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b7042-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b7042-130">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="b7042-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b7042-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7042-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
