---
title: Lista de exibição (Basic) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 1c683693c331ccfaf7355a0dd51801ed6fd39b3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853302"
---
# <a name="list-view-basic"></a><span data-ttu-id="faf8e-102">Exibição de lista (Básica)</span><span class="sxs-lookup"><span data-stu-id="faf8e-102">List View (Basic)</span></span>

<span data-ttu-id="faf8e-103">Este exemplo mostra como implementar uma exibição de lista básica que exibe o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos retornados pela [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="faf8e-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="faf8e-104">Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="faf8e-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="faf8e-105">Este exemplo mostra como implementar uma exibição de lista básica que exibe o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos retornados pela [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="faf8e-105">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="faf8e-106">Para obter mais informações sobre os componentes de uma exibição de lista, consulte [criando uma exibição de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="faf8e-106">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="faf8e-107">Para carregar este arquivo de formatação</span><span class="sxs-lookup"><span data-stu-id="faf8e-107">To load this formatting file</span></span>

1. <span data-ttu-id="faf8e-108">Copie o XML da seção do exemplo deste tópico para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="faf8e-108">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="faf8e-109">Salve o arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="faf8e-109">Save the text file.</span></span> <span data-ttu-id="faf8e-110">Certifique-se de adicionar o `format.ps1xml` extensão para o arquivo de para identificá-lo como um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="faf8e-110">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="faf8e-111">Abra o Windows PowerShell e execute o seguinte comando para carregar o arquivo de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="faf8e-111">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="faf8e-112">Esse arquivo de formatação define a exibição de um objeto que já está definido por um arquivo de formatação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="faf8e-112">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="faf8e-113">Você deve usar o `prependPath` parâmetro quando você executar o cmdlet, e você não pode carregar essa formatação de arquivo como um módulo.</span><span class="sxs-lookup"><span data-stu-id="faf8e-113">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="faf8e-114">Demonstra</span><span class="sxs-lookup"><span data-stu-id="faf8e-114">Demonstrates</span></span>

<span data-ttu-id="faf8e-115">Esse arquivo de formatação demonstra os seguintes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="faf8e-115">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="faf8e-116">O [nome](./name-element-for-view-format.md) elemento para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="faf8e-116">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="faf8e-117">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define quais objetos são exibidos pela exibição.</span><span class="sxs-lookup"><span data-stu-id="faf8e-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="faf8e-118">O [ListControl](./listcontrol-element-format.md) elemento que define a propriedade que é exibida pelo modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="faf8e-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="faf8e-119">O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento que define o que é exibido em uma linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="faf8e-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="faf8e-120">O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento que define qual propriedade é exibida.</span><span class="sxs-lookup"><span data-stu-id="faf8e-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="faf8e-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="faf8e-121">Example</span></span>

<span data-ttu-id="faf8e-122">O XML a seguir define uma exibição de lista que exibe quatro propriedades do [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="faf8e-122">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="faf8e-123">Em cada linha, o nome da propriedade é exibido seguido pelo valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="faf8e-123">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
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
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

<span data-ttu-id="faf8e-124">O exemplo a seguir mostra como o Windows PowerShell exibe o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois que esse arquivo de formato é carregado.</span><span class="sxs-lookup"><span data-stu-id="faf8e-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="faf8e-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="faf8e-125">See Also</span></span>

[<span data-ttu-id="faf8e-126">Exemplos de arquivos de formatação</span><span class="sxs-lookup"><span data-stu-id="faf8e-126">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="faf8e-127">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="faf8e-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
