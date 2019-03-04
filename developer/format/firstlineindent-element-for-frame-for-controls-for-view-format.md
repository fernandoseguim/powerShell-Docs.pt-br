---
title: Elemento FirstLineIndent para quadro de controles para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854312"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="7a3b9-102">Elemento FirstLineIndent para Frame para Controls para View (formato)</span><span class="sxs-lookup"><span data-stu-id="7a3b9-102">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="7a3b9-103">Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita.</span><span class="sxs-lookup"><span data-stu-id="7a3b9-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="7a3b9-104">Esse elemento é usado durante a definição de controles que podem ser usados por um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="7a3b9-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="7a3b9-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento controles elemento (formato) controle elemento de configuração para controles para exibição (formato) CustomControl elemento de controle para controles para elemento CustomEntries de exibição (formato) CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para controles para elemento de exibição (formato) CustomItem CustomEntry controles para o elemento de exibição (formato) do quadro para CustomItem controles para exibição (formato) FirstLineIndent elemento de quadro controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7a3b9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineIndent Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a3b9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a3b9-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a3b9-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7a3b9-107">Attributes and Elements</span></span>

<span data-ttu-id="7a3b9-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `FirstLineIndent` elemento.</span><span class="sxs-lookup"><span data-stu-id="7a3b9-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a3b9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="7a3b9-109">Attributes</span></span>

<span data-ttu-id="7a3b9-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7a3b9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a3b9-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="7a3b9-111">Child Elements</span></span>

<span data-ttu-id="7a3b9-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7a3b9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7a3b9-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="7a3b9-113">Parent Elements</span></span>

|<span data-ttu-id="7a3b9-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a3b9-114">Element</span></span>|<span data-ttu-id="7a3b9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a3b9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a3b9-116">Elemento de quadro para CustomItem controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7a3b9-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="7a3b9-117">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="7a3b9-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7a3b9-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="7a3b9-118">Text Value</span></span>

<span data-ttu-id="7a3b9-119">Especifique o número de caracteres que você deseja deslocar a primeira linha dos dados.</span><span class="sxs-lookup"><span data-stu-id="7a3b9-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a3b9-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a3b9-120">Remarks</span></span>

<span data-ttu-id="7a3b9-121">Se esse elemento for especificado, não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="7a3b9-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a3b9-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="7a3b9-122">See Also</span></span>

[<span data-ttu-id="7a3b9-123">Elemento FirstLineHanging para quadro de controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7a3b9-123">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="7a3b9-124">Elemento de quadro para CustomItem controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="7a3b9-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="7a3b9-125">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a3b9-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)