---
title: Elemento ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862232"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="fce42-102">Elemento ScriptBlock para ItemSelectionCondition para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="fce42-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="fce42-103">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="fce42-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="fce42-104">Quando esse script é avaliado para `true`, a condição é atendida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="fce42-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="fce42-105">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="fce42-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="fce42-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de exibição (formato) ExpressionBinding CustomItem para CustomControl para exibição (formato) ItemSelectionCondition elemento de associação de expressão para CustomControl para elemento de exibição (formato) ScriptBlock ItemSelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="fce42-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fce42-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fce42-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fce42-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fce42-108">Attributes and Elements</span></span>

<span data-ttu-id="fce42-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="fce42-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fce42-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="fce42-110">Attributes</span></span>

<span data-ttu-id="fce42-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fce42-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fce42-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="fce42-112">Child Elements</span></span>

<span data-ttu-id="fce42-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fce42-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fce42-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="fce42-114">Parent Elements</span></span>

|<span data-ttu-id="fce42-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="fce42-115">Element</span></span>|<span data-ttu-id="fce42-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="fce42-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fce42-117">Elemento ItemSelectionCondition para associação de expressão para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="fce42-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="fce42-118">Define a condição que deve existir para esse controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="fce42-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fce42-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="fce42-119">Text Value</span></span>

<span data-ttu-id="fce42-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="fce42-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fce42-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="fce42-121">Remarks</span></span>

<span data-ttu-id="fce42-122">Se esse elemento é usado, não é possível especificar o [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="fce42-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="fce42-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="fce42-123">See Also</span></span>

[<span data-ttu-id="fce42-124">Elemento PropertyName para ItemSelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="fce42-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fce42-125">Elemento ItemSelectionCondition para associação de expressão para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="fce42-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="fce42-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="fce42-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
