# Depurando os recursos de DSC

> Aplica-se a: Windows PowerShell 5.0

No PowerShell 5.0, foi introduzido um novo recurso na Configuração de Estado Desejado (DSC) que permite depurar um recurso de DSC como uma configuração que está sendo aplicada.

## Habilitando a depuração de DSC
Para poder depurar um recurso, é preciso habilitar a depuração chamando o cmdlet [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx). Esse cmdlet usa um parâmetro obrigatório, o **BreakAll**. É possível verificar se a depuração foi habilitada analisando o resultado de uma chamada para o [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx). A seguinte saída do PowerShell mostra o resultado de habilitar a depuração:


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## Iniciando uma configuração com a depuração habilitada
Para depurar um recurso de DSC, inicie uma configuração que chame esse recurso. Para este exemplo, analisaremos uma configuração simples que chame o recurso [WindowsFeature](windowsfeatureResource.md) a fim de garantir que o recurso "WindowsPowerShellWebAccess" seja instalado:

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
Depois de compilar a configuração, inicie chamando [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). A configuração parará quando o
Gerenciador de Configurações Local (LCM) chamar o primeiro recurso na configuração. Se você usar os parâmetros `-Verbose` e `-Wait`, a saída exibirá as linhas que você precisa inserir
para iniciar a depuração.

```powershell
PS C:\DebugTest> Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will 
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.  Use the follow
ing commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
Nesse ponto, o LCM chama o recurso e vai até o primeiro ponto de interrupção. As três últimas linhas na saída mostram como anexar ao processo e iniciar a depuração do script do recurso.

## Depurando o script de recurso

Inicie uma nova instância do ISE do PowerShell. No painel do console, digite as três últimas linhas de saída da saída `Start-DscConifiguration` como comandos, substituindo `<credentials>` por
credenciais de usuário válidas. Esta é a saída resultante.



<!--HONumber=Feb16_HO4-->
