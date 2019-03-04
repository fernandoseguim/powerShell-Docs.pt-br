---
title: Elemento ScriptBlock para SelectionCondition controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861832"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="d05ef-102">Elemento ScriptBlock para SelectionCondition para Controls para View (formato)</span><span class="sxs-lookup"><span data-stu-id="d05ef-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="d05ef-103">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="d05ef-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d05ef-104">Quando esse script é avaliado para `true`, a condição for atendida e a definição é usada.</span><span class="sxs-lookup"><span data-stu-id="d05ef-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="d05ef-105">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="d05ef-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d05ef-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para controles para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) EntrySelectedBy CustomEntry para controles para elemento de exibição (formato) SelectionCondition EntrySelectedBy para controles para exibição ( Elemento de ScriptBlock Format) para SelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d05ef-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d05ef-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d05ef-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d05ef-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d05ef-108">Attributes and Elements</span></span>

<span data-ttu-id="d05ef-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="d05ef-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d05ef-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d05ef-110">Attributes</span></span>

<span data-ttu-id="d05ef-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d05ef-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d05ef-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="d05ef-112">Child Elements</span></span>

<span data-ttu-id="d05ef-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d05ef-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d05ef-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="d05ef-114">Parent Elements</span></span>

|<span data-ttu-id="d05ef-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="d05ef-115">Element</span></span>|<span data-ttu-id="d05ef-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d05ef-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d05ef-117">Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d05ef-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="d05ef-118">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d05ef-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d05ef-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="d05ef-119">Text Value</span></span>

<span data-ttu-id="d05ef-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="d05ef-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d05ef-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="d05ef-121">Remarks</span></span>

<span data-ttu-id="d05ef-122">A condição de seleção deve especificar pelo menos um script ou a propriedade nome para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d05ef-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d05ef-123">Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d05ef-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d05ef-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d05ef-124">See Also</span></span>

[<span data-ttu-id="d05ef-125">Elemento SelectionCondition para EntrySelectedBy controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d05ef-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="d05ef-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d05ef-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
