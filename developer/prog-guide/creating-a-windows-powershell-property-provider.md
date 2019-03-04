---
title: Criar um provedor de propriedade PowerShell do Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: ade8fbd38e4f4a675e825b0d8850af0379c9d211
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858892"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Criar um provedor de propriedade do Windows PowerShell

Este tópico descreve como criar um provedor que permite ao usuário manipular as propriedades dos itens em um repositório de dados. Como consequência, esse tipo de provedor é referido como um provedor de propriedade do Windows PowerShell. Por exemplo, o provedor de registro fornecido pelos valores de chave do registro do Windows PowerShell identificadores como propriedades do item da chave do registro. Esse tipo de provedor deve adicionar o [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface para a implementação da classe do .NET.

> [!NOTE]
> Windows PowerShell fornece um arquivo de modelo que você pode usar para desenvolver um provedor do Windows PowerShell. O arquivo TemplateProvider.cs está disponível no Microsoft Windows Software Development Kit para Windows Vista e .NET Framework 3.0 Runtime Components. Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Windows PowerShell fornece um arquivo de modelo que você pode usar para desenvolver um provedor do Windows PowerShell. O arquivo TemplateProvider.cs está disponível no Microsoft Windows Software Development Kit para Windows Vista e .NET Framework 3.0 Runtime Components. Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> O modelo baixado está disponível na  **\<amostras do PowerShell >** directory. Você deve fazer uma cópia desse arquivo e usar a cópia para criar um novo provedor do Windows PowerShell, removendo qualquer funcionalidade que não é necessário.
>
> Para obter mais informações sobre outras implementações do provedor do Windows PowerShell, consulte [projetando seu provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Os métodos do seu provedor de propriedade devem gravar todos os objetos usando o [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) método.

A lista a seguir contém as seções neste tópico. Se você estiver familiarizado com a gravação de um provedor de propriedade do Windows PowerShell, leia essas informações na ordem em que ele é exibido. No entanto, se você estiver familiarizado com a gravação de um provedor de propriedade do Windows PowerShell, vá diretamente para as informações que você precisa.

- [Definindo o provedor do Windows PowerShell](#Defining-the-Windows-PowerShell-provider)

- [Definindo a funcionalidade de Base](#Defining-Base-Functionality)

- [Recuperando propriedades](#Retrieving-Properties)

- [Anexando parâmetros dinâmicos para a `Get-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [Propriedades de configuração](#Setting-Properties)

- [Anexando parâmetros dinâmicos para a `Set-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [Limpando a uma propriedade](#Clearing-Properties)

- [Anexando parâmetros dinâmicos para a `Clear-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [Criando o provedor do Windows PowerShell](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>Definindo o provedor do Windows PowerShell

Um provedor de propriedade deve criar uma classe .NET que oferece suporte a [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface. Aqui está a declaração de classe padrão do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definindo a funcionalidade de Base

O [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface pode ser anexado a qualquer uma das classes base do provedor, com exceção do [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. Adicione a funcionalidade básica que é exigida pela classe base que você está usando. Para obter mais informações sobre classes base, consulte [projetando seu provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Recuperando propriedades

Para recuperar as propriedades, o provedor deve implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) método para dar suporte a chamadas a partir de `Get-ItemProperty` cmdlet. Esse método recupera as propriedades do item localizado no caminho do provedor interno especificado (totalmente qualificado).

O `providerSpecificPickList` parâmetro indica quais propriedades a serem recuperadas. Se esse parâmetro for `null` ou estiver vazio, o método deve recuperar todas as propriedades. Além disso, [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) grava uma instância de um [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objeto que representa um recipiente de propriedades recuperadas. O método deve retornar nada.

É recomendável que a implementação de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) dá suporte a expansão de curinga de nomes de propriedade para cada elemento na lista de opções. Para fazer isso, use o [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) classe para executar a correspondência de padrões de curinga.

Aqui está a implementação padrão de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Itens a lembrar sobre a implementação GetProperty

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Ao definir a classe de provedor, um provedor de propriedade do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) método precisa garantir que o caminho passado para o método atenda aos requisitos do especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem recuperar um leitor para os objetos que são ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser escrito se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é definido como `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Get-ItemProperty

O `Get-ItemProperty` cmdlet pode exigir parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de propriedade do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) método. O `path` parâmetro indica um caminho totalmente qualificado do provedor interno, enquanto o `providerSpecificPickList` parâmetro especifica as propriedades específicas do provedor inseridas na linha de comando. Esse parâmetro pode ser `null` ou vazio se as propriedades são canalizadas para o cmdlet. Nesse caso, esse método retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto retornado para adicionar os parâmetros para o cmdlet.

Aqui está a implementação padrão de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Propriedades de configuração

Para definir propriedades, o provedor de propriedade do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método para dar suporte a chamadas do `Set-ItemProperty` cmdlet. Esse método define uma ou mais propriedades do item no caminho especificado e substitui as propriedades fornecidas conforme necessário. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) também grava uma instância de um [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objeto que representa um conjunto de propriedades atualizado Propriedades.

Aqui está a implementação padrão de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Itens a lembrar sobre a implementação do Set-ItemProperty

As seguintes condições podem se aplicar a uma implementação de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Ao definir a classe de provedor, um provedor de propriedade do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método deve garantir que o caminho passado para o método atende aos requisitos de especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem recuperar um leitor para os objetos que são ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser escrito se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é definido como `false`.

- Sua implementação do [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método deve chamar [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique se o valor retornado antes de fazer alterações ao repositório de dados. Esse método é usado para confirmar a execução de uma operação quando uma alteração é feita ao estado do sistema, por exemplo, renomear os arquivos. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envia o nome do recurso a ser alterado para o usuário, com o tempo de execução do Windows PowerShell e o tratamento de quaisquer configurações de linha de comando ou variáveis de preferência em Determinando o que deve ser exibido.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna `true`, se podem ser feitas modificações no sistema potencialmente perigosos, o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Esse método envia uma mensagem de confirmação para o usuário para permitir que os comentários adicionais indicar que a operação deve continuar.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Set-ItemProperty

O `Set-ItemProperty` cmdlet pode exigir parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de propriedade do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) método. Esse método retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O `null` valor pode ser retornado se não há parâmetros dinâmicos devem ser adicionados.

Aqui está a implementação padrão de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Limpar propriedades

Para limpar as propriedades, o provedor de propriedade do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método para dar suporte a chamadas do `Clear-ItemProperty` cmdlet. Esse método define uma ou mais propriedades para o item localizado no caminho especificado.

Aqui está a implementação padrão de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Lembrar-se sobre como implementar ClearProperty

As seguintes condições podem ser aplicáveis à sua implementação de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Ao definir a classe de provedor, um provedor de propriedade do Windows PowerShell pode declarar recursos de provedor de ExpandWildcards, filtro, incluir ou excluir, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nesses casos, a implementação de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método precisa garantir que o caminho passado para o método atenda aos requisitos do especificado recursos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por padrão, substituições desse método não devem recuperar um leitor para os objetos que são ocultados do usuário, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser escrito se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é definido como `false`.

- Sua implementação do [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método deve chamar [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique se o valor retornado antes de fazer alterações ao repositório de dados. Esse método é usado para confirmar a execução de uma operação antes que uma alteração é feita ao estado do sistema, como limpar o conteúdo. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envia o nome do recurso a ser alterado para o usuário, com o tempo de execução do Windows PowerShell levando em consideração quaisquer configurações de linha de comando ou variáveis de preferência em Determinando o que deve ser exibido.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna `true`, se podem ser feitas modificações no sistema potencialmente perigosos, o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Esse método envia uma mensagem de confirmação para o usuário para permitir que os comentários adicionais indicar que a operação potencialmente perigosa deve continuar.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Anexando parâmetros dinâmicos para o Cmdlet Clear-ItemProperty

O `Clear-ItemProperty` cmdlet pode exigir parâmetros adicionais que são especificados dinamicamente em tempo de execução. Para fornecer esses parâmetros dinâmicos, o provedor de propriedade do Windows PowerShell deve implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) método. Esse método retorna um objeto que tem propriedades e campos com análise de atributos, semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O `null` valor pode ser retornado se não há parâmetros dinâmicos devem ser adicionados.

Aqui está a implementação padrão de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Criando o provedor do Windows PowerShell

Ver [como registrar Cmdlets, provedores e hospedar aplicativos](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).
Ver [como registrar Cmdlets, provedores e hospedar aplicativos](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Consulte Também

[Provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Provedor de PowerShell do Windows seu design](./designing-your-windows-powershell-provider.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)