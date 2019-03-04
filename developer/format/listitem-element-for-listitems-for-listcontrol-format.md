---
title: Elemento ListItem para ListItems para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855152"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="d0115-102">Elemento ListItem para ListItems para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="d0115-103">Define a propriedade ou o script cujo valor é exibido em uma linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="d0115-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="d0115-104">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento ListControl (formato) ListEntries elemento de configuração para ListControl (formato) ListEntry elemento do elemento ListControl (formato) ListItems para ListControl (formato) ListItem para elemento ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0115-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0115-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0115-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0115-106">Attributes and Elements</span></span>

<span data-ttu-id="d0115-107">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `ListItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="d0115-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="d0115-108">Apenas uma propriedade ou o script pode ser especificado.</span><span class="sxs-lookup"><span data-stu-id="d0115-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0115-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0115-109">Attributes</span></span>

<span data-ttu-id="d0115-110">Não</span><span class="sxs-lookup"><span data-stu-id="d0115-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0115-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="d0115-111">Child Elements</span></span>

|<span data-ttu-id="d0115-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0115-112">Element</span></span>|<span data-ttu-id="d0115-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0115-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0115-114">Elemento FormatString para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d0115-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d0115-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d0115-116">Especifica uma cadeia de caracteres de formato que define como o valor da propriedade ou o script é exibido.</span><span class="sxs-lookup"><span data-stu-id="d0115-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="d0115-117">Elemento ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d0115-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d0115-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d0115-119">Define a condição que deve existir para esse item de lista a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d0115-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="d0115-120">Elemento de rótulo para o item de lista para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d0115-121">Elemento opcional</span><span class="sxs-lookup"><span data-stu-id="d0115-121">Optional element</span></span><br /><br /> <span data-ttu-id="d0115-122">Especifica o rótulo que é exibido à esquerda do valor de propriedade ou o script na linha.</span><span class="sxs-lookup"><span data-stu-id="d0115-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="d0115-123">Elemento PropertyName para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d0115-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d0115-124">Optional element.</span></span><br /><br /> <span data-ttu-id="d0115-125">Especifica a propriedade .NET cujo valor é exibido na linha.</span><span class="sxs-lookup"><span data-stu-id="d0115-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="d0115-126">Elemento ScriptBlock para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d0115-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d0115-127">Optional element.</span></span><br /><br /> <span data-ttu-id="d0115-128">Especifica o script cujo valor é exibido na linha.</span><span class="sxs-lookup"><span data-stu-id="d0115-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d0115-129">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="d0115-129">Parent Elements</span></span>

|<span data-ttu-id="d0115-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0115-130">Element</span></span>|<span data-ttu-id="d0115-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0115-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0115-132">Elemento ListItems para controle de lista (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="d0115-133">Define as propriedades e os scripts cujos valores são exibidos na exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="d0115-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0115-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0115-134">Remarks</span></span>

<span data-ttu-id="d0115-135">Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d0115-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d0115-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0115-136">Example</span></span>

<span data-ttu-id="d0115-137">Este exemplo mostra os elementos XML que definem três linhas da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="d0115-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="d0115-138">As duas primeiras linhas exibirão o valor de uma propriedade do .NET, e a última linha exibe um valor gerado por um script.</span><span class="sxs-lookup"><span data-stu-id="d0115-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="d0115-139">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d0115-139">See Also</span></span>

[<span data-ttu-id="d0115-140">Elemento ListItems (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="d0115-141">Elemento FormatString para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d0115-142">Elemento de rótulo para o item de lista (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d0115-143">Elemento PropertyName para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d0115-144">Elemento ScriptBlock para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="d0115-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d0115-145">Criando uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="d0115-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d0115-146">Escrevendo um formatação do Windows PowerShell e tipos de arquivo</span><span class="sxs-lookup"><span data-stu-id="d0115-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
