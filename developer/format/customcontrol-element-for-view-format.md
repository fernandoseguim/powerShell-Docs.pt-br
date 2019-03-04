---
title: Elemento CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861252"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="04bcc-102">Elemento CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="04bcc-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="04bcc-103">Define um formato de controle personalizado para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="04bcc-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="04bcc-104">Configuração (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="04bcc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04bcc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04bcc-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="04bcc-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="04bcc-106">Attributes and Elements</span></span>

<span data-ttu-id="04bcc-107">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="04bcc-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="04bcc-108">Você deve especificar um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="04bcc-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="04bcc-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="04bcc-109">Attributes</span></span>

<span data-ttu-id="04bcc-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="04bcc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04bcc-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="04bcc-111">Child Elements</span></span>

|<span data-ttu-id="04bcc-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="04bcc-112">Element</span></span>|<span data-ttu-id="04bcc-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="04bcc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04bcc-114">Elemento CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="04bcc-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="04bcc-115">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="04bcc-115">Required element.</span></span><br /><br /> <span data-ttu-id="04bcc-116">Fornece as definições do modo de exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="04bcc-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="04bcc-117">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="04bcc-117">Parent Elements</span></span>

|<span data-ttu-id="04bcc-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="04bcc-118">Element</span></span>|<span data-ttu-id="04bcc-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="04bcc-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04bcc-120">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="04bcc-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="04bcc-121">Define uma exibição que é usada para exibir um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="04bcc-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="04bcc-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="04bcc-122">Remarks</span></span>

<span data-ttu-id="04bcc-123">Na maioria dos casos, somente uma definição, é necessária para cada modo de exibição de controle, mas é possível fornecer várias definições, se você quiser usar a mesma exibição para exibir objetos diferentes do .NET.</span><span class="sxs-lookup"><span data-stu-id="04bcc-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="04bcc-124">Nesses casos, você pode fornecer uma definição separada para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="04bcc-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="04bcc-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="04bcc-125">See Also</span></span>

[<span data-ttu-id="04bcc-126">Elemento CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="04bcc-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="04bcc-127">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="04bcc-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="04bcc-128">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="04bcc-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
