---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859402"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="7dceb-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="7dceb-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="7dceb-103">Este exemplo mostra como substituir a [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) métodos para dar suporte a chamadas para o `Get-Item` e `Set-Item` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7dceb-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="7dceb-104">A classe de provedor nessa amostra deriva de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="7dceb-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7dceb-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="7dceb-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7dceb-106">Sua classe de provedor será provavelmente derivar de uma das seguintes classes e, possivelmente, implementar outras interfaces de provedor:</span><span class="sxs-lookup"><span data-stu-id="7dceb-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="7dceb-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="7dceb-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="7dceb-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="7dceb-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="7dceb-109">Ver [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="7dceb-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="7dceb-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="7dceb-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="7dceb-111">Ver [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="7dceb-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="7dceb-112">Para obter mais informações sobre como escolher qual classe de provedor derivam com base nos recursos do provedor, consulte [projetando seu provedor do Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="7dceb-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="7dceb-113">Este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7dceb-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="7dceb-114">Declarando o `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="7dceb-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="7dceb-115">Definindo uma classe de provedor que deriva de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="7dceb-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="7dceb-116">Substituindo o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método para alterar o comportamento do `New-PSDrive` cmdlet, permitindo que o usuário criar novas unidades.</span><span class="sxs-lookup"><span data-stu-id="7dceb-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="7dceb-117">(Este exemplo mostra como adicionar parâmetros dinâmicos para a `New-PSDrive` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="7dceb-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="7dceb-118">Substituindo o [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método para dar suporte à remoção de unidades existentes.</span><span class="sxs-lookup"><span data-stu-id="7dceb-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="7dceb-119">Substituindo o [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para alterar o comportamento do `Get-Item` cmdlet, permitindo que o usuário recuperar itens do repositório de dados.</span><span class="sxs-lookup"><span data-stu-id="7dceb-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="7dceb-120">(Este exemplo mostra como adicionar parâmetros dinâmicos para a `Get-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="7dceb-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="7dceb-121">Substituindo o [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método para alterar o comportamento do `Set-Item` cmdlet, permitindo que o usuário atualizar os itens no armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="7dceb-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="7dceb-122">(Este exemplo mostra como adicionar parâmetros dinâmicos para a `Get-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="7dceb-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="7dceb-123">Substituindo o [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método para alterar o comportamento do `Test-Path` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7dceb-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="7dceb-124">(Este exemplo mostra como adicionar parâmetros dinâmicos para a `Test-Path` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="7dceb-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="7dceb-125">Substituindo o [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método para determinar se o caminho fornecido é válido.</span><span class="sxs-lookup"><span data-stu-id="7dceb-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="7dceb-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7dceb-126">Example</span></span>

<span data-ttu-id="7dceb-127">Este exemplo mostra como substituir os métodos necessários para obter e definir os itens em um de dados Microsoft Access base.</span><span class="sxs-lookup"><span data-stu-id="7dceb-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="7dceb-128">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="7dceb-128">See Also</span></span>

[<span data-ttu-id="7dceb-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7dceb-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="7dceb-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7dceb-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="7dceb-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7dceb-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="7dceb-132">Criando o provedor do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dceb-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)