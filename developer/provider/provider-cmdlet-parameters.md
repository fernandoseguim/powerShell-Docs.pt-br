---
title: Parâmetros de cmdlet do provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: d0fb81ee1ca1f80e216c021e1bd64771b8de4dc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860112"
---
# <a name="provider-cmdlet-parameters"></a>Parâmetros de cmdlet do provedor

Cmdlets do provedor vêm com um conjunto de parâmetros estáticos que estão disponíveis para todos os provedores que dão suporte ao cmdlet, parâmetros, bem como dinâmicos que são adicionados quando o usuário Especifica um valor determinado para determinados parâmetros estáticos do cmdlet do provedor.

## <a name="provider-cmdlet-static-parameters"></a>Parâmetros de Cmdlet estática do provedor

Parâmetros estáticos são definidos pelo Windows PowerShell. Um grande conjunto desses parâmetros é implementado pelo Windows PowerShell para fornecer consistência em todos os provedores e fornecer uma experiência de desenvolvimento mais simples. Exemplos desses parâmetros incluem o `literalPath`, `exclude`, e `include` parâmetros da `Get-Item` cmdlet. Um conjunto menor desses parâmetros pode ser substituído para fornecer ações que são específicas para seu provedor. Exemplos desses parâmetros incluem o `Path` e `Value` parâmetro do `Set-Item` cmdlet. Aqui está uma lista de parâmetros que podem ser substituídas para os cmdlets do provedor.

`Clear-Content` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` parâmetro do `Clear-Content` cmdlet Implementando o [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)método.

`Clear-Item` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` parâmetro do `Clear-Item` cmdlet Implementando a [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) método.

`Clear-ItemProperty` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` e `Name` parâmetros da `Clear-ItemProperty` cmdlet Implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método.

`Copy-Item` cmdlet, você pode definir como o provedor usará os valores passados para o `Path`, `Destination`, e `Recurse` parâmetros da `Copy-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método.

Cmdlet Get-ChildItems você pode definir como o provedor usará os valores passados para o `Path` e `Recures` parâmetros da `Get-ChildItem` cmdlet Implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) e [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) métodos.

`Get-Content` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` parâmetro do `Get-Content` cmdlet Implementando o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método.

`Get-Item` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` parâmetro do `Get-Item` cmdlet Implementando a [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método.

`Get-ItemProperty` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` e `Name` parâmetros da `Get-ItemProperty` cmdlet Implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) método.

`Invoke-Item` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` parâmetro do `Invoke-Item` cmdlet Implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)método.

`Move-Item` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` e `Destination` parâmetros da `Move-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método.

`New-Item` cmdlet, você pode definir como o provedor usará os valores passados para o `Path`, `ItemType`, e `Value` parâmetros da `New-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método.

`New-ItemProperty` cmdlet, você pode definir como o provedor usará os valores passados para o `Path`, `Name`, `PropertyType`, e `Value` parâmetros da `New-ItemProperty` cmdlet Implementando o [ Microsoft.Powershell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) método.

`Remove-Item` Você pode definir como o provedor usará os valores passados para o `Path` e `Recurse` parâmetros da `Remove-Item` cmdlet Implementando o [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método.

`Remove-ItemProperty` Você pode definir como o provedor usará os valores passados para o `Path` e `Name` parâmetros da `Remove-ItemProperty` cmdlet Implementando o [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) método.

`Rename-Item` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` e `NewName` parâmetros da `Rename-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método.

`Rename-ItemProperty` Você pode definir como o provedor usará os valores passados para o `Path`, `NewName`, e `Name` parâmetros da `Rename-ItemProperty` cmdlet Implementando o [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) método.

`Set-Content` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` parâmetro do `Set-Content` cmdlet Implementando o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método.

`Set-Item` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` e `Value` parâmetros da `Set-Item` cmdlet Implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método.

`Set-ItemProperty` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` e `Value` parâmetros da `Set-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método.

`Test-Path` cmdlet, você pode definir como o provedor usará os valores passados para o `Path` parâmetro do `Test-Path` cmdlet Implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)método.

Além disso, você não pode especificar as características desses parâmetros, como se eles são opcionais ou obrigatórias, nem pode fornecer esses parâmetros de um alias ou especificar qualquer um dos atributos de validação. Por outro lado, você pode especificar características de parâmetro nos cmdlets autônomo por meio de atributos, como o `Parameters` atributo.

## <a name="provider-cmdlet-dynamic-parameters"></a>Parâmetros de Cmdlet dinâmico do provedor

Parâmetros dinâmicos para provedores de cmdlet são semelhantes aos provedores de dinâmicos para cmdlets autônomo. Em ambos os casos, os parâmetros são adicionados ao cmdlet quando o usuário Especifica um valor determinado para um dos parâmetros padrão, como o `path` parâmetro. No entanto, nem todos os parâmetros estáticos podem ser usados para disparar a adição de parâmetros dinâmicos. Para obter mais informações sobre parâmetros dinâmicos, consulte [parâmetros dinâmicos do provedor Cmdlet](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Consulte Também

[Parâmetros de Cmdlet dinâmico do provedor](./provider-cmdlet-dynamic-parameters.md)

[Escrevendo um provedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)