---
title: Elemento de alinhamento para TableColumnItem para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858202"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="f4c10-102">Elemento Alignment para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f4c10-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="f4c10-103">Define como os dados em uma coluna da linha são exibidos.</span><span class="sxs-lookup"><span data-stu-id="f4c10-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="f4c10-104">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento TableControl elemento (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento TableColumnItems (formato) TableColumnItem elemento de configuração (formato) Elemento de alinhamento para TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f4c10-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4c10-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4c10-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4c10-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f4c10-106">Attributes and Elements</span></span>

<span data-ttu-id="f4c10-107">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Alignment` elemento.</span><span class="sxs-lookup"><span data-stu-id="f4c10-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4c10-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="f4c10-108">Attributes</span></span>

<span data-ttu-id="f4c10-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f4c10-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4c10-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="f4c10-110">Child Elements</span></span>

<span data-ttu-id="f4c10-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f4c10-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f4c10-112">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="f4c10-112">Parent Elements</span></span>

|<span data-ttu-id="f4c10-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f4c10-113">Element</span></span>|<span data-ttu-id="f4c10-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4c10-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4c10-115">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f4c10-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="f4c10-116">Define um rótulo, a largura e o alinhamento dos dados para uma coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="f4c10-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f4c10-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f4c10-117">Text Value</span></span>

<span data-ttu-id="f4c10-118">Especifique um dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4c10-118">Specify one of the following values.</span></span> <span data-ttu-id="f4c10-119">(Esses valores não diferenciam maiusculas de minúsculas).</span><span class="sxs-lookup"><span data-stu-id="f4c10-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="f4c10-120">Deslocamentos para a esquerda os dados exibidos na coluna à esquerda.</span><span class="sxs-lookup"><span data-stu-id="f4c10-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="f4c10-121">(Esse é o padrão se esse elemento não for especificado.)</span><span class="sxs-lookup"><span data-stu-id="f4c10-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="f4c10-122">Deslocamentos para a direito os dados exibidos na coluna à direita.</span><span class="sxs-lookup"><span data-stu-id="f4c10-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="f4c10-123">Centros de centro de dados exibidos na coluna.</span><span class="sxs-lookup"><span data-stu-id="f4c10-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4c10-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4c10-124">Remarks</span></span>

<span data-ttu-id="f4c10-125">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f4c10-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4c10-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f4c10-126">See Also</span></span>

[<span data-ttu-id="f4c10-127">Exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="f4c10-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f4c10-128">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f4c10-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
