---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea,powershell,segurança"
title: "Auditoria e relatórios no JEA (Just Enough Administration)"
ms.openlocfilehash: 57148bc3753bdd751bfa21fc3198aca3f8654849
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="auditing-and-reporting-on-jea"></a>Auditoria e relatórios no JEA (Just Enough Administration)

> Aplica-se a: Windows PowerShell 5.0

Após ter implantado o JEA, você desejará auditar regularmente a configuração JEA.
Isso ajudará a avaliar se as pessoas corretas têm acesso ao ponto de extremidade JEA e se suas funções atribuídas ainda são apropriadas.

Este tópico descreve as várias maneiras para fazer auditoria em um ponto de extremidade JEA.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Encontre sessões JEA registradas em um computador

Para verificar quais sessões JEA estão registradas em um computador, use o cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Os direitos efetivos do ponto de extremidade estão listados na propriedade "Permissão".
Esses usuários têm o direito de conectar-se ao ponto de extremidade JEA, mas as funções (e, por extensão, os comandos) aos quais eles têm acesso é determinado pelo campo "RoleDefinitions" no [arquivo de configuração de sessão](session-configurations.md) que foi usado para registrar o ponto de extremidade.

Você pode avaliar os mapeamentos de função em um ponto de extremidade JEA registrado expandindo os dados na propriedade "RoleDefinitions".

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Encontre recursos de função disponíveis no computador

Os arquivos de capacidade da função serão usados pelo JEA somente se estiverem armazenados em uma pasta "RoleCapabilities" dentro de um módulo de PowerShell válido.
Você pode localizar todos os recursos de função disponíveis em um computador, pesquisando a lista de módulos disponíveis.

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> A ordem dos resultados dessa função não é, necessariamente, a ordem na qual os recursos de função serão selecionados se vários recursos de função compartilham o mesmo nome.

## <a name="check-effective-rights-for-a-specific-user"></a>Verifique os direitos efetivos de um usuário específico

Depois de configurar um ponto de extremidade JEA, convém verificar quais comandos estão disponíveis a um usuário específico em uma sessão JEA.
Você pode usar [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) para enumerar todos os comandos aplicáveis a um usuário se os usuários fossem iniciar uma sessão JEA com suas associações de grupo atual.
A saída de `Get-PSSessionCapability` é idêntica à saída do usuário especificado executando o `Get-Command -CommandType All` em uma sessão JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Se os usuários não forem membros permanentes de grupos que concederiam a eles direitos adicionais de JEA, esse cmdlet poderá não refletir essas permissões adicionais.
Esse é normalmente o caso ao usar sistemas de gerenciamento de acesso privilegiado just-in-time para permitir que os usuários pertençam temporariamente a um grupo de segurança.
Sempre avalie cuidadosamente o mapeamento de usuários para as funções e os conteúdos de cada função para garantir que os usuários obtenham acesso apenas à quantidade mínima de comandos necessários para realizar seus trabalhos com êxito.

## <a name="powershell-event-logs"></a>Logs de eventos do PowerShell

Se você habilitou o log de módulo e/ou o registro em log de bloco de script no sistema, poderá encontrar eventos nos logs de eventos do Windows para cada comando executado por um usuário em suas sessões JEA.
Para localizar esses eventos, abra o Visualizador de Eventos do Windows, navegue até o log de eventos **Microsoft-Windows-PowerShell/Operational** e procure eventos com a ID do evento **4104**.

Cada entrada de log de eventos incluirá informações sobre a sessão na qual o comando foi executado.
Para sessões JEA, isso inclui informações importantes sobre o **ConnectedUser**, que é o usuário real que criou a sessão JEA, bem como o **RunAsUser**, que identifica a conta JEA usada para executar o comando.
Os logs de eventos do aplicativo mostrarão as alterações feitas pelo RunAsUser, portanto, habilitar as transcrições ou o registro em log de módulo/script é crucial para poder rastrear uma invocação de comando específica de um usuário.

## <a name="application-event-logs"></a>Logs de eventos do aplicativo

Quando você executa um comando em uma sessão JEA que interage com um aplicativo ou um serviço externo, esses aplicativos podem registrar eventos em seus próprios logs de eventos.
Diferentemente dos logs e transcrições do PowerShell, outros mecanismos de registro em log não capturarão o usuário conectado da sessão JEA e, em vez disso, registrarão somente a conta de serviço gerenciado de grupo ou o usuário virtual Run As.
Para determinar quem executou o comando, você precisará consultar uma [transcrição da sessão](#session-transcripts) ou correlacionar os logs de eventos do PowerShell com a hora e o usuário mostrados no log de eventos do aplicativo.

O log WinRM também pode ajudar a correlacionar os usuários Run As, em um log de eventos do aplicativo, com o usuário que está se conectando.
A ID do evento **193** no log **Microsoft-Windows-Windows Remote Management/Operational** registra o SID (identificador de segurança) e o nome de conta do usuário que está se conectando e do usuário Run As, sempre que uma sessão JEA é criada.

## <a name="session-transcripts"></a>Transcrições de sessão

Se você configurou o JEA para criar uma transcrição para cada sessão de usuário, uma cópia do texto de todas as ações de usuário será armazenada na pasta especificada.

Para localizar todos os diretórios de transcrição, execute o seguinte comando como administrador no computador configurado com o JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

Cada transcrição começa com informações sobre a hora em que a sessão foi iniciada, qual usuário se conectou à sessão e qual identidade JEA foi atribuída a eles.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

No corpo da transcrição são registradas as informações sobre cada comando invocado pelo usuário.
A sintaxe exata do comando que foi executado pelo usuário não está disponível nas sessões JEA devido à maneira como os comandos são transformados para a comunicação remota do PowerShell, no entanto, você ainda poderá determinar o comando efetivo que foi executado.
Abaixo está um exemplo de trecho de transcrição de um usuário executando `Get-Service Dns` em uma sessão JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Para cada comando que um usuário executa, uma linha "CommandInvocation" será escrita, descrevendo o cmdlet ou a função invocada pelo usuário.
O ParameterBindings segue cada CommandInvocation para informar sobre cada parâmetro e valor que foi fornecido com o comando.
No exemplo acima, você pode ver que o parâmetro "Nome" foi fornecido com o valor "Dns" para o cmdlet "Get-Service".

A saída de cada comando também disparará um CommandInvocation, geralmente para Out-Default. O InputObject do Out-Default é o objeto do PowerShell retornado pelo comando.
Os detalhes desse objeto estão impressos algumas linhas abaixo, imitando de perto o que o usuário veria.

## <a name="see-also"></a>Consulte também

- [Auditar ações de usuário em uma sessão JEA](audit-and-report.md)
- [*Postagem no blog sobre segurança* PowerShell ♥ the Blue Team](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

