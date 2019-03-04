---
title: Definir condições para a exibição de dados | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855642"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="62512-102">Definir condições para a exibição de dados</span><span class="sxs-lookup"><span data-stu-id="62512-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="62512-103">Ao definir quais dados são exibidos em uma exibição ou um controle, você pode especificar uma condição que deve existir para os dados a serem exibidos.</span><span class="sxs-lookup"><span data-stu-id="62512-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="62512-104">A condição pode ser disparada por uma propriedade específica, ou quando um script ou o valor da propriedade é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="62512-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="62512-105">Quando a seleção de condição for atendida, a definição da exibição ou controle é usada.</span><span class="sxs-lookup"><span data-stu-id="62512-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="62512-106">Especificando um critério de seleção para uma definição</span><span class="sxs-lookup"><span data-stu-id="62512-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="62512-107">Ao criar uma definição para um modo de exibição ou controle, o `EntrySelectedBy` elemento é usado para especificar quais objetos usará a definição ou qual condição deve existir para a definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="62512-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="62512-108">A condição é especificada pelo `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="62512-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="62512-109">No exemplo a seguir, uma condição de seleção é especificada para uma definição de uma exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="62512-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="62512-110">Neste exemplo, a definição é usada somente quando o script especificado é avaliado para `true`.</span><span class="sxs-lookup"><span data-stu-id="62512-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

<span data-ttu-id="62512-111">Não há nenhum limite para o número de condições de seleção que você pode especificar para uma definição de um modo de exibição ou controle.</span><span class="sxs-lookup"><span data-stu-id="62512-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="62512-112">Os únicos requisitos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="62512-112">The only requirements are the following:</span></span>

- <span data-ttu-id="62512-113">A condição de seleção deve especificar um nome de propriedade ou script para disparar a condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="62512-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="62512-114">Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="62512-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="62512-115">Especificando um critério de seleção para um Item</span><span class="sxs-lookup"><span data-stu-id="62512-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="62512-116">Você também pode especificar quando um item de um modo de exibição de lista ou um controle é usado, incluindo o `ItemSelectionCondition` elemento na definição de item.</span><span class="sxs-lookup"><span data-stu-id="62512-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="62512-117">No exemplo a seguir, uma condição de seleção é especificada para um item de uma exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="62512-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="62512-118">Neste exemplo, o item é usado somente quando o script é avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="62512-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="62512-119">Você pode especificar a condição somente uma seleção de um item.</span><span class="sxs-lookup"><span data-stu-id="62512-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="62512-120">E a condição deve especificar um nome de propriedade ou script para disparar a condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="62512-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="62512-121">Elementos XML</span><span class="sxs-lookup"><span data-stu-id="62512-121">XML Elements</span></span>

 <span data-ttu-id="62512-122">Os seguintes elementos XML são usados para criar uma condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="62512-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="62512-123">Os seguintes elementos especificam critérios de seleção para definições de exibição:</span><span class="sxs-lookup"><span data-stu-id="62512-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="62512-124">Elemento SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="62512-125">Elemento SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="62512-126">Elemento SelectionCondition para EntrySelectedBy para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="62512-127">Elemento SelectionCondition para EntrySelectedBy para CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="62512-128">Seleção de especificar os seguintes elementos condições comuns e modo de exibição de controle de definições:</span><span class="sxs-lookup"><span data-stu-id="62512-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="62512-129">Elemento SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="62512-130">Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="62512-131">O elemento a seguir especifica o critério de seleção para expansão de objetos de coleção:</span><span class="sxs-lookup"><span data-stu-id="62512-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="62512-132">Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="62512-133">O elemento a seguir especifica o critério de seleção para exibir um novo grupo de dados:</span><span class="sxs-lookup"><span data-stu-id="62512-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="62512-134">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="62512-135">O elemento a seguir especifica uma condição de seleção de item para uma exibição de lista:</span><span class="sxs-lookup"><span data-stu-id="62512-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="62512-136">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="62512-137">Os seguintes elementos deve especificar um critério de seleção de item para controles:</span><span class="sxs-lookup"><span data-stu-id="62512-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="62512-138">Elemento ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="62512-139">Elemento ItemSelectionCondition para ExpressionBinding controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="62512-140">Elemento ItemSelectionCondition para ExpressionBinding para CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="62512-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="62512-141">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="62512-141">See Also</span></span>

[<span data-ttu-id="62512-142">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="62512-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
