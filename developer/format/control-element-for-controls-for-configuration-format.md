---
title: Elemento de controle para controles para configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858882"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="79c47-102">Elemento Control para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="79c47-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="79c47-103">Define um controle comum que pode ser usado por todas as exibições do arquivo de formatação e o nome que é usado para fazer referência ao controle.</span><span class="sxs-lookup"><span data-stu-id="79c47-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="79c47-104">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="79c47-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79c47-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79c47-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79c47-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="79c47-106">Attributes and Elements</span></span>

<span data-ttu-id="79c47-107">As seções a seguir descrevem os atributos e elementos filho do elemento pai o `Control` elemento.</span><span class="sxs-lookup"><span data-stu-id="79c47-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="79c47-108">Você deve especificar apenas um de cada elemento filho.</span><span class="sxs-lookup"><span data-stu-id="79c47-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="79c47-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="79c47-109">Attributes</span></span>

<span data-ttu-id="79c47-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="79c47-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79c47-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="79c47-111">Child Elements</span></span>

|<span data-ttu-id="79c47-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="79c47-112">Element</span></span>|<span data-ttu-id="79c47-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="79c47-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79c47-114">Elemento CustomControl para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="79c47-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="79c47-115">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="79c47-115">Required element.</span></span><br /><br /> <span data-ttu-id="79c47-116">Define o controle.</span><span class="sxs-lookup"><span data-stu-id="79c47-116">Defines the control.</span></span>|
|[<span data-ttu-id="79c47-117">Elemento Name para o controle para a configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="79c47-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="79c47-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="79c47-118">Required element.</span></span><br /><br /> <span data-ttu-id="79c47-119">Especifica o nome usado para fazer referência ao controle.</span><span class="sxs-lookup"><span data-stu-id="79c47-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="79c47-120">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="79c47-120">Parent Elements</span></span>

|<span data-ttu-id="79c47-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="79c47-121">Element</span></span>|<span data-ttu-id="79c47-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="79c47-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79c47-123">Elemento de controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="79c47-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="79c47-124">Define os controles comuns que podem ser usados por todos os modos de exibição do arquivo de formatação ou por outros controles.</span><span class="sxs-lookup"><span data-stu-id="79c47-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="79c47-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="79c47-125">Remarks</span></span>

<span data-ttu-id="79c47-126">O nome fornecido para esse controle pode ser referenciado nos elementos a seguir:</span><span class="sxs-lookup"><span data-stu-id="79c47-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="79c47-127">Elemento ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="79c47-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="79c47-128">Elemento GroupBy para View(Format)</span><span class="sxs-lookup"><span data-stu-id="79c47-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="79c47-129">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="79c47-129">See Also</span></span>

[<span data-ttu-id="79c47-130">Elemento de controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="79c47-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="79c47-131">Elemento CustomControl para controle de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="79c47-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="79c47-132">Elemento ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="79c47-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="79c47-133">Elemento GroupBy para View(Format)</span><span class="sxs-lookup"><span data-stu-id="79c47-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="79c47-134">Elemento Name para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="79c47-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="79c47-135">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="79c47-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
