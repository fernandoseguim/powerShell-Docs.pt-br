---
title: Elemento FirstLineHanging para quadro de GroupBy (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855612"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="6f1c5-102">Elemento FirstLineHanging para Frame para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="6f1c5-102">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="6f1c5-103">Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="6f1c5-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="6f1c5-104">Esse elemento é usado ao definir como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="6f1c5-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6f1c5-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento GroupBy elemento de configuração para o modo de exibição (formato) CustomControl elemento do elemento GroupBy (formato) CustomEntries para CustomControl para elemento de CustomEntry GroupBy (formato) CustomControl para elemento de GroupBy (formato) CustomItem CustomEntry para elemento de quadro GroupBy (formato) CustomItem para elemento GroupBy (formato) FirstLineHanging de quadro para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="6f1c5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6f1c5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f1c5-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6f1c5-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6f1c5-107">Attributes and Elements</span></span>

<span data-ttu-id="6f1c5-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `FirstLineHanging` elemento.</span><span class="sxs-lookup"><span data-stu-id="6f1c5-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6f1c5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="6f1c5-109">Attributes</span></span>

<span data-ttu-id="6f1c5-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6f1c5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6f1c5-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="6f1c5-111">Child Elements</span></span>

<span data-ttu-id="6f1c5-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6f1c5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6f1c5-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="6f1c5-113">Parent Elements</span></span>

|<span data-ttu-id="6f1c5-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f1c5-114">Element</span></span>|<span data-ttu-id="6f1c5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f1c5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6f1c5-116">Elemento de quadro para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="6f1c5-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="6f1c5-117">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="6f1c5-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6f1c5-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="6f1c5-118">Text Value</span></span>

<span data-ttu-id="6f1c5-119">Especifique o número de caracteres que você deseja deslocar a primeira linha dos dados.</span><span class="sxs-lookup"><span data-stu-id="6f1c5-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f1c5-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f1c5-120">Remarks</span></span>

<span data-ttu-id="6f1c5-121">Se esse elemento for especificado, não é possível especificar o [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6f1c5-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f1c5-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="6f1c5-122">See Also</span></span>

[<span data-ttu-id="6f1c5-123">Elemento FirstLineIndent para quadro de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="6f1c5-123">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="6f1c5-124">Elemento de quadro para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="6f1c5-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="6f1c5-125">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="6f1c5-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
