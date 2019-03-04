---
title: Elemento PropertyName para SelectionCondition para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860962"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="55fe2-102">Elemento PropertyName para SelectionCondition para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="55fe2-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="55fe2-103">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="55fe2-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="55fe2-104">Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a definição é usada.</span><span class="sxs-lookup"><span data-stu-id="55fe2-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="55fe2-105">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="55fe2-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="55fe2-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento de configuração para elemento de exibição (formato) CustomEntries CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para CustomControl para exibição ( Elemento de CustomItem Format) para CustomEntry para CustomControl para elemento de exibição (formato) EntrySelectedBy CustomEntry para CustomControl para elemento de exibição (formato) SelectionCondition EntrySelectedBy para CustomControl para exibição (formato) PropertyName Elemento para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="55fe2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55fe2-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55fe2-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55fe2-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="55fe2-108">Attributes and Elements</span></span>

<span data-ttu-id="55fe2-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="55fe2-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55fe2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="55fe2-110">Attributes</span></span>

<span data-ttu-id="55fe2-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="55fe2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55fe2-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="55fe2-112">Child Elements</span></span>

<span data-ttu-id="55fe2-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="55fe2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="55fe2-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="55fe2-114">Parent Elements</span></span>

|<span data-ttu-id="55fe2-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="55fe2-115">Element</span></span>|<span data-ttu-id="55fe2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="55fe2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55fe2-117">Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="55fe2-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="55fe2-118">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="55fe2-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="55fe2-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="55fe2-119">Text Value</span></span>

<span data-ttu-id="55fe2-120">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="55fe2-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="55fe2-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="55fe2-121">Remarks</span></span>

<span data-ttu-id="55fe2-122">A condição de seleção deve especificar um nome menos de uma propriedade ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="55fe2-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="55fe2-123">Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="55fe2-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55fe2-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="55fe2-124">See Also</span></span>

[<span data-ttu-id="55fe2-125">Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="55fe2-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="55fe2-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="55fe2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
