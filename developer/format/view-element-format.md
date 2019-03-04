---
title: Exibir o elemento (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856142"
---
# <a name="view-element-format"></a><span data-ttu-id="92141-102">Elemento View (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-102">View Element (Format)</span></span>

<span data-ttu-id="92141-103">Define uma exibição que exibe um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="92141-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="92141-104">Não há nenhum limite para o número de exibições que podem ser definidas em um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="92141-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="92141-105">Elemento de exibição de ViewDefinitions elemento (formato) de (formato) do elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92141-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92141-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92141-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="92141-107">Attributes and Elements</span></span>

<span data-ttu-id="92141-108">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `View` elemento.</span><span class="sxs-lookup"><span data-stu-id="92141-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="92141-109">Você deve especificar apenas um dos elementos de filhos do controle, e você deve especificar o nome da exibição e os objetos que usam o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="92141-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="92141-110">Definindo controles personalizados, como agrupar objetos, e especifica se o modo de exibição é out-of-band são opcionais.</span><span class="sxs-lookup"><span data-stu-id="92141-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="92141-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="92141-111">Attributes</span></span>

<span data-ttu-id="92141-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="92141-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92141-113">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="92141-113">Child Elements</span></span>

|<span data-ttu-id="92141-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="92141-114">Element</span></span>|<span data-ttu-id="92141-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="92141-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92141-116">Elemento de controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="92141-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="92141-117">Optional element.</span></span><br /><br /> <span data-ttu-id="92141-118">Define um conjunto de controles que podem ser referenciados por seu nome de dentro da exibição.</span><span class="sxs-lookup"><span data-stu-id="92141-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="92141-119">Elemento CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="92141-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="92141-120">Optional element.</span></span><br /><br /> <span data-ttu-id="92141-121">Define um formato de controle personalizado para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="92141-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="92141-122">Elemento GroupBy para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="92141-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="92141-123">Optional element.</span></span><br /><br /> <span data-ttu-id="92141-124">Define como os membros dos objetos .NET são agrupados.</span><span class="sxs-lookup"><span data-stu-id="92141-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="92141-125">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="92141-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="92141-126">Optional element.</span></span><br /><br /> <span data-ttu-id="92141-127">Define um formato de lista para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="92141-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="92141-128">Elemento de nome para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="92141-129">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="92141-129">Required element.</span></span><br /><br /> <span data-ttu-id="92141-130">Especifica o nome usado para referenciar o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="92141-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="92141-131">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="92141-132">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="92141-132">Optional element.</span></span><br /><br /> <span data-ttu-id="92141-133">Define um formato de tabela para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="92141-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="92141-134">Elemento ViewSelectedBy para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="92141-135">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="92141-135">Required element.</span></span><br /><br /> <span data-ttu-id="92141-136">Define os objetos do .NET que essa exibição exibe.</span><span class="sxs-lookup"><span data-stu-id="92141-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="92141-137">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="92141-138">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="92141-138">Optional element.</span></span><br /><br /> <span data-ttu-id="92141-139">Define uma ampla (único valor) formato de lista para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="92141-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="92141-140">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="92141-140">Parent Elements</span></span>

|<span data-ttu-id="92141-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="92141-141">Element</span></span>|<span data-ttu-id="92141-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="92141-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92141-143">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="92141-144">Define os modos de exibição usados para exibir os objetos.</span><span class="sxs-lookup"><span data-stu-id="92141-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="92141-145">Comentários</span><span class="sxs-lookup"><span data-stu-id="92141-145">Remarks</span></span>

<span data-ttu-id="92141-146">Para obter mais informações sobre os componentes de diferentes modos de exibição e controles personalizados, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="92141-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="92141-147">Componentes de exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="92141-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="92141-148">Componentes de exibição de lista</span><span class="sxs-lookup"><span data-stu-id="92141-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="92141-149">Componentes de exibição ampla</span><span class="sxs-lookup"><span data-stu-id="92141-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="92141-150">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="92141-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="92141-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92141-151">Example</span></span>

<span data-ttu-id="92141-152">Este exemplo mostra uma `View` elemento que define uma exibição de tabela para o [ServiceProcess](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="92141-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="92141-153">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="92141-153">See Also</span></span>

[<span data-ttu-id="92141-154">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="92141-155">Elemento de nome para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="92141-156">Elemento ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="92141-157">Elemento de controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="92141-158">Elemento GroupBy para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="92141-159">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="92141-160">Elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="92141-161">Elemento WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="92141-162">Elemento CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="92141-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="92141-163">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="92141-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
