---
ms.date: 05/17/2018
keywords: powershell,core
title: Alterações da falha no PowerShell Core 6.0
ms.openlocfilehash: d477a9b27e8d5df6653ee40f8b606879b60a80c7
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655439"
---
# <a name="breaking-changes-for-powershell-60"></a>Alterações da falha no PowerShell Core 6.0

## <a name="features-no-longer-available-in-powershell-core"></a>Recursos não mais disponíveis no PowerShell Core

### <a name="powershell-workflow"></a>Fluxo de trabalho do PowerShell

[Fluxo de Trabalho do PowerShell][workflow] é um recurso no Windows PowerShell baseado no [Windows Workflow Foundation (WF)][workflow-foundation] que permite a criação de runbooks robustos para tarefas em paralelo ou de longa duração.

Devido à falta de suporte a Windows Workflow Foundation no .NET Core, não continuaremos a dar suporte ao Fluxo de Trabalho do PowerShell no PowerShell Core.

Futuramente, gostaríamos de habilitar o paralelismo/simultaneidade nativa na linguagem do PowerShell sem a necessidade do Fluxo de Trabalho do PowerShell.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Snap-ins personalizados

[Snap-ins do PowerShell][snapin] são um predecessor dos módulos do PowerShell que não têm ampla adoção da comunidade do PowerShell.

Devido à complexidade do suporte aos snap-ins e à falta de uso da comunidade, não oferecemos mais suporte a snap-ins personalizados no PowerShell Core.

Hoje, isso causa a falha dos módulos `ActiveDirectory` e `DnsClient` no Windows e no Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>Cmdlets do WMI v1

Devido à complexidade do suporte a dois conjuntos de módulos baseados em WMI, removemos os cmdlets WMI v1 do PowerShell Core:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Em vez disso, recomendamos que você use os cmdlets do CIM (também conhecidos como WMI v2), que fornecem a mesma funcionalidade e uma sintaxe reprojetada:

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

Devido ao uso de APIs sem suporte, removemos `Microsoft.PowerShell.LocalAccounts` do PowerShell Core até encontrarmos uma solução melhor.

### <a name="-counter-cmdlets"></a>Os cmdlets do `*-Counter`

Devido ao uso de APIs sem suporte, removemos `*-Counter` do PowerShell Core até encontrarmos uma solução melhor.

