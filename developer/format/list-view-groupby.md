---
title: (GroupBy) de exibição de lista | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: ad7ea457fe0f67bfa41f6bf81f36d4b2e4a76cb3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860142"
---
# <a name="list-view-groupby"></a><span data-ttu-id="28c4d-102">Exibição de lista (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="28c4d-102">List View (GroupBy)</span></span>

<span data-ttu-id="28c4d-103">Este exemplo mostra como implementar uma exibição de lista que separa as linhas da lista em grupos.</span><span class="sxs-lookup"><span data-stu-id="28c4d-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="28c4d-104">Este modo de exibição de lista exibe as propriedades do [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos retornados pela [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="28c4d-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="28c4d-105">Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="28c4d-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="28c4d-106">Este exemplo mostra como implementar uma exibição de lista que separa as linhas da lista em grupos.</span><span class="sxs-lookup"><span data-stu-id="28c4d-106">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="28c4d-107">Este modo de exibição de lista exibe as propriedades do [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos retornados pela [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="28c4d-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="28c4d-108">Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="28c4d-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="28c4d-109">Para carregar este arquivo de formatação</span><span class="sxs-lookup"><span data-stu-id="28c4d-109">To load this formatting file</span></span>

1. <span data-ttu-id="28c4d-110">Copie o XML da seção do exemplo deste tópico para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="28c4d-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="28c4d-111">Salve o arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="28c4d-111">Save the text file.</span></span> <span data-ttu-id="28c4d-112">Certifique-se de adicionar o `format.ps1xml` extensão para o arquivo de para identificá-lo como um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="28c4d-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="28c4d-113">Abra o Windows PowerShell e execute o seguinte comando para carregar o arquivo de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="28c4d-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="28c4d-114">Esse arquivo de formatação define a exibição de um objeto que já está definido por um arquivo de formatação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28c4d-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="28c4d-115">Você deve usar o `prependPath` parâmetro quando você executar o cmdlet, e você não pode carregar essa formatação de arquivo como um módulo.</span><span class="sxs-lookup"><span data-stu-id="28c4d-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="28c4d-116">Demonstra</span><span class="sxs-lookup"><span data-stu-id="28c4d-116">Demonstrates</span></span>

<span data-ttu-id="28c4d-117">Esse arquivo de formatação demonstra os seguintes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="28c4d-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="28c4d-118">O [nome](./name-element-for-view-format.md) elemento para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="28c4d-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="28c4d-119">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define quais objetos são exibidos pela exibição.</span><span class="sxs-lookup"><span data-stu-id="28c4d-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="28c4d-120">O [GroupBy](./viewselectedby-element-format.md) elemento que define como um novo grupo de objetos é exibido.</span><span class="sxs-lookup"><span data-stu-id="28c4d-120">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="28c4d-121">O [ListControl](./listcontrol-element-format.md) elemento que define a propriedade que é exibida pelo modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="28c4d-121">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="28c4d-122">O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento que define o que é exibido em uma linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="28c4d-122">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="28c4d-123">O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento que define qual propriedade é exibida.</span><span class="sxs-lookup"><span data-stu-id="28c4d-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="28c4d-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28c4d-124">Example</span></span>

<span data-ttu-id="28c4d-125">O XML a seguir define uma exibição de lista que começa um novo grupo sempre que o valor da [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) alterações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="28c4d-125">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="28c4d-126">Quando cada grupo é iniciado, um rótulo personalizado é exibido que inclui o novo valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="28c4d-126">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
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

<span data-ttu-id="28c4d-127">O exemplo a seguir mostra como o Windows PowerShell exibe o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois que esse arquivo de formato é carregado.</span><span class="sxs-lookup"><span data-stu-id="28c4d-127">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="28c4d-128">As linhas em branco adicionadas antes e depois o rótulo de grupo são adicionadas automaticamente pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28c4d-128">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="28c4d-129">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="28c4d-129">See Also</span></span>

[<span data-ttu-id="28c4d-130">Exemplos de arquivos de formatação</span><span class="sxs-lookup"><span data-stu-id="28c4d-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="28c4d-131">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="28c4d-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
