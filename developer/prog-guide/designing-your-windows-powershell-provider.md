---
title: Criando o provedor do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429934"
---
# <a name="designing-your-windows-powershell-provider"></a>Projetar seu provedor do Windows PowerShell

Se o produto ou a configuração expõe um conjunto de dados armazenados, como um banco de dados que o usuário desejará navegam, você deve implementar um provedor do Windows PowerShell. Além disso, se o seu produto fornece um contêiner, mesmo se ele não é um contêiner de vários níveis, faz sentido implementar um provedor do Windows PowerShell. Por exemplo, você talvez queira implementar um provedor de contêiner do Windows PowerShell se cmdlet verbo copiar, mover, renomear, novo ou remover faz sentido como uma operação em seus dados de configuração ou o produto.

## <a name="windows-powershell-paths-identify-your-provider"></a>Caminhos do Windows PowerShell identificam seu provedor

O tempo de execução do Windows PowerShell usa caminhos do Windows PowerShell para acessar o provedor apropriado do Windows PowerShell. Quando um cmdlet especifica um desses caminhos, o tempo de execução sabe qual provedor será usado para acessar o armazenamento de dados associado. Esses caminhos incluem caminhos qualificadas pela unidade, caminhos de provedor qualificado, caminhos diretos do provedor e caminhos de provedor interno. Cada provedor do Windows PowerShell deve oferecer suporte a um ou mais desses caminhos.

Para obter mais informações sobre os caminhos do Windows PowerShell, consulte como funciona o Windows PowerShell.

### <a name="defining-a-drive-qualified-path"></a>Definindo um caminho qualificado por unidade

Para permitir que o usuário acesse dados localizados em uma unidade física, o provedor do Windows PowerShell deve dar suporte a um caminho qualificado por unidade. Esse caminho inicia com o nome da unidade seguido por dois-pontos (:), por exemplo, mydrive:\abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definindo um caminho qualificado provedor

Para permitir que o tempo de execução do Windows PowerShell inicializar e inicializar o provedor, o provedor do Windows PowerShell deve dar suporte a um caminho qualificado pelo provedor. Por exemplo, sistema de arquivos::\\\uncshare\abc\bar é o caminho de provedor qualificado para o provedor do sistema de arquivos fornecido pelo Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Definindo um caminho direto de provedor

Para permitir o acesso remoto ao seu provedor do Windows PowerShell, ele deve dar suporte a um caminho direto de provedor de passar diretamente para o provedor do Windows PowerShell para o local atual. Por exemplo, o provedor de registro do Windows PowerShell pode usar \\\server\regkeypath como um caminho direto de provedor.

### <a name="defining-a-provider-internal-path"></a>Definindo um caminho de provedor interno

Para permitir que o cmdlet do provedor acessar dados usando interfaces de programação de aplicativo (APIs) do não sejam do Windows PowerShell, o provedor do Windows PowerShell deve dar suporte a um caminho de provedor interno. Esse caminho é indicado após o "::" no caminho de provedor qualificado. Por exemplo, o caminho de provedor interno para o provedor do sistema de arquivos do Windows PowerShell é \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Alterando dados armazenados

Ao substituir métodos que modificam o armazenamento de dados subjacente, sempre chamar o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método com a versão mais atualizada do item alterado por que método. A infraestrutura do provedor determina se o objeto do item precisa ser passado para o pipeline, como quando o usuário Especifica o parâmetro - PassThru. Se recuperar o item mais atualizado é uma operação cara (em termos de desempenho), você pode testar a propriedade Context.PassThru para determinar se você realmente precisa escrever o item resultante.

## <a name="choose-a-base-class-for-your-provider"></a>Escolha uma classe Base para o seu provedor

Windows PowerShell fornece um número de classes base que você pode usar para implementar seu próprio provedor do Windows PowerShell. Ao criar um provedor, escolha a classe base, descrita nesta seção, que é mais adequada às suas necessidades.

Cada classe de base do provedor do Windows PowerShell disponibiliza um conjunto de cmdlets. Esta seção descreve os cmdlets, mas ele não descreve seus parâmetros.

