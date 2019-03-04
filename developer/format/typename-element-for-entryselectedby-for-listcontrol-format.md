---
title: Elemento TypeName para EntrySelectedBy para ListControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856102"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="3c3bf-102">Elemento TypeName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3c3bf-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="3c3bf-103">Especifica um tipo .NET que usa essa entrada da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="3c3bf-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="3c3bf-104">Não há nenhum limite para o número de tipos que podem ser especificados para uma entrada da lista.</span><span class="sxs-lookup"><span data-stu-id="3c3bf-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="3c3bf-105">Elemento (formato) elemento ViewDefinitions (formato) exibição elemento (formato) elemento ListControl (formato) elemento ListEntries (formato) elemento ListEntry (formato) EntrySelectedBy elemento de configuração para elemento de TypeName ListEntry (formato) EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3c3bf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c3bf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c3bf-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c3bf-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3c3bf-107">Attributes and Elements</span></span>

<span data-ttu-id="3c3bf-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="3c3bf-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c3bf-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3c3bf-109">Attributes</span></span>

<span data-ttu-id="3c3bf-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3c3bf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c3bf-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="3c3bf-111">Child Elements</span></span>

<span data-ttu-id="3c3bf-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3c3bf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3c3bf-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="3c3bf-113">Parent Elements</span></span>

|<span data-ttu-id="3c3bf-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c3bf-114">Element</span></span>|<span data-ttu-id="3c3bf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c3bf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c3bf-116">Elemento EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3c3bf-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="3c3bf-117">Define os tipos de .NET que usam essa entrada de lista ou a condição que deve existir para essa entrada a ser usado.</span><span class="sxs-lookup"><span data-stu-id="3c3bf-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3c3bf-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="3c3bf-118">Text Value</span></span>

<span data-ttu-id="3c3bf-119">Especifique o nome totalmente qualificado do tipo .NET, como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="3c3bf-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c3bf-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c3bf-120">Remarks</span></span>

<span data-ttu-id="3c3bf-121">Cada entrada da lista deve ter pelo menos um nome de tipo, conjunto de seleção ou condição de seleção definida.</span><span class="sxs-lookup"><span data-stu-id="3c3bf-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="3c3bf-122">Para obter mais informações sobre como esse elemento é usado em uma exibição de lista, consulte [exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="3c3bf-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3c3bf-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c3bf-123">Example</span></span>

<span data-ttu-id="3c3bf-124">O exemplo a seguir mostra como especificar uma seleção definida para uma entrada de uma exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="3c3bf-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="3c3bf-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="3c3bf-125">See Also</span></span>

[<span data-ttu-id="3c3bf-126">Criando uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="3c3bf-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3c3bf-127">Elemento EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3c3bf-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="3c3bf-128">Elemento SelectionSetName para EnrtySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3c3bf-128">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="3c3bf-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c3bf-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
