---
title: Elemento ScriptBlock para ItemSelectionCondition para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855412"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="3784c-102">Elemento ScriptBlock para ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3784c-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="3784c-103">Especifica o script que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="3784c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="3784c-104">Quando esse script é avaliado para `true`, a condição é atendida e o item de lista é usado.</span><span class="sxs-lookup"><span data-stu-id="3784c-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="3784c-105">Esse elemento é usado ao definir uma exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="3784c-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="3784c-106">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento ListControl elemento (formato) ListEntries elemento de configuração para ListControl (formato) elemento ListEntry ListEntries para elemento de ListItems ListControl (formato) ListEntry para elemento ListItem ListControl (formato) ListItems para lista (Format) do controle ItemSelectionCondition elemento ListItem para elemento de ScriptBlock ListControl (formato) ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3784c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3784c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3784c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3784c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3784c-108">Attributes and Elements</span></span>

<span data-ttu-id="3784c-109">As seções a seguir descrevem atributos, elementos filho e os elementos pai do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="3784c-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3784c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3784c-110">Attributes</span></span>

<span data-ttu-id="3784c-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3784c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3784c-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="3784c-112">Child Elements</span></span>

<span data-ttu-id="3784c-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3784c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3784c-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="3784c-114">Parent Elements</span></span>

|<span data-ttu-id="3784c-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="3784c-115">Element</span></span>|<span data-ttu-id="3784c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="3784c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3784c-117">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3784c-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3784c-118">Define a condição que deve existir para esse item de lista a ser usado.</span><span class="sxs-lookup"><span data-stu-id="3784c-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3784c-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="3784c-119">Text Value</span></span>

<span data-ttu-id="3784c-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="3784c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="3784c-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="3784c-121">Remarks</span></span>

<span data-ttu-id="3784c-122">Se esse elemento é usado, não é possível especificar o `PropertyName` elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="3784c-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="3784c-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="3784c-123">See Also</span></span>

[<span data-ttu-id="3784c-124">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3784c-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
