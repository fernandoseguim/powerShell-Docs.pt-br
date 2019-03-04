---
title: Elemento ExpressionBinding para CustomItem para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860682"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="0182c-102">Elemento ExpressionBinding para CustomItem para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="0182c-103">Define os dados que são exibidos pelo controle.</span><span class="sxs-lookup"><span data-stu-id="0182c-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="0182c-104">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="0182c-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0182c-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento de configuração para elemento de exibição (formato) CustomEntries CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para CustomControl para exibição ( Elemento de CustomItem Format) para CustomEntry para CustomControl para elemento de exibição (formato) ExpressionBinding CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0182c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0182c-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0182c-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0182c-107">Attributes and Elements</span></span>

<span data-ttu-id="0182c-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="0182c-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0182c-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0182c-109">Attributes</span></span>

<span data-ttu-id="0182c-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0182c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0182c-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="0182c-111">Child Elements</span></span>

|<span data-ttu-id="0182c-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="0182c-112">Element</span></span>|<span data-ttu-id="0182c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0182c-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="0182c-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0182c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="0182c-115">Define um controle que é usado por esse controle.</span><span class="sxs-lookup"><span data-stu-id="0182c-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="0182c-116">Elemento CustomControlName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="0182c-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0182c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0182c-118">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="0182c-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="0182c-119">Elemento EnumerateCollection para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="0182c-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0182c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0182c-121">Especificado que os elementos das coleções são exibidos.</span><span class="sxs-lookup"><span data-stu-id="0182c-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="0182c-122">Elemento ItemSelectionCondition para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="0182c-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0182c-123">Optional element.</span></span><br /><br /> <span data-ttu-id="0182c-124">Define a condição que deve existir para esse controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="0182c-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="0182c-125">Elemento PropertyName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="0182c-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0182c-126">Optional element.</span></span><br /><br /> <span data-ttu-id="0182c-127">Especifica a propriedade .NET cujo valor é exibido pelo controle.</span><span class="sxs-lookup"><span data-stu-id="0182c-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="0182c-128">Elemento ScriptBlock para ExpressionBinding para CustomCustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="0182c-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0182c-129">Optional element.</span></span><br /><br /> <span data-ttu-id="0182c-130">Especifica o script cujo valor é exibido pelo controle.</span><span class="sxs-lookup"><span data-stu-id="0182c-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0182c-131">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="0182c-131">Parent Elements</span></span>

|<span data-ttu-id="0182c-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="0182c-132">Element</span></span>|<span data-ttu-id="0182c-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="0182c-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0182c-134">Elemento CustomItem para CustomEntry para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="0182c-135">Define quais dados são exibidos com o modo de exibição do controle personalizado e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="0182c-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0182c-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="0182c-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="0182c-137">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0182c-137">See Also</span></span>

[<span data-ttu-id="0182c-138">Elemento CustomControlName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0182c-139">Elemento EnumerateCollection para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0182c-140">Elemento ItemSelectionCondition para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="0182c-141">Elemento PropertyName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0182c-142">Elemento ScriptBlock para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0182c-143">Elemento CustomItem para CustomEntry para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0182c-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0182c-144">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="0182c-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
