---
manager: carmonm
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: Usando JEA
ms.technology: powershell
ms.openlocfilehash: 62e5f74d60b2fd09e302ecc12996f97e90b73f2f
ms.sourcegitcommit: 6057e6d22ef8a2095af610e0d681e751366a9773
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2017
---
# <a name="using-jea"></a>Usando JEA

> Aplica-se a: Windows PowerShell 5.0

Este tópico descreve as várias maneiras pelas quais você pode se conectar e usar um ponto de extremidade JEA.

## <a name="using-jea-interactively"></a>Usando o JEA interativamente

Se você estiver testando sua configuração JEA ou tiver tarefas simples para os usuários executarem, você poderá usar o JEA da mesma forma que faria com uma sessão de comunicação remota regular do PowerShell.
Para tarefas de comunicação remota complexas, é recomendável usar a [comunicação remota implícita](#using-jea-with-implicit-remoting) em vez disso, para facilitar para os usuários, permitindo que eles operem com os objetos de dados localmente.

Para usar o JEA interativamente, você precisará:
- Do nome do computador ao qual está se conectando (pode ser o computador local)
- Do nome do ponto de extremidade JEA registrado nesse computador
- Das credenciais para o computador que tem acesso ao ponto de extremidade JEA

Com essas informações em mãos, você pode iniciar uma sessão JEA usando [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Se a conta na qual está conectado no momento tem acesso ao ponto de extremidade JEA, você poderá omitir o parâmetro `-Credential`.

Quando o prompt do PowerShell mudar para `[localhost]: PS>` você saberá que está interagindo com a sessão remota do JEA.
Você pode executar o `Get-Command` para verificar quais comandos estão disponíveis.
Você precisará consultar o administrador para saber se há alguma restrição nos parâmetros disponíveis ou nos valores de parâmetro permitidos.

Como lembrete, as sessões JEA operam no modo NoLanguage, portanto, algumas das maneiras que você normalmente usa o PowerShell podem não estar disponíveis.
Por exemplo, você não pode usar variáveis para armazenar dados ou inspecionar as propriedades em objetos retornados de cmdlets.
Abaixo há um exemplo que mostra como você usa PowerShell atualmente e duas abordagens para obter o mesmo funcionamento de comando no modo NoLanguage.

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

Para invocações de comando mais complexas que tornam essa abordagem difícil, considere o uso de [comunicação remota implícita](#using-jea-with-implicit-remoting) ou da [criação de funções personalizadas](role-capabilities.md#creating-custom-functions) que encapsulam a funcionalidade desejada.

## <a name="using-jea-with-implicit-remoting"></a>Usando o JEA com comunicação remota implícita

O PowerShell oferece suporte a um modelo de comunicação remota alternativo no qual é possível importar cmdlets do proxy de um computador remoto para o computador local e interagir com eles como se fossem comandos locais.
Esse modelo é chamado de comunicação remota implícita e é bem explicado [nessa postagem de blog *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
A comunicação remota implícita é particularmente útil ao trabalhar com o JEA porque permite que você trabalhe com os cmdlets do JEA em um modo de linguagem completa.
Isso significa que é possível usar a conclusão de guia, variáveis, manipular objetos e até mesmo usar scripts locais para automatizar mais facilmente em um ponto de extremidade JEA.
Sempre que você invocar um comando de proxy, os dados serão enviados ao ponto de extremidade JEA no computador remoto e executados lá.

A comunicação remota implícita funciona ao importar cmdlets de uma sessão existente do PowerShell.
Opcionalmente, é possível colocar prefixos nos substantivos de cada cmdlet de proxy, com uma cadeia de caracteres à sua escolha, para distinguir quais comandos são do sistema remoto.
Um módulo de script temporário contendo todos os comandos de proxy será criado e poderá ser usado enquanto durar a sessão local do PowerShell.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Alguns sistemas poderão não ser capazes de importar uma sessão inteira do JEA devido a restrições em cmdlets padrão do JEA.
> Para contornar isso, importe apenas os comandos necessários da sessão JEA fornecendo explicitamente os nomes deles para o parâmetro `-CommandName`.
> Uma atualização futura solucionará o problema com a importação de sessões inteiras do JEA nos sistemas afetados.

Se não for possível importar uma sessão JEA devido a restrições nos parâmetros padrão do JEA, você poderá seguir as etapas abaixo para filtrar os comandos padrão do conjunto importado.
Ainda será possível usar comandos como o `Select-Object` – você usará a versão local instalada no computador em vez da versão remota, na sessão JEA.

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

Também é possível manter os cmdlets do proxy da comunicação remota implícita, usando o [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Para obter mais informações sobre a comunicação remota implícita, consulte a documentação de ajuda para [Import-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) e [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Usando o JEA de forma programática

O JEA também pode ser usado em sistemas de automação e em aplicativos de usuário, como aplicativos de assistência técnica interna e sites da Web.
A abordagem é a mesma que a da criação de aplicativos que se comunicam com pontos de extremidade irrestritos do PowerShell, com a ressalva de que o programa deve estar ciente de que o JEA está limitando os comandos que podem ser executados na sessão remota.

Para tarefas simples e únicas, você pode usar [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) para executar um conjunto de comandos usando o JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Para verificar quais comandos estão disponíveis para uso quando você se conectar a uma sessão JEA, execute o `Get-Command` e percorra os resultados para verificar os parâmetros permitidos.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Se estiver compilando um aplicativo C#, você pode criar um runspace do PowerShell que se conecta a uma sessão JEA, especificando o nome da configuração em um objeto [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx).

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

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

## <a name="using-jea-with-powershell-direct"></a>Usando o JEA com o PowerShell Direct

O Hyper-V no Windows 10 e o Windows Server 2016 oferecem o [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), um recurso que permite aos administradores do Hyper-V gerenciar máquinas virtuais com o PowerShell, independentemente da configuração da rede ou das configurações de gerenciamento remoto na máquina virtual.

É possível usar o PowerShell Direct com o JEA para conceder acesso limitado a um administrador de Hyper-V à sua VM, o que pode ser útil se a conectividade de rede com sua VM for perdida e for necessário que um administrador de datacenter corrija as configurações de rede.

Não é necessário nenhuma configuração adicional para usar o JEA com o PowerShell Direct, no entanto, o sistema operacional em execução na máquina virtual deve ser Windows 10 ou Windows Server 2016.
O administrador do Hyper-V pode se conectar ao ponto de extremidade JEA usando os parâmetros `-VMName` ou `-VMId` em cmdlets PSRemoting:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

É altamente recomendável que você crie um usuário local dedicado, sem outros direitos para gerenciar o sistema, para ser usado pelos administradores do Hyper-V.
Lembre-se de que até mesmo um usuário sem privilégios pode fazer logon em um computador Windows por padrão e, inclusive, usar o PowerShell irrestrito.
Isso lhes permite navegar (em parte do) sistema de arquivos e saber mais sobre o ambiente do sistema operacional.
Para bloquear um administrador do Hyper-V para somente acessar uma VM usando o PowerShell Direct com JEA, você precisará negar direitos de logon local à conta JEA do administrador do Hyper-V.
