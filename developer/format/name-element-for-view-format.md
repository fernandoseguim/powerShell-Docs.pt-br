---
title: Nome de elemento para o modo de exibição (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859502"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="48699-102">Elemento Name para View (formato)</span><span class="sxs-lookup"><span data-stu-id="48699-102">Name Element for View (Format)</span></span>

<span data-ttu-id="48699-103">Especifica o nome que é usado para identificar o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="48699-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="48699-104">Configuração (formato) elemento ViewDefinitions (formato) modo de exibição (formato) do elemento nome elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="48699-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48699-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48699-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48699-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="48699-106">Attributes and Elements</span></span>

<span data-ttu-id="48699-107">As seções a seguir descrevem atributos, elementos filho e o elemento pai do `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="48699-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="48699-108">Apenas um `Name` elemento é permitido para cada modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="48699-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="48699-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="48699-109">Attributes</span></span>

<span data-ttu-id="48699-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="48699-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48699-111">Elementos filhos</span><span class="sxs-lookup"><span data-stu-id="48699-111">Child Elements</span></span>

<span data-ttu-id="48699-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="48699-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="48699-113">Elementos pais</span><span class="sxs-lookup"><span data-stu-id="48699-113">Parent Elements</span></span>

|<span data-ttu-id="48699-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="48699-114">Element</span></span>|<span data-ttu-id="48699-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="48699-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48699-116">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="48699-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="48699-117">Define uma exibição que é usada para exibir os membros de um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="48699-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="48699-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="48699-118">Text Value</span></span>

<span data-ttu-id="48699-119">Especifique um nome amigável exclusivo para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="48699-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="48699-120">Esse nome pode incluir uma referência para o tipo de exibição (como um modo de exibição de tabela ou exibição de lista), qual objeto ou conjunto de objetos usam o modo de exibição, o comando retorna os objetos ou uma combinação desses elementos.</span><span class="sxs-lookup"><span data-stu-id="48699-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="48699-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="48699-121">Remarks</span></span>

<span data-ttu-id="48699-122">Para obter mais informações sobre os diferentes tipos de modos de exibição, consulte os tópicos a seguir: [Exibição de tabela](./creating-a-table-view.md), [exibição de lista](./creating-a-list-view.md), [exibição ampla](./creating-a-wide-view.md), e [exibição personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="48699-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="48699-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48699-123">Example</span></span>

<span data-ttu-id="48699-124">A exemplo a seguir mostra uma `View` elemento que define uma exibição de tabela para o [ServiceProcess](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="48699-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="48699-125">O nome do modo de exibição é "serviço".</span><span class="sxs-lookup"><span data-stu-id="48699-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="48699-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="48699-126">See Also</span></span>

[<span data-ttu-id="48699-127">Criando uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="48699-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="48699-128">Criando uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="48699-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="48699-129">Criando uma exibição ampla</span><span class="sxs-lookup"><span data-stu-id="48699-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="48699-130">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="48699-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="48699-131">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="48699-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="48699-132">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="48699-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
