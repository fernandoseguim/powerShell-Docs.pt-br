---
title: Elemento SelectionSetName para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856092"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="9b5cb-102">Elemento SelectionSetName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9b5cb-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="9b5cb-103">Especifica que um conjunto de .NET tipos de uso essa entrada da exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="9b5cb-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="9b5cb-104">Não há nenhum limite para o número de conjuntos de seleção que pode ser especificado para uma entrada.</span><span class="sxs-lookup"><span data-stu-id="9b5cb-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="9b5cb-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento EntrySelectedBy (formato) SelectionSetName elemento de configuração para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9b5cb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9b5cb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b5cb-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b5cb-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9b5cb-107">Attributes and Elements</span></span>

<span data-ttu-id="9b5cb-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9b5cb-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9b5cb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9b5cb-109">Attributes</span></span>

<span data-ttu-id="9b5cb-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9b5cb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9b5cb-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="9b5cb-111">Child Elements</span></span>

<span data-ttu-id="9b5cb-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9b5cb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9b5cb-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="9b5cb-113">Parent Elements</span></span>

|<span data-ttu-id="9b5cb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9b5cb-114">Element</span></span>|<span data-ttu-id="9b5cb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b5cb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b5cb-116">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9b5cb-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="9b5cb-117">Define os tipos de .NET que usam essa entrada ou a condição que deve existir para essa entrada a ser usado.</span><span class="sxs-lookup"><span data-stu-id="9b5cb-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9b5cb-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="9b5cb-118">Text Value</span></span>

<span data-ttu-id="9b5cb-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="9b5cb-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b5cb-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b5cb-120">Remarks</span></span>

<span data-ttu-id="9b5cb-121">Conjuntos de seleção normalmente são usados quando você deseja definir um grupo de objetos que são usados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="9b5cb-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="9b5cb-122">Por exemplo, você talvez queira criar uma exibição de tabela e uma exibição de lista para o mesmo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="9b5cb-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="9b5cb-123">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo os conjuntos de objetos para um modo de exibição](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9b5cb-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="9b5cb-124">Se você especificar uma seleção definida para uma entrada, você não pode especificar um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="9b5cb-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="9b5cb-125">Para obter mais informações sobre como especificar um tipo .NET, consulte [elemento TypeName para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="9b5cb-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="9b5cb-126">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9b5cb-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b5cb-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="9b5cb-127">See Also</span></span>

[<span data-ttu-id="9b5cb-128">Elemento EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9b5cb-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="9b5cb-129">Definindo conjuntos de objetos para um modo de exibição</span><span class="sxs-lookup"><span data-stu-id="9b5cb-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="9b5cb-130">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="9b5cb-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9b5cb-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b5cb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
