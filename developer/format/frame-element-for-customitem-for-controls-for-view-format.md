---
title: Elemento de quadro para CustomItem para controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859812"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="6c757-102">Elemento Frame para CustomItem para Controls para View (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="6c757-103">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="6c757-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="6c757-104">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="6c757-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6c757-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) CustomItem CustomEntry controles para o elemento de exibição (formato) do quadro para CustomItem controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6c757-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c757-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c757-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6c757-107">Attributes and Elements</span></span>

<span data-ttu-id="6c757-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="6c757-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c757-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="6c757-109">Attributes</span></span>

<span data-ttu-id="6c757-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6c757-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c757-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="6c757-111">Child Elements</span></span>

|<span data-ttu-id="6c757-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c757-112">Element</span></span>|<span data-ttu-id="6c757-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c757-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="6c757-114">Elemento necessário</span><span class="sxs-lookup"><span data-stu-id="6c757-114">Required Element</span></span>|
|[<span data-ttu-id="6c757-115">Elemento FirstLineHanging do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="6c757-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="6c757-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6c757-117">Especifica quantos caracteres da primeira linha é deslocada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="6c757-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="6c757-118">Elemento FirstLineIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="6c757-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="6c757-119">Optional element.</span></span><br /><br /> <span data-ttu-id="6c757-120">Especifica quantos caracteres da primeira linha é deslocada para a direita.</span><span class="sxs-lookup"><span data-stu-id="6c757-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="6c757-121">Elemento LeftIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="6c757-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="6c757-122">Optional element.</span></span><br /><br /> <span data-ttu-id="6c757-123">Especifica o número de caracteres de dados são deslocados da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="6c757-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="6c757-124">Elemento RightIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="6c757-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="6c757-125">Optional element.</span></span><br /><br /> <span data-ttu-id="6c757-126">Especifica o número de caracteres de dados são deslocados da margem direita.</span><span class="sxs-lookup"><span data-stu-id="6c757-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6c757-127">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="6c757-127">Parent Elements</span></span>

|<span data-ttu-id="6c757-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c757-128">Element</span></span>|<span data-ttu-id="6c757-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c757-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c757-130">Elemento CustomItem para CustomEntry controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="6c757-131">Define quais dados são exibidos pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="6c757-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6c757-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c757-132">Remarks</span></span>

<span data-ttu-id="6c757-133">Não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementos no mesmo `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="6c757-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c757-134">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="6c757-134">See Also</span></span>

[<span data-ttu-id="6c757-135">Elemento FirstLineHanging do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="6c757-136">Elemento FirstLineIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="6c757-137">Elemento LeftIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="6c757-138">Elemento RightIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="6c757-139">Elemento CustomItem para CustomEntry controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="6c757-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="6c757-140">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c757-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
