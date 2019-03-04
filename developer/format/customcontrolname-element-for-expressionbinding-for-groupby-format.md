---
title: Elemento CustomControlName para ExpressionBinding para GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854292"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="ad8fb-102">Elemento CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ad8fb-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="ad8fb-103">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="ad8fb-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="ad8fb-104">Esse elemento é usado ao definir como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="ad8fb-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ad8fb-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) CustomItem CustomEntry para elemento de GroupBy (formato) ExpressionBinding CustomItem para elemento de GroupBy (formato) CustomControlName ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ad8fb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad8fb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad8fb-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad8fb-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ad8fb-107">Attributes and Elements</span></span>

<span data-ttu-id="ad8fb-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="ad8fb-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad8fb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ad8fb-109">Attributes</span></span>

<span data-ttu-id="ad8fb-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ad8fb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad8fb-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="ad8fb-111">Child Elements</span></span>

<span data-ttu-id="ad8fb-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ad8fb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ad8fb-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="ad8fb-113">Parent Elements</span></span>

|<span data-ttu-id="ad8fb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="ad8fb-114">Element</span></span>|<span data-ttu-id="ad8fb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad8fb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad8fb-116">Elemento ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ad8fb-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="ad8fb-117">Define os dados que são exibidos pelo controle.</span><span class="sxs-lookup"><span data-stu-id="ad8fb-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ad8fb-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="ad8fb-118">Text Value</span></span>

<span data-ttu-id="ad8fb-119">Especifique o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="ad8fb-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad8fb-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad8fb-120">Remarks</span></span>

<span data-ttu-id="ad8fb-121">Você pode criar controles comuns que podem ser usados por todas as exibições de um arquivo de formatação, e você pode criar controles de exibição que podem ser usados por uma exibição específica.</span><span class="sxs-lookup"><span data-stu-id="ad8fb-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="ad8fb-122">Os elementos a seguir especificam os nomes desses controles:</span><span class="sxs-lookup"><span data-stu-id="ad8fb-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="ad8fb-123">Elemento Name para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="ad8fb-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="ad8fb-124">Elemento Name para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="ad8fb-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="ad8fb-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ad8fb-125">See Also</span></span>

[<span data-ttu-id="ad8fb-126">Elemento Name para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="ad8fb-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="ad8fb-127">Elemento Name para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="ad8fb-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="ad8fb-128">Elemento ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ad8fb-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="ad8fb-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad8fb-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
