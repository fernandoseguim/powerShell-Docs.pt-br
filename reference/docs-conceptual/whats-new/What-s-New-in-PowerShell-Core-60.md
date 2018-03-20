# <a name="whats-new-in-powershell-core-60"></a>Novidades no PowerShell Core 6.0

O [PowerShell Core 6.0][github] é uma nova edição do PowerShell multiplataformas (Windows, macOS e Linux), de software livre e criado para ambientes heterogêneos e a nuvem híbrida.

## <a name="moved-from-net-framework-to-net-core"></a>Movido do .NET Framework para o .NET Core

O PowerShell Core usa o [.NET Core 2.0][] como seu tempo de execução.
O .NET Core 2.0 permite que o PowerShell Core trabalhe em várias plataformas (Windows, macOS e Linux).
O PowerShell Core também expõe o conjunto de APIs oferecido pelo .NET Core 2.0 a ser usado em scripts e cmdlets do PowerShell.

O Windows PowerShell usou o tempo de execução do .NET Framework para hospedar o mecanismo do PowerShell.
Isso significa que o Windows PowerShell expõe o conjunto de APIs oferecido pelo .NET Framework.

As APIs compartilhadas entre o .NET Core e o .NET Framework são definidas como parte do [.NET Standard][].

Para obter mais informações sobre como isso afeta a compatibilidade de script/módulo entre o PowerShell Core e o Windows PowerShell, veja [compatibilidade com versões anteriores com o Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Suporte para macOS e Linux

Agora o PowerShell oficialmente dá suporte ao macOS e ao Linux, incluindo:

- Windows 7, 8.1 e 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows Server Canal Semestral][semi-annual]
- Ubuntu 14.04, 16.04 e 17.04
- Debian 8.7+ e 9+
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12+

Nossa comunidade também contribuiu com pacotes para as seguintes plataformas, mas eles não têm suporte oficialmente:

- Arch Linux
- Kali Linux
- AppImage (funciona em várias plataformas Linux)

Temos também versões experimentais (sem suporte) para as seguintes plataformas:

- Windows no ARM32/ARM64
- Raspbian (Stretch)

Inúmeras alterações foram feitas no PowerShell Core 6.0 para que ele funcione melhor em sistemas não Windows.
Algumas dessas alterações são significativas e também afetam o Windows.
Outras só estão presentes ou são aplicáveis em instalações não Windows do PowerShell Core.

