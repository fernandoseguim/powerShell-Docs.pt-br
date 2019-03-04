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
ms.openlocfilehash: e3289e9336b863b5e0998a2beb29353c82a31f79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856702"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="a920d-102">Escrever um provedor de itens</span><span class="sxs-lookup"><span data-stu-id="a920d-102">Writing an item provider</span></span>

<span data-ttu-id="a920d-103">Este tópico descreve como implementar os métodos de um provedor do Windows PowerShell que acessar e manipulam itens no armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="a920d-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="a920d-104">Para ser capaz de acessar itens, um provedor deve derivar de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="a920d-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="a920d-105">O provedor nos exemplos neste tópico usa um banco de dados como seu armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="a920d-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="a920d-106">Há vários métodos e classes auxiliares que são usadas para interagir com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a920d-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="a920d-107">Para o exemplo completo que inclui os métodos auxiliares, consulte [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="a920d-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="a920d-108">Para obter mais informações sobre provedores do Windows PowerShell, consulte [visão geral do provedor do Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a920d-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="a920d-109">Implementando os métodos de item</span><span class="sxs-lookup"><span data-stu-id="a920d-109">Implementing item methods</span></span>

<span data-ttu-id="a920d-110">O [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe expõe vários métodos que podem ser usados para acessar e manipular os itens em um repositório de dados.</span><span class="sxs-lookup"><span data-stu-id="a920d-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="a920d-111">Para obter uma lista completa desses métodos, consulte [ItemCmdletProvider métodos](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="a920d-111">For a complete list of these methods, see [ItemCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span></span> <span data-ttu-id="a920d-112">Neste exemplo, podemos implementar quatro desses métodos.</span><span class="sxs-lookup"><span data-stu-id="a920d-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="a920d-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) obtém um item em um caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="a920d-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="a920d-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) define o valor do item especificado.</span><span class="sxs-lookup"><span data-stu-id="a920d-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="a920d-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) verifica se um item existe no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="a920d-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="a920d-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) verifica um caminho para ver se ele é mapeado para um local no armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="a920d-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="a920d-117">Este tópico se baseia nas informações da [início rápido do Windows PowerShell provedor](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="a920d-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="a920d-118">Este tópico aborda os conceitos básicos de como configurar um projeto do provedor ou como implementar os métodos herdados do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe que criar e remover unidades.</span><span class="sxs-lookup"><span data-stu-id="a920d-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="a920d-119">Declarar a classe de provedor</span><span class="sxs-lookup"><span data-stu-id="a920d-119">Declaring the provider class</span></span>

<span data-ttu-id="a920d-120">Declarar o provedor a derivar as [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) de classe e decorá-la com o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="a920d-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="a920d-121">Implementando GetItem</span><span class="sxs-lookup"><span data-stu-id="a920d-121">Implementing GetItem</span></span>

<span data-ttu-id="a920d-122">O [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) é chamado pelo mecanismo do PowerShell, quando um usuário chama o [Microsoft.Powershell.Commands.Get Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet no seu provedor.</span><span class="sxs-lookup"><span data-stu-id="a920d-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.Powershell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet on your provider.</span></span> <span data-ttu-id="a920d-123">O método retorna o item no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="a920d-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="a920d-124">O exemplo de banco de dados de acesso, o método verifica se o item é a unidade em si, uma tabela no banco de dados ou uma linha no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a920d-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="a920d-125">O método envia o item para o mecanismo do PowerShell chamando o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.</span><span class="sxs-lookup"><span data-stu-id="a920d-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="a920d-126">Implementando SetItem</span><span class="sxs-lookup"><span data-stu-id="a920d-126">Implementing SetItem</span></span>

<span data-ttu-id="a920d-127">O [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método é chamado pelas chamadas de mecanismo do PowerShell quando um usuário chama o [Microsoft.Powershell.Commands.Set Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet .</span><span class="sxs-lookup"><span data-stu-id="a920d-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.Powershell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet.</span></span> <span data-ttu-id="a920d-128">Ele define o valor do item no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="a920d-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="a920d-129">O exemplo de banco de dados de acesso, faz sentido para definir o valor de um item somente se esse item é uma linha, portanto, o método gerará [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) quando o item não é uma linha.</span><span class="sxs-lookup"><span data-stu-id="a920d-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="a920d-130">Implementando ItemExists</span><span class="sxs-lookup"><span data-stu-id="a920d-130">Implementing ItemExists</span></span>

<span data-ttu-id="a920d-131">O [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método é chamado pelo mecanismo do PowerShell, quando um usuário chama o [Microsoft.Powershell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a920d-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.Powershell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span></span> <span data-ttu-id="a920d-132">O método determina se há um item no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="a920d-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="a920d-133">Se o item existir, o método passa de volta para o mecanismo do PowerShell chamando [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="a920d-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="a920d-134">Implementando IsValidPath</span><span class="sxs-lookup"><span data-stu-id="a920d-134">Implementing IsValidPath</span></span>

<span data-ttu-id="a920d-135">O [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método verifica se o caminho especificado é sintaticamente válido para o provedor atual.</span><span class="sxs-lookup"><span data-stu-id="a920d-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="a920d-136">Ele não verifica se existe um item no caminho.</span><span class="sxs-lookup"><span data-stu-id="a920d-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="a920d-137">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a920d-137">Next steps</span></span>

<span data-ttu-id="a920d-138">Um provedor típico do mundo real é capaz de dar suporte a itens que contêm outros itens e de mover itens de um caminho para outro dentro da unidade.</span><span class="sxs-lookup"><span data-stu-id="a920d-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="a920d-139">Para obter um exemplo de um provedor que dá suporte a contêineres, consulte [escrevendo um provedor de contêiner](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a920d-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="a920d-140">Para obter um exemplo de um provedor que dá suporte a itens de movimentação, consulte [escrevendo um provedor de navegação](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a920d-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a920d-141">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a920d-141">See Also</span></span>

[<span data-ttu-id="a920d-142">Escrevendo um provedor de contêiner</span><span class="sxs-lookup"><span data-stu-id="a920d-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="a920d-143">Escrevendo um provedor de navegação</span><span class="sxs-lookup"><span data-stu-id="a920d-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="a920d-144">Visão geral de provedor do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="a920d-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)