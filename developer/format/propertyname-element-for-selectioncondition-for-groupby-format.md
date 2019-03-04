---
title: Elemento PropertyName para SelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853182"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="d45ec-102">Elemento PropertyName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d45ec-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="d45ec-103">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="d45ec-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="d45ec-104">Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a definição é usada.</span><span class="sxs-lookup"><span data-stu-id="d45ec-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="d45ec-105">Esse elemento é usado ao definir como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="d45ec-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d45ec-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) EntrySelectedBy CustomEntry para elemento de GroupBy (formato) SelectionCondition EntrySelectedBy para elemento de PropertyName GroupBy (formato) SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d45ec-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d45ec-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d45ec-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d45ec-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d45ec-108">Attributes and Elements</span></span>

<span data-ttu-id="d45ec-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="d45ec-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d45ec-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d45ec-110">Attributes</span></span>

<span data-ttu-id="d45ec-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d45ec-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d45ec-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="d45ec-112">Child Elements</span></span>

<span data-ttu-id="d45ec-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d45ec-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d45ec-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="d45ec-114">Parent Elements</span></span>

|<span data-ttu-id="d45ec-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="d45ec-115">Element</span></span>|<span data-ttu-id="d45ec-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d45ec-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d45ec-117">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d45ec-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="d45ec-118">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d45ec-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d45ec-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="d45ec-119">Text Value</span></span>

<span data-ttu-id="d45ec-120">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="d45ec-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="d45ec-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="d45ec-121">Remarks</span></span>

<span data-ttu-id="d45ec-122">A condição de seleção deve especificar um nome menos de uma propriedade ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d45ec-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="d45ec-123">Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d45ec-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d45ec-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d45ec-124">See Also</span></span>

[<span data-ttu-id="d45ec-125">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d45ec-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="d45ec-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d45ec-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
