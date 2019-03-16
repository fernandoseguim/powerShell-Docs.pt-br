---
title: Guia de início rápido do Windows PowerShell provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054910"
---
# <a name="windows-powershell-provider-quickstart"></a>Início rápido do provedor do Windows PowerShell

Este tópico explica como criar um provedor do Windows PowerShell que tem a funcionalidade básica de criação de uma nova unidade. Para obter informações gerais sobre os provedores, consulte [visão geral do provedor do Windows PowerShell](./windows-powershell-provider-overview.md). Para obter exemplos de provedores com funcionalidade mais completa, consulte [Provider Samples](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Escrevendo um provedor básico

É a funcionalidade básica de mais de um provedor do Windows PowerShell criar e remover unidades. Neste exemplo, podemos implementar o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) métodos do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. Você também verá como declarar uma classe de provedor.

Quando você escreve um provedor, você pode especificar unidades-unidades padrão que são criadas automaticamente quando o provedor está disponível. Você também pode definir um método para criar novas unidades que usam esse provedor.

Os exemplos fornecidos neste tópico se baseiam os [AccessDBProviderSample02](./accessdbprovidersample02.md) amostra, que é parte de um exemplo maior que representa um banco de dados como uma unidade do Windows PowerShell.

### <a name="setting-up-the-project"></a>Configuração do projeto

No Visual Studio, crie um projeto de biblioteca de classes chamado AccessDBProviderSample. Conclua as seguintes etapas para configurar seu projeto para que o Windows PowerShell começará e o provedor será carregado para a sessão, quando você compilar e iniciar seu projeto.

##### <a name="configure-the-provider-project"></a>Configurar o projeto de provedor

1. Adicione o assembly Automation como uma referência ao seu projeto.

2. Clique em **projeto > Propriedades AccessDBProviderSample > Depurar**. Na **projeto de início**, clique em **Iniciar programa externo**e navegue até o executável do Windows PowerShell (normalmente c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. Sob **opções de inicialização**, digite o seguinte para o **argumentos de linha de comando** caixa: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Declarar a classe de provedor

Nosso provedor deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. A maioria dos provedores que fornecem a funcionalidade real (acessar e manipular itens, navegando o armazenamento de dados e obter e definir o conteúdo dos itens) derivam o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

Além de especificar que a classe deriva [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), você deve decorá-la com o [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) conforme mostrado no exemplo.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a>Implementando NewDrive

O [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método é chamado pelo mecanismo do Windows PowerShell, quando um usuário chama o [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)especificando o nome do seu provedor de cmdlet. O parâmetro PSDriveInfo é passado pelo mecanismo do Windows PowerShell e o método retorna a nova unidade ao mecanismo do Windows PowerShell. Esse método deve ser declarado dentro da classe criada acima.

O método primeiro verifica para garantir que o objeto de unidade e a raiz da unidade que foram passados existem, retornando `null` se qualquer um deles não fizer isso. Ele usa um construtor da classe AccessDBPSDriveInfo interno para criar uma nova unidade e representa uma conexão para o banco de dados do Access a unidade.

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

A seguir está a classe de AccessDBPSDriveInfo interna que inclui o construtor usado para criar uma nova unidade e contém as informações de estado para a unidade.

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a>Implementando RemoveDrive

O [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método é chamado pelo mecanismo do Windows PowerShell, quando um usuário chama o [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet. O método neste provedor fecha a conexão para o banco de dados do Access.

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```