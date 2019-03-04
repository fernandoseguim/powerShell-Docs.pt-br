---
title: Elemento ItemSelectionCondition para ExpressionBinding controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861842"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="d6259-102">Elemento ItemSelectionCondition para ExpressionBinding para Controls para View (formato)</span><span class="sxs-lookup"><span data-stu-id="d6259-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="d6259-103">Define a condição que deve existir para esse controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d6259-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="d6259-104">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="d6259-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d6259-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) CustomItem CustomEntry para controles para elemento de exibição (formato) ExpressionBinding CustomItem controles para exibição (formato) Elemento ItemSelectionCondition de ExpressionBinding controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d6259-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d6259-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6259-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d6259-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d6259-107">Attributes and Elements</span></span>

<span data-ttu-id="d6259-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="d6259-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d6259-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6259-109">Attributes</span></span>

<span data-ttu-id="d6259-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d6259-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d6259-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="d6259-111">Child Elements</span></span>

|<span data-ttu-id="d6259-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6259-112">Element</span></span>|<span data-ttu-id="d6259-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6259-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6259-114">Elemento PropertyName para ItemSelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d6259-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="d6259-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d6259-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d6259-116">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="d6259-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d6259-117">Elemento ScriptBlock para ItemSelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d6259-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="d6259-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d6259-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d6259-119">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="d6259-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d6259-120">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="d6259-120">Parent Elements</span></span>

|<span data-ttu-id="d6259-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6259-121">Element</span></span>|<span data-ttu-id="d6259-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6259-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6259-123">Elemento ExpressionBinding para CustomItem controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d6259-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="d6259-124">Define os dados que são exibidos pelo controle.</span><span class="sxs-lookup"><span data-stu-id="d6259-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d6259-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6259-125">Remarks</span></span>

<span data-ttu-id="d6259-126">Você pode especificar um nome de propriedade ou um script para essa condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d6259-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6259-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d6259-127">See Also</span></span>

[<span data-ttu-id="d6259-128">Elemento PropertyName para ItemSelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d6259-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="d6259-129">Elemento ScriptBlock para ItemSelectionCondition controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d6259-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="d6259-130">Elemento ExpressionBinding para CustomItem controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d6259-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="d6259-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6259-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
