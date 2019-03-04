---
title: Cmdlets do provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854762"
---
# <a name="provider-cmdlets"></a>Cmdlets do provedor

Os cmdlets que o usuário pode executar para gerenciar um armazenamento de dados são chamados de cmdlets do provedor. Para dar suporte a esses cmdlets, você precisará substituir alguns dos métodos definidos por classes de provedor base e interfaces.

## <a name="provider-cmdlets"></a>Cmdlets do provedor

Aqui estão os cmdlets do provedor que pode ser executados pelo usuário:

### <a name="psdrive-cmdlets"></a>Cmdlets de PSDrive

- `Get-PSDrive`: Esse cmdlet retorna que o Windows PowerShell unidades na sessão atual. Você não precisa substituir todos os métodos para dar suporte a esse cmdlet.

- `New-PSDrive`: Esse cmdlet permite ao usuário criar unidades do Windows PowerShell para acessar o armazenamento de dados. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) métodos.

- `Remove-PSDrive`: Esse cmdlet permite que o usuário remova unidades do Windows PowerShell que acessam o armazenamento de dados. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método.

### <a name="item-cmdlets"></a>Cmdlets de item

- `Clear-Item`: Esse cmdlet permite que o usuário remova o valor de um item no armazenamento de dados. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) e [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) métodos.

- `Copy-Item`: Esse cmdlet permite ao usuário copiar um item de um local para outro. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) e [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) métodos.

- `Get-Item`: Esse cmdlet permite ao usuário recuperar dados do armazenamento de dados. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) métodos.

- `Get-ChildItem`: Esse cmdlet permite ao usuário recuperar os itens filhos do item pai. Para dar suporte a esse cmdlet, substitua os métodos a seguir:

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: Esse cmdlet permite que o usuário execute a ação padrão especificada pelo item. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) e [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) métodos.

- `Move-Item`: Esse cmdlet permite que o usuário mover um item de um local para outro local. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) e [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)metod.

- `New-ItemProperty`: Esse cmdlet permite que o usuário crie um novo item no armazenamento de dados.

- `Remove-Item`: Esse cmdlet permite que o usuário remova itens do repositório de dados. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) e [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) métodos.

- `Rename-Item`: Esse cmdlet permite que o usuário renomear itens no repositório de dados. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) e [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) métodos.

- `Set-Item`: Esse cmdlet permite ao usuário atualizar os valores de itens no armazenamento de dados. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) métodos.

### <a name="item-content-cmdlets"></a>Cmdlets de conteúdo do item

- `Add-Content`: Esse cmdlet permite ao usuário adicionar conteúdo a um item.

- `Clear-Content`: Esse cmdlet permite que o usuário excluir o conteúdo de um item sem excluir o item. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) e [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) métodos.

- `Get-Content`: Esse cmdlet permite ao usuário recuperar o conteúdo de um item. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) e [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) métodos. O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método retorna um [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interface que define os métodos usados para ler o conteúdo.

- `Set-Content`: Esse cmdlet permite ao usuário atualizar o conteúdo de um item. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) e [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) métodos. O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método retorna um [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interface que define os métodos usados para gravar o conteúdo.

### <a name="item-property-cmdlets"></a>Cmdlets de propriedade do item

- `Clear-ItemProperty`: Esse cmdlet permite que o usuário exclua o valor de uma propriedade. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) e [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) métodos.

- `Copy-ItemProperty`: Esse cmdlet permite ao usuário copiar uma propriedade e seu valor de um local para outro. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) métodos.

- `Get-ItemProperty`: Este cmdlet recupera as propriedades de um item. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) e [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) métodos.

- `Move-ItemProperty`: Esse cmdlet permite que o usuário mover uma propriedade e seu valor de um local para outro. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) métodos.

- `New-ItemProperty`: Esse cmdlet permite que o usuário criar uma nova propriedade e defina seu valor. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) métodos.

- `Remove-ItemProperty`: Esse cmdlet permite ao usuário excluir uma propriedade e seu valor. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) métodos.

- `Rename-ItemProperty`: Esse cmdlet permite que o usuário altere o nome de uma propriedade. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) métodos.

- `Set-ItemProperty`: Esse cmdlet permite ao usuário atualizar as propriedades de um item. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) e [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) métodos.

### <a name="location-cmdlets"></a>Cmdlets de local

- `Get-Location`: Recupera informações sobre o local de trabalho atual. Você não precisa substituir todos os métodos para dar suporte a esse cmdlet.

- `Pop-Location`: Esse cmdlet altera o local atual para o local mais recentemente inserido na pilha. Você não precisa substituir todos os métodos para dar suporte a esse cmdlet.

- `Push-Location`: Esse cmdlet adiciona o local atual na parte superior de uma lista de locais (uma "pilha"). Você não precisa substituir todos os métodos para dar suporte a esse cmdlet.

- `Set-Location`: Esse cmdlet define o local de trabalho atual em um local especificado. Você não precisa substituir todos os métodos para dar suporte a esse cmdlet.

### <a name="path-cmdlets"></a>Cmdlets de caminho

- `Join-Path`: Esse cmdlet permite ao usuário combinar um segmento de caminho pai e filho para criar um caminho de provedor interno. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método.

- `Convert-Path`: Esse cmdlet converte um caminho de um caminho do Windows PowerShell em um caminho de provedor do Windows PowerShell.

- `Split-Path`: Retorna a parte especificada de um caminho.

- `Resolve-Path`: Resolve os caracteres curinga em um caminho e exibe o conteúdo do caminho.

- `Test-Path`: Esse cmdlet determina se todos os elementos de um caminho existem. Para dar suporte a esse cmdlet, substituir os [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) e [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) métodos.

### <a name="psprovider-cmdlets"></a>Cmdlets de PSProvider

- `Get-PSProvider`: Esse cmdlet retorna informações sobre os provedores disponíveis na sessão. Você não precisa substituir todos os métodos para dar suporte a esse cmdlet.