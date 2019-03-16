---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057613"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Este exemplo mostra como substituir os métodos de contêiner para dar suporte a chamadas para o `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlets. Esses métodos devem ser implementados quando o armazenamento de dados contiver itens que são contêineres. Um contêiner é um grupo de itens filho em um item pai comum. A classe de provedor nessa amostra deriva de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

## <a name="demonstrates"></a>Demonstra

> [!IMPORTANT]
> Sua classe de provedor provavelmente será derivado do [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Este exemplo demonstra o seguinte:

- Declarando o `CmdletProvider` atributo.

- Definindo uma classe de provedor que deriva de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

- Substituindo o [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método para alterar o comportamento do `Copy-Item` cmdlet que permite ao usuário copiar itens de um local para outro. (Este exemplo mostra como adicionar parâmetros dinâmicos para a `Copy-Item` cmdlet.)

- Substituindo o [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para alterar o comportamento do cmdlet Get-ChildItems, que permite ao usuário recuperar os itens filhos do item pai . (Este exemplo mostra como adicionar parâmetros dinâmicos para o cmdlet Get-ChildItems.)

- Substituindo o [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para alterar o comportamento do cmdlet Get-ChildItems quando o `Name` parâmetro do cmdlet é especificado.

- Substituindo o [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para alterar o comportamento do `New-Item` cmdlet, que permite que o usuário adicione itens ao repositório de dados. (Este exemplo mostra como adicionar parâmetros dinâmicos para a `New-Item` cmdlet.)

- Substituindo o [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método para alterar o comportamento do `Remove-Item` cmdlet. (Este exemplo mostra como adicionar parâmetros dinâmicos para a `Remove-Item` cmdlet.)

## <a name="example"></a>Exemplo

Este exemplo mostra como substituir os métodos necessários para copiar, criar e remover itens, bem como métodos para obter o filho itens de um item pai.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Criando o provedor do Windows PowerShell](./provider-types.md)