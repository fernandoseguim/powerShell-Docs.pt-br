---
title: Criar um provedor de PowerShell do Windows básico | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861762"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Criar um provedor básico do Windows PowerShell

Este tópico é o ponto de partida para aprender a criar um provedor do Windows PowerShell. O provedor básico descrito aqui fornece métodos para iniciar e interromper o provedor e, embora esse provedor não fornece um meio para acessar um armazenamento de dados ou para obter ou definir os dados no armazenamento de dados, ele fornece a funcionalidade básica que é exigida pelo todos os provedores.

Conforme mencionado anteriormente, o provedor básico descrito aqui, implementa métodos para iniciar e interromper o provedor. O tempo de execução do Windows PowerShell chama esses métodos para inicializar e não inicializar o provedor.

> [!NOTE]
> Você pode encontrar um exemplo desse provedor no arquivo AccessDBSampleProvider01.cs fornecido pelo Windows PowerShell.

As seções neste tópico incluem o seguinte:

- [Definição da classe de provedor do PowerShell do Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definindo informações de estado específico do provedor](#Defining-Provider-Specific-State-Information)

- [Inicializando o provedor](#Initializing-the-Provider)

- [Iniciar parâmetros dinâmicos](#Start-Dynamic-Parameters)

- [Cancelando a inicialização do provedor](#Uninitializing-the-Provider)

- [Exemplo de código](#Code-Sample)

- [Testando o provedor do Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definição da classe de provedor do PowerShell do Windows

A primeira etapa na criação de um provedor do Windows PowerShell é definir sua classe do .NET. Esse provedor básico define uma classe chamada `AccessDBProvider` que deriva de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe base.

É recomendável que você coloque suas classes de provedor em um `Providers` namespace do seu namespace de API, por exemplo, xxx. PowerShell.Providers. Este provedor usa o `Microsoft.Samples.PowerShell.Provider` namespace, no qual todas as amostras de provedor do Windows PowerShell é executado.

> [!NOTE]
> A classe para um provedor do Windows PowerShell deve ser explicitamente marcada como pública. Classes não marcadas como público padrão serão interno e não serão encontradas pelo tempo de execução do Windows PowerShell.

Aqui está a definição de classe para este provedor básico:

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Logo antes da definição de classe, você deve declarar o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo, com a sintaxe [CmdletProvider()].

Você pode definir palavras-chave de atributo adicional declarar a classe, se necessário. Observe que o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo declarado aqui inclui dois parâmetros. O primeiro parâmetro de atributo especifica o nome amigável padrão para o provedor, o que o usuário pode modificar posteriormente. O segundo parâmetro especifica os recursos definidos pelo Windows PowerShell que o provedor expõe para o tempo de execução do Windows PowerShell durante o processamento do comando. Os valores possíveis para os recursos do provedor são definidos pela [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Como esse é um provedor de base, ele dá suporte a nenhum recurso.

> [!NOTE]
> O nome totalmente qualificado do provedor do Windows PowerShell inclui o nome do assembly e outros atributos determinados pelo Windows PowerShell no registro do provedor.

## <a name="defining-provider-specific-state-information"></a>Definindo informações de estado específico do provedor

O [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe base e todas as classes derivadas são consideradas sem monitoração de estado porque o tempo de execução do Windows PowerShell cria instâncias do provedor conforme necessário. Portanto, se o provedor requer controle total e a manutenção do estado para dados específicos do provedor, ele deve derivar uma classe do [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) classe. Sua classe derivada deve definir os membros necessários para manter o estado para que os dados específicos do provedor podem ser acessados quando o tempo de execução do Windows PowerShell chama o [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para inicializar o provedor.

Um provedor do Windows PowerShell também pode manter o estado de conexão. Para obter mais informações sobre como manter o estado de conexão, consulte [criando um provedor de unidade do PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Inicializando o provedor

Para inicializar o provedor, o tempo de execução do Windows PowerShell chama o [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método quando o Windows PowerShell é iniciado. Na maior parte, o provedor pode usar a implementação padrão desse método, que simplesmente retorna o [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objeto que descreve seu provedor. No entanto, no caso em que você deseja adicionar informações de inicialização adicional, você deve implementar sua própria [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método que retorna uma versão modificada do [ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objeto que é passado ao provedor. Em geral, esse método deverá retornar fornecido [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objeto passado para ele ou um modificado [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) do objeto contém outras informações de inicialização.

Esse provedor básico não substitui esse método. No entanto, o código a seguir mostra a implementação padrão desse método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

O provedor pode manter o estado de informações específicas do provedor, conforme descrito em [definindo específicas do provedor de dados de estado](#Defining-Provider-Specific-State-Information). Nesse caso, sua implementação deve substituir a [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para retornar uma instância da classe derivada.

## <a name="start-dynamic-parameters"></a>Iniciar parâmetros dinâmicos

Sua implementação de provedor do [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método pode exigir parâmetros adicionais. Nesse caso, o provedor deve substituir a [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) método e retornar um objeto que tem propriedades e campos com a análise de atributos semelhante a um classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.

Esse provedor básico não substitui esse método. No entanto, o código a seguir mostra a implementação padrão desse método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Cancelando a inicialização do provedor

Para liberar os recursos que usa o provedor do Windows PowerShell, o provedor deve implementar seu próprio [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) método. Esse método é chamado pelo tempo de execução do Windows PowerShell para inicializar o provedor no fechamento de uma sessão.

Esse provedor básico não substitui esse método. No entanto, o código a seguir mostra a implementação padrão desse método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Testando o provedor do Windows PowerShell

Depois que o provedor do Windows PowerShell tiver sido registrado com o Windows PowerShell, você pode testá-lo, executando os cmdlets com suporte na linha de comando. Para este provedor básico, execute o novo shell e use o `Get-PSProvider` cmdlet para recuperar a lista de provedores e certifique-se de que o provedor AccessDb está presente.

```powershell
Get-PSProvider
```

A seguinte saída é exibida:

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Consulte Também

[Criação de provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Criando o provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md)