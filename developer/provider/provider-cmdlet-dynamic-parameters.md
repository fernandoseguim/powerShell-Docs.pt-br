---
title: Parâmetros dinâmicos do provedor cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058225"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Parâmetros dinâmicos de cmdlet do provedor

Provedores podem definir parâmetros dinâmicos que são adicionados a um cmdlet do provedor quando o usuário Especifica um valor determinado para um dos parâmetros estáticos do cmdlet. Por exemplo, um provedor pode adicionar diferentes parâmetros dinâmicos com base no caminho do qual o usuário Especifica quando eles chamam o `Get-Item` ou `Set-Item` cmdlets do provedor.

## <a name="dynamic-parameter-methods"></a>Métodos de parâmetro dinâmico

Parâmetros dinâmicos são definidos pela implementação de um dos métodos de parâmetro dinâmico, como o [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) e [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)metod. Esses métodos retornam um objeto que tem propriedades públicas que são decoradas com atributos semelhantes dos cmdlets autônomo. Aqui está um exemplo de uma implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) método obtido do provedor do certificado:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

Ao contrário dos parâmetros estáticos dos cmdlets do provedor, você pode especificar as características desses parâmetros da mesma forma que os parâmetros são definidos nos cmdlets autônomo. Aqui está um exemplo de uma classe de parâmetro dinâmico feito pelo provedor do certificado:

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>Parâmetros dinâmicos

Aqui está uma lista dos parâmetros estáticos que podem ser usados para adicionar parâmetros dinâmicos.

`Clear-Content` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` parâmetro do cmdlet Clear-Clear Implementando o [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) método.

`Clear-Item` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` parâmetro do `Clear-Item` cmdlet Implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) método.

`Clear-ItemProperty` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` parâmetro do `Clear-ItemProperty` cmdlet Implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) método.

`Copy-Item` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path`, `Destination`, e `Recurse` parâmetros da `Copy-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) método.

Cmdlet Get-ChildItems, você pode definir parâmetros dinâmicos que são disparados pela `Path` e `Recurse` parâmetros da `Get-ChildItem` cmdlet Implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) e [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) métodos.

`Get-Content` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` parâmetro do `Get-Content` cmdlet Implementando o [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) método.

`Get-Item` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` parâmetro do `Get-Item` cmdlet Implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) método.

`Get-ItemProperty` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` e `Name` parâmetros da `Get-ItemProperty` cmdlet Implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) método.

`Invoke-Item` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` parâmetro do `Invoke-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) método.

`Move-Item` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` e `Destination` parâmetros da `Move-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) método.

`New-Item` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path`, `ItemType`, e `Value` parâmetros da `New-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) método.

`New-ItemProperty` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path`, `Name`, `PropertyType`, e `Value` parâmetros da `New-ItemProperty` cmdlet Implementando o [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) método.

`New-PSDrive` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto retornado pela `New-PSDrive` cmdlet Implementando o [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) método.

`Remove-Item` Você pode definir parâmetros dinâmicos que são disparados pela `Path` e `Recurse` parâmetros da `Remove-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) método.

`Remove-ItemProperty` Você pode definir parâmetros dinâmicos que são disparados pela `Path` e `Name` parâmetros da `Remove-ItemProperty` cmdlet Implementando o [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) método.

`Rename-Item` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` e `NewName` parâmetros da `Rename-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) método.

`Rename-ItemProperty` Você pode definir parâmetros dinâmicos que são disparados pela `Path`, `Name`, e `NewName` parâmetros da `Rename-ItemProperty` cmdlet Implementando o [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) método.

`Set-Content` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` parâmetro do `Set-Content` cmdlet Implementando o [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) método.

`Set-Item` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` e `Value` parâmetros da `Set-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) método.

`Set-ItemProperty` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` e `Value` parâmetros da `Set-Item` cmdlet Implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) método.

`Test-Path` cmdlet, você pode definir parâmetros dinâmicos que são disparados pela `Path` parâmetro do `Test-Path` cmdlet Implementando o [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) método.

## <a name="see-also"></a>Consulte Também

[Escrevendo um provedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)