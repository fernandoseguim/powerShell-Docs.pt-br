---
title: Elemento CustomEntries para CustomControl controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861802"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="1946e-102">Elemento CustomEntries para CustomControl para Controls para View (formato)</span><span class="sxs-lookup"><span data-stu-id="1946e-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="1946e-103">Fornece as definições para o controle.</span><span class="sxs-lookup"><span data-stu-id="1946e-103">Provides the definitions for the control.</span></span> <span data-ttu-id="1946e-104">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="1946e-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1946e-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="1946e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1946e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1946e-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1946e-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1946e-107">Attributes and Elements</span></span>

<span data-ttu-id="1946e-108">As seções a seguir descrevem atributos, elementos filho e elementos pai do `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="1946e-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="1946e-109">Não há nenhum limite máximo ao número de elementos filho que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="1946e-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="1946e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1946e-110">Attributes</span></span>

<span data-ttu-id="1946e-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1946e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1946e-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="1946e-112">Child Elements</span></span>

|<span data-ttu-id="1946e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1946e-113">Element</span></span>|<span data-ttu-id="1946e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1946e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1946e-115">Elemento CustomEntry para CustomEntries controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="1946e-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="1946e-116">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="1946e-116">Required element.</span></span><br /><br /> <span data-ttu-id="1946e-117">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="1946e-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1946e-118">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="1946e-118">Parent Elements</span></span>

|<span data-ttu-id="1946e-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="1946e-119">Element</span></span>|<span data-ttu-id="1946e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="1946e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1946e-121">Elemento CustomControl para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="1946e-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="1946e-122">Define o controle usado pela exibição.</span><span class="sxs-lookup"><span data-stu-id="1946e-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1946e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="1946e-123">Remarks</span></span>

<span data-ttu-id="1946e-124">Na maioria dos casos, um controle tem apenas uma definição, que é especificada em um único `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="1946e-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="1946e-125">No entanto, é possível fornecer várias definições, se você quiser usar o mesmo controle para exibir objetos diferentes do .NET.</span><span class="sxs-lookup"><span data-stu-id="1946e-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="1946e-126">Nesses casos, você pode definir um `CustomEntry` elemento para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="1946e-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1946e-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="1946e-127">See Also</span></span>

[<span data-ttu-id="1946e-128">Elemento CustomEntry para CustomEntries controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="1946e-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="1946e-129">Elemento CustomControl para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="1946e-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1946e-130">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="1946e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
