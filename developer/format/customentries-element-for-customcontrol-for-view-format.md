---
title: Elemento CustomEntries para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861692"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="3fa38-102">Elemento CustomEntries para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="3fa38-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="3fa38-103">Fornece as definições do modo de exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="3fa38-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="3fa38-104">O modo de exibição do controle personalizado deve especificar uma ou mais definições.</span><span class="sxs-lookup"><span data-stu-id="3fa38-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="3fa38-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="3fa38-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3fa38-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fa38-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3fa38-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3fa38-107">Attributes and Elements</span></span>

<span data-ttu-id="3fa38-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomControlEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="3fa38-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="3fa38-109">Você deve especificar um ou mais elementos filho.</span><span class="sxs-lookup"><span data-stu-id="3fa38-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3fa38-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3fa38-110">Attributes</span></span>

<span data-ttu-id="3fa38-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3fa38-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3fa38-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="3fa38-112">Child Elements</span></span>

|<span data-ttu-id="3fa38-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="3fa38-113">Element</span></span>|<span data-ttu-id="3fa38-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fa38-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3fa38-115">Elemento CustomEntry para CustomEntries para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="3fa38-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="3fa38-116">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="3fa38-116">Required element.</span></span><br /><br /> <span data-ttu-id="3fa38-117">Fornece uma definição da exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="3fa38-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3fa38-118">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="3fa38-118">Parent Elements</span></span>

|<span data-ttu-id="3fa38-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="3fa38-119">Element</span></span>|<span data-ttu-id="3fa38-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fa38-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3fa38-121">Elemento CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="3fa38-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="3fa38-122">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="3fa38-122">Required element.</span></span><br /><br /> <span data-ttu-id="3fa38-123">Define um formato de controle personalizado para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="3fa38-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3fa38-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fa38-124">Remarks</span></span>

<span data-ttu-id="3fa38-125">Na maioria dos casos, um controle tem apenas uma definição, que é definida em um único `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="3fa38-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="3fa38-126">No entanto é possível ter várias definições, se você quiser usar o mesmo controle para exibir objetos diferentes do .NET.</span><span class="sxs-lookup"><span data-stu-id="3fa38-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="3fa38-127">Nesses casos, você pode definir um `CustomEntry` elemento para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="3fa38-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fa38-128">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="3fa38-128">See Also</span></span>

[<span data-ttu-id="3fa38-129">Elemento CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="3fa38-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="3fa38-130">Elemento CustomEntry para CustomEntries para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="3fa38-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3fa38-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fa38-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
