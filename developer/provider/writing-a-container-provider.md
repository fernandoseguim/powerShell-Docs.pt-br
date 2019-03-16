---
title: Escrevendo um provedor de contêiner | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 524fd900-c0fe-4d13-87f2-14903a8fd5a4
caps.latest.revision: 5
ms.openlocfilehash: bf0a73267b3cad1f50d983ebed53318ec98180e0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056457"
---
# <a name="writing-a-container-provider"></a>Escrever um provedor de contêineres

Este tópico descreve como implementar os métodos de um provedor do Windows PowerShell que dão suporte a itens que contêm outros itens, como pastas no provedor do sistema de arquivos. Para ser capaz de dar suporte a contêineres, um provedor deve derivar de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

O provedor nos exemplos neste tópico usa um banco de dados como seu armazenamento de dados. Há vários métodos e classes auxiliares que são usadas para interagir com o banco de dados. Para o exemplo completo que inclui os métodos auxiliares, consulte [AccessDBProviderSample04](./accessdbprovidersample04.md).

Para obter mais informações sobre provedores do Windows PowerShell, consulte [visão geral do provedor do Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-container-methods"></a>Implementando os métodos de contêiner

O [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe implementa métodos que dão suporte a contêineres e criar, copiar e remover itens. Para obter uma lista completa desses métodos, consulte [ContainerCmdletProvider métodos](http://msdn.microsoft.com/library/system.management.automation.provider.containercmdletprovider_methods\(v=vs.85\).aspx).

> [!NOTE]
> Este tópico se baseia nas informações da [início rápido do Windows PowerShell provedor](./windows-powershell-provider-quickstart.md). Este tópico aborda os conceitos básicos de como configurar um projeto do provedor ou como implementar os métodos herdados do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe que criar e remover unidades. Este tópico também aborda como implementar os métodos expostos pelos [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe. Para obter um exemplo que mostra como implementar os cmdlets de item, consulte [escrevendo um provedor de item](./writing-an-item-provider.md).

### <a name="declaring-the-provider-class"></a>Declarar a classe de provedor

Declarar o provedor a derivar as [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) de classe e decorá-la com o [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
   {

   }
```

### <a name="implementing-getchilditems"></a>Implementando GetChildItems

As chamadas de mecanismo do PowerShell a [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método quando um usuário chama o [Microsoft.PowerShell.Commands.Get Childitem](/dotnet/api/Microsoft.PowerShell.Commands.Get-ChildItem) cmdlet. Esse método obtém os itens que são filhos do item no caminho especificado.

No exemplo de banco de dados de acesso, o comportamento do [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método depende do tipo do item especificado. Se o item é a unidade, em seguida, os filhos são tabelas, e o método retorna o conjunto de tabelas do banco de dados. Se o item especificado for uma tabela, os filhos são as linhas da tabela. Se o item for uma linha, em seguida, ele não tiver nenhum filho, e o método retornará apenas essa linha. Todos os itens filhos são enviados para o mecanismo do PowerShell, o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.

```csharp
protected override void GetChildItems(string path, bool recurse)
       {
           // If path represented is a drive then the children in the path are
           // tables. Hence all tables in the drive represented will have to be
           // returned
           if (PathIsDrive(path))
           {
               foreach (DatabaseTableInfo table in GetTables())
               {
                   WriteItemObject(table, path, true);

                   // if the specified item exists and recurse has been set then
                   // all child items within it have to be obtained as well
                   if (ItemExists(path) && recurse)
                   {
                       GetChildItems(path + pathSeparator + table.Name, recurse);
                   }
               } // foreach (DatabaseTableInfo...
           } // if (PathIsDrive...
           else
           {
               // Get the table name, row number and type of path from the
               // path specified
               string tableName;
               int rowNumber;

               PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

               if (type == PathType.Table)
               {
                   // Obtain all the rows within the table
                   foreach (DatabaseRowInfo row in GetRows(tableName))
                   {
                       WriteItemObject(row, path + pathSeparator + row.RowNumber,
                               false);
                   } // foreach (DatabaseRowInfo...
               }
               else if (type == PathType.Row)
               {
                   // In this case the user has directly specified a row, hence
                   // just give that particular row
                   DatabaseRowInfo row = GetRow(tableName, rowNumber);
                   WriteItemObject(row, path + pathSeparator + row.RowNumber,
                               false);
               }
               else
               {
                   // In this case, the path specified is not valid
                   ThrowTerminatingInvalidPathException(path);
               }
           } // else
       }
```

### <a name="implementing-getchildnames"></a>Implementando GetChildNames

O [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método é semelhante ao [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método, exceto que ele retorna apenas a propriedade de nome dos itens e não os próprios itens.

```csharp
protected override void GetChildNames(string path,
                                     ReturnContainers returnContainers)
       {
           // If the path represented is a drive, then the child items are
           // tables. get the names of all the tables in the drive.
           if (PathIsDrive(path))
           {
               foreach (DatabaseTableInfo table in GetTables())
               {
                   WriteItemObject(table.Name, path, true);
               } // foreach (DatabaseTableInfo...
           } // if (PathIsDrive...
           else
           {
               // Get type, table name and row number from path specified
               string tableName;
               int rowNumber;

               PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

               if (type == PathType.Table)
               {
                   // Get all the rows in the table and then write out the
                   // row numbers.
                   foreach (DatabaseRowInfo row in GetRows(tableName))
                   {
                       WriteItemObject(row.RowNumber, path, false);
                   } // foreach (DatabaseRowInfo...
               }
               else if (type == PathType.Row)
               {
                   // In this case the user has directly specified a row, hence
                   // just give that particular row
                   DatabaseRowInfo row = GetRow(tableName, rowNumber);

                   WriteItemObject(row.RowNumber, path, false);
               }
               else
               {
                   ThrowTerminatingInvalidPathException(path);
               }
           } // else
       }
```

### <a name="implementing-newitem"></a>Implementando NewItem

O [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método cria um novo item do tipo especificado no caminho especificado. O mecanismo do PowerShell chama esse método quando um usuário chama o [Microsoft.PowerShell.Commands.New Item](/dotnet/api/Microsoft.PowerShell.Commands.New-Item) cmdlet.

Neste exemplo, o método implementa a lógica para determinar o caminho e o tipo correspondem. Ou seja, apenas uma tabela pode ser criada diretamente na unidade (o banco de dados), e apenas uma linha pode ser criada em uma tabela. Se o caminho especificado e o tipo de item não corresponderem dessa forma, o método gera uma exceção.

```csharp
protected override void NewItem(string path, string type,
                                   object newItemValue)
       {
           string tableName;
           int rowNumber;

           PathType pt = GetNamesFromPath(path, out tableName, out rowNumber);

           if (pt == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           // Check if type is either "table" or "row", if not throw an
           // exception
           if (!String.Equals(type, "table", StringComparison.OrdinalIgnoreCase)
               && !String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
           {
               WriteError(new ErrorRecord
                                 (new ArgumentException("Type must be either a table or row"),
                                     "CannotCreateSpecifiedObject",
                                        ErrorCategory.InvalidArgument,
                                             path
                                  )
                         );

               throw new ArgumentException("This provider can only create items of type \"table\" or \"row\"");
           }

           // Path type is the type of path of the container. So if a drive
           // is specified, then a table can be created under it and if a table
           // is specified, then a row can be created under it. For the sake of
           // completeness, if a row is specified, then if the row specified by
           // the path does not exist, a new row is created. However, the row
           // number may not match as the row numbers only get incremented based
           // on the number of rows

           if (PathIsDrive(path))
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   // Execute command using ODBC connection to create a table
                   try
                   {
                       // create the table using an sql statement
                       string newTableName = newItemValue.ToString();

                       if (!TableNameIsValid(newTableName))
                       {
                           return;
                       }
                       string sql = "create table " + newTableName
                                            + " (ID INT)";

                       // Create the table using the Odbc connection from the
                       // drive.
                       AccessDBPSDriveInfo di = this.PSDriveInfo as AccessDBPSDriveInfo;

                       if (di == null)
                       {
                           return;
                       }
                       OdbcConnection connection = di.Connection;

                       if (ShouldProcess(newTableName, "create"))
                       {
                           OdbcCommand cmd = new OdbcCommand(sql, connection);
                           cmd.ExecuteScalar();
                       }
                   }
                   catch (Exception ex)
                   {
                       WriteError(new ErrorRecord(ex, "CannotCreateSpecifiedTable",
                                 ErrorCategory.InvalidOperation, path)
                                 );
                   }
               } // if (String...
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   throw new
                       ArgumentException("A row cannot be created under a database, specify a path that represents a Table");
               }
           }// if (PathIsDrive...
           else
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   if (rowNumber < 0)
                   {
                       throw new
                           ArgumentException("A table cannot be created within another table, specify a path that represents a database");
                   }
                   else
                   {
                       throw new
                           ArgumentException("A table cannot be created inside a row, specify a path that represents a database");
                   }
               } //if (String.Equals....
               // if path specified is a row, create a new row
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   // The user is required to specify the values to be inserted
                   // into the table in a single string separated by commas
                   string value = newItemValue as string;

                   if (String.IsNullOrEmpty(value))
                   {
                       throw new
                           ArgumentException("Value argument must have comma separated values of each column in a row");
                   }
                   string[] rowValues = value.Split(',');

                   OdbcDataAdapter da = GetAdapterForTable(tableName);

                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   if (rowValues.Length != table.Columns.Count)
                   {
                       string message =
                            String.Format(CultureInfo.CurrentCulture,
                                            "The table has {0} columns and the value specified must have so many comma separated values",
                                                table.Columns.Count);

                       throw new ArgumentException(message);
                   }

                   if (!Force && (rowNumber >=0 && rowNumber < table.Rows.Count))
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                                        "The row {0} already exists. To create a new row specify row number as {1}, or specify path to a table, or use the -Force parameter",
                                                            rowNumber, table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   if (rowNumber > table.Rows.Count)
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                            "To create a new row specify row number as {0}, or specify path to a table",
                                                table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   // Create a new row and update the row with the input
                   // provided by the user
                   DataRow row = table.NewRow();
                   for (int i = 0; i < rowValues.Length; i++)
                   {
                       row[i] = rowValues[i];
                   }
                   table.Rows.Add(row);

                   if (ShouldProcess(tableName, "update rows"))
                   {
                       // Update the table from memory back to the data source
                       da.Update(ds, tableName);
                   }

               }// else if (String...
           }// else ...

       }
```

### <a name="implementing-copyitem"></a>Implementação de CopyItem

O [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) copia o item especificado no caminho especificado. O mecanismo do PowerShell chama esse método quando um usuário chama o [Microsoft.PowerShell.Commands.Copy Item](/dotnet/api/Microsoft.PowerShell.Commands.Copy-Item) cmdlet. Esse método também pode ser recursivo, copiando todos os itens filhos, além do próprio item.

Da mesma forma que o [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método, esse método executa a lógica para certificar-se de que o item especificado é do tipo correto para o caminho para o qual ele está sendo copiado. Por exemplo, se o caminho de destino for uma tabela, o item a ser copiado deve ser uma linha.

```csharp
protected override void CopyItem(string path, string copyPath, bool recurse)
       {
           string tableName, copyTableName;
           int rowNumber, copyRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);
           PathType copyType = GetNamesFromPath(copyPath, out copyTableName, out copyRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(copyPath);
           }

           // Get the table and the table to copy to
           OdbcDataAdapter da = GetAdapterForTable(tableName);
           if (da == null)
           {
               return;
           }

           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           OdbcDataAdapter cda = GetAdapterForTable(copyTableName);
           if (cda == null)
           {
               return;
           }

           DataSet cds = GetDataSetForTable(cda, copyTableName);
           DataTable copyTable = GetDataTable(cds, copyTableName);

           // if source represents a table
           if (type == PathType.Table)
           {
               // if copyPath does not represent a table
               if (copyType != PathType.Table)
               {
                   ArgumentException e = new ArgumentException("Table can only be copied on to another table location");

                   WriteError(new ErrorRecord(e, "PathNotValid",
                       ErrorCategory.InvalidArgument, copyPath));

                   throw e;
               }

               // if table already exists then force parameter should be set
               // to force a copy
               if (!Force && GetTable(copyTableName) != null)
               {
                   throw new ArgumentException("Specified path already exists");
               }

               for (int i = 0; i < table.Rows.Count; i++)
               {
                   DataRow row = table.Rows[i];
                   DataRow copyRow = copyTable.NewRow();

                   copyRow.ItemArray = row.ItemArray;
                   copyTable.Rows.Add(copyRow);
               }
           } // if (type == ...
           // if source represents a row
           else
           {
               if (copyType == PathType.Row)
               {
                   if (!Force && (copyRowNumber < copyTable.Rows.Count))
                   {
                       throw new ArgumentException("Specified path already exists.");
                   }

                   DataRow row = table.Rows[rowNumber];
                   DataRow copyRow = null;

                   if (copyRowNumber < copyTable.Rows.Count)
                   {
                       // copy to an existing row
                       copyRow = copyTable.Rows[copyRowNumber];
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                   }
                   else if (copyRowNumber == copyTable.Rows.Count)
                   {
                       // copy to the next row in the table that will
                       // be created
                       copyRow = copyTable.NewRow();
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                       copyTable.Rows.Add(copyRow);
                   }
                   else
                   {
                       // attempting to copy to a nonexistent row or a row
                       // that cannot be created now - throw an exception
                       string message = String.Format(CultureInfo.CurrentCulture,
                                             "The item cannot be specified to the copied row. Specify row number as {0}, or specify a path to the table.",
                                                    table.Rows.Count);

                       throw new ArgumentException(message);
                   }
               }
               else
               {
                   // destination path specified represents a table,
                   // create a new row and copy the item
                   DataRow copyRow = copyTable.NewRow();
                   copyRow.ItemArray = table.Rows[rowNumber].ItemArray;
                   copyRow[0] = GetNextID(copyTable);
                   copyTable.Rows.Add(copyRow);
               }
           }

           if (ShouldProcess(copyTableName, "CopyItems"))
           {
               cda.Update(cds, copyTableName);
           }

       } //CopyItem