## <a name="enginelanguage-changes"></a>Alterações de mecanismo/linguagem

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Renomear `powershell.exe` para `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Para dar aos usuários uma maneira determinística de chamar o PowerShell Core no Windows (e não no Windows PowerShell), o binário do PowerShell Core foi alterado para `pwsh.exe` no Windows e para `pwsh` em outras plataformas.

O nome abreviado também é consistente com a nomenclatura dos shells em plataformas não Windows.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Não insira quebras de linha na saída (exceto para tabelas) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Antes, a saída era alinhada à largura do console, e quebras de linha eram adicionadas à largura final do console, ou seja, a saída não era reformatada conforme o esperado se o terminal não fosse redimensionado. Essa alteração não foi aplicada às tabelas, pois elas precisam das quebras de linha para manter as colunas alinhadas.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Ignore a verificação de elemento nulo para coleções com um tipo de elemento de tipo de valor [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Para o parâmetro `Mandatory` e os atributos `ValidateNotNull` e `ValidateNotNullOrEmpty`, ignore a verificação de elemento nulo se o tipo de elemento da coleção for um tipo de valor.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Altere o `$OutputEncoding` para usar codificação `UTF-8 NoBOM` em vez de ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

A codificação anterior, ASCII (7 bits), resultaria em alteração incorreta da saída em alguns casos. Essa alteração é para tornar o `UTF-8 NoBOM` padrão, o que preserva a saída Unicode com uma codificação com suporte da maioria das ferramentas e sistemas operacionais.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Remoção de `AllScope` da maioria dos aliases padrão [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Para acelerar a criação de escopo, `AllScope` foi removido da maioria dos aliases padrão. `AllScope` foi deixado por alguns aliases usados com frequência nos quais a pesquisa foi mais rápida.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` e `-Debug` não substituem mais `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Antes, se `-Verbose` ou `-Debug` fosse especificado, substituiria o comportamento de `$ErrorActionPreference`. Com essa alteração, `-Verbose` e `-Debug` não afetam mais o comportamento de `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Alterações de cmdlet

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Invoke-RestMethod não retorna informações úteis quando nenhum dado retorna. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Quando uma API retorna apenas `null`, Invoke-RestMethod serializava isso como a cadeia de caracteres `"null"` em vez de `$null`. Essa alteração corrige a lógica em `Invoke-RestMethod` para serializar apropriadamente um JSON `null` literal de valor único como `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Remoção de `-ComputerName` dos cmdlets `*-Computer` [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Devido a problemas com a comunicação remota do RPC no CoreFX (principalmente em plataformas diferentes do Windows), e para garantir uma experiência de comunicação remota consistente no PowerShell, o parâmetro `-ComputerName` foi removido dos cmdlets `\*-Computer`. Em vez disso, use `Invoke-Command` como a maneira de executar cmdlets remotamente.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Remoção de `-ComputerName` dos cmdlets `*-Service` [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Para incentivar a consistência no uso de PSRP, o parâmetro `-ComputerName` foi removido dos cmdlets `*-Service`.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Correção de `Get-Item -LiteralPath a*b` se `a*b` não existir, a fim de retornar um erro [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Antes, se `-LiteralPath` recebesse um caractere curinga, o trataria da mesma forma que `-Path`, e se o caractere curinga não encontrasse arquivos, sairia silenciosamente. O comportamento correto deveria ser um `-LiteralPath` literal, para que se o arquivo não existir, ele cause um erro. A mudança é tratar os curingas usados com `-Literal` como literal.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` deve aplicar `PSTypeNames` na importação quando houver informações de tipo no CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Antes, os objetos exportados usando `Export-CSV` com `TypeInformation` importado com `ConvertFrom-Csv` não estavam retendo as informações de tipo. Esta mudança adiciona as informações de tipo ao membro `PSTypeNames`, se estiverem disponíveis no arquivo CSV.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` deve ser padrão em `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Essa alteração foi feita para atender aos comentários de clientes sobre o comportamento padrão de inclusão de informações de tipo no `Export-CSV`.

