---
title: Exibição ampla (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861622"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="c957e-102">Exibição ampla (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="c957e-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="c957e-103">Este exemplo mostra como implementar uma exibição ampla que exibe os grupos de [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos retornados pelo `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c957e-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="c957e-104">Para obter mais informações sobre os componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="c957e-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="c957e-105">Para carregar este arquivo de formatação</span><span class="sxs-lookup"><span data-stu-id="c957e-105">To load this formatting file</span></span>

1. <span data-ttu-id="c957e-106">Copie o XML da seção do exemplo deste tópico para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="c957e-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="c957e-107">Salve o arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="c957e-107">Save the text file.</span></span> <span data-ttu-id="c957e-108">Certifique-se de adicionar o `format.ps1xml` extensão para o arquivo de para identificá-lo como um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="c957e-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="c957e-109">Abra o Windows PowerShell e execute o seguinte comando para carregar o arquivo de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="c957e-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="c957e-110">Esse arquivo de formatação define a exibição de um objeto que já está definido por um arquivos de formatação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c957e-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="c957e-111">Você deve usar o `prependPath` parâmetro quando você executar o cmdlet, e você não pode carregar essa formatação de arquivo como um módulo.</span><span class="sxs-lookup"><span data-stu-id="c957e-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c957e-112">Demonstra</span><span class="sxs-lookup"><span data-stu-id="c957e-112">Demonstrates</span></span>

<span data-ttu-id="c957e-113">Esse arquivo de formatação demonstra os seguintes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="c957e-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="c957e-114">O [nome](./name-element-for-view-format.md) elemento para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="c957e-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="c957e-115">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define quais objetos são exibidos pela exibição.</span><span class="sxs-lookup"><span data-stu-id="c957e-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="c957e-116">O [GroupBy](./groupby-element-for-view-format.md) elemento que define quando um novo grupo é exibido.</span><span class="sxs-lookup"><span data-stu-id="c957e-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="c957e-117">O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento que define a propriedade que é exibida pelo modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="c957e-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="c957e-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c957e-118">Example</span></span>

<span data-ttu-id="c957e-119">O XML a seguir define uma exibição ampla que exibe os grupos de objetos.</span><span class="sxs-lookup"><span data-stu-id="c957e-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="c957e-120">Cada novo grupo é iniciado quando o valor de [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) alterações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c957e-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="c957e-121">O exemplo a seguir mostra como o Windows PowerShell exibe o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois que esse arquivo de formato é carregado.</span><span class="sxs-lookup"><span data-stu-id="c957e-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="c957e-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c957e-122">See Also</span></span>

[<span data-ttu-id="c957e-123">Exemplos de arquivos de formatação</span><span class="sxs-lookup"><span data-stu-id="c957e-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="c957e-124">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="c957e-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
