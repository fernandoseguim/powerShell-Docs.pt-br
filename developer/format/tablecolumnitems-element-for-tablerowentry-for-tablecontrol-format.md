---
title: Elemento TableColumnItems para TableRowEntry para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859442"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="e26ec-102">Elemento TableColumnItems para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e26ec-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="e26ec-103">Define as propriedades ou os scripts cujos valores são exibidos em uma linha.</span><span class="sxs-lookup"><span data-stu-id="e26ec-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="e26ec-104">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuração para elemento de TableRowEntry TableControl (formato) TableRowEntries para TableControl (formato) Elemento TableColumnItems para TableControlEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e26ec-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e26ec-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e26ec-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e26ec-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e26ec-106">Attributes and Elements</span></span>

<span data-ttu-id="e26ec-107">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `TableColumnItems` elemento.</span><span class="sxs-lookup"><span data-stu-id="e26ec-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e26ec-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="e26ec-108">Attributes</span></span>

<span data-ttu-id="e26ec-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e26ec-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e26ec-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="e26ec-110">Child Elements</span></span>

|<span data-ttu-id="e26ec-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="e26ec-111">Element</span></span>|<span data-ttu-id="e26ec-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e26ec-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e26ec-113">Elemento TableColumnItem para TableColumnItems para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e26ec-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="e26ec-114">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="e26ec-114">Required element.</span></span><br /><br /> <span data-ttu-id="e26ec-115">Define a propriedade ou cujo valor é exibido em uma coluna da linha do script.</span><span class="sxs-lookup"><span data-stu-id="e26ec-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e26ec-116">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="e26ec-116">Parent Elements</span></span>

|<span data-ttu-id="e26ec-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="e26ec-117">Element</span></span>|<span data-ttu-id="e26ec-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e26ec-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e26ec-119">Elemento TableRowEntry para TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e26ec-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="e26ec-120">Define os dados que são exibidos em uma linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="e26ec-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e26ec-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="e26ec-121">Remarks</span></span>

<span data-ttu-id="e26ec-122">Um `TableColumnItem` elemento é necessário para cada coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="e26ec-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="e26ec-123">A primeira entrada é exibida na primeira coluna, a segunda entrada na segunda coluna e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="e26ec-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="e26ec-124">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e26ec-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e26ec-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e26ec-125">Example</span></span>

<span data-ttu-id="e26ec-126">A exemplo a seguir mostra uma `TableColumnItems` que define três propriedades do elemento de [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="e26ec-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="e26ec-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="e26ec-127">See Also</span></span>

[<span data-ttu-id="e26ec-128">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="e26ec-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e26ec-129">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e26ec-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="e26ec-130">Elemento TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="e26ec-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="e26ec-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e26ec-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
