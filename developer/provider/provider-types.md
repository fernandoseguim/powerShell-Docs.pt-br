---
title: Tipos de provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 37689571eb1650e5991af2e7002cd037ae99dd68
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057953"
---
# <a name="provider-types"></a>Tipos de provedor

Provedores de definem sua funcionalidade básica, alterando a como os cmdlets do provedor (fornecidos pelo Windows PowerShell) executar suas ações. Por exemplo, os provedores podem usar a funcionalidade padrão do `Get-Item` cmdlet, ou eles podem alterar como esse cmdlet funciona ao recuperar itens do repositório de dados. A funcionalidade de provedor descrita neste tópico inclui a funcionalidade definida pela substituição de métodos de interfaces e classes base do provedor específico.

> [!NOTE]
> Para os recursos de provedor que são definidos previamente pelo Windows PowerShell, consulte [recursos do provedor](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6).

## <a name="drive-enabled-providers"></a>Provedores de unidade

Provedores de unidade especificam as unidades padrão disponíveis para o usuário e permitir que o usuário adicionar ou remover unidades. Na maioria dos casos, os provedores são provedores de unidade porque eles requerem alguma unidade padrão para acessar o armazenamento de dados. No entanto, ao escrever seu próprio provedor talvez ou talvez não queira permitir que o usuário criar e remover unidades.

Para criar um provedor de unidade ativada, sua classe de provedor deve derivar de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe ou outra classe que deriva dessa classe. O [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe define os seguintes métodos para as unidades padrão do provedor de implementação e suporte a `New-PSDrive` e `Remove-PSDrive` cmdlets. Na maioria dos casos, para dar suporte a um cmdlet do provedor você deve substituir o método que chama de mecanismo do Windows PowerShell para invocar o cmdlet, como o `NewDrive` método para o `New-PSDrive` cmdlet e, opcionalmente, você pode substituir um segundo método, como `NewDriveDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

- O [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método define as unidades padrão que estão disponíveis para o usuário sempre que o provedor é usado.

- O [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) métodos define como o provedor oferece suporte a `New-PSDrive` cmdlet do provedor. Esse cmdlet permite ao usuário criar unidades para acessar o armazenamento de dados.

- O [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método define como o provedor oferece suporte a `Remove-PSDrive` cmdlet do provedor. Esse cmdlet permite que o usuário remova discos do armazenamento de dados.

## <a name="item-enabled-providers"></a>Provedores de item

Provedores de item de permitir que o usuário obter, definir ou limpar os itens no armazenamento de dados. "item" é um elemento do repositório de dados que o usuário pode acessar ou gerenciar de forma independente. Para criar um provedor de item habilitado, sua classe de provedor deve derivar de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe ou outra classe que deriva dessa classe.

O [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe define os seguintes métodos para a implementação de cmdlets do provedor específico. Na maioria dos casos, para dar suporte a um cmdlet do provedor você deve substituir o método que chama de mecanismo do Windows PowerShell para invocar o cmdlet, como o `ClearItem` método para o `Clear-Item` cmdlet e, opcionalmente, você pode substituir um segundo método, como `ClearItemDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) métodos Definir como o provedor oferece suporte a `Clear-Item` cmdlet do provedor. Esse cmdlet permite que o usuário a ser removido do valor de um item no armazenamento de dados.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) métodos definem como a provedor oferece suporte ao `Get-Item` cmdlet do provedor. Esse cmdlet permite ao usuário recuperar dados do armazenamento de dados.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) métodos definem como a provedor oferece suporte ao `Set-Item` cmdlet do provedor. Esse cmdlet permite ao usuário atualizar os valores de itens no armazenamento de dados.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) e [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) métodos Definir como o provedor oferece suporte a `Invoke-Item` cmdlet do provedor. Esse cmdlet permite que o usuário execute a ação padrão especificada pelo item.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) e [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) métodos Definir como o provedor oferece suporte a `Test-Path` cmdlet do provedor. Esse cmdlet permite que o usuário determinar se todos os elementos de um caminho existem.

  Além dos métodos usados para implementar os cmdlets do provedor, o [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe também define os métodos a seguir:

- O [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) método permite que o usuário use caracteres curinga ao especificar o caminho do provedor.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) é usado para determinar se um caminho é válido sintaticamente e semanticamente para o provedor.

