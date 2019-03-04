---
title: Elemento ScriptBlock para ListItem para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855552"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="190e8-102">Elemento ScriptBlock para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="190e8-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="190e8-103">Especifica o script cujo valor é exibido na linha.</span><span class="sxs-lookup"><span data-stu-id="190e8-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="190e8-104">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento ListControl elemento (formato) ListEntries elemento de configuração para ListControl (formato) elemento ListEntry ListEntries para elemento de ListItems ListControl (formato) ListEntry para elemento ListItem ListControl (formato) ListItems para ListControl (formato) ScriptBlock elemento ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="190e8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="190e8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="190e8-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="190e8-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="190e8-106">Attributes and Elements</span></span>

<span data-ttu-id="190e8-107">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="190e8-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="190e8-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="190e8-108">Attributes</span></span>

<span data-ttu-id="190e8-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="190e8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="190e8-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="190e8-110">Child Elements</span></span>

<span data-ttu-id="190e8-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="190e8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="190e8-112">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="190e8-112">Parent Elements</span></span>

|<span data-ttu-id="190e8-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="190e8-113">Element</span></span>|<span data-ttu-id="190e8-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="190e8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="190e8-115">Elemento ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="190e8-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="190e8-116">Define a propriedade ou o script cujo valor é exibido em uma linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="190e8-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="190e8-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="190e8-117">Text Value</span></span>

<span data-ttu-id="190e8-118">Especifique o script cujo valor é exibido na linha.</span><span class="sxs-lookup"><span data-stu-id="190e8-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="190e8-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="190e8-119">Remarks</span></span>

<span data-ttu-id="190e8-120">Quando esse elemento for especificado, é possível especificar o [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="190e8-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="190e8-121">Para obter mais informações sobre como especificar scripts em uma exibição de lista, consulte [exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="190e8-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="190e8-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="190e8-122">Example</span></span>

<span data-ttu-id="190e8-123">O exemplo a seguir mostra como especificar a propriedade cujo valor é exibido.</span><span class="sxs-lookup"><span data-stu-id="190e8-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="190e8-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="190e8-124">See Also</span></span>

[<span data-ttu-id="190e8-125">Elemento PropertyName para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="190e8-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="190e8-126">Criando uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="190e8-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="190e8-127">Elemento ListItem para ListItems para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="190e8-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="190e8-128">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="190e8-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
