---
title: Elemento PropertyName para ItemSelectionCondition para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855532"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="70630-102">Elemento PropertyName para ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="70630-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="70630-103">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="70630-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="70630-104">Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição é atendida e o modo de exibição é usado.</span><span class="sxs-lookup"><span data-stu-id="70630-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="70630-105">Esse elemento é usado ao definir uma exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="70630-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="70630-106">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento de configuração para elemento de ListItems ListControl (formato) ListEntry para ListItem ListControl (formato) Elemento para ListItems para ListControl (formato) ItemSelectionCondition elemento ListItem para elemento de PropertyName ListControls ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="70630-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70630-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70630-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70630-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="70630-108">Attributes and Elements</span></span>

<span data-ttu-id="70630-109">As seções a seguir descrevem atributos, elementos filho e os elementos pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="70630-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70630-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="70630-110">Attributes</span></span>

<span data-ttu-id="70630-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="70630-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70630-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="70630-112">Child Elements</span></span>

<span data-ttu-id="70630-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="70630-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70630-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="70630-114">Parent Elements</span></span>

|<span data-ttu-id="70630-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="70630-115">Element</span></span>|<span data-ttu-id="70630-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="70630-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70630-117">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="70630-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="70630-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="70630-118">Text Value</span></span>

<span data-ttu-id="70630-119">Especifique o nome da propriedade cujo valor é exibido.</span><span class="sxs-lookup"><span data-stu-id="70630-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="70630-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="70630-120">Remarks</span></span>

<span data-ttu-id="70630-121">Se esse elemento é usado, não é possível especificar o [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="70630-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="70630-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="70630-122">See Also</span></span>

[<span data-ttu-id="70630-123">Elemento ScriptBlock para ItemSelectionCondition para ListIControl (formato)</span><span class="sxs-lookup"><span data-stu-id="70630-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="70630-124">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="70630-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="70630-125">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="70630-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
