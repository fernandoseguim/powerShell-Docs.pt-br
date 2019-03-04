---
title: Elemento FormatString para TableColumnItem para TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854322"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="43bc1-102">Elemento FormatString para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="43bc1-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="43bc1-103">Especifica um padrão de formato que define como o valor da propriedade ou o script da tabela é exibido.</span><span class="sxs-lookup"><span data-stu-id="43bc1-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="43bc1-104">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento TableControl elemento (formato) elemento TableRowEntries (formato) elemento TableRowEntry (formato) elemento TableColumnItems (formato) TableColumnItem elemento de configuração (formato) Elemento FormatString para TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="43bc1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43bc1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43bc1-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43bc1-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="43bc1-106">Attributes and Elements</span></span>

<span data-ttu-id="43bc1-107">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `FormatString` elemento.</span><span class="sxs-lookup"><span data-stu-id="43bc1-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43bc1-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="43bc1-108">Attributes</span></span>

<span data-ttu-id="43bc1-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="43bc1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43bc1-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="43bc1-110">Child Elements</span></span>

<span data-ttu-id="43bc1-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="43bc1-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43bc1-112">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="43bc1-112">Parent Elements</span></span>

|<span data-ttu-id="43bc1-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="43bc1-113">Element</span></span>|<span data-ttu-id="43bc1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="43bc1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43bc1-115">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="43bc1-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="43bc1-116">Define a propriedade ou cujo valor é exibido na coluna da linha do script.</span><span class="sxs-lookup"><span data-stu-id="43bc1-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="43bc1-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="43bc1-117">Text Value</span></span>

<span data-ttu-id="43bc1-118">Especifique o padrão que é usado para formatar os dados.</span><span class="sxs-lookup"><span data-stu-id="43bc1-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="43bc1-119">Por exemplo, esse padrão pode ser usado para formatar o valor de qualquer propriedade que é do tipo [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="43bc1-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="43bc1-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="43bc1-120">Remarks</span></span>

<span data-ttu-id="43bc1-121">Cadeias de caracteres de formato podem ser usadas ao criar modos de exibição de tabela, exibições de lista, modos de exibição amplos ou modos de exibição personalizados.</span><span class="sxs-lookup"><span data-stu-id="43bc1-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="43bc1-122">Para obter mais informações sobre como formatar um valor exibido em uma exibição, consulte [formatação exibidos dados](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="43bc1-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="43bc1-123">Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [exibição de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="43bc1-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="43bc1-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43bc1-124">Example</span></span>

<span data-ttu-id="43bc1-125">O exemplo a seguir mostra como definir uma cadeia de caracteres de formatação para o valor da `StartTime` propriedade.</span><span class="sxs-lookup"><span data-stu-id="43bc1-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="43bc1-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="43bc1-126">See Also</span></span>

[<span data-ttu-id="43bc1-127">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="43bc1-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="43bc1-128">Formatando os dados exibidos</span><span class="sxs-lookup"><span data-stu-id="43bc1-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="43bc1-129">Elemento TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="43bc1-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="43bc1-130">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="43bc1-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
