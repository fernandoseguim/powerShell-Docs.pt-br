---
title: Elemento FirstLineHanging de quadro para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ae4ad8ae3e6cb5d1174dc001b30aa84dd182a606
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860232"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="aecd3-102">Elemento FirstLineHanging para Frame para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="aecd3-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="aecd3-103">Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="aecd3-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="aecd3-104">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="aecd3-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="aecd3-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de quadro CutomControlView (formato) CustomItem para CustomControl para exibição (formato) FirstLineHanging elemento de quadro para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="aecd3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aecd3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aecd3-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aecd3-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="aecd3-107">Attributes and Elements</span></span>

<span data-ttu-id="aecd3-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `FirstLineHanging` elemento.</span><span class="sxs-lookup"><span data-stu-id="aecd3-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aecd3-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="aecd3-109">Attributes</span></span>

<span data-ttu-id="aecd3-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="aecd3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aecd3-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="aecd3-111">Child Elements</span></span>

<span data-ttu-id="aecd3-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="aecd3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aecd3-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="aecd3-113">Parent Elements</span></span>

|<span data-ttu-id="aecd3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="aecd3-114">Element</span></span>|<span data-ttu-id="aecd3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="aecd3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aecd3-116">Elemento de quadro para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="aecd3-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="aecd3-117">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="aecd3-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aecd3-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="aecd3-118">Text Value</span></span>

<span data-ttu-id="aecd3-119">Especifique o número de caracteres que você deseja deslocar a primeira linha dos dados.</span><span class="sxs-lookup"><span data-stu-id="aecd3-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="aecd3-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="aecd3-120">Remarks</span></span>

<span data-ttu-id="aecd3-121">Se esse elemento for especificado, não é possível especificar o [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="aecd3-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="aecd3-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="aecd3-122">See Also</span></span>

[<span data-ttu-id="aecd3-123">Elemento FirstLineIndent de quadro para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="aecd3-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="aecd3-124">Elemento de quadro para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="aecd3-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="aecd3-125">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="aecd3-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
