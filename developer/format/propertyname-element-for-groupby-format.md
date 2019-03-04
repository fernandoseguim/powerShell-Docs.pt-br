---
title: Elemento PropertyName para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863262"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="49580-102">Elemento PropertyName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="49580-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="49580-103">Especifica a propriedade do .NET que inicia um novo grupo sempre que seu valor é alterado.</span><span class="sxs-lookup"><span data-stu-id="49580-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="49580-104">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) PropertyName elemento GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="49580-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="49580-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49580-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49580-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="49580-106">Attributes and Elements</span></span>

<span data-ttu-id="49580-107">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="49580-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="49580-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="49580-108">Attributes</span></span>

<span data-ttu-id="49580-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="49580-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49580-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="49580-110">Child Elements</span></span>

<span data-ttu-id="49580-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="49580-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="49580-112">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="49580-112">Parent Elements</span></span>

|<span data-ttu-id="49580-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="49580-113">Element</span></span>|<span data-ttu-id="49580-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="49580-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49580-115">Elemento GroupBy para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="49580-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="49580-116">Define como um grupo de objetos do .NET é exibido.</span><span class="sxs-lookup"><span data-stu-id="49580-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="49580-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="49580-117">Text Value</span></span>

<span data-ttu-id="49580-118">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="49580-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="49580-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="49580-119">Remarks</span></span>

<span data-ttu-id="49580-120">Windows PowerShell inicia um novo grupo, sempre que o valor dessa propriedade é alterado.</span><span class="sxs-lookup"><span data-stu-id="49580-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="49580-121">Quando esse elemento for especificado, é possível especificar o [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento para iniciar um novo grupo.</span><span class="sxs-lookup"><span data-stu-id="49580-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="49580-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="49580-122">Example</span></span>

<span data-ttu-id="49580-123">O exemplo a seguir mostra como iniciar um novo grupo quando o valor de uma propriedade é alterado.</span><span class="sxs-lookup"><span data-stu-id="49580-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="49580-124">Para obter um exemplo de um arquivo de formatação completo que inclui esse elemento, consulte [exibição ampla (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="49580-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49580-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="49580-125">See Also</span></span>

[<span data-ttu-id="49580-126">Elemento GroupBy para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="49580-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="49580-127">Elemento ScriptBlock para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="49580-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="49580-128">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="49580-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
