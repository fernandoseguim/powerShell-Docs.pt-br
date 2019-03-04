---
title: Elemento SelectionSets (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853562"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="e9f60-102">Elemento SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="e9f60-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="e9f60-103">Define os conjuntos de objetos .NET que podem ser usados por todos os modos de exibição do arquivo de formatação comuns.</span><span class="sxs-lookup"><span data-stu-id="e9f60-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="e9f60-104">Os controles do arquivo de formatação e modos de exibição podem referenciar o conjunto completo de objetos usando apenas o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="e9f60-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="e9f60-105">Formato do elemento SelectionSets de elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="e9f60-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="e9f60-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9f60-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9f60-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e9f60-107">Attributes and Elements</span></span>

<span data-ttu-id="e9f60-108">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `SelectionSets` elemento.</span><span class="sxs-lookup"><span data-stu-id="e9f60-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="e9f60-109">Cada elemento filho define um conjunto de objetos que podem ser referenciados pelo nome do conjunto.</span><span class="sxs-lookup"><span data-stu-id="e9f60-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="e9f60-110">A ordem dos elementos filho não é significativa.</span><span class="sxs-lookup"><span data-stu-id="e9f60-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9f60-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e9f60-111">Attributes</span></span>

<span data-ttu-id="e9f60-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e9f60-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9f60-113">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="e9f60-113">Child Elements</span></span>

|<span data-ttu-id="e9f60-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9f60-114">Element</span></span>|<span data-ttu-id="e9f60-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9f60-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9f60-116">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="e9f60-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="e9f60-117">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="e9f60-117">Required element.</span></span><br /><br /> <span data-ttu-id="e9f60-118">Define um único conjunto de objetos .NET que pode ser referenciado pelo nome do conjunto.</span><span class="sxs-lookup"><span data-stu-id="e9f60-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e9f60-119">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="e9f60-119">Parent Elements</span></span>

|<span data-ttu-id="e9f60-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9f60-120">Element</span></span>|<span data-ttu-id="e9f60-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9f60-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9f60-122">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="e9f60-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="e9f60-123">Representa o elemento de nível superior de um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="e9f60-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e9f60-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9f60-124">Remarks</span></span>

<span data-ttu-id="e9f60-125">Você pode usar conjuntos de seleção quando você tem um conjunto de objetos relacionados que você deseja referenciar, usando um nome único, como um conjunto de objetos que estão relacionadas por meio da herança.</span><span class="sxs-lookup"><span data-stu-id="e9f60-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="e9f60-126">Ao definir seus modos de exibição, você pode especificar o conjunto de objetos usando o nome da seleção definida em vez de listar todos os objetos dentro de cada modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="e9f60-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="e9f60-127">Conjuntos de seleção comuns são especificados por seu nome ao definir os modos de exibição do arquivo de formatação ou as definições dos modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="e9f60-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="e9f60-128">Nesses casos, o `SelectionSetName` elemento filho do `ViewSelectedBy` e `EntrySelectedBy` elementos especifica o conjunto a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e9f60-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="e9f60-129">Para obter mais informações sobre conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e9f60-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9f60-130">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="e9f60-130">See Also</span></span>

[<span data-ttu-id="e9f60-131">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="e9f60-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="e9f60-132">Definindo conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="e9f60-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e9f60-133">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="e9f60-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="e9f60-134">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9f60-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
