---
title: Elemento WideControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859822"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="95010-102">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="95010-102">WideControl Element (Format)</span></span>

<span data-ttu-id="95010-103">Define uma ampla (único valor) formato de lista para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="95010-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="95010-104">Essa exibição mostra um valor de propriedade única ou script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="95010-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="95010-105">Configuração (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento WideControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="95010-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="95010-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95010-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="95010-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="95010-107">Attributes and Elements</span></span>

<span data-ttu-id="95010-108">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `WideControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="95010-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="95010-109">Não é possível especificar o `AutoSize` e `ColumnNumber` elementos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="95010-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="95010-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="95010-110">Attributes</span></span>

<span data-ttu-id="95010-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="95010-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95010-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="95010-112">Child Elements</span></span>

|<span data-ttu-id="95010-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="95010-113">Element</span></span>|<span data-ttu-id="95010-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="95010-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95010-115">Elemento AutoSize para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="95010-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="95010-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="95010-116">Optional element.</span></span><br /><br /> <span data-ttu-id="95010-117">Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.</span><span class="sxs-lookup"><span data-stu-id="95010-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="95010-118">Elemento ColumnNumber para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="95010-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="95010-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="95010-119">Optional element.</span></span><br /><br /> <span data-ttu-id="95010-120">Especifica o número de colunas exibidas no modo de exibição amplo.</span><span class="sxs-lookup"><span data-stu-id="95010-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="95010-121">Elemento WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="95010-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="95010-122">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="95010-122">Required element.</span></span><br /><br /> <span data-ttu-id="95010-123">Fornece as definições do modo de exibição ampla.</span><span class="sxs-lookup"><span data-stu-id="95010-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="95010-124">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="95010-124">Parent Elements</span></span>

|<span data-ttu-id="95010-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="95010-125">Element</span></span>|<span data-ttu-id="95010-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="95010-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95010-127">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="95010-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="95010-128">Define uma exibição que é usada para exibir um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="95010-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="95010-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="95010-129">Remarks</span></span>

<span data-ttu-id="95010-130">Ao definir uma exibição ampla, você pode adicionar o `AutoSize` elemento ou o `ColumnNumber` , mas não é possível adicionar ambos.</span><span class="sxs-lookup"><span data-stu-id="95010-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="95010-131">Na maioria dos casos, somente uma definição, é necessária para cada exibição ampla, mas é possível ter várias definições, se você quiser usar a mesma exibição para exibir objetos diferentes do .NET.</span><span class="sxs-lookup"><span data-stu-id="95010-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="95010-132">Nesses casos, você pode fornecer uma definição separada para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="95010-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="95010-133">Para obter mais informações sobre os componentes de uma exibição ampla, consulte [componentes de exibição ampla](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="95010-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="95010-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95010-134">Example</span></span>

<span data-ttu-id="95010-135">A exemplo a seguir mostra uma `WideControl` que é usado para exibir uma propriedade do elemento de [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="95010-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="95010-136">Para obter um exemplo completo de uma exibição ampla, consulte [exibição ampla (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="95010-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95010-137">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="95010-137">See Also</span></span>

[<span data-ttu-id="95010-138">Elemento AutoSize para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="95010-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="95010-139">Elemento ColumnNumber para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="95010-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="95010-140">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="95010-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="95010-141">Elemento WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="95010-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="95010-142">Exibição ampla (Basic)</span><span class="sxs-lookup"><span data-stu-id="95010-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="95010-143">Criando uma exibição ampla</span><span class="sxs-lookup"><span data-stu-id="95010-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="95010-144">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="95010-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
