---
title: Elemento CustomEntry para CustomEntries controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858772"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="62489-102">Elemento CustomEntry para CustomEntries para Controls para configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="62489-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="62489-103">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="62489-103">Provides a definition of the control.</span></span> <span data-ttu-id="62489-104">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="62489-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="62489-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para elemento de exibição (formato) CustomEntry CustomEntries controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="62489-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="62489-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62489-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62489-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="62489-107">Attributes and Elements</span></span>

<span data-ttu-id="62489-108">As seções a seguir descrevem atributos, elementos filho e os elementos pai do `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="62489-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="62489-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="62489-109">Attributes</span></span>

<span data-ttu-id="62489-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="62489-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62489-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="62489-111">Child Elements</span></span>

|<span data-ttu-id="62489-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="62489-112">Element</span></span>|<span data-ttu-id="62489-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="62489-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62489-114">Elemento EntrySelectedBy para CustomEntry controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="62489-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="62489-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="62489-115">Optional element.</span></span><br /><br /> <span data-ttu-id="62489-116">Define os tipos de .NET que usam essa definição de controle ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="62489-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="62489-117">Elemento CustomItem para CustomEntry controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="62489-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="62489-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="62489-118">Required element.</span></span><br /><br /> <span data-ttu-id="62489-119">Define como o controle exibe os dados.</span><span class="sxs-lookup"><span data-stu-id="62489-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="62489-120">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="62489-120">Parent Elements</span></span>

|<span data-ttu-id="62489-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="62489-121">Element</span></span>|<span data-ttu-id="62489-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="62489-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62489-123">Elemento CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="62489-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="62489-124">Fornece as definições para o controle.</span><span class="sxs-lookup"><span data-stu-id="62489-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="62489-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="62489-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="62489-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="62489-126">See Also</span></span>

[<span data-ttu-id="62489-127">Elemento CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="62489-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="62489-128">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="62489-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
