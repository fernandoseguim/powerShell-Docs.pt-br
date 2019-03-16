---
title: Criando um provedor do Windows PowerShell Item | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: f2c9e10f0dc392399cf062500b7f28b3d1c07f6e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055114"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Criar um provedor de itens do Windows PowerShell

Este tópico descreve como criar um provedor do Windows PowerShell que pode manipular os dados em um armazenamento de dados. Neste tópico, os elementos de dados no repositório são referidos como "itens" dos dados de armazenamento. Como consequência, um provedor que pode manipular os dados no repositório é conhecido como um provedor de item do Windows PowerShell.

> [!NOTE]
> Você pode baixar o C# arquivo de origem (AccessDBSampleProvider03.cs) para este provedor usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.
>
> Para obter mais informações sobre outras implementações do provedor do Windows PowerShell, consulte [projetando seu provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md).

O provedor de item do Windows PowerShell descrito neste tópico obtém os itens de dados de um banco de dados. Nesse caso, "item" é uma tabela no banco de dados do Access ou uma linha em uma tabela.

A lista a seguir contém as seções neste tópico. Se você estiver familiarizado com a gravação de um provedor de item do Windows PowerShell, leia essas seções na ordem em que aparecem. No entanto, se você estiver familiarizado com a gravação de um provedor de item do Windows PowerShell, vá diretamente para as informações que você precisa:

