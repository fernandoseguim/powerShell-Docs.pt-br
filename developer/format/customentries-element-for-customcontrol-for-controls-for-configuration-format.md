---
title: Elemento CustomEntries para CustomControl para controles de configuração (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856302"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="a22c3-102">Elemento CustomEntries para CustomControl para Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="a22c3-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a22c3-103">Fornece as definições de um controle comum.</span><span class="sxs-lookup"><span data-stu-id="a22c3-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="a22c3-104">Esse elemento é usado durante a definição de um controle comum que pode ser usado por todas as exibições no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="a22c3-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a22c3-105">Elemento de controles de (formato) do elemento de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para o controle para o elemento de configuração (formato) de CustomEntries para CustomControl para configuração ( Formato)</span><span class="sxs-lookup"><span data-stu-id="a22c3-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a22c3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a22c3-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a22c3-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a22c3-107">Attributes and Elements</span></span>

<span data-ttu-id="a22c3-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="a22c3-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="a22c3-109">Você deve especificar um ou mais elementos filho.</span><span class="sxs-lookup"><span data-stu-id="a22c3-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a22c3-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a22c3-110">Attributes</span></span>

<span data-ttu-id="a22c3-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a22c3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a22c3-112">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="a22c3-112">Child Elements</span></span>

|<span data-ttu-id="a22c3-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a22c3-113">Element</span></span>|<span data-ttu-id="a22c3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a22c3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a22c3-115">Elemento CustomEntry para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a22c3-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="a22c3-116">Fornece uma definição do controle comum.</span><span class="sxs-lookup"><span data-stu-id="a22c3-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a22c3-117">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="a22c3-117">Parent Elements</span></span>

|<span data-ttu-id="a22c3-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="a22c3-118">Element</span></span>|<span data-ttu-id="a22c3-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a22c3-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a22c3-120">Elemento CustomControl para controle de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a22c3-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="a22c3-121">Define um controle comum.</span><span class="sxs-lookup"><span data-stu-id="a22c3-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a22c3-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="a22c3-122">Remarks</span></span>

<span data-ttu-id="a22c3-123">Na maioria dos casos, um controle tem apenas uma definição, que é definida em um único `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="a22c3-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="a22c3-124">No entanto é possível ter várias definições, se você quiser usar o mesmo controle para exibir objetos diferentes do .NET.</span><span class="sxs-lookup"><span data-stu-id="a22c3-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="a22c3-125">Nesses casos, você pode definir um `CustomEntry` elemento para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="a22c3-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="a22c3-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a22c3-126">See Also</span></span>

[<span data-ttu-id="a22c3-127">Elemento CustomControl para controle de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a22c3-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="a22c3-128">Elemento CustomEntry para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a22c3-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="a22c3-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="a22c3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