- Suporte adicionado para recurso de curinga do comando nativo em plataformas Unix.
- A funcionalidade `more` respeita o Linux `$PAGER` e o padrão é `less`.
  Isso significa que agora você pode usar curingas com binários/comandos nativos (por exemplo, `ls *.txt`). (#3463)
- Uma barra invertida à direita é precedida automaticamente ao lidar com os argumentos do comando nativo. (#4965)
- Ignore o comutador `-ExecutionPolicy` durante a execução do PowerShell em plataformas não Windows porque a assinatura de script não tem suporte atualmente. (#3481)
- ConsoleHost corrigido para honrar `NoEcho` em plataformas Unix. (#3801)
- `Get-Help` corrigido para dar suporte à correspondência de padrão sem diferenciação de maiúsculas e minúsculas em plataformas Unix. (#3852)
- Página de manual `powershell` adicionada ao pacote

### <a name="logging"></a>Registrando em Log

No macOS, o PowerShell usa as APIs `os_log` nativas para fazer logon no [sistema de log unificado][os_log] da Apple.
No Linux, o PowerShell usa [Syslog][], uma solução de registro em log ubíqua.

### <a name="filesystem"></a>Sistema de arquivos

Inúmeras alterações foram feitas no macOS e no Linux para dar suporte a caracteres de nome de arquivo normalmente sem suporte no Windows:

- Caminhos fornecidos para os cmdlets agora são independentes de barra (/ e \ funcionam como separador de diretório)
- Agora a Especificação de diretório básico XDG é respeitada e usada por padrão:
  - O caminho de perfil do Linux/macOS está localizado em `~/.config/powershell/profile.ps1`
  - O caminho de salvamento do histórico está localizado em `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - O caminho do módulo do usuário está localizado em `~/.local/share/powershell/Modules`
- Suporte para nomes de arquivo e de pasta que contêm o caractere de dois-pontos no Unix. (#4959)
- Suporte para nomes de script ou caminhos completos com vírgulas. (#4136) (Obrigado, @TimCurwick!)
- Detectar quando `-LiteralPath` é usado para suprimir a expansão de curinga para os cmdlets de navegação. (#5038)
- `Get-ChildItem` atualizado para funcionar de maneira mais semelhante a *nix `ls -R` e aos comandos `DIR /S` nativos do Windows.
  Agora `Get-ChildItem` retorna os links simbólicos encontrados durante uma pesquisa recursiva e não pesquisa os diretórios que esses links têm como destino. (#3780)

### <a name="case-sensitivity"></a>Diferenciação de maiúsculas e minúsculas

Linux e macOS tendem a diferenciar maiúsculas de minúsculas, enquanto o Windows não diferencia maiúsculas de minúsculas preservando o uso de maiúsculas/minúsculas.
Em geral, o PowerShell não diferencia maiúsculas de minúsculas.

Por exemplo, variáveis de ambiente diferenciam maiúsculas de minúsculas no macOS e no Linux. Portanto, o uso de maiúsculas/minúsculas da variável de ambiente `PSModulePath` foi padronizado. (#3255) `Import-Module` não diferencia maiúsculas de minúsculas quando está usando um caminho de arquivo para determinar o nome do módulo. (#5097)

## <a name="support-for-side-by-side-installations"></a>Suporte para instalações lado a lado

O PowerShell Core é instalado, configurado e executado separadamente do Windows PowerShell.
O PowerShell Core tem um pacote ZIP "portátil".
Usando o pacote ZIP, você pode instalar qualquer número de versões em qualquer lugar no disco, incluindo o local para um aplicativo que usa o PowerShell como uma dependência.
A instalação lado a lado facilita o teste de novas versões do PowerShell e a migração de scripts existentes ao longo do tempo.
Lado a lado também permite compatibilidade com versões anteriores, pois os scripts podem ser fixados em versões específicas que eles exigem.

> [!NOTE]
> Por padrão, o instalador com base no MSI no Windows realiza uma instalação de atualização in-loco.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>`powershell(.exe)` foi renomeado para `pwsh(.exe)`

O nome do binário para o PowerShell Core foi alterado de `powershell(.exe)` para `pwsh(.exe)`.
Essa alteração oferece uma maneira determinística para que os usuários executem o PowerShell Core em máquinas para dar suporte a instalações lado a lado do PowerShell Core e do Windows PowerShell.
Além disso, `pwsh` é muito menor e mais fácil de digitar.

Alterações adicionais para `pwsh(.exe)` de `powershell.exe`:

- O primeiro parâmetro posicional foi alterado de `-Command` para `-File`.
  Essa alteração corrige o uso de `#!` (também conhecido como um shebang) em scripts do PowerShell que estão sendo executados de shells não PowerShell em plataformas não Windows.
  Isso também significa que você pode executar comandos como `pwsh foo.ps1` ou `pwsh fooScript` sem especificar `-File`.
  No entanto, essa alteração exige que você especifique explicitamente `-c` ou `-Command` ao tentar executar comandos como `pwsh.exe -Command Get-Command`. (#4019)
- O PowerShell Core aceita o comutador `-i` (ou `-Interactive`) para indicar um shell interativo. (&#3558;) Isso permite que o PowerShell seja usado como um shell padrão em plataformas Unix.
- Parâmetros `-importsystemmodules` e `-psconsoleFile` removidos de `pwsh.exe`. (#4995)
- `pwsh -version` alterado e ajuda interna para `pwsh.exe` para se alinhar com outras ferramentas nativas. (#4958 e #4931) (Obrigado, @iSazonov)
- Mensagens de erro de argumento inválido para `-File` e `-Command` e códigos de saída consistentes com os padrões do Unix (#4573)
- Parâmetro `-WindowStyle` adicionado no Windows. (#4573) Da mesma forma, atualizações de instalações baseadas no pacote em plataformas não Windows são atualizações in-loco.

## <a name="backwards-compatibility-with-windows-powershell"></a>Compatibilidade com versões anteriores com o Windows PowerShell

A meta do PowerShell Core é permanecer o mais compatível possível com o Windows PowerShell.
O PowerShell Core usa o [.NET Standard][] 2.0 para fornecer compatibilidade binária com assemblies .NET existentes.
Muitos módulos do PowerShell dependem desses assemblies (às vezes, DLLs), por isso o .NET Standard permite que eles continuem funcionando com o .NET Core.
O PowerShell Core também inclui uma heurística para pesquisar em pastas conhecidas – como onde o Cache de Assembly Global geralmente reside no disco – para encontrar as dependências de DLL do .NET Framework.

Saiba mais sobre o .NET Standard no [.NET Blog][], neste vídeo do [YouTube][] e por meio destas [perguntas frequentes][] no GitHub.

Melhores esforços foram feitos para garantir que os módulos "internos" e de idioma do PowerShell (como `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility` etc.) funcionem da mesma forma que funcionam no Windows PowerShell.
Em muitos casos, com a ajuda da comunidade, adicionamos novos recursos e correções de bug para esses cmdlets.
Em alguns casos, devido à ausência de uma dependência em camadas subjacentes do .NET, a funcionalidade foi removida ou não está disponível.

A maioria dos módulos fornecidos como parte do Windows (por exemplo, `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage` etc.) e outros produtos da Microsoft incluindo o Azure e do Office não foi *explicitamente* movida para o.NET Core ainda.
A equipe do PowerShell está trabalhando com essas equipes e grupos de produto para validar e mover seus módulos existentes para o PowerShell Core.
Com o .NET Standard e o [CDXML][], muitos desses módulos tradicionais do Windows PowerShell parecem funcionar no PowerShell Core, mas eles não foram validados formalmente e não têm suporte formalmente.

Instalando o módulo [`WindowsPSModulePath`][windowspsmodulepath], você pode usar os módulos do Windows PowerShell acrescentando o Windows PowerShell `PSModulePath` ao PowerShell Core `PSModulePath`.

Primeiro, instale o módulo `WindowsPSModulePath` na Galeria do PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

Depois de instalar esse módulo, execute o cmdlet `Add-WindowsPSModulePath` para adicionar o Windows PowerShell `PSModulePath` ao PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Suporte ao Docker

O PowerShell Core adiciona suporte para contêineres do Docker para todas as plataformas principais a que oferecemos suporte (incluindo várias distribuições Linux, Windows Server Core e Nano Server).

Para obter uma lista completa, confira as marcas em [ `microsoft/powershell` no Hub do Docker][docker-hub].
Para obter mais informações sobre o Docker e o PowerShell Core, veja [Docker][] no GitHub.

## <a name="ssh-based-powershell-remoting"></a>Comunicação remota do PowerShell baseada no SSH

Agora o PSRP (protocolo de comunicação remota do PowerShell) funciona com o protocolo SSH (Secure Shell ), além do PSRP tradicional baseado em WinRM.

Isso significa que você pode usar cmdlets como `Enter-PSSession` e `New-PSSession` e autenticar usando o SSH.
Tudo o que você precisa fazer é registrar o PowerShell como um subsistema com um servidor baseado em OpenSSH SSH e você pode usar seus mecanismos de autenticação existentes baseados no SSH (como senhas ou chaves privadas) com a semântica `PSSession` tradicional.

Para obter mais informações sobre como configurar e usar a comunicação remota baseada no SSH, veja [Comunicação remota do PowerShell por SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom"></a>Codificação padrão é UTF-8 sem uma BOM

No passado, cmdlets do Windows PowerShell como `Get-Content`, `Set-Content` usavam codificações diferentes, como ASCII e UTF-16.
A variação em padrões de codificação criou problemas ao misturar cmdlets sem especificar uma codificação.

Plataformas não Windows tradicionalmente usam UTF-8 sem uma BOM (marca de ordem de byte) como a codificação padrão para arquivos de texto.
Mais ferramentas e aplicativos do Windows estão saindo do UTF-16 e seguindo em direção à codificação UTF-8 sem BOM.
O PowerShell Core altera a codificação padrão para estar em conformidade com os mais amplos ecossistemas.

Isso significa que todos os cmdlets internos que usam o parâmetro `-Encoding` usam o valor `UTF8NoBOM` por padrão.
Os cmdlets a seguir são afetados por essa alteração:

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- New-ModuleManifest
- Out-File
- Select-String
- Send-MailMessage
- Set-Content

Esses cmdlets também foram atualizados para que o parâmetro `-Encoding` aceite universalmente `System.Text.Encoding`.

O valor padrão de `$OutputEncoding` também foi alterado para UTF-8.

Como prática recomendada, você deve definir explicitamente codificações em scripts usando o parâmetro `-Encoding` para produzir um comportamento determinístico entre plataformas.

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Suporte à colocação de pipelines em segundo plano com E comercial (`&`) (#3360)

Colocar `&` no final de um pipeline faz com que o pipeline seja executado como um trabalho do PowerShell.
Quando um pipeline é colocado em segundo plano, um objeto de trabalho é retornado.
Quando o pipeline estiver em execução como um trabalho, todas os cmdlets `*-Job` padrão podem ser usados para gerenciar o trabalho.
Variáveis (ignorando variáveis específicas do processo) usadas no pipeline são copiadas automaticamente para o trabalho e `Copy-Item $foo $bar &` funciona.
Além disso, o trabalho é executado no diretório atual em vez do diretório base do usuário.
Para obter mais informações sobre trabalhos do PowerShell, veja [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Controle de versão semântico

- `SemanticVersion` está compatível com `SemVer 2.0`. (#5037) (Obrigado, @iSazonov!)
- `ModuleVersion` padrão alterado em `New-ModuleManifest` para `0.0.1` para se alinhar com SemVer. (#4842) (Obrigado, @LDSpits)
- `semver` adicionado como um acelerador de tipo para `System.Management.Automation.SemanticVersion`. (#4142) (Obrigado, @oising!)
- Habilitada a comparação entre uma instância `SemanticVersion` e uma instância `Version` construída apenas com valores de versão `Major` e `Minor`.

## <a name="language-updates"></a>Atualizações de linguagem

- Implemente a análise de escape Unicode para que os usuários possam usar caracteres Unicode como argumentos, cadeias de caracteres ou nomes de variável. (#3958) (Obrigado, @rkeithhill!)
- Novo caractere de escape adicionado para ESC: `` `e``
- Suporte adicionado para conversão de enums em cadeia de caracteres (#4318) (Obrigado, @KirkMunro)
- Matriz de elemento único de conversão corrigida em uma coleção genérica. (#3170)
- Sobrecarga de intervalo de caracteres adicionada para o operador `..`, portanto `'a'..'z'` retorna os caracteres de "a" a "z". (#5026) (Obrigado, @IISResetMe!)
- Atribuição de variável corrigida para não substituir variáveis somente leitura
- Enviar por push locais de variáveis automáticas para "DottedScopes" ao colocar pontos nos cmdlets de script (#4709)
- Habilitar o uso da opção "Linha única, várias linhas" no operador de divisão (#4721) (Obrigado, @iSazonov)

## <a name="engine-updates"></a>Atualizações de mecanismos

- `$PSVersionTable` tem quatro propriedades novas:
  - `PSEdition`: é definido como `Core` no PowerShell Core e como `Desktop` no Windows PowerShell
  - `GitCommitId`: esta é a ID de confirmação Git da ramificação ou marca Git em que o PowerShell foi criado.
    Em builds lançados, provavelmente será o mesmo que `PSVersion`.
  - `OS`: esta é uma cadeia de caracteres de versão do sistema operacional retornada por `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: é retornado por `[System.Environment]::OSVersion.Platform` e está definido como `Win32NT` no Windows, `MacOSX` no macOS e `Unix` no Linux.
- Propriedade `BuildVersion` removida de `$PSVersionTable`.
  Essa propriedade foi vinculada fortemente à versão de build do Windows.
  Em vez disso, recomendamos que você use `GitCommitId` para recuperar a versão de build exata do PowerShell Core. (#3877) (Obrigado, @iSazonov!)
- Remova a propriedade `ClrVersion` de `$PSVersionTable`.
  Essa propriedade é irrelevante para .NET Core e só foi preservada no .NET Core para fins de herdados específicos não aplicáveis ao PowerShell.
- Três novas variáveis automáticas adicionadas para determinar se o PowerShell está em execução em um determinado sistema operacional: `$IsWindows`, `$IsMacOs` e `$IsLinux`.
- Adicione `GitCommitId` a faixa do PowerShell Core.
  Agora você não precisa executar `$PSVersionTable` assim que iniciar o PowerShell para obter a versão. (#3916) (Obrigado, @iSazonov!)
- Adicione um arquivo de configuração JSON chamado `powershell.config.json` em `$PSHome` para armazenar algumas configurações necessárias antes do tempo de inicialização (por exemplo, `ExecutionPolicy`).
- Não bloquear pipeline durante a execução do Windows EXE
- Enumeração habilitada de coleções de COM. (#4553)

## <a name="cmdlet-updates"></a>Atualizações de cmdlet

### <a name="new-cmdlets"></a>Novos cmdlets

- Adicione `Get-Uptime` a `Microsoft.PowerShell.Utility`.
- Adicione o comando `Remove-Alias`. (#5143) (Obrigado, @PowershellNinja!)
- Adicione `Remove-Service` ao módulo de gerenciamento. (#4858) (Obrigado, @joandrsn!)

### <a name="web-cmdlets"></a>Cmdlets da Web

- Adicione suporte à autenticação de certificados para cmdlets da Web. (#4646) (Obrigado, @markekraus)
- Adicione suporte para cabeçalhos de conteúdo para cmdlets da Web. (#4494 e #4640) (Obrigado, @markekraus)
- Adicione suporte a cabeçalho com vários links para cmdlets da Web. (#5265) (Obrigado, @markekraus!)
- Suporte à paginação de cabeçalho de link em cmdlets da Web (#3828)
  - Para `Invoke-WebRequest`, quando a resposta inclui um cabeçalho de link, criamos uma propriedade RelationLink como um dicionário que representa as URLs e atributos `rel` e garantimos que as URLs são absolutas para facilitar o uso pelo desenvolvedor.
  - Para `Invoke-RestMethod`, quando a resposta inclui um cabeçalho de link, expomos um comutador `-FollowRelLink` para seguir automaticamente links `next` `rel` até que eles não existam mais ou até o valor do parâmetro `-MaximumFollowRelLink` opcional seja clicado.
- Adicione o parâmetro `-CustomMethod` a cmdlets da Web para permitir verbos do método não padrão. (#3142) (Obrigado, @Lee303!)
- Adicione suporte do `SslProtocol` aos cmdlets da Web. (#5329) (Obrigado, @markekraus!)
- Adicione suporte de partes múltiplas aos cmdlets da Web. (#4782) (Obrigado, @markekraus)
- Adicione `-NoProxy` a cmdlets da Web para que eles ignorem a configuração do proxy em todo o sistema. (#3447) (Obrigado, @TheFlyingCorpse!)
- Agora o Agente do usuário de Cmdlets da Web relata a plataforma de sistema operacional (#4937) (Obrigado, @LDSpits)
- Adicione o comutador `-SkipHeaderValidation` aos cmdlets da Web para dar suporte à adição de cabeçalhos sem validar o valor do cabeçalho. (#4085)
- Habilite cmdlets da Web para não validar o certificado HTTPS do servidor, se necessário.
- Adicione parâmetros de autenticação aos cmdlets da Web. (#5052) (Obrigado, @markekraus)
  - Adicione `-Authentication` que fornece três opções: Basic, OAuth e portador.
  - Adicione `-Token` para obter o token de portador para opções de portador e OAuth.
  - Adicione `-AllowUnencryptedAuthentication` para ignorar a autenticação fornecida para algum esquema de transporte diferente de HTTPS.
- Adicione `-ResponseHeadersVariable` a `Invoke-RestMethod` para habilitar a captura de cabeçalhos de resposta. (#4888) (Obrigado, @markekraus)
- Corrija os cmdlets da Web para incluir a resposta HTTP na exceção quando o código de status de resposta não é de êxito. (#3201)
- Altere cmdlets da Web `UserAgent` de `WindowsPowerShell` para `PowerShell`. (#4914) (Obrigado, @markekraus)
- Adicione a detecção `ContentType` explícita `Invoke-RestMethod` (#4692)
- Corrija os cmdlets da Web `-SkipHeaderValidation` para funcionar com cabeçalhos de agente do usuário não padrão. (#4479 e #4512) (Obrigado, @markekraus)

### <a name="json-cmdlets"></a>Cmdlets JSON

- Adicione `-AsHashtable` a `ConvertFrom-Json` para retornar um `Hashtable`. (#5043) (Obrigado, @bergmeister!)
- Use o formatador mais atraente com saída `ConvertTo-Json`. (#2787) (Obrigado, @kittholland!)
- Adicione suporte de serialização `Jobject` a `ConvertTo-Json`. (#5141)
- Corrija `ConvertFrom-Json` para desserializar uma matriz de cadeias de caracteres do pipeline que juntas constroem uma cadeia de caracteres JSON completa.
  Isso corrige alguns casos em que novas linhas interromperiam a análise JSON. (#3823)
- Remova `AliasProperty "Count"` definido para `System.Array`.
  Isso remove a propriedade `Count` estranha em alguma saída `ConvertFrom-Json`. (#3231) (Obrigado, @PetSerAl!)

### <a name="csv-cmdlets"></a>Cmdlets CSV

- Adicione suporte do `PSTypeName` para `Import-Csv` e `ConvertFrom-Csv`. (#5389) (Obrigado, @markekraus!)
- Defina suporte `Import-Csv` `CR`, `LF` e `CRLF` como delimitadores de linha. (#5363) (Obrigado, @iSazonov!)
- Defina `-NoTypeInformation` como padrão em `Export-Csv` e `ConvertTo-Csv`. (#5164) (Obrigado, @markekraus)

### <a name="service-cmdlets"></a>Cmdlets de serviço

- Adicione as propriedades `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName` e `StartupType` aos objetos `ServiceController` retornados por `Get-Service`. (#4907) (Obrigado, @joandrsn)
- Adicione a funcionalidade para definir as credenciais no comando `Set-Service`. (#4844) (Obrigado, @joandrsn)

### <a name="other-cmdlets"></a>Outros cmdlets

- Adicione um parâmetro a `Get-ChildItem` chamado `-FollowSymlink` que atravessa os links simbólicos sob demanda, com verificações quanto à existência de loops de link. (#4020)
- Atualize `Add-Type` para dar suporte a `CSharpVersion7`. (#3933) (Obrigado, @iSazonov!)
- Remova o módulo `Microsoft.PowerShell.LocalAccounts` devido ao uso de APIs sem suporte até encontrar a melhor solução. (#4302)
- Remova os cmdlets `*-Counter` em `Microsoft.PowerShell.Diagnostics` devido ao uso de APIs sem suporte até encontrar a melhor solução. (#4303)
- Adicione suporte para `Invoke-Item -Path <folder>`. (#4262)
- Adicione comutadores `-Extension` e `-LeafBase` a `Split-Path` para que você possa dividir caminhos entre a extensão de nome de arquivo e o restante do nome de arquivo. (#2721) (Obrigado, @powercode!)
- Adicione os parâmetros `-Top` e `-Bottom` a `Sort-Object` para classificação N Início/fim
- Exponha um processo pai do processo, adicionando `CodeProperty "Parent"` a `System.Diagnostics.Process`. (#2850) (Obrigado, @powercode!)
- Use MB em vez de KB para colunas de memória de `Get-Process`
- Adicione o comutador `-NoNewLine` para `Out-String`. (#5056) (Obrigado, @raghav710)
- O cmdlet `Move-Item` honra os parâmetros `-Include`, `-Exclude` e `-Filter`. (#3878)
- Permita que `*` seja usado no caminho do Registro para `Remove-Item`. (#4866)
- Adicione `-Title` a `Get-Credential` e unifique a experiência de prompt entre plataformas.
- Adicione o parâmetro `-TimeOut` a `Test-Connection`. (#2492)
- Agora, os cmdlets `Get-AuthenticodeSignature` podem obter o carimbo de data/hora de assinatura de arquivo. (#4061)
- Remova o comutador `-ShowWindow` sem suporte de `Get-Help`. (#4903)
- Corrija `Get-Content -Delimiter` para não incluir o delimitador nos elementos da matriz retornada (#3706) (Obrigado, @mklement0)
- Adicione os parâmetros `Meta`, `Charset` e `Transitional` a `ConvertTo-HTML` (#4184) (Obrigado, @ergo3114)
- Adicione as propriedades `WindowsUBR` e `WindowsVersion` ao resultado `Get-ComputerInfo`
- Adicione o parâmetro `-Group` a `Get-Verb`
- Adicione o suporte `ShouldProcess` a `New-FileCatalog` e `Test-FileCatalog` (correções `-WhatIf` e `-Confirm`). (#3074) (Obrigado, @iSazonov!)
- Adicione o comutador `-WhatIf` ao cmdlet `Start-Process` (#4735) (Obrigado, @sarithsutha)
- Adicione `ValidateNotNullOrEmpty` a muitos parâmetros existentes.

## <a name="tab-completion"></a>Preenchimento de guias

- Aprimoramento da inferência de tipos no preenchimento com tab com base nos valores de variável de tempo de execução. (#2744) (Obrigado, @powercode!) Isso permite o preenchimento com tab em situações como:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Adicione o preenchimento com tab de tabela de hash para `-Property` de `Select-Object`. (#3625) (Obrigado, @powercode!)
- Habilite o preenchimento automático de argumento para `-ExcludeProperty` e `-ExpandProperty` de `Select-Object`. (#3443) (Obrigado, @iSazonov!)
- Corrija um bug no preenchimento com tab para fazer `native.exe --<tab>` chamar o complemento nativo. (#3633) (Obrigado, @powercode!)

## <a name="breaking-changes"></a>Alterações recentes

Apresentamos inúmeras alterações recentes no PowerShell Core 6.0.
Para ler mais sobre elas em detalhes, veja [Alterações recentes no PowerShell Core 6.0][breaking-changes].

## <a name="debugging"></a>Depuração

- Suporte para depuração de interferência remota para `Invoke-Command -ComputerName`. (#3015)
- Habilitar registro em log da depuração do associador no PowerShell Core

## <a name="filesystem-updates"></a>Atualizações do sistema de arquivos

- Habilite o uso do provedor de sistema de arquivos de um caminho UNC. ($4998)
- Agora, `Split-Path` funciona com raízes UNC
- Agora, `cd` sem argumentos comporta-se como `cd ~`
- PowerShell Core corrigido para permitir o uso de caminhos com mais de 260 caracteres. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Correções de bug e aprimoramentos de desempenho

Fizemos *muitos* aprimoramentos de desempenho no PowerShell, incluindo em tempo de inicialização, vários cmdlets internos e interação com binários nativos.

Corrigimos também vários bugs no PowerShell Core.
Para obter uma lista completa de correções e alterações, confira nosso [log de alterações][] no GitHub.

## <a name="telemetry"></a>Telemetria

- O PowerShell Core 6.0 adicionou telemetria ao host do console para relatar dois valores (#3620):
  - a plataforma do sistema operacional (`$PSVersionTable.OSDescription`)
  - a versão exata do PowerShell (`$PSVersionTable.GitCommitId`)

Se você deseja excluir esta telemetria, basta excluir `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` ou criar uma variável de ambiente `POWERSHELL_TELEMETRY_OPTOUT` com um dos seguintes valores: `true`, `1` ou `yes`.
A exclusão desse arquivo ou a criação de variável ignora toda a telemetria mesmo antes da primeira execução do PowerShell.
Planejamos expor esses dados de telemetria e as informações coletadas da telemetria no [painel da comunidade][community-dashboard].
Encontre mais informações sobre como usamos esses dados nesta [postagem no blog][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[log de alterações]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET Blog]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[perguntas frequentes]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
