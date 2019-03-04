---
title: Elemento ViewDefinitions (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862082"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="33f68-102">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="33f68-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="33f68-103">Define os modos de exibição usados para exibir objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="33f68-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="33f68-104">Esses modos de exibição podem exibir as propriedades e valores de script de um objeto em um formato de tabela, formato de lista, formato amplo e formato de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="33f68-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="33f68-105">Configuração (formato) ViewDefinitions (formato XML) do elemento</span><span class="sxs-lookup"><span data-stu-id="33f68-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="33f68-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33f68-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33f68-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="33f68-107">Attributes and Elements</span></span>

<span data-ttu-id="33f68-108">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `ViewDefinitions` elemento.</span><span class="sxs-lookup"><span data-stu-id="33f68-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="33f68-109">Não há nenhum limite para o número de exibições que podem ser definidas em um arquivo de formatação, e eles podem ser adicionados em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="33f68-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="33f68-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="33f68-110">Attributes</span></span>

<span data-ttu-id="33f68-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="33f68-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33f68-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="33f68-112">Child Elements</span></span>

|<span data-ttu-id="33f68-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="33f68-113">Element</span></span>|<span data-ttu-id="33f68-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="33f68-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33f68-115">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="33f68-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="33f68-116">Define uma exibição que é usada para exibir um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="33f68-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33f68-117">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="33f68-117">Parent Elements</span></span>

|<span data-ttu-id="33f68-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="33f68-118">Element</span></span>|<span data-ttu-id="33f68-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="33f68-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33f68-120">Elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="33f68-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="33f68-121">Representa o elemento de nível superior de um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="33f68-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="33f68-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="33f68-122">Remarks</span></span>

<span data-ttu-id="33f68-123">Para obter mais informações sobre os componentes de diferentes tipos de modos de exibição, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="33f68-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="33f68-124">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="33f68-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="33f68-125">Criando uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="33f68-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="33f68-126">Criando uma exibição ampla</span><span class="sxs-lookup"><span data-stu-id="33f68-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="33f68-127">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="33f68-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="33f68-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="33f68-128">Example</span></span>

<span data-ttu-id="33f68-129">Este exemplo mostra um `ViewDefinitions` elemento que contém os elementos pai para uma exibição de tabela e uma exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="33f68-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="33f68-130">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="33f68-130">See Also</span></span>

[<span data-ttu-id="33f68-131">Elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="33f68-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="33f68-132">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="33f68-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="33f68-133">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="33f68-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="33f68-134">Criando uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="33f68-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="33f68-135">Criando uma exibição ampla</span><span class="sxs-lookup"><span data-stu-id="33f68-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="33f68-136">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="33f68-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="33f68-137">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="33f68-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
