---
title: Criando uma exibição de tabela | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 832527ea4b042812c39934cd7e124201c6dc2ea4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861492"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="1a15a-102">Criar uma exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="1a15a-102">Creating a Table View</span></span>

<span data-ttu-id="1a15a-103">Uma exibição de tabela exibe dados em uma ou mais colunas.</span><span class="sxs-lookup"><span data-stu-id="1a15a-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="1a15a-104">Cada linha na tabela representa um objeto .NET, e cada coluna da tabela representa uma propriedade do objeto ou um valor de script.</span><span class="sxs-lookup"><span data-stu-id="1a15a-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="1a15a-105">Você pode definir uma exibição de tabela que exibe todas as propriedades de um objeto ou um subconjunto das propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="1a15a-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="1a15a-106">Uma exibição do modo de exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="1a15a-106">A Table View Display</span></span>

<span data-ttu-id="1a15a-107">O exemplo a seguir mostra como o Windows PowerShell exibe a [ServiceProcess](/dotnet/api/System.ServiceProcess.ServiceController) que é retornado pelo objeto de [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a15a-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="1a15a-108">Para esse objeto, o Windows PowerShell tenha definido uma exibição de tabela que exibe a `Status` propriedade, o `Name` propriedade (essa propriedade é uma propriedade de alias para o `ServiceName` propriedade) e o `DisplayName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="1a15a-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="1a15a-109">Cada linha na tabela representa um objeto retornado pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a15a-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="1a15a-110">Definindo o modo de exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="1a15a-110">Defining the Table View</span></span>

<span data-ttu-id="1a15a-111">O XML a seguir mostra o esquema de exibição de tabela para exibir o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="1a15a-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="1a15a-112">Você deve especificar cada propriedade que você deseja exibir no modo de exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="1a15a-112">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="1a15a-113">Os seguintes elementos XML são usados para definir uma exibição de lista:</span><span class="sxs-lookup"><span data-stu-id="1a15a-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="1a15a-114">O [exibição](./view-element-format.md) é o elemento pai da exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="1a15a-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="1a15a-115">(Isso é o mesmo elemento pai para a lista de modos de exibição do controle ampla e personalizadas).</span><span class="sxs-lookup"><span data-stu-id="1a15a-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="1a15a-116">O [nome](./name-element-for-view-format.md) elemento Especifica o nome da exibição.</span><span class="sxs-lookup"><span data-stu-id="1a15a-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="1a15a-117">Esse elemento é necessário para todas as exibições.</span><span class="sxs-lookup"><span data-stu-id="1a15a-117">This element is required for all views.</span></span>

- <span data-ttu-id="1a15a-118">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que usam o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="1a15a-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="1a15a-119">Esse elemento é necessário.</span><span class="sxs-lookup"><span data-stu-id="1a15a-119">This element is required.</span></span>

- <span data-ttu-id="1a15a-120">O [GroupBy](./groupby-element-for-view-format.md) elemento (não mostrado neste exemplo) que define quando um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="1a15a-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="1a15a-121">Um novo grupo é iniciado sempre que o valor de uma propriedade específica ou um script é alterado.</span><span class="sxs-lookup"><span data-stu-id="1a15a-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="1a15a-122">Esse elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a15a-122">This element is optional.</span></span>

- <span data-ttu-id="1a15a-123">O [controles](./controls-element-for-view-format.md) elemento (não mostrado neste exemplo) define os controles personalizados que são definidos pela exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="1a15a-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="1a15a-124">Controles oferecem uma maneira de especificar como os dados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="1a15a-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="1a15a-125">Esse elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a15a-125">This element is optional.</span></span> <span data-ttu-id="1a15a-126">Um modo de exibição pode definir seus próprios controles personalizados, ou ele pode usar controles comuns que podem ser usados por qualquer modo de exibição no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="1a15a-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="1a15a-127">Para obter mais informações sobre controles personalizados, consulte [criação de controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1a15a-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="1a15a-128">O [HideTableHeaders](./hidetableheaders-element-format.md) elemento (não mostrado neste exemplo) Especifica que a tabela não mostrará todos os rótulos na parte superior da tabela.</span><span class="sxs-lookup"><span data-stu-id="1a15a-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="1a15a-129">Esse elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a15a-129">This element is optional.</span></span>

- <span data-ttu-id="1a15a-130">O [TableControl](./tablecontrol-element-format.md) elemento que define as informações de cabeçalho e linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="1a15a-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="1a15a-131">Semelhante a outros modos de exibição, uma exibição de tabela pode exibir os valores das propriedades do objeto ou valores gerados por scripts.</span><span class="sxs-lookup"><span data-stu-id="1a15a-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="1a15a-132">Definindo cabeçalhos de coluna</span><span class="sxs-lookup"><span data-stu-id="1a15a-132">Defining Column Headers</span></span>

1. <span data-ttu-id="1a15a-133">O [TableHeaders](./tableheaders-element-format.md) elemento e seus elementos filho definem o que é exibido na parte superior da tabela.</span><span class="sxs-lookup"><span data-stu-id="1a15a-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="1a15a-134">O [TableColumnHeader](./tablecolumnheader-element-format.md) elemento define o que é exibido na parte superior de uma coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="1a15a-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="1a15a-135">Especifique esses elementos na ordem em que você deseja que os cabeçalhos exibidos.</span><span class="sxs-lookup"><span data-stu-id="1a15a-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="1a15a-136">Não há nenhum limite para o número desses elementos que você pode usar, mas o número de [TableColumnHeader](./tablecolumnheader-element-format.md) elementos no modo de exibição de tabela devem ser igual ao número de [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) elementos que você usa.</span><span class="sxs-lookup"><span data-stu-id="1a15a-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="1a15a-137">O [rótulo](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica o texto que é exibido.</span><span class="sxs-lookup"><span data-stu-id="1a15a-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="1a15a-138">Esse elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a15a-138">This element is optional.</span></span>

4. <span data-ttu-id="1a15a-139">O [largura](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica a largura (em caracteres) da coluna.</span><span class="sxs-lookup"><span data-stu-id="1a15a-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="1a15a-140">Esse elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a15a-140">This element is optional.</span></span>

5. <span data-ttu-id="1a15a-141">O [alinhamento](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica como o rótulo é exibido.</span><span class="sxs-lookup"><span data-stu-id="1a15a-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="1a15a-142">O rótulo pode ser alinhado à esquerda, para a direita ou centralizado.</span><span class="sxs-lookup"><span data-stu-id="1a15a-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="1a15a-143">Esse elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a15a-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="1a15a-144">Definindo as linhas da tabela</span><span class="sxs-lookup"><span data-stu-id="1a15a-144">Defining the Table Rows</span></span>

<span data-ttu-id="1a15a-145">Modos de exibição de tabela podem fornecer uma ou mais definições que especificam quais dados são exibidos nas linhas da tabela por meio dos filhos de [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="1a15a-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="1a15a-146">Observe que você pode especificar várias definições para as linhas da tabela, mas os cabeçalhos de linhas permanece a mesma, independentemente de qual definição de linha é usada.</span><span class="sxs-lookup"><span data-stu-id="1a15a-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="1a15a-147">Normalmente, uma tabela terá apenas uma definição.</span><span class="sxs-lookup"><span data-stu-id="1a15a-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="1a15a-148">No exemplo a seguir, a exibição fornece uma única definição que exibe os valores de várias propriedades do [Diagnostics? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="1a15a-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="1a15a-149">Uma exibição de tabela pode exibir o valor de uma propriedade ou o valor de um script (não mostrado no exemplo) em suas linhas.</span><span class="sxs-lookup"><span data-stu-id="1a15a-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="1a15a-150">Os seguintes elementos XML podem ser usados para fornecer definições para uma linha:</span><span class="sxs-lookup"><span data-stu-id="1a15a-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="1a15a-151">O [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento e seus elementos filho definem o que é exibido nas linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="1a15a-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="1a15a-152">O [TableRowEntry](./listentry-element-for-listcontrol-format.md) elemento fornece uma definição de linha.</span><span class="sxs-lookup"><span data-stu-id="1a15a-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="1a15a-153">Pelo menos um [TableRowEntry](./listentry-element-for-listcontrol-format.md) é necessária; no entanto, não há nenhum limite máximo ao número de elementos que podem ser adicionados.</span><span class="sxs-lookup"><span data-stu-id="1a15a-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="1a15a-154">Na maioria dos casos, um modo de exibição terá apenas uma definição.</span><span class="sxs-lookup"><span data-stu-id="1a15a-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="1a15a-155">O [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento Especifica os objetos que são exibidos por uma definição específica.</span><span class="sxs-lookup"><span data-stu-id="1a15a-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="1a15a-156">Esse elemento é opcional e é necessário somente quando você define vários [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementos que exibem objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="1a15a-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="1a15a-157">O [encapsular](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) elemento Especifica que o texto que excede a largura da coluna é exibido na próxima linha.</span><span class="sxs-lookup"><span data-stu-id="1a15a-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="1a15a-158">Por padrão, o texto que excede a largura da coluna é truncado.</span><span class="sxs-lookup"><span data-stu-id="1a15a-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="1a15a-159">O [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) elemento define as propriedades ou os scripts cujos valores são exibidos na linha.</span><span class="sxs-lookup"><span data-stu-id="1a15a-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="1a15a-160">O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou cujo valor é exibido na coluna da linha do script.</span><span class="sxs-lookup"><span data-stu-id="1a15a-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="1a15a-161">Um [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="1a15a-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="1a15a-162">A primeira entrada é exibida na primeira coluna, a segunda entrada na segunda coluna e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="1a15a-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="1a15a-163">O [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica a propriedade cujo valor é exibido na linha.</span><span class="sxs-lookup"><span data-stu-id="1a15a-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="1a15a-164">Você deve especificar uma propriedade ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1a15a-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="1a15a-165">O [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica o script cujo valor é exibido na linha.</span><span class="sxs-lookup"><span data-stu-id="1a15a-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="1a15a-166">Você deve especificar um script ou uma propriedade, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1a15a-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="1a15a-167">O [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido.</span><span class="sxs-lookup"><span data-stu-id="1a15a-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="1a15a-168">Esse elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a15a-168">This element is optional.</span></span>

- <span data-ttu-id="1a15a-169">O [alinhamento](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica como o valor da propriedade ou do script é exibido.</span><span class="sxs-lookup"><span data-stu-id="1a15a-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="1a15a-170">O valor pode ser alinhado à esquerda, para a direita ou centralizado.</span><span class="sxs-lookup"><span data-stu-id="1a15a-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="1a15a-171">Esse elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a15a-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="1a15a-172">Definindo os objetos que usam o modo de exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="1a15a-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="1a15a-173">Há duas maneiras de definir quais objetos .NET usam o modo de exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="1a15a-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="1a15a-174">Você pode usar o [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir os objetos que podem ser exibidos por todas as definições de exibição, ou você pode usar o [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento para definir quais objetos são exibidos por um definição específica do modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="1a15a-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="1a15a-175">Na maioria dos casos, um modo de exibição tem apenas uma definição, para que os objetos são normalmente definidos pelo [ViewSelectedBy](./viewselectedby-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="1a15a-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="1a15a-176">O exemplo a seguir mostra como definir os objetos exibidos pela exibição de tabela usando o [ViewSelectedBy](./viewselectedby-element-format.md) e [TypeName](./typename-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="1a15a-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="1a15a-177">Não há nenhum limite para o número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que você pode especificar, e sua ordem não é significativa.</span><span class="sxs-lookup"><span data-stu-id="1a15a-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="1a15a-178">Os seguintes elementos XML podem ser usados para especificar os objetos que são usados pelo modo de exibição de tabela:</span><span class="sxs-lookup"><span data-stu-id="1a15a-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="1a15a-179">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais objetos são exibidos pela exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="1a15a-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="1a15a-180">O [TypeName](./typename-element-for-viewselectedby-format.md) elemento Especifica o objeto .NET que é exibido pelo modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="1a15a-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="1a15a-181">O nome do tipo .NET totalmente qualificado é necessário.</span><span class="sxs-lookup"><span data-stu-id="1a15a-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="1a15a-182">Você deve especificar pelo menos um tipo ou seleção definida para o modo de exibição, mas há um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="1a15a-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="1a15a-183">O exemplo a seguir usa o [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="1a15a-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="1a15a-184">Use conjuntos de seleção em que você tem um conjunto de objetos que são exibidos usando várias exibições, como quando você define uma exibição de lista e uma exibição de tabela para os mesmos objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="1a15a-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="1a15a-185">Para obter mais informações sobre como criar um conjunto de seleção, consulte [definindo conjuntos de seleção](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1a15a-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="1a15a-186">Os seguintes elementos XML podem ser usados para especificar os objetos que são usados pelo modo de exibição de lista:</span><span class="sxs-lookup"><span data-stu-id="1a15a-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="1a15a-187">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais objetos são exibidos pela exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="1a15a-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="1a15a-188">O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento Especifica um conjunto de objetos que podem ser exibidos pela exibição.</span><span class="sxs-lookup"><span data-stu-id="1a15a-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="1a15a-189">Você deve especificar pelo menos um conjunto de seleção ou tipo para o modo de exibição, mas há um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="1a15a-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="1a15a-190">O exemplo a seguir mostra como definir os objetos exibidos por uma definição específica de exibição de tabela usando o [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="1a15a-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="1a15a-191">Usando esse elemento, você pode especificar o nome do tipo .NET do objeto, um conjunto de seleção de objetos ou uma condição de seleção que especifica quando a definição é usada.</span><span class="sxs-lookup"><span data-stu-id="1a15a-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="1a15a-192">Para obter mais informações sobre como criar condições de uma seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1a15a-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1a15a-193">Ao criar várias definições de exibição de tabela que não é possível especificar cabeçalhos de coluna diferente.</span><span class="sxs-lookup"><span data-stu-id="1a15a-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="1a15a-194">Você pode especificar apenas o que é exibido nas linhas da tabela, como quais objetos são exibidos.</span><span class="sxs-lookup"><span data-stu-id="1a15a-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="1a15a-195">Os seguintes elementos XML podem ser usados para especificar os objetos que são usados por uma definição específica de exibição de lista:</span><span class="sxs-lookup"><span data-stu-id="1a15a-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="1a15a-196">O [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento define quais objetos são exibidos pela definição.</span><span class="sxs-lookup"><span data-stu-id="1a15a-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="1a15a-197">O [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento Especifica o objeto .NET que é exibido pela definição.</span><span class="sxs-lookup"><span data-stu-id="1a15a-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="1a15a-198">Ao usar esse elemento, o nome do tipo .NET totalmente qualificado é necessário.</span><span class="sxs-lookup"><span data-stu-id="1a15a-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="1a15a-199">Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="1a15a-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="1a15a-200">O [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (não mostrado) especifica um conjunto de objetos que podem ser exibidos por essa definição.</span><span class="sxs-lookup"><span data-stu-id="1a15a-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="1a15a-201">Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="1a15a-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="1a15a-202">O [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (não mostrado) do elemento Especifica uma condição que deve existir para essa definição a ser usado.</span><span class="sxs-lookup"><span data-stu-id="1a15a-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="1a15a-203">Você deve especificar pelo menos um tipo, conjunto de seleção ou condição de seleção para a definição, mas há um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="1a15a-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="1a15a-204">Para obter mais informações sobre como definir as condições de seleção, consulte [definindo condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1a15a-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="1a15a-205">Usando cadeias de caracteres de formato</span><span class="sxs-lookup"><span data-stu-id="1a15a-205">Using Format Strings</span></span>

<span data-ttu-id="1a15a-206">Cadeias de caracteres de formatação podem ser adicionadas a uma exibição para definir como os dados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="1a15a-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="1a15a-207">O exemplo a seguir mostra como definir uma cadeia de caracteres de formatação para o valor da `StartTime` propriedade.</span><span class="sxs-lookup"><span data-stu-id="1a15a-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="1a15a-208">Os seguintes elementos XML podem ser usados para especificar um padrão de formato:</span><span class="sxs-lookup"><span data-stu-id="1a15a-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="1a15a-209">O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou cujo valor é exibido na coluna da linha do script.</span><span class="sxs-lookup"><span data-stu-id="1a15a-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="1a15a-210">Um [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="1a15a-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="1a15a-211">A primeira entrada é exibida na primeira coluna, a segunda entrada na segunda coluna e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="1a15a-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="1a15a-212">O [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica a propriedade cujo valor é exibido na linha.</span><span class="sxs-lookup"><span data-stu-id="1a15a-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="1a15a-213">Você deve especificar uma propriedade ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1a15a-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="1a15a-214">O [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão de formato que define como o valor da propriedade ou o script é exibido.</span><span class="sxs-lookup"><span data-stu-id="1a15a-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="1a15a-215">No exemplo a seguir, o `ToString` método é chamado para formatar o valor do script.</span><span class="sxs-lookup"><span data-stu-id="1a15a-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="1a15a-216">Scripts podem chamar qualquer método de um objeto.</span><span class="sxs-lookup"><span data-stu-id="1a15a-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="1a15a-217">Portanto, se um objeto tem um método, como `ToString`, que tem parâmetros de formatação, o script pode chamar esse método para formatar o valor de saída do script.</span><span class="sxs-lookup"><span data-stu-id="1a15a-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="1a15a-218">O seguinte elemento XML pode ser usado para chamar o `ToString` método:</span><span class="sxs-lookup"><span data-stu-id="1a15a-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="1a15a-219">O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou cujo valor é exibido na coluna da linha do script.</span><span class="sxs-lookup"><span data-stu-id="1a15a-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="1a15a-220">Um [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="1a15a-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="1a15a-221">A primeira entrada é exibida na primeira coluna, a segunda entrada na segunda coluna e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="1a15a-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="1a15a-222">O [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica o script cujo valor é exibido na linha.</span><span class="sxs-lookup"><span data-stu-id="1a15a-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="1a15a-223">Você deve especificar um script ou uma propriedade, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1a15a-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a15a-224">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="1a15a-224">See Also</span></span>

[<span data-ttu-id="1a15a-225">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="1a15a-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
