---
title: Elemento TableColumnHeader (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858592"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="8e9d1-102">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="8e9d1-103">Define o rótulo, a largura da coluna e o alinhamento do rótulo de uma coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="8e9d1-104">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento TableControl (formato) TableHeaders elemento de configuração para elemento de TableColumnHeader TableControl (formato) TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e9d1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e9d1-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e9d1-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e9d1-106">Attributes and Elements</span></span>

<span data-ttu-id="8e9d1-107">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TableColumnHeader` elemento.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e9d1-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e9d1-108">Attributes</span></span>

<span data-ttu-id="8e9d1-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e9d1-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="8e9d1-110">Child Elements</span></span>

|<span data-ttu-id="8e9d1-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e9d1-111">Element</span></span>|<span data-ttu-id="8e9d1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e9d1-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e9d1-113">Elemento de rótulo para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8e9d1-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-114">Optional element.</span></span><br /><br /> <span data-ttu-id="8e9d1-115">Define o rótulo que é exibido na parte superior da coluna.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="8e9d1-116">Se nenhum rótulo for especificado, o nome da propriedade cujo valor é exibido nas linhas é usado.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="8e9d1-117">Elemento de largura para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8e9d1-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-118">Required element.</span></span><br /><br /> <span data-ttu-id="8e9d1-119">Especifica a largura (em caracteres) da coluna.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="8e9d1-120">Elemento de alinhamento para TableColumbnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-120">Alignment Element for TableColumbnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8e9d1-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8e9d1-122">Especifica como o rótulo da coluna é exibido.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="8e9d1-123">Se nenhum alinhamento for especificado, o rótulo é alinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8e9d1-124">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="8e9d1-124">Parent Elements</span></span>

|<span data-ttu-id="8e9d1-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e9d1-125">Element</span></span>|<span data-ttu-id="8e9d1-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e9d1-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e9d1-127">Elemento TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="8e9d1-128">Define as colunas de uma exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e9d1-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e9d1-129">Remarks</span></span>

<span data-ttu-id="8e9d1-130">Especifique um cabeçalho para cada coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="8e9d1-131">As colunas são exibidas na ordem em que o `TableColumnHeader` elementos são definidos.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="8e9d1-132">Uma tabela deve ter o mesmo número de `TableColumnHeader` elementos como `TableRowEntry` elementos.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="8e9d1-133">O cabeçalho da coluna define como o texto na parte superior da tabela é exibido.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="8e9d1-134">As entradas de linha definem quais dados são exibidos nas linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="8e9d1-135">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e9d1-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e9d1-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e9d1-136">Example</span></span>

<span data-ttu-id="8e9d1-137">O exemplo a seguir mostra dois `TableColumnHeader` elementos.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="8e9d1-138">O primeiro elemento define uma coluna cujo rótulo é a "Coluna 1", tem uma largura de 16 caracteres e cujo rótulo é alinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="8e9d1-139">O segundo elemento define uma coluna cujo rótulo é "Coluna 2", tem uma largura de 10 caracteres e cujo rótulo está centralizado na coluna.</span><span class="sxs-lookup"><span data-stu-id="8e9d1-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="8e9d1-140">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8e9d1-140">See Also</span></span>

[<span data-ttu-id="8e9d1-141">Elemento de alinhamento para TableColumnHeader para TableContrl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-141">Alignment Element for TableColumnHeader for TableContrl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8e9d1-142">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="8e9d1-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8e9d1-143">Elemento de rótulo para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8e9d1-144">Elemento TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="8e9d1-145">Largura para TableColumnHeader para elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8e9d1-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8e9d1-146">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e9d1-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
