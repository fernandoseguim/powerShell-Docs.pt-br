---
ms.date: 06/12/2017
keywords: jea,powershell,segurança
title: Usando JEA
ms.openlocfilehash: fa3d3a3c8bc0090ec9ad788585ec5df933134173
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054672"
---
# <a name="using-jea"></a><span data-ttu-id="c0999-103">Usando JEA</span><span class="sxs-lookup"><span data-stu-id="c0999-103">Using JEA</span></span>

> <span data-ttu-id="c0999-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c0999-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c0999-105">Este tópico descreve as várias maneiras pelas quais você pode se conectar e usar um ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="c0999-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="c0999-106">Usando o JEA interativamente</span><span class="sxs-lookup"><span data-stu-id="c0999-106">Using JEA interactively</span></span>

<span data-ttu-id="c0999-107">Se você estiver testando sua configuração JEA ou tiver tarefas simples para os usuários executarem, você poderá usar o JEA da mesma forma que faria com uma sessão de comunicação remota regular do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0999-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="c0999-108">Para tarefas de comunicação remota complexas, é recomendável usar a [comunicação remota implícita](#using-jea-with-implicit-remoting) em vez disso, para facilitar para os usuários, permitindo que eles operem com os objetos de dados localmente.</span><span class="sxs-lookup"><span data-stu-id="c0999-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="c0999-109">Para usar o JEA interativamente, você precisará:</span><span class="sxs-lookup"><span data-stu-id="c0999-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="c0999-110">Do nome do computador ao qual está se conectando (pode ser o computador local)</span><span class="sxs-lookup"><span data-stu-id="c0999-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="c0999-111">Do nome do ponto de extremidade JEA registrado nesse computador</span><span class="sxs-lookup"><span data-stu-id="c0999-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="c0999-112">Das credenciais para o computador que tem acesso ao ponto de extremidade JEA</span><span class="sxs-lookup"><span data-stu-id="c0999-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="c0999-113">Com essas informações em mãos, você pode iniciar uma sessão JEA usando [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="c0999-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="c0999-114">Se a conta na qual está conectado no momento tem acesso ao ponto de extremidade JEA, você poderá omitir o parâmetro `-Credential`.</span><span class="sxs-lookup"><span data-stu-id="c0999-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="c0999-115">Quando o prompt do PowerShell mudar para `[localhost]: PS>` você saberá que está interagindo com a sessão remota do JEA.</span><span class="sxs-lookup"><span data-stu-id="c0999-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="c0999-116">Você pode executar o `Get-Command` para verificar quais comandos estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c0999-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="c0999-117">Você precisará consultar o administrador para saber se há alguma restrição nos parâmetros disponíveis ou nos valores de parâmetro permitidos.</span><span class="sxs-lookup"><span data-stu-id="c0999-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="c0999-118">Como lembrete, as sessões JEA operam no modo NoLanguage, portanto, algumas das maneiras que você normalmente usa o PowerShell podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c0999-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="c0999-119">Por exemplo, você não pode usar variáveis para armazenar dados ou inspecionar as propriedades em objetos retornados de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c0999-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="c0999-120">Abaixo há um exemplo que mostra como você usa PowerShell atualmente e duas abordagens para obter o mesmo funcionamento de comando no modo NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="c0999-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="c0999-121">Para invocações de comando mais complexas que tornam essa abordagem difícil, considere o uso de [comunicação remota implícita](#using-jea-with-implicit-remoting) ou da [criação de funções personalizadas](role-capabilities.md#creating-custom-functions) que encapsulam a funcionalidade desejada.</span><span class="sxs-lookup"><span data-stu-id="c0999-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="c0999-122">Usando o JEA com comunicação remota implícita</span><span class="sxs-lookup"><span data-stu-id="c0999-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="c0999-123">O PowerShell oferece suporte a um modelo de comunicação remota alternativo no qual é possível importar cmdlets do proxy de um computador remoto para o computador local e interagir com eles como se fossem comandos locais.</span><span class="sxs-lookup"><span data-stu-id="c0999-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="c0999-124">Esse modelo é chamado de comunicação remota implícita e é bem explicado [nessa postagem de blog *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="c0999-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="c0999-125">A comunicação remota implícita é particularmente útil ao trabalhar com o JEA porque permite que você trabalhe com os cmdlets do JEA em um modo de linguagem completa.</span><span class="sxs-lookup"><span data-stu-id="c0999-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="c0999-126">Isso significa que é possível usar a conclusão de guia, variáveis, manipular objetos e até mesmo usar scripts locais para automatizar mais facilmente em um ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="c0999-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="c0999-127">Sempre que você invocar um comando de proxy, os dados serão enviados ao ponto de extremidade JEA no computador remoto e executados lá.</span><span class="sxs-lookup"><span data-stu-id="c0999-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="c0999-128">A comunicação remota implícita funciona ao importar cmdlets de uma sessão existente do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0999-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="c0999-129">Opcionalmente, é possível colocar prefixos nos substantivos de cada cmdlet de proxy, com uma cadeia de caracteres à sua escolha, para distinguir quais comandos são do sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="c0999-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="c0999-130">Um módulo de script temporário contendo todos os comandos de proxy será criado e poderá ser usado enquanto durar a sessão local do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0999-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="c0999-131">Alguns sistemas poderão não ser capazes de importar uma sessão inteira do JEA devido a restrições em cmdlets padrão do JEA.</span><span class="sxs-lookup"><span data-stu-id="c0999-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="c0999-132">Para contornar isso, importe apenas os comandos necessários da sessão JEA fornecendo explicitamente os nomes deles para o parâmetro `-CommandName`.</span><span class="sxs-lookup"><span data-stu-id="c0999-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="c0999-133">Uma atualização futura solucionará o problema com a importação de sessões inteiras do JEA nos sistemas afetados.</span><span class="sxs-lookup"><span data-stu-id="c0999-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="c0999-134">Se não for possível importar uma sessão JEA devido a restrições nos parâmetros padrão do JEA, você poderá seguir as etapas abaixo para filtrar os comandos padrão do conjunto importado.</span><span class="sxs-lookup"><span data-stu-id="c0999-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="c0999-135">Ainda será possível usar comandos como o `Select-Object` – você usará a versão local instalada no computador em vez da versão remota, na sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="c0999-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

<span data-ttu-id="c0999-136">Também é possível manter os cmdlets do proxy da comunicação remota implícita, usando o [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="c0999-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="c0999-137">Para obter mais informações sobre a comunicação remota implícita, consulte a documentação de ajuda para [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) e [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="c0999-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="c0999-138">Usando o JEA de forma programática</span><span class="sxs-lookup"><span data-stu-id="c0999-138">Using JEA programmatically</span></span>

<span data-ttu-id="c0999-139">O JEA também pode ser usado em sistemas de automação e em aplicativos de usuário, como aplicativos de assistência técnica interna e sites da Web.</span><span class="sxs-lookup"><span data-stu-id="c0999-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="c0999-140">A abordagem é a mesma que a da criação de aplicativos que se comunicam com pontos de extremidade irrestritos do PowerShell, com a ressalva de que o programa deve estar ciente de que o JEA está limitando os comandos que podem ser executados na sessão remota.</span><span class="sxs-lookup"><span data-stu-id="c0999-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="c0999-141">Para tarefas simples e únicas, você pode usar [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) para executar um conjunto de comandos usando o JEA.</span><span class="sxs-lookup"><span data-stu-id="c0999-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="c0999-142">Para verificar quais comandos estão disponíveis para uso quando você se conectar a uma sessão JEA, execute o `Get-Command` e percorra os resultados para verificar os parâmetros permitidos.</span><span class="sxs-lookup"><span data-stu-id="c0999-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="c0999-143">Se estiver compilando um aplicativo C#, você pode criar um runspace do PowerShell que se conecta a uma sessão JEA, especificando o nome da configuração em um objeto [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="c0999-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
                    creds);                // Credentials
// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="c0999-144">Usando o JEA com o PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="c0999-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="c0999-145">O Hyper-V no Windows 10 e o Windows Server 2016 oferecem o [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), um recurso que permite aos administradores do Hyper-V gerenciar máquinas virtuais com o PowerShell, independentemente da configuração da rede ou das configurações de gerenciamento remoto na máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="c0999-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="c0999-146">É possível usar o PowerShell Direct com o JEA para conceder acesso limitado a um administrador de Hyper-V à sua VM, o que pode ser útil se a conectividade de rede com sua VM for perdida e for necessário que um administrador de datacenter corrija as configurações de rede.</span><span class="sxs-lookup"><span data-stu-id="c0999-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="c0999-147">Não é necessário nenhuma configuração adicional para usar o JEA com o PowerShell Direct, no entanto, o sistema operacional em execução na máquina virtual deve ser Windows 10 ou Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="c0999-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="c0999-148">O administrador do Hyper-V pode se conectar ao ponto de extremidade JEA usando os parâmetros `-VMName` ou `-VMId` em cmdlets PSRemoting:</span><span class="sxs-lookup"><span data-stu-id="c0999-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="c0999-149">É altamente recomendável que você crie um usuário local dedicado, sem outros direitos para gerenciar o sistema, para ser usado pelos administradores do Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="c0999-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="c0999-150">Lembre-se de que até mesmo um usuário sem privilégios pode fazer logon em um computador Windows por padrão e, inclusive, usar o PowerShell irrestrito.</span><span class="sxs-lookup"><span data-stu-id="c0999-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="c0999-151">Isso lhes permite navegar (em parte do) sistema de arquivos e saber mais sobre o ambiente do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="c0999-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="c0999-152">Para bloquear um administrador do Hyper-V para somente acessar uma VM usando o PowerShell Direct com JEA, você precisará negar direitos de logon local à conta JEA do administrador do Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="c0999-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>
