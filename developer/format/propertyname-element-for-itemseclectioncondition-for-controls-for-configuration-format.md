---
title: Elemento PropertyName para ItemSeclectionCondition para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860922"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="ec8da-102">Elemento PropertyName para ItemSelectionCondition para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="ec8da-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ec8da-103">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="ec8da-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ec8da-104">Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição é atendida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="ec8da-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="ec8da-105">Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="ec8da-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ec8da-106">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl controles para o elemento de configuração (formato) de CustomItem para CustomEntry controles para o elemento de configuração de ExpressionBinding para CustomItem para controles de configuração (formato) Elemento ItemSelectionCondition para ExpressionBinding controles para o elemento de configuração (formato) de PropertyName para ItemSeclectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="ec8da-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ec8da-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec8da-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec8da-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ec8da-108">Attributes and Elements</span></span>

<span data-ttu-id="ec8da-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="ec8da-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec8da-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ec8da-110">Attributes</span></span>

<span data-ttu-id="ec8da-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ec8da-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec8da-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="ec8da-112">Child Elements</span></span>

<span data-ttu-id="ec8da-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ec8da-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec8da-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="ec8da-114">Parent Elements</span></span>

|<span data-ttu-id="ec8da-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec8da-115">Element</span></span>|<span data-ttu-id="ec8da-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec8da-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec8da-117">Elemento ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="ec8da-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="ec8da-118">Define a condição que deve existir para esse controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ec8da-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ec8da-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="ec8da-119">Text Value</span></span>

<span data-ttu-id="ec8da-120">Especifique o nome da propriedade .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="ec8da-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec8da-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec8da-121">Remarks</span></span>

<span data-ttu-id="ec8da-122">Se esse elemento é usado, não é possível especificar o [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="ec8da-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec8da-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ec8da-123">See Also</span></span>

[<span data-ttu-id="ec8da-124">Elemento ScriptBlock para ItemSeclectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="ec8da-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="ec8da-125">Elemento ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="ec8da-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="ec8da-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec8da-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
