---
title: Elemento CustomEntries para CustomControl para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853672"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="fe3f0-102">Elemento CustomEntries para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="fe3f0-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="fe3f0-103">Fornece as definições para o controle.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-103">Provides the definitions for the control.</span></span> <span data-ttu-id="fe3f0-104">Esse elemento é usado ao definir como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="fe3f0-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="fe3f0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe3f0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe3f0-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe3f0-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fe3f0-107">Attributes and Elements</span></span>

<span data-ttu-id="fe3f0-108">As seções a seguir descrevem atributos, elementos filho e elementos pai do `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="fe3f0-109">Não há nenhum limite máximo ao número de elementos filho que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe3f0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="fe3f0-110">Attributes</span></span>

<span data-ttu-id="fe3f0-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe3f0-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="fe3f0-112">Child Elements</span></span>

|<span data-ttu-id="fe3f0-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="fe3f0-113">Element</span></span>|<span data-ttu-id="fe3f0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe3f0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe3f0-115">Elemento CustomEntry para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="fe3f0-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="fe3f0-116">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-116">Required element.</span></span><br /><br /> <span data-ttu-id="fe3f0-117">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fe3f0-118">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="fe3f0-118">Parent Elements</span></span>

|<span data-ttu-id="fe3f0-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="fe3f0-119">Element</span></span>|<span data-ttu-id="fe3f0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe3f0-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe3f0-121">Elemento CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="fe3f0-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="fe3f0-122">Define o controle personalizado que exibe o novo grupo.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fe3f0-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe3f0-123">Remarks</span></span>

<span data-ttu-id="fe3f0-124">Na maioria dos casos, um controle tem apenas uma definição, que é especificada em um único `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="fe3f0-125">No entanto, é possível fornecer várias definições, se você quiser usar o mesmo controle para exibir os grupos diferentes.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="fe3f0-126">Nesses casos, você pode definir um `CustomEntry` elemento para um grupo.</span><span class="sxs-lookup"><span data-stu-id="fe3f0-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe3f0-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="fe3f0-127">See Also</span></span>

[<span data-ttu-id="fe3f0-128">Elemento CustomEntry para CustomEntries controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="fe3f0-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="fe3f0-129">Elemento CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="fe3f0-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="fe3f0-130">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe3f0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
