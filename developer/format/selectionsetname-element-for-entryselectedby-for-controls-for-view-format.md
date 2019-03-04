---
title: Elemento SelectionSetName para EntrySelectedBy controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860992"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="0151d-102">Elemento SelectionSetName para EntrySelectedBy para Controls para View (formato)</span><span class="sxs-lookup"><span data-stu-id="0151d-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="0151d-103">Especifica um conjunto de tipos do .NET que usam essa definição do controle.</span><span class="sxs-lookup"><span data-stu-id="0151d-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="0151d-104">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="0151d-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="0151d-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para controles para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) EntrySelectedBy CustomEntry para controles para elemento de exibição (formato) SelectionSetName EntrySelectedBy para controles para exibição ( Formato)</span><span class="sxs-lookup"><span data-stu-id="0151d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0151d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0151d-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0151d-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0151d-107">Attributes and Elements</span></span>

<span data-ttu-id="0151d-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="0151d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0151d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0151d-109">Attributes</span></span>

<span data-ttu-id="0151d-110">Não</span><span class="sxs-lookup"><span data-stu-id="0151d-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="0151d-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="0151d-111">Child Elements</span></span>

<span data-ttu-id="0151d-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0151d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0151d-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="0151d-113">Parent Elements</span></span>

|<span data-ttu-id="0151d-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0151d-114">Element</span></span>|<span data-ttu-id="0151d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0151d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0151d-116">Elemento EntrySelectedBy para CustomEntry controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0151d-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="0151d-117">Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="0151d-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0151d-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="0151d-118">Text Value</span></span>

<span data-ttu-id="0151d-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="0151d-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0151d-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="0151d-120">Remarks</span></span>

<span data-ttu-id="0151d-121">Cada definição de controle deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.</span><span class="sxs-lookup"><span data-stu-id="0151d-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0151d-122">Conjuntos de seleção normalmente são usados quando você deseja definir um grupo de objetos que são usados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="0151d-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="0151d-123">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0151d-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0151d-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0151d-124">See Also</span></span>

[<span data-ttu-id="0151d-125">Elemento EntrySelectedBy para CustomEntry controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0151d-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="0151d-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="0151d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
