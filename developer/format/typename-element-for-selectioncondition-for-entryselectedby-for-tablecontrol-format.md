---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856492"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="9d7f4-102">Elemento TypeName para SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="9d7f4-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="9d7f4-103">Especifica um tipo .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="9d7f4-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="9d7f4-104">Quando esse tipo estiver presente, a condição for atendida, e a linha da tabela é usada.</span><span class="sxs-lookup"><span data-stu-id="9d7f4-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="9d7f4-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento SelectionCondition para EntrySelectedBy para elemento de TypeName TableRowEntry (formato) SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9d7f4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d7f4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d7f4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d7f4-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9d7f4-107">Attributes and Elements</span></span>

<span data-ttu-id="9d7f4-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="9d7f4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d7f4-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9d7f4-109">Attributes</span></span>

<span data-ttu-id="9d7f4-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9d7f4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d7f4-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="9d7f4-111">Child Elements</span></span>

<span data-ttu-id="9d7f4-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9d7f4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9d7f4-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="9d7f4-113">Parent Elements</span></span>

|<span data-ttu-id="9d7f4-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d7f4-114">Element</span></span>|<span data-ttu-id="9d7f4-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d7f4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d7f4-116">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9d7f4-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="9d7f4-117">Define a condição que deve existir para essa linha na tabela a ser usado.</span><span class="sxs-lookup"><span data-stu-id="9d7f4-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9d7f4-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="9d7f4-118">Text Value</span></span>

<span data-ttu-id="9d7f4-119">Especifique o nome totalmente qualificado do tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="9d7f4-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d7f4-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d7f4-120">Remarks</span></span>

<span data-ttu-id="9d7f4-121">Os critérios de seleção podem especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="9d7f4-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="9d7f4-122">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando uma entrada de exibição ou o Item está sendo usado](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9d7f4-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9d7f4-123">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9d7f4-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d7f4-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="9d7f4-124">See Also</span></span>

[<span data-ttu-id="9d7f4-125">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="9d7f4-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9d7f4-126">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="9d7f4-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9d7f4-127">Elemento SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9d7f4-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9d7f4-128">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="9d7f4-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9d7f4-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d7f4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
