---
title: Criar um provedor de conteúdo do PowerShell do Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 1bccbfab55f4ba4476678b130bd9db91eed7df80
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795310"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Criar um provedor de conteúdo do Windows PowerShell

Este tópico descreve como criar um provedor do Windows PowerShell que permite ao usuário manipular o conteúdo dos itens em um repositório de dados. Como consequência, um provedor que pode manipular o conteúdo de itens é conhecido como um provedor de conteúdo do Windows PowerShell.

> [!NOTE]
> Você pode baixar o C# arquivo de origem (AccessDBSampleProvider06.cs) para este provedor usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.
>
> Para obter mais informações sobre outras implementações do provedor do Windows PowerShell, consulte [projetando seu provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md).

A lista a seguir contém as seções neste tópico. Se você estiver familiarizado com a gravação de um provedor de conteúdo do Windows PowerShell, leia essas seções na ordem em que aparecem. No entanto, se você estiver familiarizado com a gravação de um provedor de conteúdo do Windows PowerShell, vá diretamente para as informações que você precisa.

- [Definindo a classe de provedor de conteúdo do PowerShell do Windows](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [Definindo a funcionalidade de Base](#Define-Functionality-of-Base-Class)

- [Implementando um leitor de conteúdo](#Implementing-a-Content-Reader)

- [Implementando um gravador de conteúdo](#Implementing-a-Content-Writer)

- [Recuperando o leitor de conteúdo](#Retrieving-the-Content-Reader)

- [Anexando parâmetros dinâmicos para a `Get-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [Recuperando o gravador de conteúdo](#Retrieving-the-Content-Writer)

- [Anexando parâmetros dinâmicos para a Add_Content e `Set-Content` Cmdlets](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [Limpar conteúdo](#Clearing-Content)

- [Anexando parâmetros dinâmicos para a `Clear-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [Exemplo de código](#Code-Sample)

- [Definindo tipos de objeto e formatação](#defining-object-types-and-formatting)

- [Criando o provedor do Windows PowerShell](#Building-the-Windows-PowerShell-Provider)

- [Testando o provedor do Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a>Definir a classe de provedor de conteúdo do PowerShell do Windows

Um provedor de conteúdo do Windows PowerShell deve criar uma classe .NET que oferece suporte a [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface. Aqui está a definição de classe para o provedor do item descrito nesta seção.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Observe que, desta definição, da classe de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo inclui dois parâmetros. O primeiro parâmetro especifica um nome amigável para o provedor que é usado pelo Windows PowerShell. O segundo parâmetro especifica os recursos específicos do Windows PowerShell que o provedor expõe para o tempo de execução do Windows PowerShell durante o processamento do comando. Para esse provedor, não há nenhum adicionados recursos específicos do Windows PowerShell.

## <a name="define-functionality-of-base-class"></a>Definir a funcionalidade da classe Base

Conforme descrito em [Design o Windows PowerShell provedor](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe deriva de várias outras classes fornecidas funcionalidade de provedor diferente. Um provedor de conteúdo do Windows PowerShell, portanto, normalmente define todas as funcionalidades fornecidas por essas classes.

Para obter mais informações sobre como implementar a funcionalidade para adicionar informações de inicialização de sessão específica e para liberação de recursos que são usados pelo provedor, consulte [criando um provedor básico do Windows PowerShell](./creating-a-basic-windows-powershell-provider.md). No entanto, a maioria dos provedores, incluindo o provedor descrito aqui, pode usar a implementação padrão dessa funcionalidade fornecida pelo Windows PowerShell.

Para acessar o armazenamento de dados, o provedor deve implementar os métodos do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criando um provedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular os itens de um repositório de dados, como introdução, configuração e itens de compensação, o provedor deve implementar os métodos fornecidos pela [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criando um provedor de Item do Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Para trabalhar em armazenamentos de dados de várias camadas, o provedor deve implementar os métodos fornecidos pela [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criando um provedor de contêiner do Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

Para dar suporte a comandos recursivos, contêineres aninhados e caminhos relativos, o provedor deve implementar o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe base. Além disso, este provedor de conteúdo do Windows PowerShell pode anexa [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface para o [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe base e, portanto, deve implementar os métodos fornecidos pela classe. Para obter mais informações, consulte a implementação desses métodos, consulte [implementar um provedor de PowerShell do Windows de navegação](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementando um leitor de conteúdo

Para ler o conteúdo de um item, um provedor deve implementa uma classe de leitor de conteúdo que é derivada de [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). O leitor de conteúdo para esse provedor permite o acesso ao conteúdo de uma linha em uma tabela de dados. A classe de leitor de conteúdo define um **leitura** método que recupera os dados da linha indicada e retorna uma lista que representa os dados, um **busca** método que move o leitor de conteúdo, um  **Fechar** método que fecha o leitor de conteúdo, e uma **Dispose** método.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implementando um gravador de conteúdo

Para gravar o conteúdo em um item, um provedor deve implementar um conteúdo classe gravador deriva [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). A classe do gravador de conteúdo define um **escrever** método que grava o conteúdo da linha especificada, um **busca** método que move o gravador de conteúdo, um **fechar** método fecha o Gravador de conteúdo e um **Dispose** método.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Recuperando o leitor de conteúdo

Para obter o conteúdo de um item, o provedor deve implementar o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) para dar suporte a `Get-Content` cmdlet. Esse método retorna o leitor de conteúdo para o item localizado no caminho especificado. O objeto do leitor pode ser aberto para ler o conteúdo.

Aqui está a implementação de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) para esse método para esse provedor.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Itens a lembrar sobre a implementação GetContentReader

As seguintes condições podem se aplicar a uma implementação de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Ao definir a classe de provedor, um provedor de conteúdo do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método deve garantir que o caminho passado para o método atende aos requisitos de especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem recuperar um leitor para os objetos que são ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser escrito se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é definido como `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Get-Content

O `Get-Content` cmdlet pode exigir parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de conteúdo do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) método. Esse método recupera parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o cmdlet.

Este provedor de contêiner do Windows PowerShell não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Recuperando o gravador de conteúdo

Para gravar o conteúdo em um item, o provedor deve implementar o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) para dar suporte a `Set-Content` e `Add-Content` cmdlets. Esse método retorna o gravador de conteúdo para o item localizado no caminho especificado.

Aqui está a implementação de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) para esse método.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Itens a lembrar sobre a implementação GetContentWriter

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Ao definir a classe de provedor, um provedor de conteúdo do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método deve garantir que o caminho passado para o método atende aos requisitos de especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem recuperar um gravador para objetos que são ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser escrito se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é definido como `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Anexando parâmetros dinâmicos para os Cmdlets Add-Content e Set-Content

O `Add-Content` e `Set-Content` cmdlets pode exigir parâmetros dinâmicos adicionais que são adicionados a um tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de conteúdo do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) método para lidar com eles parâmetros. Esse método recupera parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para os cmdlets.

Este provedor de contêiner do Windows PowerShell não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Limpar conteúdo

Implementa o provedor de conteúdo a [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método suportados a `Clear-Content` cmdlet. Esse método Remove o conteúdo do item no caminho especificado, mas deixa intacto o item.

Aqui está a implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método para esse provedor.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Itens a lembrar sobre a implementação ClearContent

As seguintes condições podem se aplicar a uma implementação de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Ao definir a classe de provedor, um provedor de conteúdo do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método deve garantir que o caminho passado para o método atende aos requisitos de especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem limpar o conteúdo de objetos que são ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser escrito se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é definido como `false`.

- Sua implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método deve chamar [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique se o valor retornado antes de fazer alterações ao repositório de dados. Esse método é usado para confirmar a execução de uma operação quando uma alteração é feita para o armazenamento de dados, como limpar o conteúdo. O [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) método envia o nome do recurso a ser alterado para o usuário, com o tempo de execução do Windows PowerShell quaisquer configurações de linha de comando ou uma preferência de tratamento variáveis de determinar o que deve ser exibido.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna `true`, o [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Esse método envia uma mensagem ao usuário para permitir que seus comentários para verificar se a operação deve continuar. A chamada para [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite que uma verificação adicional para modificações no sistema potencialmente perigosos.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Clear-Content

O `Clear-Content` cmdlet pode exigir parâmetros dinâmicos adicionais que são adicionados em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de conteúdo do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) método para lidar com eles parâmetros. Esse método recupera os parâmetros para o item no caminho indicado. Esse método recupera parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o cmdlet.

Este provedor de contêiner do Windows PowerShell não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definindo tipos de objeto e formatação

Ao escrever um provedor, ele pode ser necessário adicionar membros a objetos existentes ou definir novos objetos. Quando isso for feito, você deve criar um arquivo de tipos que o Windows PowerShell pode usar para identificar os membros do objeto e um arquivo de formato que define como o objeto é exibido. Para obter mais informações, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Criando o provedor do Windows PowerShell

Ver [como registrar Cmdlets, provedores e hospedar aplicativos](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testando o provedor do Windows PowerShell

Quando o provedor do Windows PowerShell tiver sido registrado com o Windows PowerShell, você pode testá-lo, executando os cmdlets com suporte na linha de comando. Por exemplo, o provedor de conteúdo de exemplo de teste.

Use o `Get-Content` cmdlet para recuperar o conteúdo do item especificado na tabela de banco de dados no caminho especificado pelo `Path` parâmetro. O `ReadCount` parâmetro especifica o número de itens para o leitor de conteúdo definido ler (padrão 1). Com a seguinte entrada de comando, o cmdlet recupera as duas linhas (itens) da tabela e exibe seu conteúdo. Observe que a saída de exemplo a seguir usa um banco de dados fictício.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
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
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>Consulte Também

[Criando provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Provedor de PowerShell do Windows seu design](./designing-your-windows-powershell-provider.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementar um provedor de navegação Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)