## <a name="container-enabled-providers"></a>Provedores de contêiner

Provedores de contêiner permitem ao usuário gerenciar os itens que são contêineres. Um contêiner é um grupo de itens filho em um item pai comum. Para criar um provedor habilitado por contêiner, sua classe de provedor deve derivar de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe ou outra classe que deriva dessa classe.

> [!IMPORTANT]
> Provedores de contêiner não podem acessar os armazenamentos de dados que contêm os contêineres aninhados. Se um item filho de um contêiner é outro contêiner, você deve implementar um provedor de navegação habilitada.

O [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe define os seguintes métodos para a implementação de cmdlets do provedor específico. Na maioria dos casos, para dar suporte a um cmdlet do provedor você deve substituir o método que chama de mecanismo do Windows PowerShell para invocar o cmdlet, como o `CopyItem` método para o `Copy-Item` cmdlet e, opcionalmente, você pode substituir um segundo método, como `CopyItemDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

- O [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) e [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) os métodos definem como o provedor oferece suporte a `Copy-Item` cmdlet do provedor. Esse cmdlet permite ao usuário copiar um item de um local para outro.

- O [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) e [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) métodos definem como o provedor oferece suporte a `Get-ChildItem` cmdlet do provedor. Esse cmdlet permite ao usuário recuperar os itens filhos do item pai.

- O [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) e [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) métodos definem como o provedor oferece suporte a `Get-ChildItem` cmdlet do provedor se seu `Name` parâmetro for especificado.

- O [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) e [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) os métodos definem como o provedor oferece suporte a `New-Item` cmdlet do provedor. Esse cmdlet permite ao usuário criar novos itens no repositório de dados.

- O [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) e [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) os métodos definem como o provedor oferece suporte a `Remove-Item` cmdlet do provedor. Esse cmdlet permite que o usuário remova itens do repositório de dados.

- O [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) e [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) os métodos definem como o provedor oferece suporte a `Rename-Item` cmdlet do provedor. Esse cmdlet permite que o usuário renomear itens no repositório de dados.

  Além dos métodos usados para implementar os cmdlets do provedor, o [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe também define os métodos a seguir:

- O [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método pode ser usado pela classe de provedor para determinar se um item tem itens filhos.

- O [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) método pode ser usado pela classe de provedor para criar um novo caminho de provedor específico de um caminho especificado.

## <a name="navigation-enabled-providers"></a>Provedores de navegação

Provedores de navegação permitem que o usuário mova itens no repositório de dados. Para criar um provedor de navegação habilitada, sua classe de provedor deve derivar de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

O [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe define os seguintes métodos para a implementação de cmdlets do provedor específico. Na maioria dos casos, para dar suporte a um cmdlet do provedor você deve substituir o método que chama de mecanismo do Windows PowerShell para invocar o cmdlet, como o `MoveItem` método para o `Move-Item` cmdlet e, opcionalmente, você pode substituir um segundo método, como `MoveItemDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) e [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) os métodos definem como o provedor oferece suporte a `Move-Item` cmdlet do provedor. Esse cmdlet permite que o usuário mover um item de um local no armazenamento para outro local.

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método define como o provedor oferece suporte a `Join-Path` cmdlet do provedor. Esse cmdlet permite ao usuário combinar um segmento de caminho pai e filho para criar um caminho de provedor interno.

  Além dos métodos usados para implementar os cmdlets do provedor, o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe também define os métodos a seguir:

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método extrai o nome do nó filho de um caminho.

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método extrai a parte do pai de um caminho.

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) método determina se o item é um contêiner item. Nesse contexto, um contêiner é um grupo de itens filho em um item pai comum.

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) método retorna um caminho para um item que está em relação a um caminho base especificado.

