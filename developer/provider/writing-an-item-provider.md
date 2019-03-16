---
title: Escrevendo um provedor de item | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058175"
---
# <a name="writing-an-item-provider"></a>Escrever um provedor de itens

Este tópico descreve como implementar os métodos de um provedor do Windows PowerShell que acessar e manipulam itens no armazenamento de dados. Para ser capaz de acessar itens, um provedor deve derivar de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

O provedor nos exemplos neste tópico usa um banco de dados como seu armazenamento de dados. Há vários métodos e classes auxiliares que são usadas para interagir com o banco de dados. Para o exemplo completo que inclui os métodos auxiliares, consulte [AccessDBProviderSample03](./accessdbprovidersample03.md)

Para obter mais informações sobre provedores do Windows PowerShell, consulte [visão geral do provedor do Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementando os métodos de item

O [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe expõe vários métodos que podem ser usados para acessar e manipular os itens em um repositório de dados. Para obter uma lista completa desses métodos, consulte [ItemCmdletProvider métodos](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx). Neste exemplo, podemos implementar quatro desses métodos. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) obtém um item em um caminho especificado. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) define o valor do item especificado. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) verifica se um item existe no caminho especificado. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) verifica um caminho para ver se ele é mapeado para um local no armazenamento de dados.

> [!NOTE]
> Este tópico se baseia nas informações da [início rápido do Windows PowerShell provedor](./windows-powershell-provider-quickstart.md). Este tópico aborda os conceitos básicos de como configurar um projeto do provedor ou como implementar os métodos herdados do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe que criar e remover unidades.

### <a name="declaring-the-provider-class"></a>Declarar a classe de provedor

Declarar o provedor a derivar as [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) de classe e decorá-la com o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implementando GetItem

O [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) é chamado pelo mecanismo do PowerShell, quando um usuário chama o [Microsoft.PowerShell.Commands.Get Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet no seu provedor. O método retorna o item no caminho especificado. O exemplo de banco de dados de acesso, o método verifica se o item é a unidade em si, uma tabela no banco de dados ou uma linha no banco de dados. O método envia o item para o mecanismo do PowerShell chamando o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>Implementando SetItem

O [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método é chamado pelas chamadas de mecanismo do PowerShell quando um usuário chama o [Microsoft.PowerShell.Commands.Set Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet . Ele define o valor do item no caminho especificado.

O exemplo de banco de dados de acesso, faz sentido para definir o valor de um item somente se esse item é uma linha, portanto, o método gerará [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) quando o item não é uma linha.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>Implementando ItemExists

O [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método é chamado pelo mecanismo do PowerShell, quando um usuário chama o [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet. O método determina se há um item no caminho especificado. Se o item existir, o método passa de volta para o mecanismo do PowerShell chamando [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>Implementando IsValidPath

O [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método verifica se o caminho especificado é sintaticamente válido para o provedor atual. Ele não verifica se existe um item no caminho.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>Próximas etapas

Um provedor típico do mundo real é capaz de dar suporte a itens que contêm outros itens e de mover itens de um caminho para outro dentro da unidade. Para obter um exemplo de um provedor que dá suporte a contêineres, consulte [escrevendo um provedor de contêiner](./writing-a-container-provider.md). Para obter um exemplo de um provedor que dá suporte a itens de movimentação, consulte [escrevendo um provedor de navegação](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Consulte Também

[Escrevendo um provedor de contêiner](./writing-a-container-provider.md)

[Escrevendo um provedor de navegação](./writing-a-navigation-provider.md)

[Visão geral de provedor do PowerShell do Windows](./windows-powershell-provider-overview.md)