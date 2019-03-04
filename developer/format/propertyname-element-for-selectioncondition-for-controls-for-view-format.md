---
title: Elemento PropertyName para SelectionCondition controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853522"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="00704-102">Elemento PropertyName para SelectionCondition para Controls para View (formato)</span><span class="sxs-lookup"><span data-stu-id="00704-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="00704-103">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="00704-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="00704-104">Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a entrada é usada.</span><span class="sxs-lookup"><span data-stu-id="00704-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="00704-105">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="00704-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="00704-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para controles para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) EntrySelectedBy CustomEntry para controles para elemento de exibição (formato) SelectionCondition EntrySelectedBy para controles para exibição ( Elemento de PropertyName Format) para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="00704-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00704-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00704-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00704-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="00704-108">Attributes and Elements</span></span>

<span data-ttu-id="00704-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="00704-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00704-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="00704-110">Attributes</span></span>

<span data-ttu-id="00704-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="00704-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00704-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="00704-112">Child Elements</span></span>

<span data-ttu-id="00704-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="00704-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="00704-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="00704-114">Parent Elements</span></span>

|<span data-ttu-id="00704-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="00704-115">Element</span></span>|<span data-ttu-id="00704-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="00704-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00704-117">Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="00704-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="00704-118">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="00704-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="00704-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="00704-119">Text Value</span></span>

<span data-ttu-id="00704-120">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="00704-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="00704-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="00704-121">Remarks</span></span>

<span data-ttu-id="00704-122">A condição de seleção deve especificar um nome menos de uma propriedade ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="00704-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="00704-123">Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="00704-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00704-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="00704-124">See Also</span></span>

[<span data-ttu-id="00704-125">Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="00704-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="00704-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="00704-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
