---
title: Elemento DefaultSettings (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: 59cc0514087cc52438e0d1271b8b77a7799eb32c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855662"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="95e64-102">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="95e64-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="95e64-103">Define as configurações comuns que se aplicam a todas as exibições do arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="95e64-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="95e64-104">Configurações comuns incluem a exibição de erros, quebra automática de texto em tabelas, definindo como coleções são expandidas e muito mais.</span><span class="sxs-lookup"><span data-stu-id="95e64-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="95e64-105">Elemento de DefaultSettings (formato) do elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="95e64-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="95e64-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95e64-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="95e64-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="95e64-107">Attributes and Elements</span></span>

<span data-ttu-id="95e64-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `DefaultSettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="95e64-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="95e64-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="95e64-109">Attributes</span></span>

<span data-ttu-id="95e64-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="95e64-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95e64-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="95e64-111">Child Elements</span></span>

|<span data-ttu-id="95e64-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="95e64-112">Element</span></span>|<span data-ttu-id="95e64-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="95e64-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95e64-114">Elemento DisplayError (Frmat)</span><span class="sxs-lookup"><span data-stu-id="95e64-114">DisplayError Element (Frmat)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="95e64-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="95e64-115">Optional element.</span></span><br /><br /> <span data-ttu-id="95e64-116">Especifica que a cadeia de caracteres #ERR é exibida quando ocorre um erro ao exibir uma parte dos dados.</span><span class="sxs-lookup"><span data-stu-id="95e64-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="95e64-117">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="95e64-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="95e64-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="95e64-118">Optional element.</span></span><br /><br /> <span data-ttu-id="95e64-119">Define as diferentes maneiras em que os objetos do .NET são expandidas quando eles são exibidos em uma exibição.</span><span class="sxs-lookup"><span data-stu-id="95e64-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="95e64-120">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="95e64-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="95e64-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="95e64-121">Optional element.</span></span><br /><br /> <span data-ttu-id="95e64-122">Especifica o número mínimo de propriedades de um objeto deve ter para exibir o objeto em uma exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="95e64-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="95e64-123">Elemento ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="95e64-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="95e64-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="95e64-124">Optional element.</span></span><br /><br /> <span data-ttu-id="95e64-125">Especifica que o registro completo de erro é exibido quando ocorre um erro ao exibir uma parte dos dados.</span><span class="sxs-lookup"><span data-stu-id="95e64-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="95e64-126">Elemento WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="95e64-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="95e64-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="95e64-127">Optional element.</span></span><br /><br /> <span data-ttu-id="95e64-128">Especifica que os dados em uma tabela são movidos para a próxima linha se ela não se ajustam a largura da coluna.</span><span class="sxs-lookup"><span data-stu-id="95e64-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="95e64-129">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="95e64-129">Parent Elements</span></span>

|<span data-ttu-id="95e64-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="95e64-130">Element</span></span>|<span data-ttu-id="95e64-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="95e64-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95e64-132">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="95e64-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="95e64-133">Representa o elemento de nível superior de um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="95e64-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="95e64-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="95e64-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="95e64-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="95e64-135">See Also</span></span>

[<span data-ttu-id="95e64-136">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="95e64-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="95e64-137">Elemento DisplayError (Frmat)</span><span class="sxs-lookup"><span data-stu-id="95e64-137">DisplayError Element (Frmat)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="95e64-138">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="95e64-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="95e64-139">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="95e64-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="95e64-140">Elemento ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="95e64-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="95e64-141">Elemento WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="95e64-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="95e64-142">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="95e64-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
