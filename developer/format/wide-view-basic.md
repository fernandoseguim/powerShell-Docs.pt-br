---
title: Exibição ampla (Basic) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860102"
---
# <a name="wide-view-basic"></a><span data-ttu-id="25d09-102">Exibição ampla (Básica)</span><span class="sxs-lookup"><span data-stu-id="25d09-102">Wide View (Basic)</span></span>

<span data-ttu-id="25d09-103">Este exemplo mostra como implementar uma exibição ampla básica que exibe o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos retornados pelo `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25d09-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="25d09-104">Para obter mais informações sobre os componentes de uma exibição ampla, consulte [criando uma exibição ampla](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="25d09-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="25d09-105">Para carregar este arquivo de formatação</span><span class="sxs-lookup"><span data-stu-id="25d09-105">To load this formatting file</span></span>

1. <span data-ttu-id="25d09-106">Copie o XML da seção do exemplo deste tópico para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="25d09-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="25d09-107">Salve o arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="25d09-107">Save the text file.</span></span> <span data-ttu-id="25d09-108">Certifique-se de adicionar o `format.ps1xml` extensão para o arquivo de para identificá-lo como um arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="25d09-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="25d09-109">Abra o Windows PowerShell e execute o seguinte comando para carregar o arquivo de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="25d09-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="25d09-110">Esse arquivo de formatação define a exibição de um objeto que já está definido por um arquivo de formatação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25d09-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="25d09-111">Você deve usar o `prependPath` parâmetro quando você executar o cmdlet, e você não pode carregar essa formatação de arquivo como um módulo.</span><span class="sxs-lookup"><span data-stu-id="25d09-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="25d09-112">Demonstra</span><span class="sxs-lookup"><span data-stu-id="25d09-112">Demonstrates</span></span>

<span data-ttu-id="25d09-113">Esse arquivo de formatação demonstra os seguintes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="25d09-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="25d09-114">O [nome](./name-element-for-view-format.md) elemento para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="25d09-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="25d09-115">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define quais objetos são exibidos pela exibição.</span><span class="sxs-lookup"><span data-stu-id="25d09-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="25d09-116">O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento que define a propriedade que é exibida pelo modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="25d09-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="25d09-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25d09-117">Example</span></span>

<span data-ttu-id="25d09-118">O XML a seguir define uma exibição ampla que exibe o valor de [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) propriedade.</span><span class="sxs-lookup"><span data-stu-id="25d09-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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

<span data-ttu-id="25d09-119">O exemplo a seguir mostra como o Windows PowerShell exibe o [ServiceProcess? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois que esse arquivo de formato é carregado.</span><span class="sxs-lookup"><span data-stu-id="25d09-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="25d09-120">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="25d09-120">See Also</span></span>

[<span data-ttu-id="25d09-121">Exemplos de arquivos de formatação</span><span class="sxs-lookup"><span data-stu-id="25d09-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="25d09-122">Gravar um arquivo de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="25d09-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
