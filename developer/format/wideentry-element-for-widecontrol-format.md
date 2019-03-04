---
title: Elemento WideEntry para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856522"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="3d45f-102">Elemento WideEntry para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3d45f-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="3d45f-103">Fornece uma definição da exibição ampla.</span><span class="sxs-lookup"><span data-stu-id="3d45f-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="3d45f-104">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) elemento WideEntries (formato) WideEntry elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="3d45f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d45f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d45f-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d45f-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3d45f-106">Attributes and Elements</span></span>

<span data-ttu-id="3d45f-107">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `WideEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="3d45f-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="3d45f-108">Você deve especificar um único `WideItem` elemento filho.</span><span class="sxs-lookup"><span data-stu-id="3d45f-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d45f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3d45f-109">Attributes</span></span>

<span data-ttu-id="3d45f-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3d45f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d45f-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="3d45f-111">Child Elements</span></span>

|<span data-ttu-id="3d45f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3d45f-112">Element</span></span>|<span data-ttu-id="3d45f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d45f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d45f-114">Elemento EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3d45f-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="3d45f-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3d45f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3d45f-116">Define os tipos de .NET que usam essa definição ampla de entrada ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="3d45f-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="3d45f-117">Elemento WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="3d45f-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="3d45f-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="3d45f-118">Required element.</span></span><br /><br /> <span data-ttu-id="3d45f-119">Define a propriedade ou o script cujo valor é exibido.</span><span class="sxs-lookup"><span data-stu-id="3d45f-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3d45f-120">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="3d45f-120">Parent Elements</span></span>

|<span data-ttu-id="3d45f-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3d45f-121">Element</span></span>|<span data-ttu-id="3d45f-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d45f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d45f-123">Elemento WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="3d45f-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="3d45f-124">Fornece as definições do modo de exibição ampla.</span><span class="sxs-lookup"><span data-stu-id="3d45f-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d45f-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d45f-125">Remarks</span></span>

<span data-ttu-id="3d45f-126">Uma exibição ampla é um formato de lista que exibe um valor de propriedade única ou script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="3d45f-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="3d45f-127">Ao contrário de outros tipos de modos de exibição, você pode especificar apenas um elemento de item para cada definição de exibição.</span><span class="sxs-lookup"><span data-stu-id="3d45f-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="3d45f-128">Para obter mais informações sobre os outros componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3d45f-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3d45f-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d45f-129">Example</span></span>

<span data-ttu-id="3d45f-130">A exemplo a seguir mostra uma `WideEntry` que define um único elemento `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="3d45f-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="3d45f-131">O `WideItem` elemento define a propriedade cujo valor é exibido no modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="3d45f-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="3d45f-132">Para obter um exemplo completo de uma exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="3d45f-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d45f-133">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="3d45f-133">See Also</span></span>

[<span data-ttu-id="3d45f-134">Criando uma exibição ampla</span><span class="sxs-lookup"><span data-stu-id="3d45f-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3d45f-135">Elemento SelectionCondition para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3d45f-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="3d45f-136">Elemento SelectionSetName para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3d45f-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="3d45f-137">Elemento TypeName para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3d45f-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="3d45f-138">Elemento WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="3d45f-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="3d45f-139">Elemento WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="3d45f-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="3d45f-140">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d45f-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
