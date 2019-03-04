---
title: Elemento CustomControlName para ExpressionBinding para CustomControl para exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860432"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="f5a76-102">Elemento CustomControlName para ExpressionBinding para CustomControl para View (formato)</span><span class="sxs-lookup"><span data-stu-id="f5a76-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="f5a76-103">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="f5a76-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="f5a76-104">Esse elemento é usado ao definir uma exibição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="f5a76-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f5a76-105">Elemento (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento CustomControl elemento de configuração para elemento de exibição (formato) CustomEntries CustomControl para elemento de exibição (formato) CustomEntry CustomEntries para CustomItem do modo de exibição (formato) Elemento para CustomEntry para exibição (formato) ExpressionBinding elemento do elemento CustomItem (formato) CustomControlName para associação de expressão para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f5a76-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5a76-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5a76-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5a76-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f5a76-107">Attributes and Elements</span></span>

<span data-ttu-id="f5a76-108">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="f5a76-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5a76-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f5a76-109">Attributes</span></span>

<span data-ttu-id="f5a76-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f5a76-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5a76-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="f5a76-111">Child Elements</span></span>

<span data-ttu-id="f5a76-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f5a76-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5a76-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="f5a76-113">Parent Elements</span></span>

|<span data-ttu-id="f5a76-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f5a76-114">Element</span></span>|<span data-ttu-id="f5a76-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5a76-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5a76-116">Elemento ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f5a76-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f5a76-117">Define os dados que são exibidos pelo controle.</span><span class="sxs-lookup"><span data-stu-id="f5a76-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f5a76-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f5a76-118">Text Value</span></span>

<span data-ttu-id="f5a76-119">Especifique o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="f5a76-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5a76-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5a76-120">Remarks</span></span>

<span data-ttu-id="f5a76-121">Você pode criar controles comuns que podem ser usados por todas as exibições de um arquivo de formatação e você pode criar controles de exibição que podem ser usados por uma exibição específica.</span><span class="sxs-lookup"><span data-stu-id="f5a76-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="f5a76-122">Os nomes desses controles são especificados por elementos a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5a76-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="f5a76-123">Elemento Name para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="f5a76-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="f5a76-124">Elemento Name para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="f5a76-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="f5a76-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f5a76-125">See Also</span></span>

[<span data-ttu-id="f5a76-126">Elemento Name para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="f5a76-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="f5a76-127">Elemento Name para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="f5a76-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="f5a76-128">Elemento ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f5a76-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f5a76-129">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5a76-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
