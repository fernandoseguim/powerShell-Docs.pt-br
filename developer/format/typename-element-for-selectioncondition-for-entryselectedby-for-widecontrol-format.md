---
title: Elemento TypeName para SelectionCondition para EntrySelectedBy para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055965"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="ec671-102">Elemento TypeName para SelectionCondition para EntrySelectedBy para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="ec671-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="ec671-103">Especifica um tipo .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="ec671-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="ec671-104">Quando esse tipo estiver presente, a definição é usada.</span><span class="sxs-lookup"><span data-stu-id="ec671-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="ec671-105">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento de configuração para elemento de SelectionCondition WideEntry (formato) EntrySelectedBy para elemento de TypeName WideEntry (formato) SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ec671-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ec671-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec671-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec671-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ec671-107">Attributes and Elements</span></span>

<span data-ttu-id="ec671-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="ec671-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec671-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ec671-109">Attributes</span></span>

<span data-ttu-id="ec671-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ec671-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec671-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="ec671-111">Child Elements</span></span>

<span data-ttu-id="ec671-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ec671-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec671-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="ec671-113">Parent Elements</span></span>

|<span data-ttu-id="ec671-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec671-114">Element</span></span>|<span data-ttu-id="ec671-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec671-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec671-116">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ec671-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ec671-117">Define a condição que deve existir para essa entrada larga a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ec671-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ec671-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="ec671-118">Text Value</span></span>

<span data-ttu-id="ec671-119">Especifique o nome totalmente qualificado do tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="ec671-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec671-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec671-120">Remarks</span></span>

<span data-ttu-id="ec671-121">Os critérios de seleção podem especificar um tipo .NET ou uma seleção definida, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="ec671-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="ec671-122">Para obter mais informações sobre como usar condições de seleção, consulte [definindo condições para quando os dados são exibidos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ec671-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ec671-123">Para obter mais informações sobre outros componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ec671-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec671-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ec671-124">See Also</span></span>

[<span data-ttu-id="ec671-125">Criando uma exibição ampla</span><span class="sxs-lookup"><span data-stu-id="ec671-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ec671-126">Definir condições para quando os dados são exibidos</span><span class="sxs-lookup"><span data-stu-id="ec671-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ec671-127">Elemento SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ec671-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ec671-128">Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ec671-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="ec671-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec671-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
