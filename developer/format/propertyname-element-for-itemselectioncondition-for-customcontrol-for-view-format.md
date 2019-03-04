---
title: Elemento PropertyName para ItemSelectionCondition para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854782"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="c273f-102">Elemento PropertyName para ItemSelectionCondition para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="c273f-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="c273f-103">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="c273f-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c273f-104">Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição é atendida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="c273f-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="c273f-105">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="c273f-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="c273f-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de exibição (formato) ExpressionBinding CustomItem para CustomControl para exibição (formato) ItemSelectionCondition elemento de associação de expressão para CustomControl para elemento de exibição (formato) PropertyName ItemSelectionCondition para CustomControl (formato de exibição</span><span class="sxs-lookup"><span data-stu-id="c273f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="c273f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c273f-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c273f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c273f-108">Attributes and Elements</span></span>

<span data-ttu-id="c273f-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="c273f-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c273f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c273f-110">Attributes</span></span>

<span data-ttu-id="c273f-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c273f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c273f-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="c273f-112">Child Elements</span></span>

<span data-ttu-id="c273f-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c273f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c273f-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="c273f-114">Parent Elements</span></span>

|<span data-ttu-id="c273f-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c273f-115">Element</span></span>|<span data-ttu-id="c273f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c273f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c273f-117">Elemento ItemSelectionCondition para associação de expressão para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="c273f-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="c273f-118">Define a condição que deve existir para esse controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c273f-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c273f-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="c273f-119">Text Value</span></span>

<span data-ttu-id="c273f-120">Especifique o nome da propriedade .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="c273f-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="c273f-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="c273f-121">Remarks</span></span>

<span data-ttu-id="c273f-122">Se esse elemento é usado, não é possível especificar o [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="c273f-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="c273f-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c273f-123">See Also</span></span>

[<span data-ttu-id="c273f-124">Elemento ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="c273f-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c273f-125">Elemento ItemSelectionCondition para associação de expressão para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="c273f-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="c273f-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="c273f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
