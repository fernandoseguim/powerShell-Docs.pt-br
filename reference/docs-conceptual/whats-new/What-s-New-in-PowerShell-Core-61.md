---
title: Novidades no PowerShell Core 6.1
description: Novos recursos e alterações liberados no PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 5e2fe3c819ed638b2c14d7d40e08b7c32953147f
ms.sourcegitcommit: 59e568ac9fa8ba28e2c96932b7c84d4a855fed2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46289218"
---
# <a name="whats-new-in-powershell-core-61"></a>Novidades no PowerShell Core 6.1

Abaixo está uma seleção de alguns dos principais recursos novos e alterações que foram introduzidos no PowerShell Core 6.1.

Também há **toneladas** de "coisas chatas" que tornam o PowerShell mais rápido e mais estável (além de muitas e muitas correções de bugs)!
Para obter uma lista completa de alterações, confira nosso [log de alterações no GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Apesar de citarmos alguns nomes abaixo, obrigado a [todos os colaboradores da comunidade](https://github.com/PowerShell/PowerShell/graphs/contributors) que possibilitaram esta versão.

## <a name="net-core-21"></a>.NET Core 2.1

O PowerShell Core 6.1 migrou para o .NET Core 2.1 depois de ter sido [liberado em maio](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resultando em muitas melhorias no PowerShell, incluindo:

- aprimoramentos de desempenho (veja [abaixo](#performance-improvements))
- Suporte a Alpine Linux (versão prévia)
- [Suporte à ferramenta global .NET](/dotnet/core/tools/global-tools) – em breve no PowerShell
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>Pacote de compatibilidade do Windows para o .NET Core

No Windows, a equipe do .NET enviou o [pacote de compatibilidade do Windows para o .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), um conjunto de assemblies que devolve algumas APIs removidas ao .NET Core no Windows.

Adicionamos o pacote de compatibilidade do Windows à versão do PowerShell Core 6.1 para que os módulos ou scripts que usam essas APIs possam acreditar que estarão disponíveis.

O pacote de compatibilidade do Windows permite que o PowerShell Core use **mais de 1900 cmdlets que acompanham a atualização de outubro de 2018 do Windows 10 e o Windows Server 2019**.

## <a name="support-for-application-whitelisting"></a>Suporte à lista de permissões de aplicativos

O PowerShell Core 6.1 tem paridade com o Windows PowerShell 5.1, com suporte para lista de permissões de aplicativos do [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) e do [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control).
A lista de permissões de aplicativos permite um controle granular de quais binários podem ser executados, usado com o [modo de linguagem restrita](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/) do PowerShell.

## <a name="performance-improvements"></a>Aprimoramentos do desempenho

O PowerShell Core 6.0 fez alguns aprimoramentos significativos no desempenho.
O PowerShell Core 6.1 continua aumentando a velocidade de determinadas operações.

Por exemplo, `Group-Object` foi acelerado em 66%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tempo (s)   | 25,178                 | 19,653              | 6,641               |
| Aceleração (%) | N/D                    | 21,9%               | 66,2%               |

Da mesma forma, a classificação de cenários como este melhorou em mais de 15%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tempo (s)   | 12,170                 | 8,493               | 7,08                |
| Aceleração (%) | N/D                    | 30,2%               | 16,6%               |

`Import-Csv` também acelerou significativamente após uma regressão do Windows PowerShell.
O exemplo a seguir usa um CSV de teste com 26.616 linhas e seis colunas:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tempo (s)   | 0,441                  | 1,069               | 0,268                  |
| Aceleração (%) | N/D                    | -142,4%             | 74,9% (39,2% de WPS) |

Por fim, a conversão de JSON em `PSObject` acelerou em mais de 50% desde o Windows PowerShell.
O exemplo a seguir usa um arquivo JSON de teste de cerca de 2MB:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tempo (s)   | 0,259                  | 0,577               | 0,125                  |
| Aceleração (%) | N/D                    | -122,8%             | 78,3% (51,7% de WPS) |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a>Verificar `system32` se há módulos de caixa de entrada compatíveis no Windows

Na atualização 1809 do Windows 10 e no Windows Server 2019, atualizamos alguns módulos do PowerShell na caixa de entrada para marcá-los como compatíveis com o PowerShell Core.

Quando o PowerShell Core 6.1 for iniciado, ele incluirá `$windir\System32` automaticamente como parte da variável de ambiente `PSModulePath`.
No entanto, expõe módulos somente para `Get-Module` e `Import-Module` se seu `CompatiblePSEdition` está marcado como compatível `Core`.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> Você pode ver diferentes módulos disponíveis dependendo de quais funções e recursos estão instalados.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

Pode substituir esse comportamento para mostrar todos os módulos usando o parâmetro de opção `-SkipEditionCheck`.
Também adicionamos uma propriedade `PSEdition` à saída de tabela.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Para obter mais informações sobre esse comportamento, confira [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Cmdlets de markdown e renderização

O markdown é um padrão para a criação de documentos de texto não criptografado legíveis com formatação básica que possam ser renderizados em HTML.

Adicionamos alguns cmdlets em um 6.1 o que permite converter e renderizar documentos de Markdown no console, incluindo:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Por exemplo, `Show-Markdown` renderiza um arquivo markdown no console:

![Exemplo de Markdown do show](./images/markdown_example.png)

Para obter mais informações sobre como esses cmdlets funcionam, confira [essa RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Sinalizadores de recursos experimentais

Com os sinalizadores de recursos experimentais, os usuários podem habilitar recursos que não foram finalizados.
Esses recursos experimentais não têm suporte e podem conter bugs.

Você pode aprender mais sobre esse recurso no [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Aprimoramentos do cmdlet da Web

Graças a [@markekraus](https://github.com/markekraus), uma grande quantidade de melhorias foi feita em nossos cmdlets da Web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
e [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).

- [PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) – conjunto de codificação padrão para UTF-8 para respostas `application-json`
- Parâmetro [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` para permitir cabeçalhos `Content-Type` que não estão em conformidade com as regras
- Parâmetro [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` para dar suporte ao suporte `multipart/form-data` simplificado
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) – Em conformidade, tratamento de chaves de relação sem distinção entre maiúsculas e minúsculas
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) – Adicionar parâmetro `-Resume` para cmdlets da Web

## <a name="remoting-improvements"></a>Aprimoramentos na comunicação remota

### <a name="powershell-direct-tries-to-use-powershell-core-first"></a>O PowerShell Direct tenta usar primeiro o PowerShell Core

O [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) é um recurso do PowerShell e do Hyper-V que permite que você se conecte a uma VM do Hyper-V sem conectividade de rede ou outros serviços de gerenciamento remoto.

No passado, o PowerShell Direct era conectado usando a instância do Windows PowerShell de caixa de entrada na VM.
Agora, o PowerShell Direct primeiro tenta se conectar usando algum `pwsh.exe` disponível na variável de ambiente `PATH`.
Se `pwsh.exe` não estiver disponível, o PowerShell Direct voltará a usar `powershell.exe`.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` já cria pontos de extremidade de comunicação remota separados para versões prévias

`Enable-PSRemoting` já cria duas configurações de sessão de comunicação remota:

- Uma para a versão principal do PowerShell. Por exemplo, `PowerShell.6`. Esse ponto de extremidade que pode ser utilizado em versões secundárias é atualizado como a configuração de sessão do PowerShell 6 "para todo o sistema"
- Uma configuração de sessão específica da versão, por exemplo: `PowerShell.6.1.0`

Esse comportamento será útil se você quiser ter várias versões do PowerShell 6 instaladas e acessíveis no mesmo computador.

Além disso, as versões prévias do PowerShell já têm suas próprias configurações de sessão de comunicação remota depois de executar o cmdlet `Enable-PSRemoting`:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

A saída poderá ser diferente se você ainda não tiver configurado o WinRM.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Em seguida, pode ver as configurações de sessão separadas do PowerShell para a versão prévia e builds estáveis do PowerShell 6, assim como para cada versão específica.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>Sintaxe `user@host:port` com suporte para o SSH

Os clientes do SSH geralmente dão suporte a uma cadeia de conexão no formato `user@host:port`.
Com a adição de SSH como um protocolo de comunicação remota do PowerShell, adicionamos suporte para esse formato de cadeia de conexão:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>Opção de MSI para adicionar o menu de contexto de shell do Explorer no Windows

Graças a [@bergmeister](https://github.com/bergmeister), já é possível habilitar um menu de contexto no Windows. Agora, você pode abrir a instalação do PowerShell 6.1 para todo o sistema por meio de qualquer pasta no Windows Explorer:

![Menu de contexto do shell do PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a>Coisas boas

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>"Executar como administrador" na lista de atalhos do Windows

Graças a [@bergmeister](https://github.com/bergmeister), a lista de atalhos do PowerShell Core passou a incluir "Executar como administrador":

![Executar como administrador na lista de atalhos do PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` retorna ao diretório anterior

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

Ou no Linux:

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

Além, `cd` e `cd --` mudam para `$HOME`.

### `Test-Connection`

Graças a [@iSazonov](https://github.com/iSazonov), o [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet foi movido para o PowerShell Core.

### <a name="update-help-as-non-admin"></a>`Update-Help` como não administrador

Por demanda popular, `Update-Help` não precisa mais ser executado como um administrador.
Agora, o padrão de `Update-Help` é salvar a ajuda em uma pasta no escopo do usuário.

### <a name="new-methodsproperties-on-pscustomobject"></a>Novos métodos/propriedades em `PSCustomObject`

Graças a [@iSazonov](https://github.com/iSazonov), incluímos novos métodos e propriedades em `PSCustomObject`.
`PSCustomObject` passou a incluir uma propriedade `Count`/`Length` que informa o número de itens.

Os dois exemplos retornam `2` como o número de `PSCustomObjects` na coleção.

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Length
```

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Count
```

Esse trabalho também inclui os métodos `ForEach` e `Where`, que permitem que você utilize e filtre os itens `PSCustomObject`:

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).ForEach({$_.foo+1})
```

```Output
2
3
```

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).Where({$_.foo -gt 1})
```

```Output
foo
---
  2
```

### `Where-Object -Not`

Graças a @SimonWahlin, incluímos o parâmetro `-Not` em `Where-Object`.
Agora, é possível filtrar um objeto no pipeline por inexistência de uma propriedade ou um valor de propriedade nula/vazia.

Por exemplo, esse comando retorna todos os serviços que não têm serviços dependentes definidos:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` cria um documento de UTF-8 sem marca de ordem de byte

Dada nossa migração para UTF-8 sem marca de ordem de byte no PowerShell 6.0, atualizamos o cmdlet `New-ModuleManifest` para criar um documento UTF-8 sem marca de ordem de byte ao invés de um UTF-16.

### <a name="conversions-from-psmethod-to-delegate"></a>Conversões de PSMethod para delegado

Graças a [@powercode](https://github.com/powercode), passamos a dar suporte para a conversão de `PSMethod` em um delegado.
Assim, é possível fazer coisas como passar `PSMethod` `[M]::DoubleStrLen` como valor delegado para `[M]::AggregateString`:

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

Para obter mais informações sobre essa alteração, confira [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Desvio padrão em `Measure-Object`

Graças a [@CloudyDino](https://github.com/CloudyDino), incluímos uma propriedade `StandardDeviation` em `Measure-Object`:

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

Graças a [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` passou a ter o parâmetro `Password`, que pega um `SecureString`. Assim, você pode usá-lo de forma não interativa:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Remoção da função `more`

No passado, o PowerShell enviou uma função no Windows chamada `more`, que encapsulou `more.com`.
Essa função foi removida.

Além disso, a função `help` foi alterada para usar `more.com` no Windows ou o pager padrão do sistema especificado por `$env:PAGER` em plataformas não Windows.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>Agora, `cd DriveName:` retorna os usuários para o diretório de trabalho atual na unidade

Anteriormente, o uso de `Set-Location` ou `cd` para retornar para um PSDrive enviava aos usuários ao local padrão para essa unidade.

Graças a [@mcbobke](https://github.com/mcbobke), os usuários são enviados ao último diretório de trabalho atual conhecido para a sessão.

### <a name="windows-powershell-type-accelerators"></a>Aceleradores de tipo do Windows PowerShell

No Windows PowerShell, incluímos os seguintes aceleradores de tipo para facilitar o trabalho com os respectivos tipos:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

Esses aceleradores de tipo não foram incluídos no PowerShell 6, mas foram incluídos no PowerShell 6.1 em execução no Windows.

Esses tipos são úteis para construir objetos AD e WMI facilmente.

É possível, por exemplo, consultar usando LDAP:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

O exemplo a seguir cria um objeto CIM Win32_OperatingSystem:

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

Esse exemplo retorna um objeto ManagementClass para a classe Win32_OperatingSystem.

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>Alias `-lp` para todos os parâmetros `-LiteralPath`

Graças a [@kvprasoon](https://github.com/kvprasoon), passamos a ter um alias de parâmetro `-lp` para todos os cmdlets internos do PowerShell que têm um parâmetro `-LiteralPath`.

## <a name="breaking-changes"></a>Alterações da falha

### <a name="msi-based-installation-paths-on-windows"></a>Caminhos de instalação baseada em MSI no Windows

No Windows, o pacote MSI passou a ser instalado neste caminho:

- `$env:ProgramFiles\PowerShell\6\` para a instalação estável do 6.x
- `$env:ProgramFiles\PowerShell\6-preview\` para a instalação da versão prévia do 6.x

Essa alteração garante que o PowerShell Core possa ser atualizado/atendido pelo Microsoft Update.

Para obter mais informações, confira [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>A telemetria só pode ser desabilitada com uma variável de ambiente

O PowerShell Core envia dados telemétricos básicos à Microsoft quando é iniciado. Os dados incluem o nome do sistema operacional, a versão do sistema operacional e a versão do PowerShell. Com esses dados, podemos entender melhor os ambientes nos quais o PowerShell é usado, além de priorizar novos recursos e correções.

Para recusar essa telemetria, defina a variável de ambiente `POWERSHELL_TELEMETRY_OPTOUT` para `true`, `yes` ou `1`. Não damos mais suporte à exclusão do arquivo `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` para desabilitar a telemetria.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Autenticação básica não permitida por HTTP na Comunicação Remota do PowerShell em plataformas Unix

Para evitar o uso de tráfego não criptografado, a Comunicação Remota do PowerShell em plataformas Unix agora exige o uso de NTLM/Negotiate ou HTTPS.

Para obter mais informações sobre essas alterações, confira [PR #6799](https://github.com/PowerShell/PowerShell/pull/6799).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>`VisualBasic` removido como linguagem com suporte em Add-Type

No passado, era possível compilar o código do Visual Basic usando o cmdlet `Add-Type`.
O Visual Basic raramente era usado com `Add-Type`. Removemos esse recurso para reduzir o tamanho do PowerShell.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Usos limpos de `CommandTypes.Workflow` e `WorkflowInfoCleaned`

Para obter mais informações sobre essas alterações, confira [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).
