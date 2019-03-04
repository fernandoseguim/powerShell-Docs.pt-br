---
title: Diretrizes de desenvolvimento consultoria | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 97a2d3587f8f69edc92150474e94a620ff9a2f71
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854542"
---
# <a name="advisory-development-guidelines"></a>Diretrizes para desenvolvimento de consultoria

Esta seção descreve as diretrizes que você deve considerar para garantir o bom experiências do usuário e de desenvolvimento. Às vezes, eles podem se aplicar, e, às vezes, eles não podem.

## <a name="design-guidelines"></a>Diretrizes de design

- [Suporte para um parâmetro InputObject (AD01)](./advisory-development-guidelines.md#AD01)

- [Suporte para o parâmetro Force (AD02)](./advisory-development-guidelines.md#AD02)

- [Lidar com as credenciais por meio do Windows PowerShell (AD03)](./advisory-development-guidelines.md#AD03)

- [Oferece suporte a parâmetros de codificação (AD04)](./advisory-development-guidelines.md#AD04)

- [Cmdlets de teste deve retornar um valor booliano (AD05)](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a>Diretrizes de código

- [Siga as convenções de nomenclatura de classe Cmdlet (AC01)](./advisory-development-guidelines.md#AC01)

- [Se nenhuma entrada do Pipeline substituir o método BeginProcessing (AC02)](./advisory-development-guidelines.md#AC02)

- [Para lidar com solicitações de interrupção de substituem o método StopProcessing (AC03)](./advisory-development-guidelines.md#AC03)

- [Implementar a Interface IDisposable (AC04)](./advisory-development-guidelines.md#AC04)

- [Usar tipos de parâmetro amigável à serialização (AC05)](./advisory-development-guidelines.md#AC05)

- [Use SecureString para dados confidenciais (AC06)](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a>Diretrizes de design

As diretrizes a seguir devem ser consideradas ao criar cmdlets. Quando você encontrar uma diretriz de Design que se aplica à sua situação, certifique-se de examinar as diretrizes de código para obter diretrizes semelhantes.

### <a name="support-an-inputobject-parameter-ad01"></a>Suporte para um parâmetro InputObject (AD01)

Como o Windows PowerShell funciona diretamente com objetos do Microsoft .NET Framework, um objeto do .NET Framework costuma estar disponível que corresponda exatamente ao tipo de usuário precisa executar uma operação específica. `InputObject` é o nome padrão para um parâmetro que usa esse objeto como entrada. Por exemplo, a amostra **Stop-Proc** cmdlet na [StopProc Tutorial](./stopproc-tutorial.md) define um `InputObject` parâmetro de tipo de processo que dá suporte à entrada do pipeline. O usuário pode obter um conjunto de objetos de processo, manipulá-los para selecionar os objetos exatos para interromper e, em seguida, passá-los para o **Stop-Proc** cmdlet diretamente.

### <a name="support-the-force-parameter-ad02"></a>Suporte para o parâmetro Force (AD02)

Ocasionalmente, um cmdlet precisa proteger o usuário de executar uma operação solicitada. Deve dar suporte a um cmdlet tal um `Force` parâmetro para permitir que o usuário substitua essa proteção se o usuário tem permissões para executar a operação.

Por exemplo, o [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet não remove normalmente um arquivo somente leitura. No entanto, esse cmdlet dá suporte a um `Force` parâmetro para que um usuário pode forçar a remoção de um arquivo somente leitura. Se o usuário já tem permissão para modificar o atributo somente leitura, e o usuário remove o arquivo, use o `Force` parâmetro simplifica a operação. No entanto, se o usuário não tem permissão para remover o arquivo, o `Force` parâmetro não tem nenhum efeito.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Lidar com as credenciais por meio do Windows PowerShell (AD03)

Um cmdlet deve definir um `Credential` parâmetro para representar as credenciais. Esse parâmetro deve ser do tipo [pscredential](/dotnet/api/System.Management.Automation.PSCredential) e devem ser definidas usando uma declaração de atributo de credencial. Esse suporte automaticamente solicita ao usuário para o nome de usuário, a senha ou para ambos, quando uma credencial completa não é fornecida diretamente. Para obter mais informações sobre o atributo de credencial, consulte [declaração de atributo de credencial](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Oferece suporte a parâmetros de codificação (AD04)

Se seu cmdlet lê ou grava texto ou de um formato binário, como gravar ou ler um arquivo em um sistema de arquivos, o cmdlet deve ter o parâmetro de codificação que especifica como o texto está codificado no formato binário.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Cmdlets de teste deve retornar um valor booliano (AD05)

Cmdlets que executam testes em relação a seus recursos deve retornar um [System. Boolean](/dotnet/api/System.Boolean) tipo para o pipeline, de forma que eles podem ser usados em expressões condicionais.

## <a name="code-guidelines"></a>Diretrizes de código

As diretrizes a seguir devem ser consideradas ao escrever o código do cmdlet. Quando você encontrar uma diretriz que se aplica à sua situação, certifique-se de examinar as diretrizes de Design para obter diretrizes semelhantes.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Siga as convenções de nomenclatura de classe Cmdlet (AC01)

Por seguir convenções de nomenclatura padrão, você fazer seus cmdlets mais detectáveis e ajudar o usuário a entender exatamente o que os cmdlets fazem. Essa prática é particularmente importante para outros desenvolvedores usando o Windows PowerShell porque os cmdlets são tipos públicos.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Definir um Cmdlet no Namespace correto

Você normalmente define a classe para um cmdlet em um namespace do .NET Framework que acrescenta ". Comandos"para o namespace que representa o produto no qual o cmdlet é executado. Por exemplo, os cmdlets que estão incluídos com o Windows PowerShell são definidos na `Microsoft.PowerShell.Commands` namespace.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Nomeie a classe do Cmdlet para corresponder ao nome do Cmdlet

Ao nomear a classe do .NET Framework que implementa um cmdlet, nomeie a classe "*\<verbo >**\<substantivo >**\<comando >*", em que você substitua o  *\<Verbo >* e  *\<substantivo >* espaços reservados com o verbo e substantivo usado para o nome do cmdlet. Por exemplo, o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet é implementado por uma classe chamada `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Se nenhuma entrada do Pipeline substituir o método BeginProcessing (AC02)

Se seu cmdlet não aceita entrada do pipeline, o processamento deve ser implementado na [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método. O uso desse método permite que o Windows PowerShell manter a ordem entre os cmdlets. O primeiro cmdlet no pipeline sempre retorna seus objetos antes dos cmdlets restantes no pipeline de obter a oportunidade de começar seu processamento.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Para lidar com solicitações de interrupção de substituem o método StopProcessing (AC03)

Substituir a [System.Management.Automation.Cmdlet.Stopprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) método para que seu cmdlet pode lidar com sinal de parada. Alguns cmdlets levar muito tempo para concluir sua operação, e eles permitem que um longo tempo passe entre as chamadas para o tempo de execução do Windows PowerShell, como quando o cmdlet bloqueia o thread em chamadas RPC de longa execução. Isso inclui cmdlets que fazem chamadas para o [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método, para o [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método e outros comentários mecanismos que podem levar muito tempo para ser concluída. Nesses casos, o usuário talvez precise enviar um sinal de parada para esses cmdlets.

### <a name="implement-the-idisposable-interface-ac04"></a>Implementar a Interface IDisposable (AC04)

Se seu cmdlet tiver objetos que não são descartados de (gravado no pipeline) o [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, seu cmdlet pode exigir a disposição do objeto adicionais. Por exemplo, se seu cmdlet abre um identificador de arquivo em seu [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método e mantém o identificador aberto para uso pelo [System.Management.Automation.Cmdlet.Processrecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, esse identificador deve ser fechado no final do processamento.

O tempo de execução do Windows PowerShell nem sempre chama a [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Por exemplo, o [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método não pode ser chamado se o cmdlet foi cancelado no Centro por meio de sua operação ou se um encerramento ocorrerá erro em qualquer parte do cmdlet. Portanto, a classe do .NET Framework para um cmdlet que requer a limpeza do objeto deve implementar completo [System. IDisposable](/dotnet/api/System.IDisposable) padrão de interface, incluindo o finalizador, para que o tempo de execução do Windows PowerShell possa chamar ambos o [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) métodos no final do processamento.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Usar tipos de parâmetro amigável à serialização (AC05)

Para dar suporte a executar o cmdlet em computadores remotos, use os tipos que podem ser facilmente serializados no computador cliente e, em seguida, reidratados no computador do servidor. Os tipos de acompanhamento são amigável à serialização.

Tipos primitivos:

- Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 e UInt64.

- Valor booliano, Guid, Byte [], período de tempo, DateTime, Uri e versão.

- XmlDocument de char, cadeia de caracteres.

Tipos de rehydratable internos:

- PSPrimitiveDictionary

- SwitchParmeter

- PSListModifier

- PSCredential

- IPAddress, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- RegistrySecurity DirectorySecurity, FileSecurity,

Outros tipos:

- SecureString

- Contêineres (listas e dicionários do tipo acima)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Use SecureString para dados confidenciais (AC06)

Ao lidar com dados confidenciais sempre usar o [SecureString](/dotnet/api/System.Security.SecureString) tipo de dados. Isso pode incluir parâmetros, bem como retornar dados confidenciais para o pipeline de entrada do pipeline.

## <a name="see-also"></a>Consulte Também

[Diretrizes de desenvolvimento necessárias](./required-development-guidelines.md)

[Diretrizes de desenvolvimento altamente incentivados](./strongly-encouraged-development-guidelines.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