Antes, o cmdlet geraria um comentário na primeira linha contendo o nome do tipo do objeto. A alteração serve para suprimir isso por padrão, pois é algo que não é compreendido pela maioria das ferramentas. Use `-IncludeTypeInformation` para reter o comportamento anterior.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Os cmdlets da Web devem avisar quando `-Credential` for enviado por conexões não criptografadas [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Ao usar HTTP, todo conteúdo, incluindo senhas, é enviado como texto não criptografado. Essa alteração serve para não permitir isso por padrão, e retornar um erro se as credenciais estiverem sendo passadas de maneira insegura. Os usuários podem ignorar isso usando a opção `-AllowUnencryptedAuthentication`.

## <a name="api-changes"></a>Alterações de API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Remoção da classe `AddTypeCommandBase` [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

A classe `AddTypeCommandBase` foi removida de `Add-Type` para melhorar o desempenho. Essa classe é usada apenas pelo cmdlet Add-Type e não deve afetar os usuários.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Unificação dos cmdlets com o parâmetro `-Encoding` para o tipo `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

O valor de `-Encoding`, `Byte`, foi removido dos cmdlets do provedor do sistema de arquivos. Agora, um novo parâmetro, `-AsByteStream`, é usado para especificar a exigência de um fluxo de bytes como entrada, ou que a saída seja um fluxo de bytes.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Adição de um mensagem de erro melhor para o parâmetro `-UFormat` vazio ou nulo [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Antes, ao passar uma cadeia de caracteres de formato vazio para `-UFormat`, uma mensagem de erro inútil era exibida. Um erro mais descritivo foi adicionado.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Limpeza do código de console [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Os seguintes recursos foram removidos, pois eles não têm suporte no PowerShell Core, e não há planos para adicionar suporte, já que eles existem por motivos de herança para o Windows PowerShell: opção `-psconsolefile` e o código, opção `-importsystemmodules` e o código e código de alteração de fonte.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Remoção do suporte a `RunspaceConfiguration` [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Antes, ao criar um runspace do PowerShell de forma programática usando a API, era possível usar o [`RunspaceConfiguration`][runspaceconfig] herdado ou o [`InitialSessionState`][iss] mais recente. Essa alteração removeu o suporte a `RunspaceConfiguration`, e só dá suporte a `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` associa argumentos a `$input` em vez de `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Uma posição incorreta de um parâmetro resultou na passagem de argumentos como entrada, e não como argumentos.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Remoção da opção `-showwindow` sem suporte do `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` depende do WPF, para o qual não há suporte no CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Permissão para que * seja usado no caminho do registro para `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Antes, se `-LiteralPath` recebesse um caractere curinga, o trataria da mesma forma que `-Path`, e se o caractere curinga não encontrasse arquivos, sairia silenciosamente. O comportamento correto deveria ser um `-LiteralPath` literal, para que se o arquivo não existir, ele cause um erro. A mudança é tratar os curingas usados com `-Literal` como literal.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Correção do teste de falha de `Set-Service` [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Antes, se `New-Service -StartupType foo` fosse usado, `foo` era ignorado e o serviço era criado com algum tipo de inicialização padrão. Essa alteração serve para lançar explicitamente um erro para um tipo de inicialização inválida.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Renomear `$IsOSX` para `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

A nomenclatura no PowerShell deve ser consistente com nossa nomenclatura e estar de acordo com o uso da Apple do macOS, em vez de OSX. No entanto, para facilitar a leitura e manter a consistência, permaneceremos com o uso de maiúsculas e minúsculas do padrão Pascal.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Mensagem de erro consistente quando um script inválido é passado para -File, erro mais claro ao receber argumentos ambíguos [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Altera os códigos de saída de `pwsh.exe` para alinhar com as convenções Unix

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Remoção de `LocalAccount` e de cmdlets dos módulos `Diagnostics`. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Devido à falta de suporte às APIs, o módulo `LocalAccounts` e os cmdlets `Counter` no módulo `Diagnostics` foram removidos até encontrarmos uma solução melhor.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>A execução de script do powershell com o parâmetro bool não funciona [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Antes, usar o powershell.exe (agora `pwsh.exe`) para executar um script do PowerShell usando `-File` não fornecia uma maneira de passar $true/$false como valores de parâmetro. Adicionamos o suporte para $true/$false como valores analisados para parâmetros. Também há suporte para valores de opção, pois a sintaxe documentada no momento não funciona.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Remoção da propriedade `ClrVersion` de `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

A propriedade `ClrVersion` de `$PSVersionTable` não é útil com CoreCLR, os usuários finais não devem usar esse valor para determinar a compatibilidade.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Alteração do parâmetro posicional para `powershell.exe` de `-Command` para `-File` [4019 #](https://github.com/PowerShell/PowerShell/issues/4019)

Habilitação geral do uso do PowerShell em plataformas diferentes do Windows. Isso significa que, em sistemas baseados em Unix, você pode tornar um script executável para invocar o PowerShell automaticamente, em vez de invocar explicitamente `pwsh`. Isso também significa que agora você pode fazer coisas como `powershell foo.ps1` ou `powershell fooScript` sem especificar `-File`. No entanto, essa alteração agora exige que você especifique explicitamente `-c` ou `-Command` ao tentar fazer coisas como `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementação da análise de escape de Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u#### `` ou `` `u{####} `` é convertido no caractere Unicode correspondente. Para gerar um `` `u `` literal, escape o acento grave: ``` ``u ```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Altere a codificação `New-ModuleManifest` para `UTF8NoBOM` em plataformas que não são o Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Antes, `New-ModuleManifest` criava manifestos psd1 em UTF-16 com BOM, criando um problema para as ferramentas do Linux. Essa alteração da falha altera a codificação de `New-ModuleManifest` para UTF (sem BOM) em plataformas que não são Windows.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Impedir que `Get-ChildItem` faça a recursão em links simbólicos (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Essa alteração alinha mais `Get-ChildItem` ao Unix `ls -r` e aos comandos nativos `dir /s` do Windows. Como os comandos mencionados, o cmdlet exibe links simbólicos para diretórios encontrados durante a recursão, mas não faz a recursão neles.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Correção de `Get-Content -Delimiter` para não incluir o delimitador nas linhas retornadas [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Antes, a saída durante o uso de `Get-Content -Delimiter` era inconsistente e inconveniente, pois exigia mais processamento dos dados para remover o delimitador. Essa alteração remove o delimitador das linhas retornadas.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementação do Format-Hex em C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

O parâmetro `-Raw` agora é "não operacional" (ou seja, não faz nada). A partir de agora, toda a saída será exibida com uma representação verdadeira de números que incluem todos os bytes de seu tipo (o que o parâmetro `-Raw` fazia antes dessa alteração).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>O PowerShell como um shell padrão não funciona com o comando de script [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

Em Unix, é padrão dos shells aceitar `-i` para um shell interativo, e muitas ferramentas esperam esse comportamento (`script` por exemplo e ao configurar o PowerShell como o shell padrão) e chama o shell com a opção `-i`. Essa alteração causa falhas, pois, antes, `-i` podia ser usado como uma síntese disponível para corresponder `-inputformat`, e agora precisa ser `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Correção de erro de digitação no nome da propriedade Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` foi digitado incorretamente como `BiosSeralNumber` e foi alterado para a ortografia correta.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Adição dos cmdlets `Get-StringHash` e `Get-FileHash` [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

A mudança é que alguns algoritmos de hash não têm suporte do CoreFX, portanto, não estão mais disponíveis:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Adição de validação em cmdlets `Get-*`, em que passar $null retorna todos os objetos em vez do erro [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Agora, passar `$null` para qualquer uma das seguintes opções gera um erro:

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Adição de suporte ao Formato do Arquivo de Log Estendido do W3C em `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Antes, o cmdlet `Import-Csv` não podia ser usado para importar diretamente os arquivos de log no formato de log estendido do W3C e uma ação adicional seria necessária. Com essa alteração, há suporte para o formato de log estendido W3C.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problema de associação de parâmetro com `ValueFromRemainingArguments` nas funções de PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

Agora, `ValueFromRemainingArguments` retorna os valores como uma matriz em vez de um único valor que é uma matriz.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` foi removido do `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Remoção da propriedade `BuildVersion` de `$PSVersionTable`. Essa propriedade foi vinculada à versão de build do Windows. Em vez disso, recomendamos que você use `GitCommitId` para recuperar a versão de build exata do PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Alterações nos cmdlets da Web

A API do .NET subjacente dos cmdlets Web foi alterada para `System.Net.Http.HttpClient`. Essa alteração fornece muitos benefícios. No entanto, essa alteração, junto com a falta de interoperabilidade com o Internet Explorer, resultou em várias alterações com falha em `Invoke-WebRequest` e `Invoke-RestMethod`.

- Agora, `Invoke-WebRequest` dá suporte apenas à Análise de HTML básica. `Invoke-WebRequest` sempre retorna um objeto `BasicHtmlWebResponseObject`. As propriedades `ParsedHtml` e `Forms` foram removidas.
- Agora, os valores de `BasicHtmlWebResponseObject.Headers` são `String[]`, em vez de `String`.
- Agora, `BasicHtmlWebResponseObject.BaseResponse` é um objeto de `System.Net.Http.HttpResponseMessage`.
- A propriedade `Response` nas exceções do cmdlet da Web agora é um objeto `System.Net.Http.HttpResponseMessage`.
- Agora, a análise de cabeçalho RFC estrita é padrão para o parâmetro `-Headers` e `-UserAgent`. Isso pode ser ignorado com `-SkipHeaderValidation`.
- Os esquemas de URI `file://` e `ftp://` não têm mais suporte.
- As configurações de `System.Net.ServicePointManager` não são mais cumpridas.
- No momento, não há uma autenticação baseada em certificado disponível no macOS.
- O uso de `-Credential` sobre uma URI `http://` resultará em erro. Use um URI `https://` ou forneça o parâmetro `-AllowUnencryptedAuthentication` para suprimir o erro.
- `-MaximumRedirection` Agora produz um erro de encerramento quando as tentativas de redirecionamento excederem o limite fornecido em vez de retornar os resultados do último redirecionamento.
