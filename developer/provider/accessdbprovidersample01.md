---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854152"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="10017-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="10017-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="10017-103">Este exemplo mostra como declarar uma classe de provedor que deriva diretamente a [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="10017-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="10017-104">Ele é incluído aqui apenas para fins de integridade.</span><span class="sxs-lookup"><span data-stu-id="10017-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="10017-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="10017-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10017-106">Sua classe de provedor será provavelmente derivar de uma das seguintes classes e, possivelmente, implementar outras interfaces de provedor:</span><span class="sxs-lookup"><span data-stu-id="10017-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="10017-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="10017-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="10017-108">Ver [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="10017-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="10017-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="10017-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="10017-110">Ver [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="10017-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="10017-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="10017-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="10017-112">Ver [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="10017-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="10017-113">Para obter mais informações sobre como escolher qual classe de provedor derivam com base nos recursos do provedor, consulte [projetando seu provedor do Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="10017-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="10017-114">Este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="10017-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="10017-115">Declarando o `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="10017-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="10017-116">Definindo uma classe de provedor que deriva diretamente a [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="10017-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="10017-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10017-117">Example</span></span>

<span data-ttu-id="10017-118">Este exemplo mostra como definir uma classe de provedor e como declarar o `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="10017-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a><span data-ttu-id="10017-119">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="10017-119">See Also</span></span>

[<span data-ttu-id="10017-120">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="10017-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="10017-121">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="10017-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="10017-122">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="10017-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="10017-123">Criando o provedor do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="10017-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)