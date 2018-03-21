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
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="67b45-103">Auditoria e relatórios no JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="67b45-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="67b45-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="67b45-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="67b45-105">Após ter implantado o JEA, você desejará auditar regularmente a configuração JEA.</span><span class="sxs-lookup"><span data-stu-id="67b45-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="67b45-106">Isso ajudará a avaliar se as pessoas corretas têm acesso ao ponto de extremidade JEA e se suas funções atribuídas ainda são apropriadas.</span><span class="sxs-lookup"><span data-stu-id="67b45-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="67b45-107">Este tópico descreve as várias maneiras para fazer auditoria em um ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="67b45-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="67b45-108">Encontre sessões JEA registradas em um computador</span><span class="sxs-lookup"><span data-stu-id="67b45-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="67b45-109">Para verificar quais sessões JEA estão registradas em um computador, use o cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="67b45-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="67b45-110">Os direitos efetivos do ponto de extremidade estão listados na propriedade "Permissão".</span><span class="sxs-lookup"><span data-stu-id="67b45-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="67b45-111">Esses usuários têm o direito de conectar-se ao ponto de extremidade JEA, mas as funções (e, por extensão, os comandos) aos quais eles têm acesso é determinado pelo campo "RoleDefinitions" no [arquivo de configuração de sessão](session-configurations.md) que foi usado para registrar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="67b45-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="67b45-112">Você pode avaliar os mapeamentos de função em um ponto de extremidade JEA registrado expandindo os dados na propriedade "RoleDefinitions".</span><span class="sxs-lookup"><span data-stu-id="67b45-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="67b45-113">Encontre recursos de função disponíveis no computador</span><span class="sxs-lookup"><span data-stu-id="67b45-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="67b45-114">Os arquivos de capacidade da função serão usados pelo JEA somente se estiverem armazenados em uma pasta "RoleCapabilities" dentro de um módulo de PowerShell válido.</span><span class="sxs-lookup"><span data-stu-id="67b45-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="67b45-115">Você pode localizar todos os recursos de função disponíveis em um computador, pesquisando a lista de módulos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="67b45-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

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
> <span data-ttu-id="67b45-116">A ordem dos resultados dessa função não é, necessariamente, a ordem na qual os recursos de função serão selecionados se vários recursos de função compartilham o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="67b45-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="67b45-117">Verifique os direitos efetivos de um usuário específico</span><span class="sxs-lookup"><span data-stu-id="67b45-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="67b45-118">Depois de configurar um ponto de extremidade JEA, convém verificar quais comandos estão disponíveis a um usuário específico em uma sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="67b45-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="67b45-119">Você pode usar [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) para enumerar todos os comandos aplicáveis a um usuário se os usuários fossem iniciar uma sessão JEA com suas associações de grupo atual.</span><span class="sxs-lookup"><span data-stu-id="67b45-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="67b45-120">A saída de `Get-PSSessionCapability` é idêntica à saída do usuário especificado executando o `Get-Command -CommandType All` em uma sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="67b45-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="67b45-121">Se os usuários não forem membros permanentes de grupos que concederiam a eles direitos adicionais de JEA, esse cmdlet poderá não refletir essas permissões adicionais.</span><span class="sxs-lookup"><span data-stu-id="67b45-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="67b45-122">Esse é normalmente o caso ao usar sistemas de gerenciamento de acesso privilegiado just-in-time para permitir que os usuários pertençam temporariamente a um grupo de segurança.</span><span class="sxs-lookup"><span data-stu-id="67b45-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="67b45-123">Sempre avalie cuidadosamente o mapeamento de usuários para as funções e os conteúdos de cada função para garantir que os usuários obtenham acesso apenas à quantidade mínima de comandos necessários para realizar seus trabalhos com êxito.</span><span class="sxs-lookup"><span data-stu-id="67b45-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="67b45-124">Logs de eventos do PowerShell</span><span class="sxs-lookup"><span data-stu-id="67b45-124">PowerShell event logs</span></span>

<span data-ttu-id="67b45-125">Se você habilitou o log de módulo e/ou o registro em log de bloco de script no sistema, poderá encontrar eventos nos logs de eventos do Windows para cada comando executado por um usuário em suas sessões JEA.</span><span class="sxs-lookup"><span data-stu-id="67b45-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="67b45-126">Para localizar esses eventos, abra o Visualizador de Eventos do Windows, navegue até o log de eventos **Microsoft-Windows-PowerShell/Operational** e procure eventos com a ID do evento **4104**.</span><span class="sxs-lookup"><span data-stu-id="67b45-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="67b45-127">Cada entrada de log de eventos incluirá informações sobre a sessão na qual o comando foi executado.</span><span class="sxs-lookup"><span data-stu-id="67b45-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="67b45-128">Para sessões JEA, isso inclui informações importantes sobre o **ConnectedUser**, que é o usuário real que criou a sessão JEA, bem como o **RunAsUser**, que identifica a conta JEA usada para executar o comando.</span><span class="sxs-lookup"><span data-stu-id="67b45-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="67b45-129">Os logs de eventos do aplicativo mostrarão as alterações feitas pelo RunAsUser, portanto, habilitar as transcrições ou o registro em log de módulo/script é crucial para poder rastrear uma invocação de comando específica de um usuário.</span><span class="sxs-lookup"><span data-stu-id="67b45-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="67b45-130">Logs de eventos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="67b45-130">Application event logs</span></span>

