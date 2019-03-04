---
title: Exemplos de provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853122"
---
# <a name="provider-samples"></a>Amostras de provedor

Esta seção inclui exemplos de provedores que acessam um banco de dados do Microsoft Access. Esses exemplos incluem as classes de provedor que derivam de todas as classes de provedor base.

## <a name="in-this-section"></a>Nesta seção

Esta seção inclui os seguintes tópicos:

[Exemplo de AccessDBProviderSample01](./accessdbprovidersample01.md) Este exemplo mostra como declarar a classe de provedor que deriva diretamente de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe. Ele é incluído aqui apenas para fins de integridade.

[AccessDBProviderSample02](./accessdbprovidersample02.md) Este exemplo mostra como substituir o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) métodos para dar suporte a chamadas para o `New-PSDrive` e `Remove-PSDrive` cmdlets. A classe de provedor nessa amostra deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.

[AccessDBProviderSample03](./accessdbprovidersample03.md) Este exemplo mostra como substituir o [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) métodos para dar suporte a chamadas para o `Get-Item` e `Set-Item` cmdlets. A classe de provedor nessa amostra deriva de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

[AccessDBProviderSample04](./accessdbprovidersample04.md) Este exemplo mostra como substituir os métodos de contêiner para dar suporte a chamadas para o `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlets. Esses métodos devem ser implementados quando o armazenamento de dados contiver itens que são contêineres. Um contêiner é um grupo de itens filho em um item pai comum. A classe de provedor nessa amostra deriva de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

[AccessDBProviderSample05](./accessdbprovidersample05.md) Este exemplo mostra como substituir os métodos de contêiner para dar suporte a chamadas para o `Move-Item` e `Join-Path` cmdlets. Esses métodos deverão ser implementados quando o usuário precisar mover itens dentro de um contêiner e se o armazenamento de dados contiver contêineres aninhados. A classe de provedor nessa amostra deriva de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

[AccessDBProviderSample06](./accessdbprovidersample06.md) Este exemplo mostra como substituir os métodos de conteúdo para dar suporte a chamadas para o `Clear-Content`, `Get-Content`, e `Set-Content` cmdlets. Esses métodos devem ser implementados quando o usuário precisa gerenciar o conteúdo dos itens no armazenamento de dados. A classe de provedor nessa amostra deriva de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe e implementa o [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

## <a name="see-also"></a>Consulte Também

[Escrevendo um provedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)