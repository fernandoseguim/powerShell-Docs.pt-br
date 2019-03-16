---
title: Criar um provedor de navegação do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 40454f880b57d5b3a8a8ded21c8c97aebba027fe
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055063"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Criar um provedor de navegação do Windows PowerShell

Este tópico descreve como criar um provedor de navegação do Windows PowerShell que pode navegar o armazenamento de dados. Esse tipo de provedor dá suporte a comandos recursivos, contêineres aninhados e caminhos relativos.

> [!NOTE]
> Você pode baixar o C# arquivo de origem (AccessDBSampleProvider05.cs) para este provedor usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.
>
> Para obter mais informações sobre outras implementações do provedor do Windows PowerShell, consulte [projetando seu provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md).

O provedor descrito aqui permite que o identificador de usuário de um banco de dados como uma unidade para que o usuário possa navegar para as tabelas de dados no banco de dados. Ao criar seu próprio provedor de navegação, você pode implementar métodos que podem fazer caminhos qualificadas pela unidade necessários para a navegação, normalizar caminhos relativos, mover itens de repositório de dados, bem como os métodos que obtém nomes de filho, obtém o caminho pai de um item e de teste para identificar se um item é um contêiner.

> [!CAUTION]
> Lembre-se de que este design pressupõe um banco de dados que tem um campo com a ID de nome e o tipo do campo é LongInteger.

A lista a seguir inclui as seções neste tópico. Se você estiver familiarizado com a gravação de um provedor de navegação do Windows PowerShell, leia essas informações na ordem em que ele é exibido. No entanto, se você estiver familiarizado com a gravação de um provedor de navegação do Windows PowerShell, vá diretamente para as informações que você precisa.

