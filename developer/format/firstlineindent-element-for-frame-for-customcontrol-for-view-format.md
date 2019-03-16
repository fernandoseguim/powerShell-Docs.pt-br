---
title: Elemento FirstLineIndent de quadro para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054842"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="a2bfb-102">Elemento FirstLineIndent para Frame para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="a2bfb-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="a2bfb-103">Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita.</span><span class="sxs-lookup"><span data-stu-id="a2bfb-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="a2bfb-104">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="a2bfb-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="a2bfb-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de quadro CustomControlView (formato) CustomItem para CustomControl para elemento de FirstLineIndent de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a2bfb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="a2bfb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2bfb-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a2bfb-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a2bfb-107">Attributes and Elements</span></span>

<span data-ttu-id="a2bfb-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `FirstLineIndent` elemento.</span><span class="sxs-lookup"><span data-stu-id="a2bfb-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a2bfb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a2bfb-109">Attributes</span></span>

<span data-ttu-id="a2bfb-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a2bfb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a2bfb-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="a2bfb-111">Child Elements</span></span>

<span data-ttu-id="a2bfb-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a2bfb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a2bfb-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="a2bfb-113">Parent Elements</span></span>

|<span data-ttu-id="a2bfb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a2bfb-114">Element</span></span>|<span data-ttu-id="a2bfb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2bfb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a2bfb-116">Elemento de quadro para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a2bfb-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="a2bfb-117">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="a2bfb-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a2bfb-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="a2bfb-118">Text Value</span></span>

<span data-ttu-id="a2bfb-119">Especifique o número de caracteres que você deseja deslocar a primeira linha dos dados.</span><span class="sxs-lookup"><span data-stu-id="a2bfb-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2bfb-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2bfb-120">Remarks</span></span>

<span data-ttu-id="a2bfb-121">Se esse elemento for especificado, não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="a2bfb-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2bfb-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a2bfb-122">See Also</span></span>

[<span data-ttu-id="a2bfb-123">Elemento FirstLineHanging de quadro para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a2bfb-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a2bfb-124">Elemento de quadro para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a2bfb-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a2bfb-125">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="a2bfb-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
