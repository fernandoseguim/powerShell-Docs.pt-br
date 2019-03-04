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
ms.openlocfilehash: 9ec6caedcb7cf20d4aab2216cd8a9707269d9452
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854952"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="42e9a-102">Elemento FirstLineIndent para Frame para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="42e9a-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="42e9a-103">Especifica quantos caracteres, a primeira linha de dados é deslocada para a direita.</span><span class="sxs-lookup"><span data-stu-id="42e9a-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="42e9a-104">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="42e9a-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="42e9a-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento elemento CustomControl (formato) CustomEntries elemento de configuração para CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para elemento CustomItem de exibição (formato) CustomEntry para elemento de quadro CutomControlView (formato) CustomItem para CustomControl para elemento de FirstLineIndent de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="42e9a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="42e9a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42e9a-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42e9a-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="42e9a-107">Attributes and Elements</span></span>

<span data-ttu-id="42e9a-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `FirstLineIndent` elemento.</span><span class="sxs-lookup"><span data-stu-id="42e9a-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42e9a-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="42e9a-109">Attributes</span></span>

<span data-ttu-id="42e9a-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="42e9a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42e9a-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="42e9a-111">Child Elements</span></span>

<span data-ttu-id="42e9a-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="42e9a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="42e9a-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="42e9a-113">Parent Elements</span></span>

|<span data-ttu-id="42e9a-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="42e9a-114">Element</span></span>|<span data-ttu-id="42e9a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="42e9a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42e9a-116">Elemento de quadro para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="42e9a-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="42e9a-117">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="42e9a-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="42e9a-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="42e9a-118">Text Value</span></span>

<span data-ttu-id="42e9a-119">Especifique o número de caracteres que você deseja deslocar a primeira linha dos dados.</span><span class="sxs-lookup"><span data-stu-id="42e9a-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="42e9a-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="42e9a-120">Remarks</span></span>

<span data-ttu-id="42e9a-121">Se esse elemento for especificado, não é possível especificar o [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="42e9a-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="42e9a-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="42e9a-122">See Also</span></span>

[<span data-ttu-id="42e9a-123">Elemento FirstLineHanging de quadro para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="42e9a-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42e9a-124">Elemento de quadro para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="42e9a-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42e9a-125">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="42e9a-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
