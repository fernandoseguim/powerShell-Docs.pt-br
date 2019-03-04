---
title: Elemento de quadros para CustomItem para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862972"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="5b4d1-102">Elemento Frame para CustomItem para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5b4d1-103">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="5b4d1-104">Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5b4d1-105">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl controles para o elemento de configuração (formato) de CustomItem para CustomEntry controles para o elemento de quadro de configuração para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b4d1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b4d1-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b4d1-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5b4d1-107">Attributes and Elements</span></span>

<span data-ttu-id="5b4d1-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b4d1-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5b4d1-109">Attributes</span></span>

<span data-ttu-id="5b4d1-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b4d1-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="5b4d1-111">Child Elements</span></span>

|<span data-ttu-id="5b4d1-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5b4d1-112">Element</span></span>|<span data-ttu-id="5b4d1-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b4d1-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="5b4d1-114">Elemento necessário</span><span class="sxs-lookup"><span data-stu-id="5b4d1-114">Required Element</span></span>|
|[<span data-ttu-id="5b4d1-115">Elemento FirstLineHanging de quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="5b4d1-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="5b4d1-117">Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="5b4d1-118">Elemento FirstLineIndent de quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="5b4d1-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-119">Optional element.</span></span><br /><br /> <span data-ttu-id="5b4d1-120">Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="5b4d1-121">Elemento LeftIndent de quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="5b4d1-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-122">Optional element.</span></span><br /><br /> <span data-ttu-id="5b4d1-123">Especifica o número de caracteres de dados são deslocados da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="5b4d1-124">Elemento RightIndent de quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="5b4d1-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-125">Optional element.</span></span><br /><br /> <span data-ttu-id="5b4d1-126">Especifica o número de caracteres de dados são deslocados da margem direita.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5b4d1-127">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="5b4d1-127">Parent Elements</span></span>

|<span data-ttu-id="5b4d1-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="5b4d1-128">Element</span></span>|<span data-ttu-id="5b4d1-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b4d1-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b4d1-130">Elemento CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="5b4d1-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="5b4d1-131">Define quais dados são exibidos pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5b4d1-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b4d1-132">Remarks</span></span>

<span data-ttu-id="5b4d1-133">Não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementos no mesmo `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="5b4d1-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b4d1-134">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5b4d1-134">See Also</span></span>

[<span data-ttu-id="5b4d1-135">Elemento FirstLineHanging de quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="5b4d1-136">Elemento FirstLineIndent de quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="5b4d1-137">Elemento LeftIndent de quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="5b4d1-138">Elemento RightIndent de quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5b4d1-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="5b4d1-139">Elemento CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="5b4d1-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="5b4d1-140">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b4d1-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
