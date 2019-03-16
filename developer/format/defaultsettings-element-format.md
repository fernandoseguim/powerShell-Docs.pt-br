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
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059058"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="c066f-102">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="c066f-103">Define as configurações comuns que se aplicam a todas as exibições do arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="c066f-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="c066f-104">Configurações comuns incluem a exibição de erros, quebra automática de texto em tabelas, definindo como coleções são expandidas e muito mais.</span><span class="sxs-lookup"><span data-stu-id="c066f-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="c066f-105">Elemento de DefaultSettings (formato) do elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c066f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c066f-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c066f-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c066f-107">Attributes and Elements</span></span>

<span data-ttu-id="c066f-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `DefaultSettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="c066f-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c066f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c066f-109">Attributes</span></span>

<span data-ttu-id="c066f-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c066f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c066f-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="c066f-111">Child Elements</span></span>

|<span data-ttu-id="c066f-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c066f-112">Element</span></span>|<span data-ttu-id="c066f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c066f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c066f-114">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="c066f-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c066f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c066f-116">Especifica que a cadeia de caracteres #ERR é exibida quando ocorre um erro ao exibir uma parte dos dados.</span><span class="sxs-lookup"><span data-stu-id="c066f-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="c066f-117">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="c066f-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c066f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c066f-119">Define as diferentes maneiras em que os objetos do .NET são expandidas quando eles são exibidos em uma exibição.</span><span class="sxs-lookup"><span data-stu-id="c066f-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="c066f-120">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="c066f-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c066f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c066f-122">Especifica o número mínimo de propriedades de um objeto deve ter para exibir o objeto em uma exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="c066f-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="c066f-123">Elemento ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="c066f-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c066f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c066f-125">Especifica que o registro completo de erro é exibido quando ocorre um erro ao exibir uma parte dos dados.</span><span class="sxs-lookup"><span data-stu-id="c066f-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="c066f-126">Elemento WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="c066f-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c066f-127">Optional element.</span></span><br /><br /> <span data-ttu-id="c066f-128">Especifica que os dados em uma tabela são movidos para a próxima linha se ela não se ajustam a largura da coluna.</span><span class="sxs-lookup"><span data-stu-id="c066f-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c066f-129">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="c066f-129">Parent Elements</span></span>

|<span data-ttu-id="c066f-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="c066f-130">Element</span></span>|<span data-ttu-id="c066f-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="c066f-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c066f-132">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="c066f-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="c066f-133">Representa o elemento de nível superior de um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="c066f-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c066f-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="c066f-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c066f-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c066f-135">See Also</span></span>

[<span data-ttu-id="c066f-136">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="c066f-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="c066f-137">Elemento DisplayError (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="c066f-138">Elemento EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="c066f-139">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="c066f-140">Elemento ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="c066f-141">Elemento WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="c066f-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="c066f-142">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="c066f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