Usando o estado de sessão, o tempo de execução do Windows PowerShell disponibiliza vários cmdlets do local para certos provedores do Windows PowerShell, como o `Get-Location`, `Set-Location`, `Pop-Location`, e `Push-Location` cmdlets. Você pode usar o `Get-Help` cmdlet para obter informações sobre esses cmdlets de local.

### <a name="cmdletprovider-base-class"></a>Classe base CmdletProvider

O [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe define um provedor básico do Windows PowerShell. Esta classe oferece suporte à declaração do provedor e fornece um número de propriedades e métodos que estão disponíveis para todos os provedores do Windows PowerShell. A classe é invocada com o `Get-PSProvider` cmdlet para listar todos os provedores disponíveis para uma sessão. A implementação desse cmdlet é fornecida pelo estado de sessão.

> [!NOTE]
> Provedores do Windows PowerShell estão disponíveis para todos os escopos de linguagem do Windows PowerShell.

### <a name="drivecmdletprovider-base-class"></a>Classe base DriveCmdletProvider

O [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe define um provedor de unidade do Windows PowerShell que dá suporte a operações de adicionando novas unidades, removendo as unidades existentes e inicializando unidades padrão. Por exemplo, o provedor FileSystem fornecido pelo Windows PowerShell inicializa unidades para todos os volumes são montados como discos rígidos e unidades de dispositivo de CD/DVD.

Essa classe deriva de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe base. A tabela a seguir lista os cmdlets expostos por esta classe. Além das listadas, o `Get-PSDrive` cmdlet (exposto pelo estado de sessão) é um cmdlet relacionado que é usado para recuperar as unidades disponíveis.

|Cmdlet|Definição|
|------------|----------------|
|`New-PSDrive`|Cria uma nova unidade para a sessão e transmite as informações da unidade.|
|`Remove-PSDrive`|Remove uma unidade da sessão.|

### <a name="itemcmdletprovider-base-class"></a>Classe base ItemCmdletProvider

O [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe define um provedor de item do Windows PowerShell que executa operações em itens individuais do repositório de dados, e não assume nenhum contêiner ou recursos de navegação. Essa classe deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base. A tabela a seguir lista os cmdlets expostos por esta classe.

|Cmdlet|Definição|
|------------|----------------|
|`Clear-Item`|Limpa o conteúdo atual de itens no local especificado e substitui-lo com o valor de "Limpar" especificado pelo provedor. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Get-Item`|Recupera itens do local especificado e, em seguida, transmite os objetos resultantes.|
|`Invoke-Item`|Invoca a ação padrão para o item no caminho especificado.|
|`Set-Item`|Define um item no local especificado com o valor indicado. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Resolve-Path`|Resolve os caracteres curinga para um caminho do Windows PowerShell e informações de caminho de fluxos.|
|`Test-Path`|Testa o caminho especificado e retorna `true` caso ele exista e `false` caso contrário. Esse cmdlet é implementado para dar suporte a `IsContainer` parâmetro para o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.|

### <a name="containercmdletprovider-base-class"></a>Classe base ContainerCmdletProvider

O [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe define um provedor de contêiner do Windows PowerShell que expõe um contêiner, para itens de repositório de dados para o usuário. Lembre-se de que um provedor de contêiner do Windows PowerShell pode ser usado somente quando há um contêiner (não há contêineres aninhados) com itens nele. Se houver contêineres aninhados, você deve implementar um provedor de navegação do Windows PowerShell.

Essa classe deriva de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe base. A tabela a seguir define os cmdlets implementados por esta classe.

|Cmdlet|Definição|
|------------|----------------|
|`Copy-Item`|Copia os itens de um local para outro. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Get-Childitem`|Recupera os itens filho no local especificado e, em seguida, transmite-os como objetos.|
|`New-Item`|Cria novos itens no local especificado e, em seguida, transmite o objeto resultante.|
|`Remove-Item`|Remove itens do local especificado.|
|`Rename-Item`|Renomeia um item no local especificado. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|

### <a name="navigationcmdletprovider-base-class"></a>Classe base NavigationCmdletProvider

O [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe define um provedor de navegação do Windows PowerShell que executa operações para itens que usam mais de um contêiner. Essa classe deriva de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe base. A tabela a seguir lista os cmdlets expostos por esta classe.

|Cmdlet|Definição|
|------------|----------------|
|Combinar caminhos|Combina dois caminhos em um único caminho, usando um delimitador específico do provedor entre caminhos. Esse cmdlet transmite as cadeias de caracteres.|
|`Move-Item`|Move os itens no local especificado. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|

Um cmdlet relacionado é o cmdlet do caminho de análise básico fornecido pelo Windows PowerShell. Esse cmdlet pode ser usado para analisar um caminho do Windows PowerShell para dar suporte a `Parent` parâmetro. Ela transmite a cadeia de caracteres de caminho pai.

## <a name="select-provider-interfaces-to-support"></a>Selecione as Interfaces de provedor para suporte

Além de derivar de uma das classes base do Windows PowerShell, o provedor do Windows PowerShell pode dar suporte a outras funcionalidades, derivando de uma ou mais das seguintes interfaces de provedor. Esta seção define as interfaces e os cmdlets com suporte de cada. Ele descreve os parâmetros para os cmdlets de interface tem suporte. Informações de parâmetro de cmdlet estão disponíveis online usando o `Get-Command` e `Get-Help` cmdlets.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

O [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface define um provedor de conteúdo que executa operações no conteúdo de um item de dados. A tabela a seguir lista os cmdlets expostos por esta interface.

|Cmdlet|Definição|
|------------|----------------|
|`Add-Content`|Acrescenta os comprimentos de valor indicado para o conteúdo do item especificado. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Clear-Content`|Define o conteúdo do item especificado para o valor "Limpar". Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Get-Content`|Recupera o conteúdo dos itens especificados e transmite os objetos resultantes.|
|`Set-Content`|Substitui o conteúdo existente para os itens especificados. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

O [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface define um provedor do Windows PowerShell de propriedade que executa operações nas propriedades de itens no armazenamento de dados. A tabela a seguir lista os cmdlets expostos por esta interface.

> [!NOTE]
> O `Path` parâmetro sobre esses cmdlets indica um caminho para um item em vez de identificar uma propriedade.

|Cmdlet|Definição|
|------------|----------------|
|`Clear-ItemProperty`|Define as propriedades dos itens especificados para o valor "Limpar". Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Get-ItemProperty`|Recupera as propriedades dos itens especificados e transmite os objetos resultantes.|
|`Set-ItemProperty`|Define as propriedades dos itens especificados com os valores indicados. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interface, derivada de [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), define um provedor que especifica os parâmetros dinâmicos para seus cmdlets com suporte. Esse tipo de provedor lida com operações para os quais propriedades podem ser definidas em tempo de execução, por exemplo, uma nova operação de propriedade. Essas operações não são possíveis em itens de ter definido estaticamente propriedades. A tabela a seguir lista os cmdlets expostos por esta interface.

|Cmdlet|Definição|
|------------|----------------|
|`Copy-ItemProperty`|Copia uma propriedade do item especificado para outro item. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Move-ItemProperty`|Move uma propriedade do item especificado para outro item. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`New-ItemProperty`|Cria uma propriedade nos itens especificados e transmite os objetos resultantes.|
|`Remove-ItemProperty`|Remove uma propriedade para os itens especificados.|
|`Rename-ItemProperty`|Renomeia uma propriedade dos itens especificados. Esse cmdlet não passa um objeto de saída por meio do pipeline, a menos que seu `PassThru` parâmetro for especificado.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

O [System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) interface adiciona a funcionalidade de descritor de segurança para um provedor. Essa interface permite que o usuário obter e definir informações de descritor de segurança para um item no armazenamento de dados. A tabela a seguir lista os cmdlets expostos por esta interface.

|Cmdlet|Definição|
|------------|----------------|
|`Get-Acl`|Recupera as informações contidas em uma lista de controle de acesso (ACL), que é parte de um descritor de segurança usado para proteger recursos do sistema operacional, por exemplo, um arquivo ou um objeto.|
|`Set-Acl`|Define as informações de uma ACL. Ele está na forma de uma instância do [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) no item (NS) designado para o caminho especificado. Esse cmdlet pode definir as informações sobre arquivos, chaves e subchaves no registro, ou qualquer outro item de provedor, se o provedor do Windows PowerShell oferece suporte a configuração de informações de segurança.|

## <a name="see-also"></a>Consulte Também

[Criação de provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Como funciona o Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[SDK do Windows PowerShell](../windows-powershell-reference.md)