---
title: Elemento TableRowEntries para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055726"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="c5b2c-102">Elemento TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c5b2c-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="c5b2c-103">Define as linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="c5b2c-103">Defines the rows of the table.</span></span>

<span data-ttu-id="c5b2c-104">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento TableControl (formato) TableRowEntries elemento de configuração para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c5b2c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c5b2c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5b2c-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c5b2c-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c5b2c-106">Attributes and Elements</span></span>

<span data-ttu-id="c5b2c-107">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `TableRowEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="c5b2c-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5b2c-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c5b2c-108">Attributes</span></span>

<span data-ttu-id="c5b2c-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c5b2c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c5b2c-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="c5b2c-110">Child Elements</span></span>

|<span data-ttu-id="c5b2c-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5b2c-111">Element</span></span>|<span data-ttu-id="c5b2c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5b2c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5b2c-113">Elemento TableRowEntry para TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c5b2c-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="c5b2c-114">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="c5b2c-114">Required element.</span></span><br /><br /> <span data-ttu-id="c5b2c-115">Define os dados que são exibidos em uma linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="c5b2c-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c5b2c-116">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="c5b2c-116">Parent Elements</span></span>

|<span data-ttu-id="c5b2c-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5b2c-117">Element</span></span>|<span data-ttu-id="c5b2c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5b2c-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5b2c-119">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c5b2c-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="c5b2c-120">Define um formato de tabela para um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="c5b2c-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c5b2c-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5b2c-121">Remarks</span></span>

<span data-ttu-id="c5b2c-122">Você deve especificar um ou mais `TableRowEntry` elementos para o modo de exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="c5b2c-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="c5b2c-123">Não há nenhum limite máximo ao número de `TableRowEntry` elementos que podem ser adicionados nem é sua ordem significativa.</span><span class="sxs-lookup"><span data-stu-id="c5b2c-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="c5b2c-124">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c5b2c-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c5b2c-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5b2c-125">Example</span></span>

<span data-ttu-id="c5b2c-126">A exemplo a seguir mostra uma `TableRowEntries` que define uma linha que exibe os valores de duas propriedades de elemento de [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="c5b2c-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="c5b2c-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c5b2c-127">See Also</span></span>

[<span data-ttu-id="c5b2c-128">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="c5b2c-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c5b2c-129">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c5b2c-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="c5b2c-130">Elemento TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c5b2c-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="c5b2c-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5b2c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
