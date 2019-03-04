---
title: Elemento TypeName para EntrySelectedBy para CustomEntry para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858832"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="4cdf4-102">Elemento TypeName para EntrySelectedBy para Controls para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="4cdf4-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="4cdf4-103">Especifica um tipo .NET que usa essa definição da exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="4cdf4-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="4cdf4-104">Não há nenhum limite para o número de tipos que podem ser especificados para uma definição.</span><span class="sxs-lookup"><span data-stu-id="4cdf4-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="4cdf4-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para elemento de exibição (formato) TypeName EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="4cdf4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4cdf4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4cdf4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4cdf4-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4cdf4-107">Attributes and Elements</span></span>

<span data-ttu-id="4cdf4-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="4cdf4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4cdf4-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4cdf4-109">Attributes</span></span>

<span data-ttu-id="4cdf4-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4cdf4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4cdf4-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="4cdf4-111">Child Elements</span></span>

<span data-ttu-id="4cdf4-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4cdf4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4cdf4-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="4cdf4-113">Parent Elements</span></span>

|<span data-ttu-id="4cdf4-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="4cdf4-114">Element</span></span>|<span data-ttu-id="4cdf4-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4cdf4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4cdf4-116">Elemento EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="4cdf4-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="4cdf4-117">Define os tipos de .NET que usam essa definição de exibição do controle personalizado ou a condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="4cdf4-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4cdf4-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="4cdf4-118">Text Value</span></span>

<span data-ttu-id="4cdf4-119">Especifique o nome totalmente qualificado do tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="4cdf4-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4cdf4-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="4cdf4-120">Remarks</span></span>

<span data-ttu-id="4cdf4-121">Cada definição de exibição do controle personalizado deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.</span><span class="sxs-lookup"><span data-stu-id="4cdf4-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4cdf4-122">Para obter mais informações sobre os componentes de uma exibição de controle personalizado, consulte [criação de controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4cdf4-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4cdf4-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4cdf4-123">See Also</span></span>

[<span data-ttu-id="4cdf4-124">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="4cdf4-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4cdf4-125">Elemento EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="4cdf4-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4cdf4-126">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4cdf4-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
