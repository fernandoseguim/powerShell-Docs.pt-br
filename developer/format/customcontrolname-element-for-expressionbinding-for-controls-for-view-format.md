---
title: Elemento CustomControlName para ExpressionBinding controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855592"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="8adc3-102">Elemento CustomControlName para ExpressionBinding para Controls para View (formato)</span><span class="sxs-lookup"><span data-stu-id="8adc3-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="8adc3-103">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="8adc3-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="8adc3-104">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="8adc3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8adc3-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) CustomItem CustomEntry para controles para elemento de exibição (formato) ExpressionBinding CustomItem controles para exibição (formato) CustomControlName Elemento para ExpressionBindine controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8adc3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8adc3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8adc3-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8adc3-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8adc3-107">Attributes and Elements</span></span>

<span data-ttu-id="8adc3-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="8adc3-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8adc3-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8adc3-109">Attributes</span></span>

<span data-ttu-id="8adc3-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8adc3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8adc3-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="8adc3-111">Child Elements</span></span>

<span data-ttu-id="8adc3-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8adc3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8adc3-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="8adc3-113">Parent Elements</span></span>

|<span data-ttu-id="8adc3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8adc3-114">Element</span></span>|<span data-ttu-id="8adc3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8adc3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8adc3-116">Elemento ExpressionBinding para CustomItem controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8adc3-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="8adc3-117">Define os dados que são exibidos pelo controle.</span><span class="sxs-lookup"><span data-stu-id="8adc3-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8adc3-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8adc3-118">Text Value</span></span>

<span data-ttu-id="8adc3-119">Especifique o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="8adc3-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="8adc3-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="8adc3-120">Remarks</span></span>

<span data-ttu-id="8adc3-121">Você pode criar controles comuns que podem ser usados por todas as exibições de um arquivo de formatação, e você pode criar controles de exibição que podem ser usados por uma exibição específica.</span><span class="sxs-lookup"><span data-stu-id="8adc3-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="8adc3-122">Os elementos a seguir especificam os nomes desses controles:</span><span class="sxs-lookup"><span data-stu-id="8adc3-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="8adc3-123">Elemento Name para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="8adc3-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="8adc3-124">Elemento Name para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8adc3-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="8adc3-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8adc3-125">See Also</span></span>

[<span data-ttu-id="8adc3-126">Elemento Name para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="8adc3-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="8adc3-127">Elemento Name para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8adc3-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="8adc3-128">Elemento ExpressionBinding para CustomItem controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8adc3-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="8adc3-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="8adc3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
