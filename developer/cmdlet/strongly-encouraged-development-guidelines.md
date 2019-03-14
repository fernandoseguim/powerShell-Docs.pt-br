---
title: Altamente incentivado diretrizes de desenvolvimento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: c11e50913d2654b786e0e8cfeaf41454999bf75e
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794955"
---
# <a name="strongly-encouraged-development-guidelines"></a>Diretrizes de desenvolvimento altamente recomendadas

Esta seção descreve as diretrizes que você deve seguir quando você escreve seus cmdlets. Eles são separados em diretrizes para criação de cmdlets e diretrizes para escrever seu código do cmdlet. Você pode achar que essas diretrizes não são aplicáveis para cada cenário. No entanto, se elas se aplicam, e você não seguir essas diretrizes, os usuários podem ter uma experiência ruim quando eles usam seus cmdlets.

## <a name="design-guidelines"></a>Diretrizes de design

- [Use um substantivo específico para um nome de Cmdlet (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Usar Pascal Case para nomes de Cmdlet (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Diretrizes de Design de parâmetro (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Fornecer comentários ao usuário (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Criar um arquivo de ajuda de Cmdlet (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Diretrizes de código

- [Parâmetros de codificação (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Dá suporte à entrada de Pipeline bem definido (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Gravar registros únicos para o Pipeline (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Verifique os Cmdlets diferencia maiusculas de minúsculas e preserva (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Diretrizes de design

As diretrizes a seguir devem ser seguidas durante a criação de cmdlets para garantir uma experiência de usuário consistente entre o uso de seus cmdlets e outros cmdlets. Quando você encontrar uma diretriz de Design que se aplica à sua situação, certifique-se de examinar as diretrizes de código para obter diretrizes semelhantes.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Use um substantivo específico para um nome de Cmdlet (SD01)

Substantivos usados na nomeação do cmdlet precisam ser muito específico para que o usuário possa descobrir seus cmdlets. Prefixo substantivos genéricos como "servidor" com uma versão abreviada do nome do produto. Por exemplo, se um substantivo refere-se a um servidor que está executando uma instância do Microsoft SQL Server, use um substantivo, como "SQLServer". A combinação de substantivos específicos e a lista curta de verbos aprovados permitem ao usuário descobrir rapidamente e prever sua funcionalidade, evitando duplicação entre os nomes de cmdlet.

Para aprimorar a experiência do usuário, o substantivo que você escolhe para um nome de cmdlet deve ser singular. Por exemplo, use o nome `Get-Process` em vez de **processos Get**. É melhor seguir essa regra para todos os nomes de cmdlet, mesmo quando um cmdlet é provável atuar em mais de um item.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Usar Pascal Case para nomes de Cmdlet (SD02)

Use Pascal case para nomes de parâmetro. Em outras palavras, colocar em maiuscula a primeira letra do verbo e todos os termos usados no substantivo. Por exemplo, "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>Diretrizes de Design de parâmetro (SD03)

Um cmdlet precisa de parâmetros que receber os dados no qual ele deve operar e parâmetros que indica as informações que são usadas para determinar as características da operação. Por exemplo, um cmdlet pode ter um `Name` parâmetro que recebe dados de pipeline e o cmdlet pode ter um `Force` parâmetro para indicar que o cmdlet pode ser forçado a executar sua operação. Não há nenhum limite para o número de parâmetros que um cmdlet pode definir.

#### <a name="use-standard-parameter-names"></a>Usar nomes de parâmetro padrão

O cmdlet deve usar nomes de parâmetro padrão para que o usuário pode determinar rapidamente o que significa que um determinado parâmetro. Se um nome mais específico for necessário, use um nome de parâmetro padrão e, em seguida, especifique um nome mais específico como um alias. Por exemplo, o `Get-Service` cmdlet tem um parâmetro que tem um nome genérico (`Name`) e um alias mais específico (`ServiceName`). Os dois termos podem ser usados para especificar o parâmetro.

Para obter mais informações sobre nomes de parâmetros e seus tipos de dados, consulte [nome do parâmetro de Cmdlet e diretrizes de funcionalidade](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Usar nomes de parâmetro no Singular

Evite usar nomes no plural para parâmetros cujo valor é um único elemento. Isso inclui parâmetros que usam matrizes ou lista porque o usuário pode fornecer uma matriz ou lista com apenas um elemento.

Nomes de parâmetro no plural devem ser usados apenas nesses casos onde o valor do parâmetro é sempre um valor de elementos múltiplos. Nesses casos, o cmdlet deve verificar se vários elementos são fornecidos e o cmdlet deve exibir um aviso ao usuário se não forem fornecidos vários elementos.

#### <a name="use-pascal-case-for-parameter-names"></a>Usar Pascal Case para nomes de parâmetro

Use Pascal case para nomes de parâmetro. Em outras palavras, colocar em maiuscula a primeira letra de cada palavra no nome do parâmetro, incluindo a primeira letra do nome. Por exemplo, o nome do parâmetro `ErrorAction` usa a capitalização correta. Os nomes de parâmetro a seguir usam a capitalização incorreta:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parâmetros que usam uma lista de opções

Há duas maneiras de criar um parâmetro cujo valor pode ser selecionado em um conjunto de opções.

- Definir um tipo de enumeração (ou usar um tipo de enumeração existente) que especifica os valores válidos. Em seguida, use o tipo de enumeração para criar um parâmetro desse tipo.

- Adicione a **ValidateSet** à declaração de parâmetro de atributo. Para obter mais informações sobre esse atributo, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Use tipos de padrão para parâmetros

Para garantir a consistência com outros cmdlets, use tipos padrão para parâmetros, onde quer que possível. Para obter mais informações sobre os tipos que devem ser usados para parâmetros diferentes, consulte [tipos e nomes de parâmetro de Cmdlet padrão](./standard-cmdlet-parameter-names-and-types.md). Este tópico fornece links para vários tópicos que descrevem os nomes e tipos do .NET Framework para grupos de parâmetros padrão, como os "parâmetros de atividade".

#### <a name="use-strongly-typed-net-framework-types"></a>Usar tipos do Framework .NET fortemente tipados

Parâmetros devem ser definidos como tipos do .NET Framework para fornecer melhor validação de parâmetro. Por exemplo, os parâmetros que são restritos a um valor de um conjunto de valores devem ser definidos como um tipo de enumeração. Para dar suporte a um valor de identificador de recurso uniforme (URI), defina o parâmetro como um [System. URI](/dotnet/api/System.Uri) tipo. Evite parâmetros de cadeias de caracteres básicas para propriedades de texto de forma tudo, exceto livre.

#### <a name="use-consistent-parameter-types"></a>Usar tipos de parâmetro consistentes

Quando o mesmo parâmetro é usado por vários cmdlets, use sempre o mesmo tipo de parâmetro.  Por exemplo, se o `Process` parâmetro é um [System.Int16](/dotnet/api/System.Int16) de tipo para um cmdlet, não faça a `Process` parâmetro para outro cmdlet um [System.Uint16](/dotnet/api/System.UInt16) tipo.

#### <a name="parameters-that-take-true-and-false"></a>Parâmetros que usam True e False

Se o parâmetro aceita apenas `true` e `false`, defina o parâmetro como tipo [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter). Um parâmetro de opção é tratado como `true` quando ele é especificado em um comando. Se o parâmetro não estiver incluído em um comando, o Windows PowerShell considera o valor do parâmetro a ser `false`. Não defina parâmetros booleanos.

Se o parâmetro precisa diferenciar entre os valores de 3: $true, $false e "não especificado,", em seguida, definir um parâmetro de tipo anulável\<bool >.  A necessidade de um dia 3, "não especificado" normalmente ocorre quando o cmdlet pode modificar uma propriedade booleana de um objeto. Nesse caso, "não especificado" significa para não alterar o valor atual da propriedade.

#### <a name="support-arrays-for-parameters"></a>Suporte a matrizes de parâmetros

Com frequência, os usuários devem executar a mesma operação em relação a vários argumentos. Para esses usuários, um cmdlet deve aceitar uma matriz como parâmetro de entrada para que um usuário pode passar argumentos para o parâmetro como uma variável do Windows PowerShell. Por exemplo, o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet usa uma matriz de cadeias de caracteres que identificam os nomes dos processos para recuperar.

#### <a name="support-the-passthru-parameter"></a>Suporte para o parâmetro PassThru

Por padrão, vários cmdlets que modificam o sistema, como o [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) atuam como "coletores" para objetos de cmdlet e não retornam um resultado. Esses cmdlet deve implementar o `PassThru` parâmetro para forçar o cmdlet para retornar um objeto. Quando o `PassThru` parâmetro for especificado, o cmdlet retorna um objeto usando uma chamada para o [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Por exemplo, o comando a seguir interrompe o processo Calc e passa o processo resultante para o pipeline.

```powershell
Stop-Process calc -passthru
```

Na maioria dos casos, adicionar, conjunto e novos cmdlets deve dar suporte a um `PassThru` parâmetro.

#### <a name="support-parameter-sets"></a>Suporte a conjuntos de parâmetros

Um cmdlet destina-se para realizar uma única finalidade. No entanto, frequentemente há mais de uma maneira de descrever a operação ou o destino da operação. Por exemplo, um processo poderá ser identificado por seu nome, por seu identificador ou por um objeto de processo. O cmdlet deve dar suporte a todas as representações razoáveis de seus destinos. Normalmente, o cmdlet satisfaz esse requisito, especificando os conjuntos de parâmetros (conhecidos como conjuntos de parâmetros) que funcionam em conjunto. Um único parâmetro pode pertencer a qualquer número de conjuntos de parâmetros. Para obter mais informações sobre conjuntos de parâmetros, consulte [conjuntos de parâmetros do Cmdlet](./cmdlet-parameter-sets.md).

Quando você especificar conjuntos de parâmetros, defina apenas um parâmetro no conjunto a ser ValueFromPipeline. Para obter mais informações sobre como declarar o **parâmetro** atributo, consulte [ParameterAttribute declaração](./parameter-attribute-declaration.md).

Quando conjuntos de parâmetros são usados, o conjunto de parâmetros padrão é definido o **Cmdlet** atributo. O conjunto de parâmetros padrão deve incluir os parâmetros mais probabilidade de ser usado em uma sessão interativa do Windows PowerShell. Para obter mais informações sobre como declarar o **Cmdlet** atributo, consulte [declaração CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Fornecer comentários ao usuário (SD04)

Use as diretrizes nesta seção para fornecer comentários ao usuário. Este comentário permite ao usuário a serem consideradas o que está ocorrendo no sistema de e para tomar decisões mais administrativas.

O tempo de execução do Windows PowerShell permite que um usuário especificar como lidar com a saída de cada chamada para o `Write` método definindo uma variável de preferência. O usuário pode definir várias variáveis de preferência, incluindo uma variável que determina se o sistema deve exibir informações e uma variável que determina se o sistema deve consultar o usuário antes de executar uma ação adicional.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Suporte a WriteWarning, WriteVerbose e métodos WriteDebug

Um cmdlet deve chamar o [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método quando o cmdlet está prestes a realizar uma operação que pode ter um resultado não intencional. Por exemplo, um cmdlet deve chamar esse método se o cmdlet estiver prestes a substituir um arquivo somente leitura.

Um cmdlet deve chamar o [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método quando o usuário requer alguns detalhes sobre o que está fazendo o cmdlet. Por exemplo, um cmdlet deve chamar essas informações se o autor do cmdlet perceber que há cenários que podem exigir mais informações sobre o que está fazendo o cmdlet.

O cmdlet deve chamar o [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método quando um engenheiro de suporte do produto ou o desenvolvedor deve entender o que corrompeu a operação do cmdlet. Não é necessário para o cmdlet para chamar o [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método o mesmo código que chama o [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método porque o `Debug` parâmetro apresenta os dois conjuntos de informações.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>WriteProgress suporte para operações que levam muito tempo

Operações de cmdlet que levam muito tempo para ser concluída e que não pode ser executado em segundo plano deve dar suporte a progresso se comunicando através de chamadas periódicas para o [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.

#### <a name="use-the-host-interfaces"></a>Use as Interfaces de Host

Ocasionalmente, um cmdlet deve se comunicar diretamente com o usuário em vez de usando os vários escrever ou devem métodos compatíveis com o [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Nesse caso, o cmdlet deve derivar do [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe e usar o [System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) propriedade. Essa propriedade oferece suporte a diferentes níveis de tipo de comunicação, incluindo os tipos de PromptForChoice, um aviso e WriteLine/ReadLine. Nível mais específico, ele também fornece maneiras para ler e gravar as chaves individuais e para lidar com buffers.

A menos que um cmdlet é projetado especificamente para gerar uma interface gráfica do usuário (GUI), ele não deve ignorar o host usando o [System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) propriedade. Um exemplo de um cmdlet que é projetado para gerar uma GUI é o [Out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet.

> [!NOTE]
> Cmdlets não deve usar o [System. console](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Criar um arquivo de ajuda de Cmdlet (SD05)

Para cada assembly de cmdlet, crie um arquivo de Help.xml que contém informações sobre o cmdlet. Essas informações incluem uma descrição do cmdlet, as descrições dos parâmetros do cmdlet, exemplos de uso do cmdlet e muito mais.

## <a name="code-guidelines"></a>Diretrizes de código

As diretrizes a seguir devem ser seguidas durante a codificação de cmdlets para garantir uma experiência de usuário consistente entre o uso de seus cmdlets e outros cmdlets. Quando você encontrar uma diretriz de código que se aplica à sua situação, certifique-se de examinar as diretrizes de Design para obter diretrizes semelhantes.

### <a name="coding-parameters-sc01"></a>Parâmetros de codificação (SC01)

Definir um parâmetro ao declarar uma propriedade pública de classe do cmdlet é decorado com o **parâmetro** atributo. Parâmetros não é necessário ser membros estáticos da classe derivada do .NET Framework para o cmdlet. Para obter mais informações sobre como declarar o **parâmetro** atributo, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Dá suporte a caminhos do Windows PowerShell

O caminho do Windows PowerShell é o mecanismo de normalização de acesso aos namespaces. Quando você atribui um caminho do Windows PowerShell para um parâmetro no cmdlet, o usuário pode definir um personalizado "unidade" que atua como um atalho para um caminho específico. Quando um usuário designa tal uma unidade, os dados armazenados, como os dados no registro, podem ser usados de maneira consistente.

Se seu cmdlet permite que o usuário especificar um arquivo ou uma fonte de dados, ele deve definir um parâmetro do tipo [System. String](/dotnet/api/System.String). Se mais de uma unidade for compatível, o tipo deve ser uma matriz. O nome do parâmetro deve ser `Path`, com um alias de `PSPath`. Além disso, o `Path` parâmetro deve dar suporte a caracteres curinga. Se o suporte para caracteres curinga não é necessário, defina um `LiteralPath` parâmetro.

Se os dados que o cmdlet lê ou grava tem que ser um arquivo, o cmdlet deve aceitar a entrada de caminho do Windows PowerShell e o cmdlet deve usar o [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) propriedade a traduzir o Windows Caminhos do PowerShell em caminhos que reconhece o sistema de arquivos. Os mecanismos específicos incluem os seguintes métodos:

- [System.Management.Automation.Pscmdlet.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pscmdlet.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Se os dados que o cmdlet lê ou grava serão apenas um conjunto de cadeias de caracteres em vez de um arquivo, o cmdlet deve usar as informações de conteúdo do provedor (`Content` membro) para ler e gravar. Essas informações são obtidas a partir de [System.Management.Automation.Provider.Cmdletprovider.Invokeprovider*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) propriedade. Esses mecanismos permitem outros armazenamentos de dados para participar de leitura e gravação de dados.

#### <a name="support-wildcard-characters"></a>Suporte a caracteres curinga

Um cmdlet deve dar suporte a caracteres curinga se possível. Suporte para caracteres curinga ocorre em vários locais em um cmdlet (especialmente quando um parâmetro usa uma cadeia de caracteres para identificar um objeto de um conjunto de objetos). Por exemplo, a amostra **Stop-Proc** cmdlet do [StopProc Tutorial](./stopproc-tutorial.md) define um `Name` parâmetro para manipular cadeias de caracteres que representam os nomes de processo. Esse parâmetro dá suporte a caracteres curinga para que o usuário pode especificar facilmente os processos a interromper.

Quando o suporte para curingas caracteres está disponível, uma operação de cmdlet geralmente produz uma matriz. Ocasionalmente, ele não faz sentido para dar suporte a uma matriz porque o usuário pode usar apenas um único item por vez. Por exemplo, o [Set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet precisa dar suporte a uma matriz porque o usuário está definindo apenas um único local. Nesse caso, o cmdlet ainda ofereça suporte a caracteres curinga, mas ele força a resolução para um único local.

Para obter mais informações sobre padrões de caractere curinga, consulte [que dão suporte a curingas nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Definindo objetos

Esta seção contém diretrizes para definir objetos para os cmdlets e para estender os objetos existentes.

##### <a name="define-standard-members"></a>Definir membros padrão

Defina membros padrão para estender um tipo de objeto em um arquivo Types.ps1xml personalizado (use o arquivo Types.ps1xml do Windows PowerShell como um modelo). Membros padrão são definidos por um nó com o nome PSStandardMembers. Essas definições permitem que o tempo de execução do Windows PowerShell para trabalhar com o seu objeto de maneira consistente e de outros cmdlets.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Definir ObjectMembers para ser usados como parâmetros

Se você estiver criando um objeto para um cmdlet, certifique-se de que seus membros mapeiam diretamente para os parâmetros dos cmdlets que irá usá-lo. Esse mapeamento permite que o objeto a ser enviado com facilidade para o pipeline e a ser passado de um cmdlet para outro.

Objetos do .NET Framework preexistentes que são retornados pelo cmdlets frequentemente estão faltando alguns membros importantes ou convenientes que são necessários para o desenvolvedor de scripts ou o usuário. Esses membros ausentes podem ser especialmente importantes para exibição e criação de nomes de membro correto para que o objeto pode ser passado para o pipeline corretamente. Crie um arquivo Types.ps1xml personalizado para documentar esses membros necessários. Quando você cria esse arquivo, recomendamos a seguinte convenção de nomenclatura: *< Your_Product_Name >*. Types.ps1xml.

Por exemplo, você pode adicionar um `Mode` script de propriedade para o [FileInfo](/dotnet/api/System.IO.FileInfo) tipo para exibir os atributos de um arquivo de forma mais clara. Além disso, você pode adicionar um `Count` propriedade de alias para o [System. array](/dotnet/api/System.Array) tipo para permitir o uso consistente com esse nome de propriedade (em vez de `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implemente a Interface IComparable

Implementar uma [System. IComparable](/dotnet/api/System.IComparable) interface em todos os objetos de saída. Isso permite que os objetos de saída para facilmente ser redirecionado para diversos cmdlets de classificação e análise.

##### <a name="update-display-information"></a>Atualizar informações de exibição

Se a exibição para um objeto não fornecer os resultados esperados, criar um personalizado  *\<YourProductName >*. Arquivo Format.ps1xml para esse objeto.

### <a name="support-well-defined-pipeline-input-sc02"></a>Dá suporte à entrada de Pipeline bem definido (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implemente para o meio de um Pipeline

Implementar um cmdlet, supondo que ele será chamado no meio de um pipeline (ou seja, outros cmdlets irá produzir sua entrada ou consumir sua saída). Por exemplo, você pode pressupor que o `Get-Process` cmdlet, pois ele gera dados, é usado apenas como o primeiro cmdlet em um pipeline. No entanto, como esse cmdlet é projetado para o meio de um pipeline, esse cmdlet permite que dados ou os cmdlets anteriores no pipeline para especificar os processos para recuperar.

#### <a name="support-input-from-the-pipeline"></a>Suporte a entrada do Pipeline

Em cada conjunto de parâmetros para um cmdlet, inclua pelo menos um parâmetro que dá suporte à entrada do pipeline. Suporte para entrada de pipeline permite que o usuário recuperar dados ou objetos, enviá-los para o conjunto de parâmetros corretos e passar os resultados diretamente para um cmdlet.

Um parâmetro aceita a entrada do pipeline se a **parâmetro** atributo inclui a `ValueFromPipeline` palavra-chave, o `ValueFromPipelineByPropertyName` palavra-chave atributo ou ambas as palavras-chave em sua declaração. Se nenhum dos parâmetros em um parâmetro definido suporte a `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` palavras-chave, o cmdlet significativamente não podem ser colocadas após outro cmdlet porque ele irá ignorar qualquer entrada do pipeline.

#### <a name="support-the-processrecord-method"></a>Suporte para o método ProcessRecord

Para aceitar todos os registros do cmdlet anterior no pipeline, o cmdlet deve implementar o [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método. Windows PowerShell chama esse método várias vezes, uma vez para cada registro que é enviado ao seu cmdlet.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Gravar registros únicos para o Pipeline (SC03)

Quando um cmdlet retorna objetos, o cmdlet deve gravar objetos imediatamente conforme eles são gerados. O cmdlet não deve mantê-las para o buffê-los em uma matriz combinada. Os cmdlets que recebem os objetos como entrada, em seguida, será capazes de processar, exibir, ou para processar e exibir os objetos de saída sem atraso. Objetos de um cmdlet que gera a saída de um de cada vez deve chamar o [System.Management.Automation.Cmdlet.Writeobject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Um cmdlet que gera os objetos de saída em lotes (por exemplo, porque uma API subjacente retorna uma matriz de objetos de saída) deve chamar o [System.Managemet.Automation.Cmdlet.Writeobject](/dotnet/api/System.Managemet.Automation.Cmdlet.WriteObject) método com seu segundo parâmetro definido para `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Verifique os Cmdlets diferencia maiusculas de minúsculas e preserva (SC04)

Por padrão, o próprio Windows PowerShell diferencia maiusculas de minúsculas. No entanto, como ela lida com muitos sistemas preexistentes, Windows PowerShell preserve a capitalização para facilidade de operação e compatibilidade. Em outras palavras, se um caractere é fornecido em letras maiusculas, Windows PowerShell mantém em letras maiusculas. Para sistemas funcionam muito bem, um cmdlet precisa seguem Esta convenção. Se possível, ele deve operar em maiusculas e minúsculas. No entanto, ele deve, preserve a capitalização original para cmdlets que ocorrem posteriormente em um comando ou no pipeline.

## <a name="see-also"></a>Consulte Também

[Diretrizes de desenvolvimento necessárias](./required-development-guidelines.md)

[Diretrizes de desenvolvimento de consultoria](./advisory-development-guidelines.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
