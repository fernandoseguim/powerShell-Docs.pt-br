---
title: Elemento de quadro para CustomItem para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854842"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="cb66d-102">Elemento Frame para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="cb66d-103">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="cb66d-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="cb66d-104">Esse elemento é usado ao definir como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="cb66d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cb66d-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) CustomItem CustomEntry para elemento de quadro GroupBy (formato) CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cb66d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb66d-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cb66d-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cb66d-107">Attributes and Elements</span></span>

<span data-ttu-id="cb66d-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="cb66d-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cb66d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="cb66d-109">Attributes</span></span>

<span data-ttu-id="cb66d-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cb66d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cb66d-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="cb66d-111">Child Elements</span></span>

|<span data-ttu-id="cb66d-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb66d-112">Element</span></span>|<span data-ttu-id="cb66d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb66d-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="cb66d-114">Elemento necessário</span><span class="sxs-lookup"><span data-stu-id="cb66d-114">Required Element</span></span>|
|[<span data-ttu-id="cb66d-115">Elemento FirstLineHanging para quadro de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="cb66d-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="cb66d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="cb66d-117">Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="cb66d-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="cb66d-118">Elemento FirstLineIndent para quadro de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="cb66d-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="cb66d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="cb66d-120">Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita.</span><span class="sxs-lookup"><span data-stu-id="cb66d-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="cb66d-121">Elemento LeftIndent para quadro de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="cb66d-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="cb66d-122">Optional element.</span></span><br /><br /> <span data-ttu-id="cb66d-123">Especifica o número de caracteres de dados são deslocados da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="cb66d-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="cb66d-124">[Elemento RightIndent para quadro de GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent elemento</span><span class="sxs-lookup"><span data-stu-id="cb66d-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="cb66d-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="cb66d-125">Optional element.</span></span><br /><br /> <span data-ttu-id="cb66d-126">Especifica o número de caracteres de dados são deslocados da margem direita.</span><span class="sxs-lookup"><span data-stu-id="cb66d-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cb66d-127">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="cb66d-127">Parent Elements</span></span>

|<span data-ttu-id="cb66d-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb66d-128">Element</span></span>|<span data-ttu-id="cb66d-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb66d-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb66d-130">Elemento CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="cb66d-131">Define quais dados são exibidos pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="cb66d-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cb66d-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb66d-132">Remarks</span></span>

<span data-ttu-id="cb66d-133">Não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementos no mesmo `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="cb66d-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb66d-134">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="cb66d-134">See Also</span></span>

[<span data-ttu-id="cb66d-135">Elemento FirstLineHanging para quadro de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="cb66d-136">Elemento FirstLineIndent para quadro de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="cb66d-137">Elemento LeftIndent para quadro de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="cb66d-138">Elemento RightIndent para quadro de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="cb66d-139">Elemento CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="cb66d-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="cb66d-140">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb66d-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
