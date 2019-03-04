---
title: Elemento TypeName para SelectionCondition para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858802"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="00848-102">Elemento TypeName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="00848-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="00848-103">Especifica um tipo .NET que dispara a condição.</span><span class="sxs-lookup"><span data-stu-id="00848-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="00848-104">Esse elemento é usado ao definir como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="00848-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="00848-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) EntrySelectedBy CustomEntry para elemento de GroupBy (formato) SelectionCondition EntrySelectedBy para elemento de TypeName GroupBy (formato) SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="00848-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00848-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00848-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="00848-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="00848-107">Attributes and Elements</span></span>

<span data-ttu-id="00848-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="00848-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00848-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="00848-109">Attributes</span></span>

<span data-ttu-id="00848-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="00848-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00848-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="00848-111">Child Elements</span></span>

<span data-ttu-id="00848-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="00848-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="00848-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="00848-113">Parent Elements</span></span>

|<span data-ttu-id="00848-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="00848-114">Element</span></span>|<span data-ttu-id="00848-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="00848-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00848-116">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="00848-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="00848-117">Define uma condição que deve existir para a definição de controle a ser usado.</span><span class="sxs-lookup"><span data-stu-id="00848-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="00848-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="00848-118">Text Value</span></span>

<span data-ttu-id="00848-119">Especifique o nome totalmente qualificado do tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="00848-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="00848-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="00848-120">Remarks</span></span>

<span data-ttu-id="00848-121">Quando esse elemento for especificado, é possível especificar o `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="00848-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="00848-122">Para obter mais informações sobre como definir as condições de seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="00848-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00848-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="00848-123">See Also</span></span>

[<span data-ttu-id="00848-124">Elemento SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="00848-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="00848-125">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="00848-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
