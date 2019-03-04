---
title: Elemento PropertyName para SelectionCondition para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861022"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="5ef83-102">Elemento PropertyName para SelectionCondition para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="5ef83-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5ef83-103">Especifica a propriedade do .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="5ef83-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5ef83-104">Quando essa propriedade estiver presente ou quando ela é avaliada como `true`, a condição for atendida e a entrada é usada.</span><span class="sxs-lookup"><span data-stu-id="5ef83-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="5ef83-105">Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="5ef83-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5ef83-106">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl controles para o elemento de configuração (formato) de EntrySelectedBy para CustomEntry controles para o elemento de configuração (formato) de SelectionCondition para EntrySelectedBy para CustomEntry para configuração ( Elemento de PropertyName Format) para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="5ef83-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ef83-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ef83-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ef83-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5ef83-108">Attributes and Elements</span></span>

<span data-ttu-id="5ef83-109">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="5ef83-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ef83-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ef83-110">Attributes</span></span>

<span data-ttu-id="5ef83-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5ef83-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ef83-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="5ef83-112">Child Elements</span></span>

<span data-ttu-id="5ef83-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5ef83-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5ef83-114">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="5ef83-114">Parent Elements</span></span>

|<span data-ttu-id="5ef83-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ef83-115">Element</span></span>|<span data-ttu-id="5ef83-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ef83-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ef83-117">Elemento SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5ef83-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="5ef83-118">Define uma condição que deve existir para uma definição de controle comum a ser usado.</span><span class="sxs-lookup"><span data-stu-id="5ef83-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5ef83-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="5ef83-119">Text Value</span></span>

<span data-ttu-id="5ef83-120">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="5ef83-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ef83-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ef83-121">Remarks</span></span>

<span data-ttu-id="5ef83-122">A condição de seleção deve especificar um nome menos de uma propriedade ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="5ef83-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="5ef83-123">Para obter mais informações sobre como as condições de seleção podem ser usadas, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5ef83-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ef83-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5ef83-124">See Also</span></span>

[<span data-ttu-id="5ef83-125">Elemento SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="5ef83-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="5ef83-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ef83-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
