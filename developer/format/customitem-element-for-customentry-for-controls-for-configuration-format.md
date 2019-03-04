---
title: Elemento CustomItem para CustomEntry para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862932"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="1bd1c-102">Elemento CustomItem para CustomEntry para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd1c-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1bd1c-103">Define quais dados são exibidos pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="1bd1c-104">Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1bd1c-105">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl controles para o elemento de configuração (formato) de CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="1bd1c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="1bd1c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1bd1c-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1bd1c-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1bd1c-107">Attributes and Elements</span></span>

<span data-ttu-id="1bd1c-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="1bd1c-109">Para obter mais informações, consulte comentários.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="1bd1c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1bd1c-110">Attributes</span></span>

<span data-ttu-id="1bd1c-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1bd1c-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="1bd1c-112">Child Elements</span></span>

|<span data-ttu-id="1bd1c-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1bd1c-113">Element</span></span>|<span data-ttu-id="1bd1c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1bd1c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1bd1c-115">Elemento ExpressionBinding para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd1c-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="1bd1c-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1bd1c-117">Define os dados que são exibidos pelo controle.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="1bd1c-118">Elemento de quadro para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd1c-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="1bd1c-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1bd1c-120">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="1bd1c-121">Elemento de nova linha para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd1c-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="1bd1c-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-122">Optional element.</span></span><br /><br /> <span data-ttu-id="1bd1c-123">Adiciona uma linha em branco para a exibição do controle.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="1bd1c-124">Elemento de texto para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd1c-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="1bd1c-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-125">Optional element.</span></span><br /><br /> <span data-ttu-id="1bd1c-126">Adiciona texto, como parênteses ou colchetes, para a exibição do controle.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1bd1c-127">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="1bd1c-127">Parent Elements</span></span>

|<span data-ttu-id="1bd1c-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="1bd1c-128">Element</span></span>|<span data-ttu-id="1bd1c-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="1bd1c-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1bd1c-130">Elemento CustomEntry para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd1c-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="1bd1c-131">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1bd1c-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="1bd1c-132">Remarks</span></span>

<span data-ttu-id="1bd1c-133">Ao especificar os elementos filho do `CustomItem` elemento, tenha em mente o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1bd1c-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="1bd1c-134">Os elementos filho devem ser adicionados na sequência a seguir: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="1bd1c-135">Não há nenhum limite máximo ao número de sequências que você pode especificar.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="1bd1c-136">Em cada sequência, não há nenhum limite máximo ao número de `ExpressionBinding` elementos que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="1bd1c-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bd1c-137">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="1bd1c-137">See Also</span></span>

[<span data-ttu-id="1bd1c-138">Elemento ExpressionBinding para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd1c-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="1bd1c-139">Elemento de quadro para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd1c-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="1bd1c-140">Elemento de nova linha para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd1c-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="1bd1c-141">Elemento de texto para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="1bd1c-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="1bd1c-142">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bd1c-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
