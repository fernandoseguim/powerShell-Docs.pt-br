---
title: Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855572"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="0946b-102">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0946b-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="0946b-103">Especifica o bloco de script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="0946b-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="0946b-104">Quando esse script é avaliado para `true`, a condição for atendida e a entrada da tabela é usada.</span><span class="sxs-lookup"><span data-stu-id="0946b-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="0946b-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato) elemento ScriptBlock SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0946b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0946b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0946b-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0946b-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0946b-107">Attributes and Elements</span></span>

<span data-ttu-id="0946b-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="0946b-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0946b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0946b-109">Attributes</span></span>

<span data-ttu-id="0946b-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0946b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0946b-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="0946b-111">Child Elements</span></span>

<span data-ttu-id="0946b-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0946b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0946b-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="0946b-113">Parent Elements</span></span>

|<span data-ttu-id="0946b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0946b-114">Element</span></span>|<span data-ttu-id="0946b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0946b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0946b-116">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0946b-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="0946b-117">Define a condição que deve existir para essa entrada de tabela a ser usado.</span><span class="sxs-lookup"><span data-stu-id="0946b-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0946b-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="0946b-118">Text Value</span></span>

<span data-ttu-id="0946b-119">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="0946b-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="0946b-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="0946b-120">Remarks</span></span>

<span data-ttu-id="0946b-121">A condição de seleção deve especificar pelo menos um nome de propriedade ou o bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="0946b-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="0946b-122">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0946b-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0946b-123">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0946b-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0946b-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0946b-124">See Also</span></span>

[<span data-ttu-id="0946b-125">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="0946b-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0946b-126">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="0946b-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0946b-127">Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0946b-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="0946b-128">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0946b-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="0946b-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="0946b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
