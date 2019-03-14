---
title: Visão geral do Windows PowerShell provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 0d4addc0a064873701ae15c204dbd335f3374ab7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795616"
---
# <a name="windows-powershell-provider-overview"></a>Visão geral do provedor do Windows PowerShell

Um provedor do Windows PowerShell permite que qualquer armazenamento de dados a ser exposta como um sistema de arquivos, como se fosse uma unidade montada. Por exemplo, o provedor de registro interno permite que você navegue no registro, como você navegaria o `c` unidade do computador. Um provedor também pode substituir a `Item` cmdlets (por exemplo, `Get-Item`, `Set-Item`, etc.), de modo que os dados em seu armazenamento de dados podem ser tratados como arquivos e diretórios são tratados ao navegar em um sistema de arquivos. Para obter mais informações sobre os provedores internos no Windows PowerShell, unidades e provedores, consulte [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Provedores e unidades

Um provedor define a lógica que é usada para acessar, navegar e editar um armazenamento de dados, enquanto uma unidade Especifica um ponto de entrada específica para um armazenamento de dados (ou uma parte de um armazenamento de dados) que é do tipo definido pelo provedor. Por exemplo, o provedor Registry permite acessar seções e chaves em um registro, e as unidades HKLM e HKCU especificam as seções correspondentes no registro. As unidades HKLM e HKCU usam o provedor de registro.

Quando você escreve um provedor, você pode especificar unidades-unidades padrão que são criadas automaticamente quando o provedor está disponível. Você também pode definir um método para criar novas unidades que usam esse provedor.

## <a name="type-of-providers"></a>Tipo de provedores

Há vários tipos de provedores, cada uma delas fornece um nível de funcionalidade diferente. Um provedor é implementado como uma classe que deriva de um dos descendentes de [System.Management.Automation.Sessionstatecategory.Cmdletprovider](/dotnet/api/System.Management.Automation.SessionStateCategory.CmdletProvider) classe. Para obter informações sobre os diferentes tipos de provedores, consulte [tipos de provedor](./provider-types.md).

## <a name="provider-cmdlets"></a>Cmdlets do provedor

Provedores podem implementar métodos que correspondem aos cmdlets, criando comportamentos personalizados para os cmdlets quando usado em uma unidade de provedor. Dependendo do tipo de provedor, diferentes conjuntos de cmdlets estão disponíveis. Para obter uma lista completa dos cmdlets disponíveis para personalização de provedores, consulte [cmdlets do provedor](./provider-cmdlets.md).

## <a name="provider-paths"></a>Caminhos de provedor

Os usuários navegam unidades de provedor, como sistemas de arquivos. Por isso, eles esperam a sintaxe de caminhos para corresponder aos caminhos usados na navegação no sistema de arquivos. Quando um usuário executa um cmdlet do provedor, eles especificarem um caminho para o item a ser acessado. O caminho especificado pode ser interpretado de várias maneiras. Um provedor deve oferecer suporte a um ou mais dos seguintes tipos de caminho.

### <a name="drive-qualified-paths"></a>Caminhos qualificadas pela unidade

Um caminho qualificado a unidade é uma combinação da unidade do Windows PowerShell por meio do qual o item for acessado, o contêiner e sub-recipientes na qual o item está localizado e o nome do item. (As unidades são definidas pelo provedor que é usado para acessar o armazenamento de dados. Esse caminho inicia com o nome da unidade seguido por dois-pontos (:). Por exemplo: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Caminhos de provedor qualificado

Para permitir que o mecanismo do Windows PowerShell inicializar e cancelar a inicialização de seu provedor, o provedor deve oferecer suporte a um caminho qualificado pelo provedor. Por exemplo, o usuário pode inicializar e inicializar o provedor FileSystem porque define o seguinte caminho de provedor qualificado: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Caminhos diretos do provedor

Para permitir o acesso remoto ao seu provedor do Windows PowerShell, ele deve dar suporte a um caminho direto de provedor de passar diretamente para o provedor do Windows PowerShell para o local atual. Por exemplo, o provedor de registro do Windows PowerShell pode usar `\\server\regkeypath` como um caminho direto de provedor.

### <a name="provider-internal-paths"></a>Caminhos de provedor interno

Para permitir que o cmdlet do provedor acessar dados usando interfaces de programação de aplicativo (APIs) do não sejam do Windows PowerShell, o provedor do Windows PowerShell deve dar suporte a um caminho de provedor interno. Esse caminho é indicado após o "::" no caminho de provedor qualificado. Por exemplo, o caminho de provedor interno para o provedor do sistema de arquivos do Windows PowerShell é `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Substituindo parâmetros do cmdlet

O comportamento de alguns cmdlets específicos do provedor pode ser substituído por um provedor. Para obter uma lista de parâmetros que podem ser substituídas e como substituí-las em sua classe de provedor, consulte [parâmetros de cmdlet do provedor](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Parâmetros dinâmicos

Provedores podem definir parâmetros dinâmicos que são adicionados a um cmdlet do provedor quando o usuário Especifica um valor determinado para um dos parâmetros estáticos do cmdlet. Um provedor faz isso Implementando um ou mais métodos de parâmetro dinâmico. Para obter uma lista de parâmetros de cmdlet que pode ser usado para adicionar o parâmetro dinâmico e os métodos usados para implementá-las, consulte [parâmetros dinâmicos do provedor cmdlet](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Recursos do provedor

O [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração define uma série de recursos que podem dar suporte a provedores. Isso inclui a capacidade de usar caracteres curinga, filtrar itens e oferece suporte a transações. Para especificar recursos para um provedor, adicione uma lista de valores da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração, combinada com uma lógica `OR` operação, como o [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) propriedade (o segundo parâmetro do atributo) a [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo para a sua classe de provedor. Por exemplo, o seguinte atributo especifica que o provedor oferece suporte a [System.Management.Automation.Provider.Providercapabilities.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.ShouldProcess) e [ System.Management.Automation.Provider.Providercapabilities.Transactions](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.Transactions) recursos.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Ajuda de cmdlet do provedor

Ao escrever um provedor, você pode implementar sua própria ajuda para os cmdlets do provedor que dão suporte a você. Isso inclui um único tópico de ajuda para cada cmdlet do provedor ou várias versões de um tópico de ajuda para casos em que o cmdlet do provedor atua variam de acordo com o uso de parâmetros dinâmicos. Para dar suporte a Ajuda de cmdlet específico do provedor, o provedor deve implementar o [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) interface.

As chamadas de mecanismo do Windows PowerShell a [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) método para exibir o tópico da Ajuda para seus cmdlets do provedor. O mecanismo fornece o nome do cmdlet que o usuário especificado ao executar o `Get-Help` cmdlet e o caminho atual do usuário. O caminho atual será necessário se seu provedor implementa as versões diferentes do mesmo provedor cmdlet para unidades diferentes. O método deve retornar uma cadeia de caracteres que contém o XML para o cmdlet Help.

O conteúdo para o arquivo de Ajuda é gravado usando PSMAML XML. Isso é o mesmo esquema XML que é usado para gravar o conteúdo da Ajuda para cmdlets autônomo. Adicione o conteúdo de sua ajuda para o arquivo de ajuda para o seu provedor de cmdlet personalizado sob o `CmdletHelpPaths` elemento. A exemplo a seguir mostra o `command` elemento para um cmdlet do provedor única e ele mostra como especificar o nome do provedor cmdlet que seu provedor. Dá suporte a

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>Consulte Também

[Funcionalidade de provedor do PowerShell do Windows](./provider-types.md)

[Cmdlets do provedor](./provider-cmdlets.md)

[Escrevendo um provedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)