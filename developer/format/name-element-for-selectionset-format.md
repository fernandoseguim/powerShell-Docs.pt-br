---
title: Nome de elemento para SelectionSet (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858162"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="61191-102">Elemento Name para SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="61191-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="61191-103">Especifica o nome usado para referenciar o conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="61191-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="61191-104">Elemento (formato) elemento SelectionSets (formato) elemento SelectionSet (formato) nome elemento de configuração SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="61191-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="61191-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61191-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61191-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="61191-106">Attributes and Elements</span></span>

<span data-ttu-id="61191-107">As seções a seguir descrevem os atributos, elementos filho e o elemento pai do `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="61191-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="61191-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="61191-108">Attributes</span></span>

<span data-ttu-id="61191-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="61191-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="61191-110">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="61191-110">Child Elements</span></span>

<span data-ttu-id="61191-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="61191-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="61191-112">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="61191-112">Parent Elements</span></span>

|<span data-ttu-id="61191-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="61191-113">Element</span></span>|<span data-ttu-id="61191-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="61191-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61191-115">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="61191-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="61191-116">Define um único conjunto de objetos .NET que pode ser referenciado pelo nome do conjunto.</span><span class="sxs-lookup"><span data-stu-id="61191-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="61191-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="61191-117">Text Value</span></span>

<span data-ttu-id="61191-118">Especifique o nome para referenciar o conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="61191-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="61191-119">Há não há restrições em relação a quais caracteres podem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="61191-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="61191-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="61191-120">Remarks</span></span>

<span data-ttu-id="61191-121">O nome especificado aqui é usado no `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="61191-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="61191-122">O conjunto de seleção que pode ser usado por uma exibição, por uma definição de uma exibição (modos de exibição podem ter várias definições), ou ao especificar uma condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="61191-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="61191-123">Para obter mais informações sobre conjuntos de seleção, consulte [definindo define de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="61191-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="61191-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61191-124">Example</span></span>

<span data-ttu-id="61191-125">Este exemplo mostra um `SelectionSet` elemento que define quatro tipos de .NET.</span><span class="sxs-lookup"><span data-stu-id="61191-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="61191-126">O nome do conjunto de seleção é "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="61191-126">The name of the selection set is "FileSystemTypes".</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="61191-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="61191-127">See Also</span></span>

[<span data-ttu-id="61191-128">Definindo conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="61191-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="61191-129">Elemento SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="61191-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="61191-130">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="61191-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
