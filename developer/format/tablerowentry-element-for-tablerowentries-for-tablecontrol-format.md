---
title: Elemento TableRowEntry para TableRowEntries para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58059867"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="90b99-102">Elemento TableRowEntry para TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90b99-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="90b99-103">Define os dados que são exibidos em uma linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="90b99-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="90b99-104">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento TableControl (formato) TableRowEntries elemento de configuração para elemento de TableRowEntry TableControl (formato) TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90b99-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="90b99-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90b99-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90b99-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="90b99-106">Attributes and Elements</span></span>

<span data-ttu-id="90b99-107">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TableRowEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="90b99-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="90b99-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="90b99-108">Attributes</span></span>

<span data-ttu-id="90b99-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="90b99-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90b99-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="90b99-110">Child Elements</span></span>

|<span data-ttu-id="90b99-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="90b99-111">Element</span></span>|<span data-ttu-id="90b99-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="90b99-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90b99-113">Elemento EntrySelectedBy para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90b99-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="90b99-114">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="90b99-114">Required element.</span></span><br /><br /> <span data-ttu-id="90b99-115">Define os objetos cujos valores de propriedade são exibidos na linha.</span><span class="sxs-lookup"><span data-stu-id="90b99-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="90b99-116">Elemento TableColumnItems para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90b99-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="90b99-117">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="90b99-117">Required element.</span></span><br /><br /> <span data-ttu-id="90b99-118">Define as propriedades ou os scripts cujos valores são exibidos.</span><span class="sxs-lookup"><span data-stu-id="90b99-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="90b99-119">Elemento de agrupamento para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90b99-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="90b99-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="90b99-120">Optional element.</span></span><br /><br /> <span data-ttu-id="90b99-121">Especifica que o texto que excede a largura da coluna é exibido na próxima linha.</span><span class="sxs-lookup"><span data-stu-id="90b99-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="90b99-122">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="90b99-122">Parent Elements</span></span>

|<span data-ttu-id="90b99-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="90b99-123">Element</span></span>|<span data-ttu-id="90b99-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="90b99-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90b99-125">Elemento TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90b99-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="90b99-126">Define as linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="90b99-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="90b99-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="90b99-127">Remarks</span></span>

<span data-ttu-id="90b99-128">Uma `TableColumnItems` e um elemento `EntrySelectedBy` elemento deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="90b99-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="90b99-129">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="90b99-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="90b99-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90b99-130">Example</span></span>

<span data-ttu-id="90b99-131">A exemplo a seguir mostra uma `TableRowEntry` que define uma linha que exibe os valores de duas propriedades de elemento de [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="90b99-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="90b99-132">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="90b99-132">See Also</span></span>

[<span data-ttu-id="90b99-133">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="90b99-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="90b99-134">Elemento EntrySelectedBy para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90b99-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="90b99-135">Elemento TableColumnItems para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90b99-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="90b99-136">Elemento TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90b99-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="90b99-137">Elemento de agrupamento para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="90b99-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="90b99-138">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="90b99-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
