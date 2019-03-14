---
title: Criar um provedor de contêiner do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: de75e19abc0ee440e724fba7bf578ce240fbf2df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795446"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Criar um provedor de contêineres do Windows PowerShell

Este tópico descreve como criar um provedor do Windows PowerShell que pode funcionar em armazenamentos de dados de várias camadas. Para esse tipo de armazenamento de dados, do armazenamento de nível superior contém os itens de raiz e cada nível subsequente é conhecido como um nó de itens filho. Ao permitir que o usuário trabalhar em nós filho, um usuário pode interagir hierarquicamente por meio do armazenamento de dados.

Provedores que podem trabalhar em repositórios de dados de vários níveis são chamados de provedores de contêiner do Windows PowerShell. No entanto, lembre-se de que um provedor de contêiner do Windows PowerShell pode ser usado somente quando há um contêiner (não há contêineres aninhados) com itens nele. Se houver contêineres aninhados, você deve implementar um provedor de navegação do Windows PowerShell. Para obter mais informações sobre a implementação do provedor de navegação do Windows PowerShell, consulte [criando um provedor de navegação do Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Você pode baixar o C# arquivo de origem (AccessDBSampleProvider04.cs) para este provedor usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.
>
> Para obter mais informações sobre outras implementações do provedor do Windows PowerShell, consulte [projetando seu provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md).

O provedor de contêiner do Windows PowerShell descrito aqui define o banco de dados como seu único contêiner, com as tabelas e linhas do banco de dados definidos como itens do contêiner.

> [!CAUTION]
> Lembre-se de que este design pressupõe um banco de dados que tem um campo com a ID de nome e o tipo do campo é LongInteger.

Aqui está uma lista das seções neste tópico. Se você estiver familiarizado com a gravação de um provedor de contêiner do Windows PowerShell, leia essas informações na ordem em que ele é exibido. No entanto, se você estiver familiarizado com a gravação de um provedor de contêiner do Windows PowerShell, vá diretamente para as informações que você precisa.

- [Definindo uma classe de provedor de contêiner do Windows PowerShell](#Defining-a-Windows-PowerShell-Container-Provider-Class)

- [Definindo a funcionalidade de Base](#defining-base-functionality)

- [Recuperando itens filho](#Retrieving-Child-Items)

- [Anexando parâmetros dinâmicos para a `Get-ChildItem` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet)

- [Recuperando nomes de itens filho](#Retrieving-Child-Item-Names)

- [Anexando parâmetros dinâmicos para a `Get-ChildItem` Cmdlet (nome)](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))

- [Renomeando itens](#Renaming-Items)

- [Anexando parâmetros dinâmicos para a `Rename-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Rename-Item-Cmdlet)

- [Criando novos itens](#Creating-New-Items)

- [Anexando parâmetros dinâmicos para a `New-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-New-Item-Cmdlet)

- [Removendo itens](#Removing-Items)

- [Anexando parâmetros dinâmicos para a `Remove-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Remove-Item-Cmdlet)

- [Consultar itens filho](#Querying-for-Child-Items)

- [Itens de cópia](#Copying-Items)

- [Anexando parâmetros dinâmicos para a `Copy-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Copy-Item-Cmdlet)

- [Exemplo de código](#Code-Sample)

- [Criando o provedor do Windows PowerShell](#Building-the-Windows-PowerShell-Provider)

- [Testando o provedor do Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definindo uma classe de provedor de contêiner do Windows PowerShell

Um provedor de contêiner do Windows PowerShell deve definir uma classe .NET que deriva de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe base. Aqui está a definição de classe para o provedor de contêiner do Windows PowerShell descrito nesta seção.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Observe que, desta definição, da classe de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo inclui dois parâmetros. O primeiro parâmetro especifica um nome amigável para o provedor que é usado pelo Windows PowerShell. O segundo parâmetro especifica os recursos específicos do Windows PowerShell que o provedor expõe para o tempo de execução do Windows PowerShell durante o processamento do comando. Para esse provedor, não há nenhum recursos específicos do Windows PowerShell que são adicionados.

## <a name="defining-base-functionality"></a>Definindo a funcionalidade de Base

Conforme descrito em [projetando seu provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe deriva de várias outras classes fornecidas funcionalidade de provedor diferente. Um provedor de contêiner do Windows PowerShell, portanto, precisa definir toda a funcionalidade fornecida por essas classes.

Para implementar a funcionalidade para adicionar informações de inicialização de sessão específica e para liberação de recursos que são usados pelo provedor, consulte [criando um provedor básico do Windows PowerShell](./creating-a-basic-windows-powershell-provider.md). No entanto, a maioria dos provedores (incluindo o provedor descrito aqui) pode usar a implementação padrão dessa funcionalidade fornecida pelo Windows PowerShell.

Para obter acesso ao armazenamento de dados, o provedor deve implementar os métodos do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criando um provedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular os itens de um repositório de dados, como introdução, configuração e itens de compensação, o provedor deve implementar os métodos fornecidos pela [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criando um provedor de Item do Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Recuperando itens filho

Para recuperar um item filho, o provedor de contêiner do Windows PowerShell deve substituir a [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para dar suporte a chamadas a partir de `Get-ChildItem` cmdlet. Esse método recupera itens filho do armazenamento de dados e os grava no pipeline como objetos. Se o `recurse` parâmetro do cmdlet for especificado, o método recupera todos os filhos, independentemente de qual nível, eles correm. Se o `recurse` parâmetro não for especificado, o método recupera um único nível de filhos.

Aqui está a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para esse provedor. Observe que esse método recupera os itens filho em todas as tabelas de banco de dados quando o caminho indica o banco de dados e recupera os itens filho das linhas da tabela, se o caminho indica uma tabela de dados.

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
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Itens a lembrar sobre a implementação GetChildItems

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Ao definir a classe de provedor, um provedor de contêiner do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método precisa garantir que o caminho passado para o método atenda aos requisitos do especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- A implementação deste método deve levar em conta nenhuma forma de acesso para o item que pode tornar o item visível para o usuário. Por exemplo, se um usuário tiver acesso de gravação para um arquivo usando o provedor FileSystem (fornecido pelo Windows PowerShell), mas não o acesso de leitura, o arquivo ainda existe e [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retorna `true`. Sua implementação pode exigir a verificação de um item pai para ver se o filho pode ser enumerado.

- Ao escrever vários itens, o [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método pode levar algum tempo. Você pode projetar seu provedor para gravar os itens usando o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método por vez. Usando essa técnica apresentará os itens para o usuário em um fluxo.

- Sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) é responsável por impedir a recursão infinita quando há links circular e assim por diante. Uma exceção de terminação apropriada deve ser gerada para refletir uma condição desse tipo.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Get-ChildItem

Às vezes, o `Get-ChildItem` cmdlet que chama [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de contêiner do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) método. Esse método recupera parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o `Get-ChildItem` cmdlet.

Este provedor de contêiner do Windows PowerShell não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Recuperando nomes de itens filho

Para recuperar os nomes dos itens filho, o provedor de contêiner do Windows PowerShell deve substituir a [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para dar suporte a chamadas a partir de `Get-ChildItem`cmdlet quando seu `Name` parâmetro for especificado. Esse método recupera os nomes dos itens filho para os nomes de item de caminho ou filho especificados para todos os contêineres se o `returnAllContainers` parâmetro do cmdlet é especificado. Um nome de filho é a parte da folha de um caminho. Por exemplo, o nome do filho para o caminho c:\windows\system32\abc.dll é "abc.dll". O nome do filho para o diretório c:\windows\system32 é "system32".

Aqui está a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para esse provedor. Observe que o método recupera nomes de tabela se o caminho especificado indica o banco de dados do Access (unidade) e os números de linha, se o caminho indica uma tabela.

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
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Itens a lembrar sobre a implementação GetChildNames

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Ao definir a classe de provedor, um provedor de contêiner do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método precisa garantir que o caminho passado para o método atenda aos requisitos do especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

  > [!NOTE]
  > Uma exceção a essa regra ocorre quando o `returnAllContainers` parâmetro do cmdlet é especificado. Nesse caso, o método deve recuperar qualquer nome do filho para um contêiner, mesmo se ele não coincide com os valores da [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), ou [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) propriedades.

- Por padrão, substituições desse método não devem recuperar nomes de objetos que geralmente são ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade for especificada. Se o caminho especificado indica um contêiner, o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade não é necessária.

- Sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) é responsável por impedir a recursão infinita quando há links circular e assim por diante. Uma exceção de terminação apropriada deve ser gerada para refletir uma condição desse tipo.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Anexando parâmetros dinâmicos para o Cmdlet Get-ChildItem (nome)

Às vezes, o `Get-ChildItem` cmdlet (com o `Name` parâmetro) requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de contêiner do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) método. Esse método recupera os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o `Get-ChildItem` cmdlet.

Este provedor não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Renomeando itens

Para renomear um item, um provedor de contêiner do Windows PowerShell deve substituir a [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método para dar suporte a chamadas a partir de `Rename-Item` cmdlet. Esse método altera o nome do item no caminho especificado para o novo nome fornecido. O novo nome sempre deve ser relativo ao item pai (contêiner).

Este provedor não substitui o [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método. No entanto, o seguinte é a implementação padrão.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Itens a lembrar sobre a implementação RenameItem

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Ao definir a classe de provedor, um provedor de contêiner do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método precisa garantir que o caminho passado para o método atenda aos requisitos do especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- O [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método destina-se para a modificação do nome de um item somente e não para operações de movimentação. Sua implementação do método deve gravar um erro se o `newName` parâmetro contém separadores de caminho ou, caso contrário, pode fazer com que o item alterar o local de seu pai.

- Por padrão, substituições desse método não devem o renomear objetos, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade for especificada. Se o caminho especificado indica um contêiner, o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade não é necessária.

- Sua implementação do [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método deve chamar [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificar seu valor de retorno antes de fazer alterações ao repositório de dados. Esse método é usado para confirmar a execução de uma operação quando uma alteração é feita ao estado do sistema, por exemplo, renomear os arquivos. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envia o nome do recurso a ser alterado para o usuário, com o tempo de execução do Windows PowerShell levando em consideração quaisquer configurações de linha de comando ou variáveis de preferência em Determinando o que deve ser exibido.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna `true`, o [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Esse método envia uma mensagem de confirmação de uma mensagem para o usuário para permitir que os comentários adicionais dizer se a operação deve continuar. Um provedor deve chamar [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como uma verificação adicional para modificações no sistema potencialmente perigosos.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Rename-Item

Às vezes, o `Rename-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de contêiner do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) método. Esse método recupera os parâmetros para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o `Rename-Item` cmdlet.

Este provedor de recipiente não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Criando novos itens

Para criar novos itens, um provedor do contêiner deve implementar o [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para dar suporte a chamadas a partir de `New-Item` cmdlet. Esse método cria um item de dados localizado no caminho especificado. O `type` parâmetro do cmdlet contém o tipo definido pelo provedor para o novo item. Por exemplo, o provedor do sistema de arquivos usa um `type` parâmetro com um valor de "file" ou "directory". O `newItemValue` parâmetro do cmdlet especifica um valor específico do provedor para o novo item.

Aqui está a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para esse provedor.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Itens a lembrar sobre a implementação NewItem

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- O [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método precisar realizar uma comparação não diferencia maiusculas da cadeia de caracteres passada a `type` parâmetro. Ele também deve permitir correspondências menos ambíguas. Por exemplo, para os tipos "file" e "directory", somente a primeira letra é necessária para resolver a ambiguidade. Se o `type` parâmetro indica um tipo que não é possível criar o seu provedor, o [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método deve gravar uma ArgumentException com uma mensagem o provedor que indica os tipos pode criar.

- Para o `newItemValue` parâmetro, a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método é recomendado para aceitar as cadeias de caracteres de no mínimo. Ele também deve aceitar o tipo de objeto que é recuperado de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para o mesmo caminho. O [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método pode usar o [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) método para converter tipos o tipo desejado.

- Sua implementação do [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método deve chamar [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificar seu valor de retorno antes de fazer alterações ao repositório de dados. Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna true, o [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método como uma verificação adicional para modificações no sistema potencialmente perigosos.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet New-Item

Às vezes, o `New-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor do contêiner deve implementar o [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) método. Esse método recupera os parâmetros para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o `New-Item` cmdlet.

Este provedor não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Removendo itens

Para remover itens, o provedor do Windows PowerShell deve substituir a [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método para dar suporte a chamadas do `Remove-Item` cmdlet. Este método exclui um item do armazenamento de dados no caminho especificado. Se o `recurse` parâmetro do `Remove-Item` cmdlet é definida como `true`, o método Remove todos os itens filho, independentemente de seu nível. Se o parâmetro for definido como `false`, o método remove apenas um único item no caminho especificado.

Este provedor não dá suporte a remoção de item. No entanto, o código a seguir é a implementação padrão de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Itens a lembrar sobre a implementação RemoveItem

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Ao definir a classe de provedor, um provedor de contêiner do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método precisa garantir que o caminho passado para o método atenda aos requisitos do especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem o remover objetos, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade é definida como true. Se o caminho especificado indica um contêiner, o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade não é necessária.

- Sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) é responsável por impedir a recursão infinita quando há links circular e assim por diante. Uma exceção de terminação apropriada deve ser gerada para refletir uma condição desse tipo.

- Sua implementação do [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método deve chamar [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificar seu valor de retorno antes de fazer alterações ao repositório de dados. Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna `true`, o [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método como uma verificação adicional para modificações no sistema potencialmente perigosos.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Remove-Item

Às vezes, o `Remove-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor do contêiner deve implementar o [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) método para lidar com esses parâmetros. Esse método recupera os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o `Remove-Item` cmdlet.

Este provedor de recipiente não implementa esse método. No entanto, o código a seguir é a implementação padrão de [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Consultar itens filho

Para verificar se os itens filho existem no caminho especificado, o provedor de contêiner do Windows PowerShell deve substituir a [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método. Esse método retornará `true` se o item tiver filhos, e `false` caso contrário. Para um caminho nulo ou vazio, o método considera todos os itens no armazenamento de dados para serem filhos e retorna `true`.

Aqui está a substituição para o [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método. Se houver mais de duas partes do caminho criados pelo método auxiliar ChunkPath, o método retorna `false`, já que apenas um contêiner de banco de dados e um contêiner de tabela são definidos. Para obter mais informações sobre esse método auxiliar, consulte o método ChunkPath é discutido [criando um provedor de Item do Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Itens a lembrar sobre a implementação HasChildItems

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Se o provedor do contêiner expõe uma raiz que contém os pontos de montagem interessante, a implementação de [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método deverá retornar `true`quando um valor nulo ou uma cadeia de caracteres vazia é passada para o caminho.

## <a name="copying-items"></a>Copiando itens

Para copiar itens, o provedor do contêiner deve implementar o [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método para dar suporte a chamadas a partir de `Copy-Item` cmdlet. Esse método copia um item de dados do local indicado pelo `path` parâmetro do cmdlet para o local indicado pelo `copyPath` parâmetro. Se o `recurse` parâmetro for especificado, o método copia todos os sub-recipientes. Se o parâmetro não for especificado, o método copia somente um único nível de itens.

Este provedor não implementa esse método. No entanto, o código a seguir é a implementação padrão de [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Itens a lembrar sobre a implementação de CopyItem

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Ao definir a classe de provedor, um provedor de contêiner do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método precisa garantir que o caminho passado para o método atenda aos requisitos do especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem copiar objetos em objetos existentes, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Por exemplo, o provedor FileSystem não copiará c:\temp\abc.txt ao longo de um arquivo c:\abc.txt existente, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Se o caminho especificado na `copyPath` parâmetro existe e indica um contêiner, o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade não é necessária. Nesse caso, [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) deve copiar o item indicado pelo `path` parâmetro para o contêiner é indicado pelo `copyPath` parâmetro como um filho.

- Sua implementação de [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) é responsável por impedir a recursão infinita quando há links circular e assim por diante. Uma exceção de terminação apropriada deve ser gerada para refletir uma condição desse tipo.

- Sua implementação do [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método deve chamar [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificar seu valor de retorno antes de fazer alterações ao repositório de dados. Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna true, o [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método como uma verificação adicional para modificações no sistema potencialmente perigosos. Para obter mais informações sobre como chamar esses métodos, consulte [renomear itens](#Renaming-Items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Copy-Item

Às vezes, o `Copy-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de contêiner do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) método para lidar com eles parâmetros. Esse método recupera os parâmetros para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o `Copy-Item` cmdlet.

Este provedor não implementa esse método. No entanto, o código a seguir é a implementação padrão de [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Criando o provedor do Windows PowerShell

Ver [como registrar Cmdlets, provedores e hospedar aplicativos](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testando o provedor do Windows PowerShell

Quando o provedor do Windows PowerShell tiver sido registrado com o Windows PowerShell, você pode testá-lo, executando os cmdlets com suporte na linha de comando. Lembre-se de que a saída de exemplo a seguir usa um banco de dados fictício.

1. Execute o `Get-ChildItem` cmdlet para recuperar a lista de itens filho de uma tabela de clientes no banco de dados do Access.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   A seguinte saída é exibida.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Execute o `Get-ChildItem` cmdlet novamente para recuperar os dados de uma tabela.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   A seguinte saída é exibida.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Agora use o `Get-Item` cmdlet para recuperar os itens na linha 0 na tabela de dados.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   A seguinte saída é exibida.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Reutilizar `Get-Item` para recuperar os dados para os itens na linha 0.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   A seguinte saída é exibida.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. Agora use o `New-Item` cmdlet para adicionar uma linha a uma tabela existente. O `Path` parâmetro especifica o caminho completo para a linha e deve indicar um número de linha que é maior que o número existente de linhas na tabela. O `Type` parâmetro indica "linha" para especificar que tipo de item a ser adicionado. Por fim, o `Value` parâmetro especifica uma lista delimitada por vírgulas de valores de coluna para a linha.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAdress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Verificar a exatidão da nova operação de item da seguinte maneira.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   A seguinte saída é exibida.

   ```output
   ID        : 3
   FirstName : Eric
   LastName  : Gruber
   Email     : ericgruber@fabrikam.com
   Title     : President
   Company   : Fabrikam
   WorkPhone : (425) 555-0100
   Address   : 4567 Main Street
   City      : Buffalo
   State     : NY
   Zip       : 98052
   Country   : USA
   ```

## <a name="see-also"></a>Consulte Também

[Criação de provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Criando o provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Implementando um provedor de Item de Windows PowerShell](./creating-a-windows-powershell-item-provider.md)

[Implementando um provedor de PowerShell do Windows de navegação](./creating-a-windows-powershell-navigation-provider.md)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)