- [Definição da classe de provedor do Windows PowerShell Item](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [Definindo a funcionalidade de Base](#Defining-Base-Functionality)

- [Verificação de validade do caminho](#Checking-for-Path-Validity)

- [Determinando se existe um Item](#Determining-if-an-Item-Exists)

- [Anexando parâmetros dinâmicos para a `Test-Path` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [Recuperação de um Item](#Retrieving-an-Item)

- [Anexando parâmetros dinâmicos para a `Get-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [Definindo um Item](#Setting-an-Item)

- [Anexando parâmetros dinâmicos para a `Set-Item` Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [Limpar um Item](#Clearing-an-Item)

- [Anexando parâmetros dinâmicos para o Cmdlet Clear-Item](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [Executar uma ação padrão para um Item](#Performing-a-Default-Action-for-an-Item)

- [Recuperando parâmetros dinâmicos para InvokeDefaultAction](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [Implementando os métodos e Classes auxiliares](#Implementing-Helper-Methods-and-Classes)

- [Exemplo de código](#Code-Sample)

- [Definindo tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o provedor do Windows PowerShell](#Building-the-Windows-PowerShell-provider)

- [Testando o provedor do Windows PowerShell](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definição da classe de provedor do Windows PowerShell Item

Um provedor de item do Windows PowerShell deve definir uma classe .NET que deriva de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe base. A seguir está a definição de classe para o provedor do item descrito nesta seção.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Observe que, desta definição, da classe de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo inclui dois parâmetros. O primeiro parâmetro especifica um nome amigável para o provedor que é usado pelo Windows PowerShell. O segundo parâmetro especifica os recursos específicos do Windows PowerShell que o provedor expõe para o tempo de execução do Windows PowerShell durante o processamento do comando. Para esse provedor, não há nenhum adicionados recursos específicos do Windows PowerShell.

## <a name="defining-base-functionality"></a>Definindo a funcionalidade de Base

Conforme descrito em [Design o Windows PowerShell provedor](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe deriva de várias outras classes fornecidas diferentes funcionalidade de provedor. Um provedor de item do Windows PowerShell, portanto, deve definir todas as funcionalidades fornecidas por essas classes.

Para obter mais informações sobre como implementar a funcionalidade para adicionar informações de inicialização de sessão específica e para liberação de recursos usados pelo provedor, consulte [criando um provedor básico do Windows PowerShell](./creating-a-basic-windows-powershell-provider.md). No entanto, a maioria dos provedores, incluindo o provedor descrito aqui, pode usar a implementação padrão dessa funcionalidade fornecida pelo Windows PowerShell.

Antes do provedor de item do Windows PowerShell pode manipular os itens no repositório, ele deve implementar os métodos do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe para acessar o armazenamento de dados base. Para obter mais informações sobre como implementar essa classe, consulte [criando um provedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Verificação de validade do caminho

Ao procurar um item de dados, o tempo de execução do Windows PowerShell fornece um caminho do Windows PowerShell para o provedor, conforme definido na seção "Conceitos PSPath" [como o Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Um provedor de item do Windows PowerShell deve verificar a validade de sintática e semântica de qualquer caminho passado para ele com a implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método. Esse método retornará `true` se o caminho é válido, e `false` caso contrário. Estar ciente de que a implementação desse método não deve verificar a existência do item no caminho, mas apenas que o caminho é sintaticamente e semanticamente correta.

Aqui está a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método para esse provedor. Observe que essa implementação chama um método auxiliar de NormalizePath para converter todos os separadores no caminho para um uniforme.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Determinando se existe um Item

Depois de verificar o caminho, o tempo de execução do Windows PowerShell deve determinar se um item de dados existe nesse caminho. Para dar suporte a esse tipo de consulta, o provedor de item do Windows PowerShell implementa o [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método. Esse método retornará `true` um item for encontrado no caminho especificado e `false` (padrão) caso contrário.

Aqui está a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método para esse provedor. Observe que esse método chama os métodos auxiliares PathIsDrive, ChunkPath e GetTable e usa um provedor definido pelo objeto DatabaseTableInfo.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Itens a lembrar sobre a implementação ItemExists

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Ao definir a classe de provedor, um provedor de item do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método deve garantir que o caminho passado para o método atende aos requisitos dos recursos especificados. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- A implementação deste método deve lidar com qualquer forma de acesso para o item que pode tornar o item visível para o usuário. Por exemplo, se um usuário tiver acesso de gravação para um arquivo usando o provedor FileSystem (fornecido pelo Windows PowerShell), mas não o acesso de leitura, o arquivo ainda existe e [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retorna `true`. Sua implementação pode exigir a verificação de um item pai para ver se o item filho pode ser enumerado.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Test-Path

Às vezes, o `Test-Path` cmdlet que chama [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos do PowerShell do Windows item provedor deve implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) método. Esse método recupera os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o `Test-Path` cmdlet.

Este provedor de item do Windows PowerShell não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Recuperação de um Item

Para recuperar um item, o provedor de item do Windows PowerShell deve substituir [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para dar suporte a chamadas a partir de `Get-Item` cmdlet. Esse método grava o item usando o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.

Aqui está a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para esse provedor. Observe que esse método usa os métodos auxiliares GetTable e GetRow para recuperar itens que são tabelas no banco de dados do Access ou linhas em uma tabela de dados.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Itens a lembrar sobre a implementação GetItem

As seguintes condições podem se aplicar a uma implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Ao definir a classe de provedor, um provedor de item do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) deve garantir que o caminho passado para o método atende a esses requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem recuperar objetos que geralmente são ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Por exemplo, o [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para as verificações de provedor do sistema de arquivos o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade antes de tentar chamar [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) ocultas ou arquivos do sistema.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Get-Item

Às vezes, o `Get-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos do PowerShell do Windows item provedor deve implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) método. Esse método recupera os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o `Get-Item` cmdlet.

Este provedor não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Definindo um Item

Para definir um item, o provedor de item do Windows PowerShell deve substituir a [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método para dar suporte a chamadas do `Set-Item` cmdlet. Esse método define o valor do item no caminho especificado.

Este provedor não fornece uma substituição para o [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método. No entanto, o seguinte é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Itens a lembrar sobre a implementação SetItem

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Ao definir a classe de provedor, um provedor de item do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) deve garantir que o caminho passado para o método atende a esses requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem definir ou gravar objetos que são ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser enviado para o [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método se o caminho representa um item oculto e [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é definido como `false`.

- Sua implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método deve chamar [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)e verifique se o valor retornado antes de fazer alterações ao repositório de dados. Esse método é usado para confirmar a execução de uma operação quando uma alteração é feita para o armazenamento de dados, por exemplo, exclusão de arquivos. O [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) método envia o nome do recurso a ser alterado para o usuário, com o tempo de execução do Windows PowerShell levando em conta todas as configurações de linha de comando ou variáveis de preferência determinar o que deve ser exibido.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna `true`, o [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Esse método envia uma mensagem ao usuário para permitir que seus comentários para verificar se a operação deve continuar. A chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite que uma verificação adicional para modificações no sistema potencialmente perigosos.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Recuperando parâmetros dinâmicos para SetItem

Às vezes, o `Set-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos do PowerShell do Windows item provedor deve implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) método. Esse método recupera os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o `Set-Item` cmdlet.

Este provedor não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Limpar um Item

Para limpar um item, o provedor de item do Windows PowerShell implementa o [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) método para dar suporte a chamadas a partir de `Clear-Item` cmdlet. Esse método apaga o item de dados no caminho especificado.

Este provedor não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Itens a lembrar sobre a implementação ClearItem

As seguintes condições podem se aplicar a uma implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Ao definir a classe de provedor, um provedor de item do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) deve garantir que o caminho passado para o método atende a esses requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem definir ou gravar objetos que são ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser enviado para o [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método se o caminho representa um item que está oculto do usuário e [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é definido como `false`.

- Sua implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método deve chamar [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)e verifique se o valor retornado antes de fazer alterações ao repositório de dados. Esse método é usado para confirmar a execução de uma operação quando uma alteração é feita para o armazenamento de dados, por exemplo, exclusão de arquivos. O [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) método envia o nome do recurso a ser alterada para o usuário, com o tempo de execução do Windows PowerShell e lidar com quaisquer configurações de linha de comando ou uma preferência variáveis de determinar o que deve ser exibido.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna `true`, o [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Esse método envia uma mensagem ao usuário para permitir que seus comentários para verificar se a operação deve continuar. A chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite que uma verificação adicional para modificações no sistema potencialmente perigosos.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Recuperar parâmetros dinâmicos para ClearItem

Às vezes, o `Clear-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos do PowerShell do Windows item provedor deve implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) método. Esse método recupera os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o `Clear-Item` cmdlet.

Este provedor de item não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Executar uma ação padrão para um Item

Um provedor de item do Windows PowerShell pode implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) método para dar suporte a chamadas do `Invoke-Item` cmdlet, que permite que o provedor para Execute uma ação padrão para o item no caminho especificado. Por exemplo, o provedor FileSystem pode usar esse método para chamar ShellExecute para um item específico.

Este provedor não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Itens a lembrar sobre a implementação InvokeDefaultAction

As seguintes condições podem se aplicar a uma implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Ao definir a classe de provedor, um provedor de item do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) deve garantir que o caminho passado para o método atende a esses requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem definir ou gravar objetos ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser enviado para o [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método se o caminho representa um item que está oculto do usuário e [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é definido como `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Recuperar parâmetros dinâmicos para InvokeDefaultAction

Às vezes, o `Invoke-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos do PowerShell do Windows item provedor deve implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) método. Esse método recupera os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou um [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros dinâmicos para a `Invoke-Item` cmdlet.

Este provedor de item não implementa esse método. No entanto, o código a seguir é a implementação padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementando os métodos e Classes auxiliares

Este provedor de item implementa vários métodos auxiliares e classes que são usadas pelo público substituem métodos definidos pelo Windows PowerShell. O código para esses métodos e classes auxiliares são mostrados na [exemplo de código](#Code-Sample) seção.

### <a name="normalizepath-method"></a>Método NormalizePath

Este provedor de item implementa um método auxiliar de NormalizePath para garantir que o caminho tem um formato consistente. O formato especificado usa uma barra invertida (\\) como um separador.

### <a name="pathisdrive-method"></a>Método PathIsDrive

Este provedor de item implementa um método auxiliar de PathIsDrive para determinar se o caminho especificado é, na verdade, o nome da unidade.

### <a name="chunkpath-method"></a>Método ChunkPath

Este provedor de item implementa um método auxiliar ChunkPath que divide o caminho especificado para que o provedor possa identificar seus elementos individuais. Ele retorna que uma matriz composta de elementos de caminho.

### <a name="gettable-method"></a>Método getTable

Este provedor de item implementa o método auxiliar GetTables que retorna um objeto DatabaseTableInfo que representa informações sobre a tabela especificada na chamada.

### <a name="getrow-method"></a>Método GetRow

O [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método desse provedor de item chama o método auxiliar GetRows. Esse método auxiliar recupera um objeto de DatabaseRowInfo que representa informações sobre a linha especificada na tabela.

### <a name="databasetableinfo-class"></a>Classe DatabaseTableInfo

Este provedor de item define uma classe de DatabaseTableInfo que representa uma coleção de informações em uma tabela de dados no banco de dados. Essa classe é semelhante para o [DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) classe.

O provedor de item de exemplo define um método de DatabaseTableInfo.GetTables que retorna uma coleção de objetos de informações da tabela definindo as tabelas no banco de dados. Esse método inclui um bloco try/catch para garantir que qualquer erro de banco de dados aparece como uma linha com zero entradas.

### <a name="databaserowinfo-class"></a>Classe DatabaseRowInfo

Este provedor de item define a classe auxiliar DatabaseRowInfo que representa uma linha em uma tabela do banco de dados. Essa classe é semelhante para o [FileInfo](/dotnet/api/System.IO.FileInfo) classe.

O provedor de exemplo define um método de DatabaseRowInfo.GetRows para retornar uma coleção de objetos de informações de linha da tabela especificada. Esse método inclui um bloco try/catch para interceptar exceções. Quaisquer erros resultará em nenhuma informação de linha.

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definindo tipos de objeto e formatação

Ao escrever um provedor, ele pode ser necessário adicionar membros a objetos existentes ou definir novos objetos. Quando terminar, crie um arquivo de tipos que o Windows PowerShell pode usar para identificar os membros do objeto e um arquivo de formato que define como o objeto é exibido. Para obter mais informações, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Criando o provedor do Windows PowerShell

Ver [como registrar Cmdlets, provedores e hospedar aplicativos](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testando o provedor do Windows PowerShell

Quando esse provedor de item do Windows PowerShell é registrado com o Windows PowerShell, somente o basic de teste e funcionalidade do provedor de unidade. Para testar a manipulação de itens, você também deve implementar a funcionalidade de contêiner descrita [implementando um provedor do contêiner de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Consulte Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Criação de provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Criando o provedor do seu Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como funciona o Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Criar um provedor de contêiner Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Criar um provedor de unidade Windows PowerShell](./creating-a-windows-powershell-drive-provider.md)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)