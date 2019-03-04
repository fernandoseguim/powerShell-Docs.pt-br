---
title: Arquivos de formatação personalizada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860602"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="5f1c7-102">Arquivos de formatação personalizada</span><span class="sxs-lookup"><span data-stu-id="5f1c7-102">Custom Formatting Files</span></span>

<span data-ttu-id="5f1c7-103">O formato de exibição para os objetos retornados pelo cmdlets, funções e scripts são definidas usando arquivos de formatação (format.ps1xml arquivos).</span><span class="sxs-lookup"><span data-stu-id="5f1c7-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="5f1c7-104">Vários desses arquivos são fornecidos pelo Windows PowerShell para definir o formato de exibição padrão para os objetos retornados pelos cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="5f1c7-105">No entanto, você também pode criar seus próprios arquivos de formatação personalizados para substituir os formatos de exibição padrão ou para definir a exibição de objetos retornados pelos seus próprios comandos.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="5f1c7-106">Windows PowerShell usa os dados nesses arquivos de formatação para determinar o que é exibido e como os dados são formatados.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="5f1c7-107">Os dados exibidos podem incluir as propriedades de um objeto ou o valor de um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="5f1c7-108">Blocos de script são usados se você quiser exibir algum valor que não está disponível diretamente das propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="5f1c7-109">Por exemplo, você talvez queira adicionar o valor de duas propriedades de um objeto e exibir a soma como uma parte separada dos dados.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="5f1c7-110">Quando você escreve sua própria formatação de arquivo, você precisará definir *modos de exibição* para os objetos que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="5f1c7-111">Você pode definir uma exibição única para cada objeto, você pode definir uma exibição única para vários objetos, ou você pode definir vários modos de exibição para o mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="5f1c7-112">Não há nenhum limite para o número de modos de exibição que você pode definir.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f1c7-113">Arquivos de formatação não determinam os elementos de um objeto que são retornados para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="5f1c7-114">Quando um objeto é retornado para o pipeline, todos os membros desse objeto estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="5f1c7-115">Modos de exibição de formato</span><span class="sxs-lookup"><span data-stu-id="5f1c7-115">Format Views</span></span>

<span data-ttu-id="5f1c7-116">Formatação de modos de exibição podem exibir objetos em um formato de tabela, um formato de lista, um formato amplo e um formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="5f1c7-117">Geralmente, cada definição de formatação é descrita por um conjunto de marcas XML que descrevem um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="5f1c7-118">Cada modo de exibição contém o nome da exibição, os objetos que usam o modo de exibição e os elementos da exibição, como as informações de linha e coluna para uma exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="5f1c7-119">As exibições a seguir estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-119">The following views are available.</span></span>

<span data-ttu-id="5f1c7-120">Exibição de tabela lista as propriedades de um objeto ou um valor de bloco de script em uma ou mais colunas.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="5f1c7-121">Cada coluna representa uma propriedade do objeto ou um valor de bloco de script.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="5f1c7-122">Você pode definir uma exibição de tabela que exibe todas as propriedades de um objeto, um subconjunto das propriedades de um objeto ou uma combinação de propriedades e valores de bloco de script.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="5f1c7-123">Cada linha da tabela representa um objeto retornado.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="5f1c7-124">Para obter mais informações sobre este modo de exibição, consulte [exibição de tabela](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="5f1c7-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="5f1c7-125">Exibição de lista lista as propriedades de um objeto ou um valor de bloco de script em uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="5f1c7-126">Cada linha da lista exibe o nome da propriedade seguido pelo valor do bloco de script ou de propriedade ou um rótulo opcional.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="5f1c7-127">Para obter mais informações sobre este modo de exibição, consulte [exibição de lista](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5f1c7-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="5f1c7-128">Exibição ampla com a lista de uma única propriedade de um objeto ou um valor de bloco de script em uma ou mais colunas.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="5f1c7-129">Não há nenhum rótulo ou o cabeçalho para este modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-129">There is no label or header for this view.</span></span> <span data-ttu-id="5f1c7-130">Para obter mais informações sobre este modo de exibição, consulte [exibição ampla](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="5f1c7-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="5f1c7-131">Exibição personalizada mostra uma exibição personalizável de propriedades do objeto ou valores de bloco de script que não seguem a estrutura rígida de modos de exibição de tabela, exibições de lista ou exibições amplas.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="5f1c7-132">Você pode definir uma exibição personalizada de autônomo, ou você pode definir uma exibição personalizada que é usada por outro modo de exibição, como uma exibição de tabela ou exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="5f1c7-133">Para obter mais informações sobre este modo de exibição, consulte [modo de exibição personalizado](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5f1c7-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="5f1c7-134">Elementos XML de modo de exibição</span><span class="sxs-lookup"><span data-stu-id="5f1c7-134">View XML Elements</span></span>

<span data-ttu-id="5f1c7-135">O exemplo a seguir mostra as marcas XML usadas para definir uma exibição de tabela que contém duas colunas.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="5f1c7-136">O [ViewDefinitions](../format/viewdefinitions-element-format.md) é o elemento de contêiner para todas as exibições definidas no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="5f1c7-137">O [exibição](../format/view-element-format.md) elemento define a tabela específica, a lista, o modo de exibição amplo ou personalizado.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="5f1c7-138">Dentro de cada exibição, o [nome](../format/name-element-for-view-format.md) elemento Especifica o nome da exibição, o [ViewSelectedBy](../format/viewselectedby-element-format.md) elemento define os objetos que usam o modo de exibição e os elementos de controle diferentes (como o `TableControl` elemento) definem o formato da exibição.</span><span class="sxs-lookup"><span data-stu-id="5f1c7-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="5f1c7-139">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5f1c7-139">See Also</span></span>

[<span data-ttu-id="5f1c7-140">Exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="5f1c7-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="5f1c7-141">Exibição de lista</span><span class="sxs-lookup"><span data-stu-id="5f1c7-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="5f1c7-142">Exibição ampla</span><span class="sxs-lookup"><span data-stu-id="5f1c7-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="5f1c7-143">Modo de exibição personalizado</span><span class="sxs-lookup"><span data-stu-id="5f1c7-143">Custom View</span></span>](../format/creating-custom-controls.md)

<span data-ttu-id="5f1c7-144">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="5f1c7-144">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
