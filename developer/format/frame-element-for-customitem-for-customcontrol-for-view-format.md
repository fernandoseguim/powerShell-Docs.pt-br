---
title: Elemento de quadro para CustomItem para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054774"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="32a7a-102">Elemento Frame para CustomItem para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="32a7a-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="32a7a-103">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="32a7a-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="32a7a-104">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="32a7a-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="32a7a-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de quadro CustomControlView (formato) CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="32a7a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="32a7a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32a7a-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="32a7a-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="32a7a-107">Attributes and Elements</span></span>

<span data-ttu-id="32a7a-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="32a7a-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="32a7a-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="32a7a-109">Attributes</span></span>

<span data-ttu-id="32a7a-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="32a7a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="32a7a-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="32a7a-111">Child Elements</span></span>

|<span data-ttu-id="32a7a-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="32a7a-112">Element</span></span>|<span data-ttu-id="32a7a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="32a7a-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="32a7a-114">Elemento necessário</span><span class="sxs-lookup"><span data-stu-id="32a7a-114">Required Element</span></span>|
|[<span data-ttu-id="32a7a-115">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="32a7a-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="32a7a-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="32a7a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="32a7a-117">Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="32a7a-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="32a7a-118">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="32a7a-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="32a7a-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="32a7a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="32a7a-120">Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita.</span><span class="sxs-lookup"><span data-stu-id="32a7a-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="32a7a-121">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="32a7a-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="32a7a-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="32a7a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="32a7a-123">Especifica o número de caracteres de dados são deslocados da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="32a7a-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="32a7a-124">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="32a7a-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="32a7a-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="32a7a-125">Optional element.</span></span><br /><br /> <span data-ttu-id="32a7a-126">Especifica o número de caracteres de dados são deslocados da margem direita.</span><span class="sxs-lookup"><span data-stu-id="32a7a-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="32a7a-127">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="32a7a-127">Parent Elements</span></span>

|<span data-ttu-id="32a7a-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="32a7a-128">Element</span></span>|<span data-ttu-id="32a7a-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="32a7a-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="32a7a-130">Elemento CustomItem para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="32a7a-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="32a7a-131">Define quais dados são exibidos pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="32a7a-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="32a7a-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="32a7a-132">Remarks</span></span>

<span data-ttu-id="32a7a-133">Não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementos no mesmo `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="32a7a-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="32a7a-134">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="32a7a-134">See Also</span></span>

[<span data-ttu-id="32a7a-135">Elemento FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="32a7a-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="32a7a-136">Elemento FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="32a7a-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="32a7a-137">Elemento LeftIndent</span><span class="sxs-lookup"><span data-stu-id="32a7a-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="32a7a-138">Elemento RightIndent</span><span class="sxs-lookup"><span data-stu-id="32a7a-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="32a7a-139">Elemento CustomItem para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="32a7a-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="32a7a-140">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="32a7a-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