- [Definindo uma classe de provedor de navegação de PS](#Define-the-Windows-PowerShell-provider)

- [Definindo a funcionalidade de Base](#Defining-Base-Functionality)

- [Criação de um caminho de PS](#Creating-a-Windows-PowerShell-Path)

- [Recuperando o caminho pai](#Retrieving-the-Parent-Path)

- [Recuperar o nome de caminho filho](#Retrieve-the-Child-Path-Name)

- [Determinando se um Item é um contêiner](#Determining-if-an-Item-is-a-Container)

- [Mover um Item](#Moving-an-Item)

- [Anexando parâmetros dinâmicos para a `Move-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [Normalizar um caminho relativo](#Normalizing-a-Relative-Path)

- [Exemplo de código](#Code-Sample)

- [Definindo tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o provedor do Windows PowerShell](#Building-the-Windows-PowerShell-provider)

- [Testando o provedor do Windows PowerShell](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>Definir o provedor do Windows PowerShell

Um provedor de navegação do Windows PowerShell deve criar uma classe .NET que deriva de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe base. Aqui está a definição de classe para o provedor de navegação descrito nesta seção.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Observe que, neste provedor, o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo inclui dois parâmetros. O primeiro parâmetro especifica um nome amigável para o provedor que é usado pelo Windows PowerShell. O segundo parâmetro especifica os recursos específicos do Windows PowerShell que o provedor expõe para o tempo de execução do Windows PowerShell durante o processamento do comando. Para esse provedor, não há nenhum recursos específicos do Windows PowerShell que são adicionados.

## <a name="defining-base-functionality"></a>Definindo a funcionalidade de Base

Conforme descrito em [Design de seu provedor de PS](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) deriva de classe base de várias outras classes que forneceu um provedor diferente funcionalidade. Um provedor de navegação do Windows PowerShell, portanto, deve definir todas as funcionalidades fornecidas por essas classes.

Para implementar a funcionalidade para adicionar informações de inicialização de sessão específica e para liberação de recursos que são usados pelo provedor, consulte [criando um provedor básico do PS](./creating-a-basic-windows-powershell-provider.md). No entanto, a maioria dos provedores (incluindo o provedor descrito aqui) pode usar a implementação padrão dessa funcionalidade fornecida pelo Windows PowerShell.

Para obter acesso ao armazenamento de dados por meio de uma unidade do Windows PowerShell, você deve implementar os métodos do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criando um provedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular os itens de um repositório de dados, como introdução, configuração e itens de compensação, o provedor deve implementar os métodos fornecidos pela [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criando um provedor de Item do Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Para obter os itens filho ou seus nomes, de armazenamento de dados, bem como os métodos que criar, copiar, renomeiam e remover itens, você deve implementar os métodos fornecidos pelo [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criando um provedor de contêiner do Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Criação de um caminho do Windows PowerShell

Provedor de navegação do Windows PowerShell usar um caminho provedor interno do Windows PowerShell para navegar os itens do repositório de dados. Para criar um caminho de provedor interno de provedor deve implementar o [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método para dar suporte às chamadas do cmdlet combinar-Path. Esse método combina um caminho pai e filho em um caminho de provedor interno, usando um separador de caminho de provedor específico entre os caminhos pai e filho.

A implementação padrão usa caminhos com "/" ou "\\"como o separador de caminho, normaliza o separador de caminho para"\\", combina as partes do caminho pai e filho com o separador entre eles e, em seguida, retorna uma cadeia de caracteres que contém o caminhos combinados.

Este provedor de navegação não implementa esse método. No entanto, o código a seguir é a implementação padrão do [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Itens a lembrar sobre a implementação MakePath

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- Sua implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método não deve validar o caminho como um caminho totalmente qualificado legal em que o namespace do provedor. Lembre-se de que cada parâmetro pode representar apenas uma parte de um caminho e as partes combinadas não podem gerar um caminho totalmente qualificado. Por exemplo, o [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método para o provedor do sistema de arquivos pode receber "windows\system32" no `parent` parâmetro e "abc.dll" o `child` parâmetro. O método une esses valores com a "\\" separador e retorna "windows\system32\abc.dll", que não é um caminho de sistema de arquivo totalmente qualificado.

  > [!IMPORTANT]
  > As partes do caminho fornecidas na chamada para [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) pode conter caracteres não são permitidos no namespace de provedor. Provavelmente, esses caracteres são usados para expansão de curinga e a implementação desse método não deve removê-los.

## <a name="retrieving-the-parent-path"></a>Recuperando o caminho pai

Implementam provedores de navegação do Windows PowerShell a [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método para recuperar a parte do pai do indicado completa ou parcial caminho específico do provedor. O método remove a parte do filho do caminho e retorna o pai de parte do caminho. O `root` parâmetro especifica o caminho totalmente qualificado para a raiz de uma unidade. Esse parâmetro pode ser nula ou vazia se não for uma unidade montada em uso para a operação de recuperação. Se uma raiz for especificada, o método deve retornar um caminho para um contêiner na mesma árvore de raiz.

O provedor de navegação de exemplo não substitui esse método, mas usa a implementação padrão. Ele aceita caminhos que usam ambos "/" e "\\" como separadores de caminho. Ele primeiro normaliza o caminho para ter apenas "\\" separadores, em seguida, divide o caminho pai desativar o último "\\" e retorna o caminho pai.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Lembrar sobre a implementação GetParentPath

Sua implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método deve dividir o caminho lexicalmente no separador de caminho para o namespace do provedor. Por exemplo, o provedor filesystem usa esse método para procurar o último "\\" e retorna todos os itens à esquerda do separador.

## <a name="retrieve-the-child-path-name"></a>Recuperar o nome de caminho filho

Seu implementa de provedor de navegação de [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método para recuperar o nome (elemento de folha) do filho do item localizado em todo o indicado ou caminho parcial de específico do provedor.

O provedor de navegação de exemplo não substitui esse método. A implementação padrão é mostrada abaixo. Ele aceita caminhos que usam ambos "/" e "\\" como separadores de caminho. Ele primeiro normaliza o caminho para ter apenas "\\" separadores, em seguida, divide o caminho pai desativar o último "\\" e retorna o nome do filho parte do caminho.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Itens a lembrar sobre a implementação GetChildName

Sua implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método deve dividir o caminho lexicalmente no separador de caminho. Se o caminho fornecido não contém nenhum separador de caminho, o método deve retornar o caminho sem modificações.

> [!IMPORTANT]
> O caminho fornecido na chamada para esse método pode conter os caracteres são ilegais no namespace do provedor. Esses caracteres são mais prováveis usados para expansão de curinga ou correspondência da expressão regular e a implementação desse método não deve removê-los.

## <a name="determining-if-an-item-is-a-container"></a>Determinando se um Item é um contêiner

O provedor de navegação pode implementar o [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) método para determinar se o caminho especificado indica um contêiner. Ela retorna true se o caminho representa um contêiner e false caso contrário. O usuário precisa ser capaz de usar esse método o `Test-Path` cmdlet para o caminho fornecido.

O código a seguir mostra a [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementação no nosso provedor de navegação de amostra. O método verifica se o caminho especificado está correto e se a tabela existe e retorna true se o caminho indica um contêiner.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Itens a lembrar sobre a implementação IsItemContainer

Seu provedor de navegação de classe do .NET pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, do [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nesse caso, a implementação de [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) precisa garantir que o caminho passou atende aos requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) propriedade.

## <a name="moving-an-item"></a>Mover um Item

Suportados a `Move-Item` implementa de seu provedor de navegação do cmdlet, o [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método. Esse método Move o item especificado pela `path` parâmetro para o contêiner no caminho fornecido no `destination` parâmetro.

O provedor de navegação de exemplo não substitui o [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método. A seguir está a implementação padrão.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Itens a lembrar sobre a implementação MoveItem

Seu provedor de navegação de classe do .NET pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, do [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nesse caso, a implementação de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) deve garantir que o caminho passado atende aos requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o **CmdletProvider.Exclude** propriedade.

Por padrão, substituições desse método não devem mover objetos sobre os objetos existentes, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Por exemplo, o provedor filesystem não copiará c:\temp\abc.txt ao longo de um arquivo c:\bar.txt existente, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Se o caminho especificado na `destination` parâmetro existe e é um contêiner, o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade não é necessária. Nesse caso, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) deve mover o item indicado pelo `path` parâmetro para o contêiner é indicado pelo `destination` parâmetro como um filho.

Sua implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método deve chamar [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificar seu valor de retorno antes de fazer alterações ao repositório de dados. Esse método é usado para confirmar a execução de uma operação quando uma alteração é feita ao estado do sistema, por exemplo, excluindo arquivos. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envia o nome do recurso a ser alterado para o usuário, com o tempo de execução do Windows PowerShell levando em consideração quaisquer configurações de linha de comando ou variáveis de preferência em Determinando o que deve ser exibido ao usuário.

Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna `true`, o [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Esse método envia uma mensagem ao usuário para permitir que seus comentários para dizer se a operação deve continuar. Seu provedor deve chamar [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como uma verificação adicional para modificações no sistema potencialmente perigosos.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Move-Item

Às vezes, o `Move-Item` cmdlet requer parâmetros adicionais que são fornecidos dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de navegação deve implementar o [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) método para obter os valores de parâmetro obrigatório do item no caminho indicado e retornar um objeto que tem propriedades e campos com análise atributos semelhante a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.

Este provedor de navegação não implementa esse método. No entanto, o código a seguir é a implementação padrão de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Normalizar um caminho relativo

Seu implementa de provedor de navegação de [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) método normalizar o caminho totalmente qualificado é indicado no `path` parâmetro como estando em relação ao caminho especificado pela `basePath` parâmetro. O método retorna uma representação de cadeia de caracteres do caminho normalizado. Ele grava um erro se o `path` parâmetro especifica um caminho inexistente.

O provedor de navegação de exemplo não substitui esse método. A seguir está a implementação padrão.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Itens a lembrar sobre a implementação NormalizeRelativePath

Sua implementação de [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) deve analisar o `path` parâmetro, mas ele não precisa usar a análise puramente sintática. São incentivados a esse método para usar o caminho para pesquisar as informações de caminho no armazenamento de dados e criar um caminho que coincide com o uso de maiusculas e minúsculas de design e padronizado a sintaxe do caminho.

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definindo tipos de objeto e formatação

É possível para um provedor adicionar membros a objetos existentes ou para definir novos objetos. Para obter mais informações, consulte[estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Criando o provedor do Windows PowerShell

Para obter mais informações, consulte [como registrar Cmdlets, provedores e aplicativos Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testando o provedor do Windows PowerShell

Quando o provedor do Windows PowerShell tiver sido registrado com o Windows PowerShell, você pode testá-lo, executando os cmdlets com suporte na linha de comando, incluindo os cmdlets disponibilizados por derivação. Este exemplo irá testar o provedor de navegação de exemplo.

1. Execute seu novo shell e use o `Set-Location` cmdlet para definir o caminho para indicar o banco de dados do Access.

   ```powershell
   Set-Location mydb:
   ```

2. Agora, execute o `Get-Childitem` cmdlet para recuperar uma lista dos itens de banco de dados, que são as tabelas de banco de dados disponíveis. Para cada tabela, esse cmdlet também recupera o número de linhas da tabela.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Use o `Set-Location` cmdlet novamente para definir o local da tabela de dados de funcionários.

   ```powershell
   Set-Location Employees
   ```

4. Agora vamos usar o `Get-Location` cmdlet para recuperar o caminho para a tabela de funcionários.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. Agora use o `Get-Childitem` cmdlet canalizados para o `Format-Table` cmdlet. Esse conjunto de cmdlets recupera os itens para a tabela de dados de funcionários, que são as linhas da tabela. Eles são formatados conforme especificado pelo `Format-Table` cmdlet.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. Agora você pode executar o `Get-Item` cmdlet para recuperar os itens de linha 0 da tabela de dados de funcionários.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Use o `Get-Item` cmdlet novamente para recuperar os dados de funcionário para os itens na linha 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Consulte Também

[Criando provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Provedor de PowerShell do Windows seu design](./designing-your-windows-powershell-provider.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementar um provedor de contêiner Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)