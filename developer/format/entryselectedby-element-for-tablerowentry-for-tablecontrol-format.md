---
title: Elemento EntrySelectedBy para TableRowEntry para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058752"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="241a3-102">Elemento EntrySelectedBy para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="241a3-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="241a3-103">Define os tipos de .NET que usam essa definição de exibição de tabela ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="241a3-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="241a3-104">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="241a3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="241a3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="241a3-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="241a3-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="241a3-106">Attributes and Elements</span></span>

<span data-ttu-id="241a3-107">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="241a3-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="241a3-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="241a3-108">Attributes</span></span>

<span data-ttu-id="241a3-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="241a3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="241a3-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="241a3-110">Child Elements</span></span>

|<span data-ttu-id="241a3-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="241a3-111">Element</span></span>|<span data-ttu-id="241a3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="241a3-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="241a3-113">Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="241a3-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="241a3-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="241a3-114">Optional element.</span></span><br /><br /> <span data-ttu-id="241a3-115">Define a condição que deve existir para essa definição de exibição de tabela a ser usado.</span><span class="sxs-lookup"><span data-stu-id="241a3-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="241a3-116">Elemento SelectionSetName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="241a3-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="241a3-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="241a3-117">Optional element.</span></span><br /><br /> <span data-ttu-id="241a3-118">Especifica um conjunto de tipos do .NET que usam essa definição de exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="241a3-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="241a3-119">Elemento TypeName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="241a3-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="241a3-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="241a3-120">Optional element.</span></span><br /><br /> <span data-ttu-id="241a3-121">Especifica um tipo .NET que usa essa definição de exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="241a3-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="241a3-122">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="241a3-122">Parent Elements</span></span>

|<span data-ttu-id="241a3-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="241a3-123">Element</span></span>|<span data-ttu-id="241a3-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="241a3-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="241a3-125">Elemento TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="241a3-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="241a3-126">Define os dados que são exibidos em uma linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="241a3-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="241a3-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="241a3-127">Remarks</span></span>

<span data-ttu-id="241a3-128">Você deve especificar pelo menos um critério de seleção para uma definição de exibição de tabela, conjunto de seleção ou tipo.</span><span class="sxs-lookup"><span data-stu-id="241a3-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="241a3-129">Não há nenhum limite máximo ao número de elementos filho que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="241a3-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="241a3-130">Condições de seleção são usadas para definir uma condição que deve existir para a definição a serem usadas, como quando um objeto tem uma propriedade específica ou um valor de propriedade específico ou um script que é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="241a3-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="241a3-131">Para obter mais informações sobre condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="241a3-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="241a3-132">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="241a3-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="241a3-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="241a3-133">Example</span></span>

<span data-ttu-id="241a3-134">A exemplo a seguir mostra um `TableRowEntry` que é usado para exibir as propriedades do elemento de [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="241a3-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="241a3-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="241a3-135">See Also</span></span>

[<span data-ttu-id="241a3-136">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="241a3-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="241a3-137">Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="241a3-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="241a3-138">Elemento SelectionSetName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="241a3-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="241a3-139">Elemento TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="241a3-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="241a3-140">Elemento TypeName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="241a3-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="241a3-141">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="241a3-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
