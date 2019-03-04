---
title: Elemento de rótulo para TableColumnHeader para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 59dfd40b95d5088a711eb89cf101eb31a4b159f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856082"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="c3102-102">Elemento Label para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c3102-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="c3102-103">Define o rótulo que é exibido na parte superior de uma coluna.</span><span class="sxs-lookup"><span data-stu-id="c3102-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="c3102-104">Esse elemento é usado ao definir uma exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="c3102-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="c3102-105">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento TableControl (formato) TableHeaders elemento de configuração para elemento de TableColumnHeader TableControl (formato) TableHeaders para elemento de rótulo TableControl (formato) TableColumnHeader para TablControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c3102-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TablControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3102-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3102-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3102-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c3102-107">Attributes and Elements</span></span>

<span data-ttu-id="c3102-108">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Label` elemento.</span><span class="sxs-lookup"><span data-stu-id="c3102-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="c3102-109">Apenas um rótulo é permitido para cada coluna.</span><span class="sxs-lookup"><span data-stu-id="c3102-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3102-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c3102-110">Attributes</span></span>

<span data-ttu-id="c3102-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c3102-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3102-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="c3102-112">Child Elements</span></span>

<span data-ttu-id="c3102-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c3102-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3102-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="c3102-114">Parent Elements</span></span>

|<span data-ttu-id="c3102-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c3102-115">Element</span></span>|<span data-ttu-id="c3102-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3102-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3102-117">Elemento TableColumnHeader para TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c3102-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="c3102-118">Define um rótulo, a largura e o alinhamento dos dados para uma coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="c3102-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c3102-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="c3102-119">Text Value</span></span>

<span data-ttu-id="c3102-120">Especifique o texto que é exibido na parte superior da coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="c3102-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="c3102-121">Não há nenhum caractere restrito para o rótulo de coluna.</span><span class="sxs-lookup"><span data-stu-id="c3102-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3102-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3102-122">Remarks</span></span>

<span data-ttu-id="c3102-123">Se nenhum rótulo for especificado, o nome da propriedade cujo valor é exibido nas linhas é usado.</span><span class="sxs-lookup"><span data-stu-id="c3102-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="c3102-124">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c3102-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c3102-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3102-125">Example</span></span>

<span data-ttu-id="c3102-126">Este exemplo mostra um `TableColumnHeader` elemento cujo rótulo é "Coluna 1".</span><span class="sxs-lookup"><span data-stu-id="c3102-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="c3102-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c3102-127">See Also</span></span>

[<span data-ttu-id="c3102-128">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="c3102-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c3102-129">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="c3102-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="c3102-130">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3102-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
