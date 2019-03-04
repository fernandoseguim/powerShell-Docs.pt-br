---
title: (Rótulos) de exibição de lista | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 2bb62ab3e4fa1db9b3af8c82eb9035aa4f3e31c0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860122"
---
# <a name="list-view-labels"></a><span data-ttu-id="fa8c8-102">Exibição de lista (rótulos)</span><span class="sxs-lookup"><span data-stu-id="fa8c8-102">List View (Labels)</span></span>

<span data-ttu-id="fa8c8-103">Este exemplo mostra como implementar uma exibição de lista que exibe um rótulo personalizado para cada linha da lista.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="fa8c8-104">Este modo de exibição de lista exibe as propriedades do [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) que é retornado pelo objeto de [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="fa8c8-105">Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="fa8c8-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="fa8c8-106">Este exemplo mostra como implementar uma exibição de lista que exibe um rótulo personalizado para cada linha da lista.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-106">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="fa8c8-107">Este modo de exibição de lista exibe as propriedades do [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) que é retornado pelo objeto de [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="fa8c8-108">Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="fa8c8-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="fa8c8-109">Para carregar este arquivo de formatação</span><span class="sxs-lookup"><span data-stu-id="fa8c8-109">To load this formatting file</span></span>

1. <span data-ttu-id="fa8c8-110">Copie o XML da seção do exemplo deste tópico para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="fa8c8-111">Salve o arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-111">Save the text file.</span></span> <span data-ttu-id="fa8c8-112">Certifique-se de adicionar o `format.ps1xml` extensão para o arquivo de para identificá-lo como um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="fa8c8-113">Abra o Windows PowerShell e execute o seguinte comando para carregar o arquivo de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="fa8c8-114">Esse arquivo de formatação define a exibição de um objeto que já está definido por um arquivo de formatação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="fa8c8-115">Você deve usar o `prependPath` parâmetro quando você executar o cmdlet, e você não pode carregar essa formatação de arquivo como um módulo.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fa8c8-116">Demonstra</span><span class="sxs-lookup"><span data-stu-id="fa8c8-116">Demonstrates</span></span>

<span data-ttu-id="fa8c8-117">Esse arquivo de formatação demonstra os seguintes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="fa8c8-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="fa8c8-118">O [nome](./name-element-for-view-format.md) elemento para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="fa8c8-119">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define quais objetos são exibidos pela exibição.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="fa8c8-120">O [ListControl](./listcontrol-element-format.md) elemento que define a propriedade que é exibida pelo modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-120">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="fa8c8-121">O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento que define o que é exibido em uma linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-121">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="fa8c8-122">O [rótulo](./label-element-for-listitem-for-listcontrol-format.md) elemento que define o que é exibido em uma linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-122">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="fa8c8-123">O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento que define qual propriedade é exibida.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="fa8c8-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa8c8-124">Example</span></span>

<span data-ttu-id="fa8c8-125">O XML a seguir define uma exibição de lista que exibe um rótulo personalizado em cada linha.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-125">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="fa8c8-126">Nesse caso, o rótulo inclui o nome da propriedade com cada letra maiuscula e a palavra "propriedade".</span><span class="sxs-lookup"><span data-stu-id="fa8c8-126">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="fa8c8-127">Em cada linha, o nome da propriedade é exibido seguido pelo valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-127">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="fa8c8-128">O exemplo a seguir mostra como o Windows PowerShell exibe o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois que esse arquivo de formato é carregado.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-128">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="fa8c8-129">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="fa8c8-129">See Also</span></span>

[<span data-ttu-id="fa8c8-130">Exemplos de arquivos de formatação</span><span class="sxs-lookup"><span data-stu-id="fa8c8-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="fa8c8-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa8c8-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
