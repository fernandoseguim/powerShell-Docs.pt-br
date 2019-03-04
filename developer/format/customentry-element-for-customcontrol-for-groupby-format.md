---
title: Elemento CustomEntry para CustomControl para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860362"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="9db68-102">Elemento CustomEntry para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9db68-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="9db68-103">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="9db68-103">Provides a definition of the control.</span></span> <span data-ttu-id="9db68-104">Esse elemento é usado ao definir como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="9db68-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9db68-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9db68-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9db68-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9db68-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9db68-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9db68-107">Attributes and Elements</span></span>

<span data-ttu-id="9db68-108">As seções a seguir descrevem atributos, elementos filho e os elementos pai do `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="9db68-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9db68-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9db68-109">Attributes</span></span>

<span data-ttu-id="9db68-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9db68-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9db68-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="9db68-111">Child Elements</span></span>

|<span data-ttu-id="9db68-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="9db68-112">Element</span></span>|<span data-ttu-id="9db68-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9db68-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9db68-114">Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9db68-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="9db68-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9db68-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9db68-116">Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="9db68-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="9db68-117">Elemento CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9db68-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="9db68-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="9db68-118">Required element.</span></span><br /><br /> <span data-ttu-id="9db68-119">Define como o controle exibe os dados.</span><span class="sxs-lookup"><span data-stu-id="9db68-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9db68-120">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="9db68-120">Parent Elements</span></span>

|<span data-ttu-id="9db68-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="9db68-121">Element</span></span>|<span data-ttu-id="9db68-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="9db68-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9db68-123">Elemento CustomEntries para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9db68-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="9db68-124">Fornece as definições para o controle.</span><span class="sxs-lookup"><span data-stu-id="9db68-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9db68-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="9db68-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="9db68-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="9db68-126">See Also</span></span>

[<span data-ttu-id="9db68-127">Elemento EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9db68-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="9db68-128">Elemento CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9db68-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="9db68-129">Elemento CustomEntries para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="9db68-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="9db68-130">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="9db68-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
