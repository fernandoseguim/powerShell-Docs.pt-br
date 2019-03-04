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
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Este exemplo mostra como substituir a [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) métodos para dar suporte a chamadas para o `Get-Item` e `Set-Item` cmdlets. A classe de provedor nessa amostra deriva de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

## <a name="demonstrates"></a>Demonstra

> [!IMPORTANT]
> Sua classe de provedor será provavelmente derivar de uma das seguintes classes e, possivelmente, implementar outras interfaces de provedor:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe. Ver [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe. Ver [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Para obter mais informações sobre como escolher qual classe de provedor derivam com base nos recursos do provedor, consulte [projetando seu provedor do Windows PowerShell](./provider-types.md).

Este exemplo demonstra o seguinte:

- Declarando o `CmdletProvider` atributo.

- Definindo uma classe de provedor que deriva de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

- Substituindo o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método para alterar o comportamento do `New-PSDrive` cmdlet, permitindo que o usuário criar novas unidades. (Este exemplo mostra como adicionar parâmetros dinâmicos para a `New-PSDrive` cmdlet.)

- Substituindo o [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método para dar suporte à remoção de unidades existentes.

- Substituindo o [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para alterar o comportamento do `Get-Item` cmdlet, permitindo que o usuário recuperar itens do repositório de dados. (Este exemplo mostra como adicionar parâmetros dinâmicos para a `Get-Item` cmdlet.)

- Substituindo o [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método para alterar o comportamento do `Set-Item` cmdlet, permitindo que o usuário atualizar os itens no armazenamento de dados. (Este exemplo mostra como adicionar parâmetros dinâmicos para a `Get-Item` cmdlet.)

- Substituindo o [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método para alterar o comportamento do `Test-Path` cmdlet. (Este exemplo mostra como adicionar parâmetros dinâmicos para a `Test-Path` cmdlet.)

- Substituindo o [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método para determinar se o caminho fornecido é válido.

## <a name="example"></a>Exemplo

Este exemplo mostra como substituir os métodos necessários para obter e definir os itens em um de dados Microsoft Access base.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Criando o provedor do Windows PowerShell](./provider-types.md)