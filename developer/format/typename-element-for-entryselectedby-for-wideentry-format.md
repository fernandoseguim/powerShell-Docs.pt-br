---
title: Elemento TypeName para EntrySelectedBy para WideEntry (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862642"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="415cd-102">Elemento TypeName para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="415cd-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="415cd-103">Especifica um tipo .NET para a definição.</span><span class="sxs-lookup"><span data-stu-id="415cd-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="415cd-104">A definição é usada sempre que esse objeto é exibido.</span><span class="sxs-lookup"><span data-stu-id="415cd-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="415cd-105">Configuração (formato) do elemento elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento WideControl (formato) elemento WideEntries (formato) elemento WideEntry (formato) EntrySelectedBy elemento do elemento WideEntry (formato) TypeName para WideEntry ( Formato)</span><span class="sxs-lookup"><span data-stu-id="415cd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="415cd-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="415cd-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="415cd-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="415cd-107">Attributes and Elements</span></span>

<span data-ttu-id="415cd-108">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="415cd-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="415cd-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="415cd-109">Attributes</span></span>

<span data-ttu-id="415cd-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="415cd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="415cd-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="415cd-111">Child Elements</span></span>

<span data-ttu-id="415cd-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="415cd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="415cd-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="415cd-113">Parent Elements</span></span>

|<span data-ttu-id="415cd-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="415cd-114">Element</span></span>|<span data-ttu-id="415cd-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="415cd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="415cd-116">Elemento EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="415cd-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="415cd-117">Define os tipos de .NET que usam essa entrada ampla ou a condição que deve existir para essa entrada a ser usado.</span><span class="sxs-lookup"><span data-stu-id="415cd-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="415cd-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="415cd-118">Text Value</span></span>

<span data-ttu-id="415cd-119">Especifique o nome totalmente qualificado do tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="415cd-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="415cd-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="415cd-120">Remarks</span></span>

<span data-ttu-id="415cd-121">Cada entrada ampla deve especificar um ou mais tipos de .NET, um conjunto de seleção ou a condição de seleção que deve existir para a definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="415cd-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="415cd-122">Para obter mais informações sobre outros componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="415cd-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="415cd-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="415cd-123">See Also</span></span>

[<span data-ttu-id="415cd-124">Criando uma exibição ampla</span><span class="sxs-lookup"><span data-stu-id="415cd-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="415cd-125">Elemento EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="415cd-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="415cd-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="415cd-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