<span data-ttu-id="67b45-131">Quando você executa um comando em uma sessão JEA que interage com um aplicativo ou um serviço externo, esses aplicativos podem registrar eventos em seus próprios logs de eventos.</span><span class="sxs-lookup"><span data-stu-id="67b45-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="67b45-132">Diferentemente dos logs e transcrições do PowerShell, outros mecanismos de registro em log não capturarão o usuário conectado da sessão JEA e, em vez disso, registrarão somente a conta de serviço gerenciado de grupo ou o usuário virtual Run As.</span><span class="sxs-lookup"><span data-stu-id="67b45-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="67b45-133">Para determinar quem executou o comando, você precisará consultar uma [transcrição da sessão](#session-transcripts) ou correlacionar os logs de eventos do PowerShell com a hora e o usuário mostrados no log de eventos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="67b45-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="67b45-134">O log WinRM também pode ajudar a correlacionar os usuários Run As, em um log de eventos do aplicativo, com o usuário que está se conectando.</span><span class="sxs-lookup"><span data-stu-id="67b45-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="67b45-135">A ID do evento **193** no log **Microsoft-Windows-Windows Remote Management/Operational** registra o SID (identificador de segurança) e o nome de conta do usuário que está se conectando e do usuário Run As, sempre que uma sessão JEA é criada.</span><span class="sxs-lookup"><span data-stu-id="67b45-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="67b45-136">Transcrições de sessão</span><span class="sxs-lookup"><span data-stu-id="67b45-136">Session transcripts</span></span>

<span data-ttu-id="67b45-137">Se você configurou o JEA para criar uma transcrição para cada sessão de usuário, uma cópia do texto de todas as ações de usuário será armazenada na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="67b45-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="67b45-138">Para localizar todos os diretórios de transcrição, execute o seguinte comando como administrador no computador configurado com o JEA:</span><span class="sxs-lookup"><span data-stu-id="67b45-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="67b45-139">Cada transcrição começa com informações sobre a hora em que a sessão foi iniciada, qual usuário se conectou à sessão e qual identidade JEA foi atribuída a eles.</span><span class="sxs-lookup"><span data-stu-id="67b45-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="67b45-140">No corpo da transcrição são registradas as informações sobre cada comando invocado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="67b45-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="67b45-141">A sintaxe exata do comando que foi executado pelo usuário não está disponível nas sessões JEA devido à maneira como os comandos são transformados para a comunicação remota do PowerShell, no entanto, você ainda poderá determinar o comando efetivo que foi executado.</span><span class="sxs-lookup"><span data-stu-id="67b45-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="67b45-142">Abaixo está um exemplo de trecho de transcrição de um usuário executando `Get-Service Dns` em uma sessão JEA:</span><span class="sxs-lookup"><span data-stu-id="67b45-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="67b45-143">Para cada comando que um usuário executa, uma linha "CommandInvocation" será escrita, descrevendo o cmdlet ou a função invocada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="67b45-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="67b45-144">O ParameterBindings segue cada CommandInvocation para informar sobre cada parâmetro e valor que foi fornecido com o comando.</span><span class="sxs-lookup"><span data-stu-id="67b45-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="67b45-145">No exemplo acima, você pode ver que o parâmetro "Nome" foi fornecido com o valor "Dns" para o cmdlet "Get-Service".</span><span class="sxs-lookup"><span data-stu-id="67b45-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="67b45-146">A saída de cada comando também disparará um CommandInvocation, geralmente para Out-Default.</span><span class="sxs-lookup"><span data-stu-id="67b45-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span> <span data-ttu-id="67b45-147">O InputObject do Out-Default é o objeto do PowerShell retornado pelo comando.</span><span class="sxs-lookup"><span data-stu-id="67b45-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="67b45-148">Os detalhes desse objeto estão impressos algumas linhas abaixo, imitando de perto o que o usuário veria.</span><span class="sxs-lookup"><span data-stu-id="67b45-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="67b45-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67b45-149">See also</span></span>

- [<span data-ttu-id="67b45-150">Auditar ações de usuário em uma sessão JEA</span><span class="sxs-lookup"><span data-stu-id="67b45-150">Audit user actions in a JEA session</span></span>](audit-and-report.md)
- [<span data-ttu-id="67b45-151">*Postagem no blog sobre segurança* PowerShell ♥ the Blue Team</span><span class="sxs-lookup"><span data-stu-id="67b45-151">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

