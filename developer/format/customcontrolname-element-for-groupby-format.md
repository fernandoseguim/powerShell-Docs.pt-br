---
title: Elemento CustomControlName para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860302"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="7acdf-102">Elemento CustomControlName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7acdf-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="7acdf-103">Especifica o nome de um controle personalizado que é usado para exibir o novo grupo.</span><span class="sxs-lookup"><span data-stu-id="7acdf-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="7acdf-104">Esse elemento é usado durante a definição de uma tabela, a lista, o modo de exibição de controle personalizado ou largos.</span><span class="sxs-lookup"><span data-stu-id="7acdf-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="7acdf-105">Elemento (formato) elemento ViewDefinitions (formato) exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControlName elemento de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="7acdf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7acdf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7acdf-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7acdf-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7acdf-107">Attributes and Elements</span></span>

<span data-ttu-id="7acdf-108">As seções a seguir descrevem os atributos, elementos filho e elementos pai do `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="7acdf-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7acdf-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="7acdf-109">Attributes</span></span>

<span data-ttu-id="7acdf-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7acdf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7acdf-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="7acdf-111">Child Elements</span></span>

<span data-ttu-id="7acdf-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7acdf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7acdf-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="7acdf-113">Parent Elements</span></span>

|<span data-ttu-id="7acdf-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="7acdf-114">Element</span></span>|<span data-ttu-id="7acdf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="7acdf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7acdf-116">Elemento GroupBy para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7acdf-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="7acdf-117">Define como o Windows PowerShell exibe um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="7acdf-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7acdf-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="7acdf-118">Text Value</span></span>

<span data-ttu-id="7acdf-119">Especifique o nome do controle personalizado que é usado para exibir um novo grupo.</span><span class="sxs-lookup"><span data-stu-id="7acdf-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="7acdf-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="7acdf-120">Remarks</span></span>

<span data-ttu-id="7acdf-121">Você pode criar controles comuns que podem ser usados por todas as exibições de um arquivo de formatação, e você pode criar controles de exibição que podem ser usados por uma exibição específica.</span><span class="sxs-lookup"><span data-stu-id="7acdf-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="7acdf-122">Os elementos a seguir especificam os nomes desses controles personalizados:</span><span class="sxs-lookup"><span data-stu-id="7acdf-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="7acdf-123">Elemento Name para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="7acdf-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="7acdf-124">Elemento Name para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7acdf-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="7acdf-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="7acdf-125">See Also</span></span>

[<span data-ttu-id="7acdf-126">Elemento GroupBy para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7acdf-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="7acdf-127">Elemento Name para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="7acdf-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="7acdf-128">Elemento Name para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7acdf-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="7acdf-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7acdf-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
