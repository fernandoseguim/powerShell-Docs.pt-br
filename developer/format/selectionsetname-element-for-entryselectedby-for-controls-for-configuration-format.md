---
title: Elemento SelectionSetName para EntrySelectedBy para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860902"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="d476b-102">Elemento SelectionSetName para EntrySelectedBy para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="d476b-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d476b-103">Especifica um conjunto de tipos do .NET que usam essa definição do controle.</span><span class="sxs-lookup"><span data-stu-id="d476b-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="d476b-104">Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="d476b-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d476b-105">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl controles para o elemento de configuração (formato) de EntrySelectedBy para CustomEntry controles para o elemento de configuração (formato) de SelectionSetName para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="d476b-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d476b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d476b-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d476b-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d476b-107">Attributes and Elements</span></span>

<span data-ttu-id="d476b-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="d476b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d476b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d476b-109">Attributes</span></span>

<span data-ttu-id="d476b-110">Não</span><span class="sxs-lookup"><span data-stu-id="d476b-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d476b-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="d476b-111">Child Elements</span></span>

<span data-ttu-id="d476b-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d476b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d476b-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="d476b-113">Parent Elements</span></span>

|<span data-ttu-id="d476b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="d476b-114">Element</span></span>|<span data-ttu-id="d476b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d476b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d476b-116">Elemento EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="d476b-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="d476b-117">Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d476b-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d476b-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="d476b-118">Text Value</span></span>

<span data-ttu-id="d476b-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="d476b-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d476b-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="d476b-120">Remarks</span></span>

<span data-ttu-id="d476b-121">Cada definição de controle deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.</span><span class="sxs-lookup"><span data-stu-id="d476b-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d476b-122">Conjuntos de seleção normalmente são usados quando você deseja definir um grupo de objetos que são usados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="d476b-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d476b-123">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d476b-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d476b-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d476b-124">See Also</span></span>

[<span data-ttu-id="d476b-125">Elemento EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="d476b-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="d476b-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d476b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
