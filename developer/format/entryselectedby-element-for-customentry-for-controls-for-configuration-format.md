---
title: Elemento EntrySelectedBy para CustomEntry para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059211"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="a4f08-102">Elemento EntrySelectedBy para CustomEntry para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f08-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a4f08-103">Define os tipos de .NET que usam a definição do controle comum ou a condição que deve existir para esse controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="a4f08-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="a4f08-104">Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="a4f08-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a4f08-105">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl controles para o elemento de configuração (formato) de EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f08-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a4f08-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4f08-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a4f08-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a4f08-107">Attributes and Elements</span></span>

<span data-ttu-id="a4f08-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="a4f08-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a4f08-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a4f08-109">Attributes</span></span>

<span data-ttu-id="a4f08-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a4f08-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a4f08-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="a4f08-111">Child Elements</span></span>

|<span data-ttu-id="a4f08-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4f08-112">Element</span></span>|<span data-ttu-id="a4f08-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4f08-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4f08-114">Elemento SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f08-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="a4f08-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a4f08-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a4f08-116">Define a condição que deve existir para a definição de controle comum a ser usado.</span><span class="sxs-lookup"><span data-stu-id="a4f08-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="a4f08-117">Elemento SelectionSetName para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f08-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="a4f08-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a4f08-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a4f08-119">Especifica um conjunto de tipos do .NET que usam essa definição do controle comum.</span><span class="sxs-lookup"><span data-stu-id="a4f08-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="a4f08-120">Elemento TypeName para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f08-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="a4f08-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a4f08-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a4f08-122">Especifica um tipo .NET que usa essa definição do controle comum.</span><span class="sxs-lookup"><span data-stu-id="a4f08-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a4f08-123">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="a4f08-123">Parent Elements</span></span>

|<span data-ttu-id="a4f08-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4f08-124">Element</span></span>|<span data-ttu-id="a4f08-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4f08-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4f08-126">Elemento CustomEntry para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f08-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="a4f08-127">Fornece uma definição do controle comum.</span><span class="sxs-lookup"><span data-stu-id="a4f08-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a4f08-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4f08-128">Remarks</span></span>

<span data-ttu-id="a4f08-129">No mínimo, cada definição deve ter pelo menos um tipo .NET, conjunto de seleção ou condição de seleção especificada.</span><span class="sxs-lookup"><span data-stu-id="a4f08-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="a4f08-130">Não há nenhum limite máximo ao número de tipos, conjuntos de seleção ou condições de seleção que você pode especificar.</span><span class="sxs-lookup"><span data-stu-id="a4f08-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4f08-131">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a4f08-131">See Also</span></span>

[<span data-ttu-id="a4f08-132">Elemento SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f08-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="a4f08-133">Elemento SelectionSetName para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f08-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="a4f08-134">Elemento CustomEntry para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f08-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="a4f08-135">Elemento TypeName para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a4f08-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="a4f08-136">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4f08-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
