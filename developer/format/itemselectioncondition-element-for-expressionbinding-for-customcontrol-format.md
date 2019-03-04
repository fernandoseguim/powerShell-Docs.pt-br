---
title: Elemento ItemSelectionCondition para ExpressionBinding para CustomControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858182"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="4b177-102">Elemento ItemSelectionCondition para ExpressionBinding para CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="4b177-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="4b177-103">Define a condição que deve existir para esse controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="4b177-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="4b177-104">Não há nenhum limite para o número de condições de seleção que pode ser especificado para um item de controle.</span><span class="sxs-lookup"><span data-stu-id="4b177-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="4b177-105">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="4b177-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="4b177-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de exibição (formato) ExpressionBinding CustomItem para CustomControl para exibição (formato) ItemSelectionCondition elemento de associação de expressão para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="4b177-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b177-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b177-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b177-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4b177-108">Attributes and Elements</span></span>

<span data-ttu-id="4b177-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="4b177-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b177-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="4b177-110">Attributes</span></span>

<span data-ttu-id="4b177-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4b177-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b177-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="4b177-112">Child Elements</span></span>

|<span data-ttu-id="4b177-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="4b177-113">Element</span></span>|<span data-ttu-id="4b177-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b177-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b177-115">Elemento PropertyName para ItemSelectionCondition para CustomControl (formato de exibição</span><span class="sxs-lookup"><span data-stu-id="4b177-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="4b177-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4b177-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4b177-117">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="4b177-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="4b177-118">Elemento ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="4b177-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="4b177-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4b177-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4b177-120">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="4b177-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4b177-121">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="4b177-121">Parent Elements</span></span>

|<span data-ttu-id="4b177-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="4b177-122">Element</span></span>|<span data-ttu-id="4b177-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b177-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b177-124">Elemento ExpressionBinding para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="4b177-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="4b177-125">Define os dados que são exibidos pelo controle.</span><span class="sxs-lookup"><span data-stu-id="4b177-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4b177-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b177-126">Remarks</span></span>

<span data-ttu-id="4b177-127">Você pode especificar um nome de propriedade ou um script para essa condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="4b177-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b177-128">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4b177-128">See Also</span></span>

[<span data-ttu-id="4b177-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b177-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="4b177-130">Elemento ExpressionBinding para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="4b177-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
