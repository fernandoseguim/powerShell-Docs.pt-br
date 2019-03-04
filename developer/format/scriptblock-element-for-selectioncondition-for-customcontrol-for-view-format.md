---
title: Elemento ScriptBlock para SelectionCondition para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857412"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="aea2c-102">Elemento ScriptBlock para SelectionCondition para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="aea2c-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="aea2c-103">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="aea2c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="aea2c-104">Quando esse script é avaliado para `true`, a condição for atendida e a definição é usada.</span><span class="sxs-lookup"><span data-stu-id="aea2c-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="aea2c-105">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="aea2c-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="aea2c-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento de configuração para elemento de exibição (formato) CustomEntries CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para CustomControl para exibição ( Elemento de CustomItem Format) para CustomEntry para CustomControl para elemento de exibição (formato) SelectionCondition EntrySelectedBy para CustomControl para elemento de exibição (formato) ScriptBlock SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="aea2c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aea2c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aea2c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aea2c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="aea2c-108">Attributes and Elements</span></span>

<span data-ttu-id="aea2c-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="aea2c-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aea2c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="aea2c-110">Attributes</span></span>

<span data-ttu-id="aea2c-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="aea2c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aea2c-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="aea2c-112">Child Elements</span></span>

<span data-ttu-id="aea2c-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="aea2c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aea2c-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="aea2c-114">Parent Elements</span></span>

|<span data-ttu-id="aea2c-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="aea2c-115">Element</span></span>|<span data-ttu-id="aea2c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="aea2c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aea2c-117">Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="aea2c-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="aea2c-118">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="aea2c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aea2c-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="aea2c-119">Text Value</span></span>

<span data-ttu-id="aea2c-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="aea2c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="aea2c-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="aea2c-121">Remarks</span></span>

<span data-ttu-id="aea2c-122">A condição de seleção deve especificar pelo menos um script ou a propriedade nome para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="aea2c-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="aea2c-123">Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="aea2c-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aea2c-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="aea2c-124">See Also</span></span>

[<span data-ttu-id="aea2c-125">Elemento SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="aea2c-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="aea2c-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aea2c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
