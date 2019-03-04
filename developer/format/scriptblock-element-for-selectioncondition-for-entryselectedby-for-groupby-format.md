---
title: Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853072"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="e3ff6-102">Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e3ff6-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="e3ff6-103">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="e3ff6-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e3ff6-104">Quando esse script é avaliado para `true`, a condição for atendida e a definição é usada.</span><span class="sxs-lookup"><span data-stu-id="e3ff6-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="e3ff6-105">Esse elemento é usado ao definir como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="e3ff6-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e3ff6-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) EntrySelectedBy CustomEntry para elemento de GroupBy (formato) SelectionCondition EntrySelectedBy para elemento de GroupBy (formato) ScriptBlock SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e3ff6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3ff6-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3ff6-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3ff6-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e3ff6-108">Attributes and Elements</span></span>

<span data-ttu-id="e3ff6-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="e3ff6-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3ff6-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e3ff6-110">Attributes</span></span>

<span data-ttu-id="e3ff6-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e3ff6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3ff6-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="e3ff6-112">Child Elements</span></span>

<span data-ttu-id="e3ff6-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e3ff6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3ff6-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="e3ff6-114">Parent Elements</span></span>

|<span data-ttu-id="e3ff6-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3ff6-115">Element</span></span>|<span data-ttu-id="e3ff6-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3ff6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3ff6-117">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e3ff6-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="e3ff6-118">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e3ff6-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3ff6-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e3ff6-119">Text Value</span></span>

<span data-ttu-id="e3ff6-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="e3ff6-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3ff6-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3ff6-121">Remarks</span></span>

<span data-ttu-id="e3ff6-122">A condição de seleção deve especificar pelo menos um script ou a propriedade nome para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="e3ff6-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e3ff6-123">Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e3ff6-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3ff6-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="e3ff6-124">See Also</span></span>

[<span data-ttu-id="e3ff6-125">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="e3ff6-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="e3ff6-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3ff6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