## <a name="content-enabled-providers"></a>Provedores de conteúdo

Provedores de conteúdo é permitir que o usuário limpar, obter ou definir o conteúdo dos itens em um repositório de dados. Por exemplo, o provedor FileSystem permite que você desmarque, obter e definir o conteúdo dos arquivos no sistema de arquivos. Para criar um provedor de conteúdo habilitado, sua classe de provedor deve implementar os métodos do [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

O [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface define os seguintes métodos para a implementação de cmdlets do provedor específico. Na maioria dos casos, para dar suporte a um cmdlet do provedor você deve substituir o método que chama de mecanismo do Windows PowerShell para invocar o cmdlet, como o `ClearContent` método para o `Clear-Content` cmdlet e, opcionalmente, você pode substituir um segundo método, como `ClearContentDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

- O [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) e [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)os métodos definem como o provedor oferece suporte a `Clear-Content` cmdlet do provedor. Esse cmdlet permite que o usuário excluir o conteúdo de um item sem excluir o item.

- O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) e [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) métodos definem como o provedor oferece suporte a `Get-Content` cmdlet do provedor. Esse cmdlet permite ao usuário recuperar o conteúdo de um item. O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método retorna um [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interface que define os métodos usados para ler o conteúdo.

- O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) e [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) métodos definem como o provedor oferece suporte a `Set-Content` cmdlet do provedor. Esse cmdlet permite ao usuário atualizar o conteúdo de um item. O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método retorna um [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interface que define os métodos usados para gravar o conteúdo.

## <a name="property-enabled-providers"></a>Provedores de propriedade

Provedores de propriedade permitem ao usuário gerenciar as propriedades dos itens no repositório de dados. Para criar um provedor de propriedade habilitada, sua classe de provedor deve implementar os métodos do [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfaces. Na maioria dos casos, para dar suporte a um cmdlet do provedor você deve substituir o método que chama de mecanismo do Windows PowerShell para invocar o cmdlet, como o `ClearProperty` método para o cmdlet Clear-propriedade e, opcionalmente, você pode substituir um segundo método, como `ClearPropertyDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

O [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface define os seguintes métodos para a implementação de cmdlets específicos do provedor:

- O [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) e [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) métodos definem como o provedor oferece suporte a `Clear-ItemProperty` cmdlet do provedor. Esse cmdlet permite que o usuário exclua o valor de uma propriedade.

- O [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) e [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)os métodos definem como o provedor oferece suporte a `Get-ItemProperty` cmdlet do provedor. Esse cmdlet permite que o usuário ao recuperar a propriedade de um item.

- O [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) e [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)os métodos definem como o provedor oferece suporte a `Set-ItemProperty` cmdlet do provedor. Esse cmdlet permite ao usuário atualizar as propriedades de um item.

  O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interface define os seguintes métodos para a implementação de cmdlets específicos do provedor:

- O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) métodos definem como o provedor oferece suporte a `Copy-ItemProperty` cmdlet do provedor. Esse cmdlet permite ao usuário copiar uma propriedade e seu valor de um local para outro.

- O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) métodos definem como o provedor oferece suporte a `Move-ItemProperty` cmdlet do provedor. Esse cmdlet permite que o usuário mover uma propriedade e seu valor de um local para outro.

- O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) métodos definem como o provedor oferece suporte a `New-ItemProperty` cmdlet do provedor. Esse cmdlet permite que o usuário criar uma nova propriedade e defina seu valor.

- O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) métodos definem como o provedor oferece suporte a `Remove-ItemProperty` cmdlet. Esse cmdlet permite ao usuário excluir uma propriedade e seu valor.

- O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) métodos definem como o provedor oferece suporte a `Rename-ItemProperty` cmdlet. Esse cmdlet permite que o usuário altere o nome de uma propriedade.

## <a name="see-also"></a>Consulte Também

[Escrevendo um provedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)