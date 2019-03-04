---
title: Elemento WideItem para WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862622"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="17b06-102">Elemento WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="17b06-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="17b06-103">Define a propriedade ou o script cujo valor é exibido.</span><span class="sxs-lookup"><span data-stu-id="17b06-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="17b06-104">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) WideItem elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="17b06-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="17b06-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17b06-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="17b06-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="17b06-106">Attributes and Elements</span></span>

<span data-ttu-id="17b06-107">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="17b06-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="17b06-108">O elemento `FormatString` é opcional.</span><span class="sxs-lookup"><span data-stu-id="17b06-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="17b06-109">No entanto, você deve especificar uma `PropertyName` ou `ScriptBlock` elemento, mas você não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="17b06-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="17b06-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="17b06-110">Attributes</span></span>

<span data-ttu-id="17b06-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="17b06-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="17b06-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="17b06-112">Child Elements</span></span>

|<span data-ttu-id="17b06-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="17b06-113">Element</span></span>|<span data-ttu-id="17b06-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="17b06-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17b06-115">Elemento FormatString para WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="17b06-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="17b06-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="17b06-116">Optional element.</span></span><br /><br /> <span data-ttu-id="17b06-117">Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido no modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="17b06-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="17b06-118">Elemento PropertyName para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="17b06-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="17b06-119">Especifica a propriedade do objeto cujo valor é exibido no modo de exibição amplo.</span><span class="sxs-lookup"><span data-stu-id="17b06-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="17b06-120">Elemento ScriptBlock para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="17b06-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="17b06-121">Especifica o script cujo valor é exibido no modo de exibição amplo.</span><span class="sxs-lookup"><span data-stu-id="17b06-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="17b06-122">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="17b06-122">Parent Elements</span></span>

|<span data-ttu-id="17b06-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="17b06-123">Element</span></span>|<span data-ttu-id="17b06-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="17b06-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17b06-125">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="17b06-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="17b06-126">Fornece uma definição da exibição ampla.</span><span class="sxs-lookup"><span data-stu-id="17b06-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="17b06-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="17b06-127">Remarks</span></span>

<span data-ttu-id="17b06-128">Para obter mais informações sobre os componentes de uma exibição ampla, consulte [exibição ampla](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="17b06-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="17b06-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17b06-129">Example</span></span>

<span data-ttu-id="17b06-130">A exemplo a seguir mostra uma `WideEntry` que define um único elemento `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="17b06-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="17b06-131">O `WideItem` elemento define a propriedade ou cujo valor é exibido no modo de exibição de script.</span><span class="sxs-lookup"><span data-stu-id="17b06-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="17b06-132">Para obter um exemplo completo de uma exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="17b06-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17b06-133">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="17b06-133">See Also</span></span>

[<span data-ttu-id="17b06-134">Elemento FormatString para WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="17b06-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="17b06-135">Elemento PropertyName para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="17b06-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="17b06-136">Elemento ScriptBlock para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="17b06-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="17b06-137">Elemento WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="17b06-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="17b06-138">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="17b06-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
