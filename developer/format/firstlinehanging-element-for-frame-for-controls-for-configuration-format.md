---
title: Elemento FirstLineHanging de quadro para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861332"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="39d26-102">Elemento FirstLineHanging para Frame para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="39d26-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="39d26-103">Especifica quantos caracteres, a primeira linha de dados é deslocada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="39d26-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="39d26-104">Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="39d26-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="39d26-105">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Elemento de CustomEntry Format) para CustomControl para controles para configuração (formato) elemento CustomItem CustomEntry controles para o elemento de quadro de configuração para CustomItem controles para o elemento de configuração (formato) de FirstLineHanging para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="39d26-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="39d26-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39d26-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="39d26-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39d26-107">Attributes and Elements</span></span>

<span data-ttu-id="39d26-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `FirstLineHanging` elemento.</span><span class="sxs-lookup"><span data-stu-id="39d26-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="39d26-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="39d26-109">Attributes</span></span>

<span data-ttu-id="39d26-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="39d26-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="39d26-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="39d26-111">Child Elements</span></span>

<span data-ttu-id="39d26-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="39d26-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="39d26-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="39d26-113">Parent Elements</span></span>

|<span data-ttu-id="39d26-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="39d26-114">Element</span></span>|<span data-ttu-id="39d26-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="39d26-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="39d26-116">Elemento de quadro para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="39d26-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="39d26-117">Define como os dados são exibidos, como o deslocamento de dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="39d26-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="39d26-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="39d26-118">Text Value</span></span>

<span data-ttu-id="39d26-119">Especifique o número de caracteres que você deseja deslocar a primeira linha dos dados.</span><span class="sxs-lookup"><span data-stu-id="39d26-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="39d26-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="39d26-120">Remarks</span></span>

<span data-ttu-id="39d26-121">Se esse elemento for especificado, não é possível especificar o `FirstLineIndent` elemento.</span><span class="sxs-lookup"><span data-stu-id="39d26-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="39d26-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="39d26-122">See Also</span></span>

[<span data-ttu-id="39d26-123">Elemento de quadro para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="39d26-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="39d26-124">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="39d26-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
