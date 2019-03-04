---
title: Elemento ItemSelectionCondition para ExpressionBinding para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861682"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="768eb-102">Elemento ItemSelectionCondition para ExpressionBinding para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="768eb-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="768eb-103">Define a condição que deve existir para esse controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="768eb-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="768eb-104">Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="768eb-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="768eb-105">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl controles para o elemento de configuração (formato) de CustomItem para CustomEntry controles para o elemento de configuração de ExpressionBinding para CustomItem para controles de configuração (formato) Elemento ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="768eb-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="768eb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="768eb-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="768eb-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="768eb-107">Attributes and Elements</span></span>

<span data-ttu-id="768eb-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="768eb-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="768eb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="768eb-109">Attributes</span></span>

<span data-ttu-id="768eb-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="768eb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="768eb-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="768eb-111">Child Elements</span></span>

|<span data-ttu-id="768eb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="768eb-112">Element</span></span>|<span data-ttu-id="768eb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="768eb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="768eb-114">Elemento PropertyName para ItemSelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="768eb-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="768eb-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="768eb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="768eb-116">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="768eb-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="768eb-117">Elemento ScriptBlock para ItemSelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="768eb-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="768eb-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="768eb-118">Optional element.</span></span><br /><br /> <span data-ttu-id="768eb-119">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="768eb-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="768eb-120">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="768eb-120">Parent Elements</span></span>

|<span data-ttu-id="768eb-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="768eb-121">Element</span></span>|<span data-ttu-id="768eb-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="768eb-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="768eb-123">Elemento ExpressionBinding para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="768eb-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="768eb-124">Define os dados que são exibidos pelo controle.</span><span class="sxs-lookup"><span data-stu-id="768eb-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="768eb-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="768eb-125">Remarks</span></span>

<span data-ttu-id="768eb-126">Você pode especificar um nome de propriedade ou um script para essa condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="768eb-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="768eb-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="768eb-127">See Also</span></span>

[<span data-ttu-id="768eb-128">Elemento PropertyName para ItemSelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="768eb-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="768eb-129">Elemento ScriptBlock para ItemSelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="768eb-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="768eb-130">Elemento ExpressionBinding para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="768eb-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="768eb-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="768eb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
