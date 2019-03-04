---
title: Elemento SelectionSetName para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860152"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="57159-102">Elemento SelectionSetName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="57159-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="57159-103">Especifica um conjunto de objetos .NET para a entrada da lista.</span><span class="sxs-lookup"><span data-stu-id="57159-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="57159-104">Não há nenhum limite para o número de conjuntos de seleção que pode ser especificado para uma entrada.</span><span class="sxs-lookup"><span data-stu-id="57159-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="57159-105">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento ListControl (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para elemento de SelectionSetName ListEntry (formato) EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="57159-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57159-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57159-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57159-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="57159-107">Attributes and Elements</span></span>

<span data-ttu-id="57159-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="57159-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57159-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="57159-109">Attributes</span></span>

<span data-ttu-id="57159-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="57159-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57159-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="57159-111">Child Elements</span></span>

<span data-ttu-id="57159-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="57159-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="57159-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="57159-113">Parent Elements</span></span>

|<span data-ttu-id="57159-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="57159-114">Element</span></span>|<span data-ttu-id="57159-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="57159-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57159-116">Elemento EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="57159-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="57159-117">Define os tipos de .NET que usam essa entrada de lista ou a condição que deve existir para essa entrada a ser usado.</span><span class="sxs-lookup"><span data-stu-id="57159-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="57159-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="57159-118">Text Value</span></span>

<span data-ttu-id="57159-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="57159-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="57159-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="57159-120">Remarks</span></span>

<span data-ttu-id="57159-121">Cada entrada da lista deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.</span><span class="sxs-lookup"><span data-stu-id="57159-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="57159-122">Conjuntos de seleção normalmente são usados quando você deseja definir um grupo de objetos que são usados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="57159-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="57159-123">Por exemplo, você talvez queira criar uma exibição de tabela e uma exibição de lista para o mesmo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="57159-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="57159-124">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo os conjuntos de objetos para um modo de exibição](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="57159-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="57159-125">Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="57159-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="57159-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57159-126">Example</span></span>

<span data-ttu-id="57159-127">O exemplo a seguir mostra como especificar uma seleção definida para uma entrada de uma exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="57159-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="57159-128">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="57159-128">See Also</span></span>

[<span data-ttu-id="57159-129">Criando uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="57159-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="57159-130">Elemento EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="57159-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="57159-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="57159-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
