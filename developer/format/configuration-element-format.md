---
title: O elemento de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856322"
---
# <a name="configuration-element-format"></a><span data-ttu-id="ae9be-102">Elemento Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="ae9be-102">Configuration Element (Format)</span></span>

<span data-ttu-id="ae9be-103">Representa o elemento de nível superior de um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="ae9be-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="ae9be-104">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="ae9be-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="ae9be-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae9be-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ae9be-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ae9be-106">Attributes and Elements</span></span>

<span data-ttu-id="ae9be-107">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Configuration` elemento.</span><span class="sxs-lookup"><span data-stu-id="ae9be-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="ae9be-108">Esse elemento deve ser o elemento raiz para cada arquivo de formatação, e esse elemento deve conter pelo menos um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="ae9be-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae9be-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ae9be-109">Attributes</span></span>

<span data-ttu-id="ae9be-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ae9be-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ae9be-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="ae9be-111">Child Elements</span></span>

|<span data-ttu-id="ae9be-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae9be-112">Element</span></span>|<span data-ttu-id="ae9be-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae9be-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae9be-114">Elemento de controles para configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="ae9be-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="ae9be-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ae9be-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ae9be-116">Define os controles comuns que podem ser usados por todos os modos de exibição do arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="ae9be-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="ae9be-117">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="ae9be-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="ae9be-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ae9be-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ae9be-119">Define as configurações comuns que se aplicam a todas as exibições do arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="ae9be-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="ae9be-120">Formato do elemento SelectionSets</span><span class="sxs-lookup"><span data-stu-id="ae9be-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="ae9be-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ae9be-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ae9be-122">Define os conjuntos de objetos .NET que podem ser usados por todos os modos de exibição do arquivo de formatação comuns.</span><span class="sxs-lookup"><span data-stu-id="ae9be-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="ae9be-123">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="ae9be-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="ae9be-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ae9be-124">Optional element.</span></span><br /><br /> <span data-ttu-id="ae9be-125">Define os modos de exibição usados para exibir os objetos.</span><span class="sxs-lookup"><span data-stu-id="ae9be-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ae9be-126">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="ae9be-126">Parent Elements</span></span>

<span data-ttu-id="ae9be-127">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ae9be-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae9be-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae9be-128">Remarks</span></span>

<span data-ttu-id="ae9be-129">Arquivos de formatação definem como os objetos são exibidos.</span><span class="sxs-lookup"><span data-stu-id="ae9be-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="ae9be-130">Na maioria dos casos, esse elemento de raiz contém uma [ViewDefinitions](./viewdefinitions-element-format.md) elemento que define a tabela, lista e modos de exibição amplos do arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="ae9be-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="ae9be-131">Além das definições de exibição, o arquivo de formatação pode definir conjuntos de seleção, configurações e controles que essas exibições podem usar comuns.</span><span class="sxs-lookup"><span data-stu-id="ae9be-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae9be-132">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ae9be-132">See Also</span></span>

[<span data-ttu-id="ae9be-133">Elemento de controles para configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="ae9be-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="ae9be-134">Elemento DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="ae9be-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="ae9be-135">Elemento SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="ae9be-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="ae9be-136">Elemento ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="ae9be-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="ae9be-137">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae9be-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
