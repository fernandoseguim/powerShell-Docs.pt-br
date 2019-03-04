---
title: Elemento WideEntries para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853272"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="c0e99-102">Elemento WideEntries para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c0e99-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="c0e99-103">Fornece as definições do modo de exibição ampla.</span><span class="sxs-lookup"><span data-stu-id="c0e99-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="c0e99-104">O modo de exibição amplo deve especificar uma ou mais definições.</span><span class="sxs-lookup"><span data-stu-id="c0e99-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="c0e99-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) WideEntries elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="c0e99-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0e99-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0e99-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0e99-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c0e99-107">Attributes and Elements</span></span>

<span data-ttu-id="c0e99-108">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `WideEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="c0e99-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="c0e99-109">Pelo menos um elemento filho deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="c0e99-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0e99-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c0e99-110">Attributes</span></span>

<span data-ttu-id="c0e99-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c0e99-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0e99-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="c0e99-112">Child Elements</span></span>

|<span data-ttu-id="c0e99-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0e99-113">Element</span></span>|<span data-ttu-id="c0e99-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0e99-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0e99-115">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c0e99-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="c0e99-116">Fornece uma definição da exibição ampla.</span><span class="sxs-lookup"><span data-stu-id="c0e99-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0e99-117">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="c0e99-117">Parent Elements</span></span>

|<span data-ttu-id="c0e99-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0e99-118">Element</span></span>|<span data-ttu-id="c0e99-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0e99-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0e99-120">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c0e99-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="c0e99-121">Define uma ampla (único valor) formato de lista para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="c0e99-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0e99-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0e99-122">Remarks</span></span>

<span data-ttu-id="c0e99-123">Uma exibição ampla é um formato de lista que exibe um valor de propriedade única ou script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="c0e99-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="c0e99-124">Para obter mais informações sobre os componentes de uma exibição ampla, consulte [componentes de exibição ampla](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="c0e99-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c0e99-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c0e99-125">Example</span></span>

<span data-ttu-id="c0e99-126">A exemplo a seguir mostra uma `WideEntries` que define um único elemento `WideEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="c0e99-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="c0e99-127">O `WideEntry` elemento contém um único `WideItem` elemento que define qual valor de propriedade ou o script é exibido no modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="c0e99-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="c0e99-128">Para obter um exemplo completo de uma exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="c0e99-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c0e99-129">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c0e99-129">See Also</span></span>

[<span data-ttu-id="c0e99-130">Criando uma exibição ampla</span><span class="sxs-lookup"><span data-stu-id="c0e99-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c0e99-131">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c0e99-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="c0e99-132">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c0e99-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="c0e99-133">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0e99-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