```

### <a name="implementing-removeitem"></a>Implementando RemoveItem

O [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método Remove o item no caminho especificado. O mecanismo do PowerShell chama esse método quando um usuário chama o [Microsoft.PowerShell.Commands.Remove Item](/dotnet/api/Microsoft.PowerShell.Commands.Remove-Item) cmdlet.

```csharp
protected override void RemoveItem(string path, bool recurse)
       {
           string tableName;
           int rowNumber = 0;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               // if recurse flag has been specified, delete all the rows as well
               if (recurse)
               {
                   OdbcDataAdapter da = GetAdapterForTable(tableName);
                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   for (int i = 0; i < table.Rows.Count; i++)
                   {
                       table.Rows[i].Delete();
                   }

                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       da.Update(ds, tableName);
                       RemoveTable(tableName);
                   }
               }//if (recurse...
               else
               {
                   // Remove the table
                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       RemoveTable(tableName);
                   }
               }
           }
           else if (type == PathType.Row)
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               table.Rows[rowNumber].Delete();

               if (ShouldProcess(path, "RemoveItem"))
               {
                   da.Update(ds, tableName);
               }
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

## <a name="next-steps"></a>Próximas etapas

Um provedor típico do mundo real é capaz de mover itens de um caminho para outro dentro da unidade. Para obter um exemplo de um provedor que dá suporte a itens de movimentação, consulte [escrevendo um provedor de navegação](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Consulte Também

[Escrevendo um provedor de navegação](./writing-a-navigation-provider.md)

[Visão geral de provedor do PowerShell do Windows](./windows-powershell-provider-overview.md)