---
title: Criar um provedor de unidade do PowerShell do Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 174d3a6860790295e1b73f32d9c1bad46b653917
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055641"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Criar um provedor de unidade do Windows PowerShell

Este tópico descreve como criar um provedor de unidade do Windows PowerShell que fornece uma maneira de acessar um armazenamento de dados por meio de uma unidade do Windows PowerShell. Esse tipo de provedor é também denominado provedores de unidade do Windows PowerShell. As unidades do Windows PowerShell usadas pelo provedor fornecem os meios para se conectar ao armazenamento de dados.

O provedor da unidade do Windows PowerShell descrito aqui fornece acesso a um banco de dados do Microsoft Access. Para esse provedor, a unidade do Windows PowerShell representa o banco de dados (é possível adicionar qualquer número de unidades para um provedor de unidade), os contêineres de nível superior da unidade representam as tabelas no banco de dados e os itens dos contêineres representam as linhas em as tabelas.

Aqui está uma lista das seções neste tópico. Se você estiver familiarizado com a gravação de um provedor de unidade do Windows PowerShell, leia essas seções na ordem em que aparecem. No entanto, se você estiver familiarizado com a gravação de um provedor de unidade, vá diretamente para as informações que você precisa.

- [Definição da classe de provedor do PowerShell do Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definindo a funcionalidade de Base](#Defining-Base-Functionality)

- [Criando informações de estado da unidade](#Creating-Drive-State-Information)

- [Criando uma unidade](#Creating-a-Drive)

- [Anexando parâmetros dinâmicos a NewDrive](#Attaching-Dynamic-Parameters-to-NewDrive)

- [Removendo uma unidade](#Removing-a-Drive)

- [Unidades de inicialização padrão](#Initializing-Default-Drives)

- [Exemplo de código](#Code-Sample)

- [Testando o provedor de unidade do PowerShell do Windows](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definição da classe de provedor do PowerShell do Windows

Seu provedor de unidade deve definir uma classe .NET que deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base. Aqui está a definição de classe para este provedor de unidade:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Observe que neste exemplo, o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo especifica um nome amigável para o provedor e os recursos específicos do Windows PowerShell que o provedor expõe o tempo de execução do Windows PowerShell durante o processamento do comando. Os valores possíveis para os recursos do provedor são definidos pela [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Este provedor de unidade não suporta qualquer um desses recursos.

## <a name="defining-base-functionality"></a>Definindo a funcionalidade de Base

Conforme descrito em [Design o Windows PowerShell provedor](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe deriva de [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe base que define os métodos necessários para inicializar e cancelando a inicialização do provedor. Para implementar a funcionalidade para adicionar informações de inicialização de sessão específica e para liberação de recursos que são usados pelo provedor, consulte [criando um provedor básico do Windows PowerShell](./creating-a-basic-windows-powershell-provider.md). No entanto, a maioria dos provedores (incluindo o provedor descrito aqui) pode usar a implementação padrão dessa funcionalidade fornecida pelo Windows PowerShell.

## <a name="creating-drive-state-information"></a>Criando informações de estado da unidade

Todos os provedores do Windows PowerShell são considerados sem monitoração de estado, o que significa que seu provedor de unidade precisa criar quaisquer informações de estado que é necessária para o tempo de execução do Windows PowerShell quando ele chama o provedor.

Para este provedor de unidade, a conexão ao banco de dados é mantido como parte das informações de unidade incluem informações de estado. Aqui está o código que mostra como essas informações são armazenadas do [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto que descreve a unidade:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Criando uma unidade

Para permitir que o tempo de execução do Windows PowerShell criar uma unidade, o provedor da unidade deve implementar o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método. O código a seguir mostra a implementação do [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método para este provedor de unidade:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

Sua substituição desse método deve fazer o seguinte:

- Verifique se que o [System.Management.Automation.PSDriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) membro existe e que uma conexão ao armazenamento de dados pode ser feita.

- Criar uma unidade e preencher o membro de conexão, suportados a `New-PSDrive` cmdlet.

- Validar a [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto para a unidade proposto.

- Modificar a [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) do objeto que descreve a unidade com qualquer informação de confiabilidade ou de desempenho necessários, ou fornecer dados extras para os chamadores usando a unidade.

- Lidar com falhas usando o [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método e, em seguida, retorno `null`.

  Esse método retorna as informações do disco que foi passadas para o método ou uma versão específica do provedor dele.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Anexando parâmetros dinâmicos a NewDrive

O `New-PSDrive` cmdlet tem suportada pelo seu provedor de unidade pode exigir parâmetros adicionais. Para anexar esses parâmetros dinâmicos para o cmdlet, o provedor implementa o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) método. Esse método retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.

Este provedor de unidade não substitui esse método. No entanto, o código a seguir mostra a implementação padrão desse método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Removendo uma unidade

Para fechar a conexão de banco de dados, o provedor da unidade deve implementar o [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método. Este método fecha a conexão para a unidade depois de limpar todas as informações específicas do provedor.

O código a seguir mostra a implementação do [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método para este provedor de unidade:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Se a unidade pode ser removida, o método deve retornar as informações transmitidas para o método por meio de `drive` parâmetro. Se a unidade não pode ser removida, o método deve gravar uma exceção e, em seguida, retornar `null`. Se seu provedor não substitui esse método, a implementação padrão desse método retorna apenas as informações de unidade passadas como entrada.

## <a name="initializing-default-drives"></a>Unidades de inicialização padrão

Seu implementa de provedor de unidade do [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método montar unidades. Por exemplo, o provedor do Active Directory pode montar uma unidade para o contexto de nomenclatura se o computador tiver ingressado em um domínio padrão.

Esse método retorna uma coleção de informações sobre as unidades inicializadas da unidade ou uma coleção vazia. A chamada para esse método é feita após a tempo de execução do Windows PowerShell chama o [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para inicializar o provedor.

Este provedor de unidade não substitui o [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método. No entanto, o código a seguir mostra a implementação do padrão, que retorna uma coleção vazia de unidade:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Itens a lembrar sobre a implementação InitializeDefaultDrives

Todos os provedores de unidade devem montar uma unidade de raiz para ajudar o usuário com capacidade de descoberta. A unidade raiz pode listar os locais que servem como raízes para outras unidades montadas. Por exemplo, o provedor do Active Directory pode criar uma unidade que lista os contextos de nomenclatura encontrados no `namingContext` atributos na raiz do ambiente do sistema distribuído (DSE). Isso ajuda os usuários a descobrir os pontos de montagem para outras unidades.

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Testando o provedor de unidade do PowerShell do Windows

Quando o provedor do Windows PowerShell tiver sido registrado com o Windows PowerShell, você pode testá-lo, executando os cmdlets com suporte na linha de comando, incluindo qualquer cmdlets disponibilizados por derivação. Vamos testar o provedor de unidade de exemplo.

1. Execute o `Get-PSProvider` cmdlet para recuperar a lista de provedores para garantir que o provedor da unidade AccessDB está presente:

   **PS> `Get-PSProvider`**

   A seguinte saída é exibida:

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Certifique-se de que um nome de servidor de banco de dados (DSN) existe para o banco de dados, acessando o **fontes de dados** parte a **ferramentas administrativas** para o sistema operacional. No **DSN de usuário** da tabela, clique duas vezes em **banco de dados do MS Access** e adicione o caminho de unidade C:\ps\northwind.mdb.

3. Crie uma nova unidade usando o provedor de unidade de exemplo:

   **PS > new-psdrive-mydb nome-raiz c:\ps\northwind.mdb - psprovider AccessDb**

   A seguinte saída é exibida:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Valide a conexão. Como a conexão é definida como um membro da unidade, você pode verificar usando o cmdlet Get-PDDrive.

   > [!NOTE]
   > O usuário ainda não é possível interagir com o provedor como uma unidade, como o provedor precisa de funcionalidade de contêiner para a interação. Para obter mais informações, consulte [criando um provedor de contêiner do Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

   **PS > .connection (get-psdrive mydb)**

   A seguinte saída é exibida:

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. Remova a unidade e sair do shell:

   **PS > remove-psdrive mydb**

   **PS > Sair**

## <a name="see-also"></a>Consulte Também

[Criação de provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Projetar seu provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Criar um provedor de PowerShell do Windows básico](./creating-a-basic-windows-powershell-provider.md)