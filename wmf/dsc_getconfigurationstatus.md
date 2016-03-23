# Detalhes sobre o status de configuração

O cmdlet `Get-DscConfigurationStatus` obtém informações sobre o status de configuração desde um nó de destino. Será retornado um objeto avançado, que inclui informações de alto nível sobre se a execução da configuração foi bem-sucedida ou não. É possível examinar o objeto para descobrir detalhes sobre a execução da configuração como:

* Todos os recursos que falharam
* Qualquer recurso que solicitou uma reinicialização
* Definições de metaconfiguração em tempo de execução da configuração
* Etc.

O seguinte conjunto de parâmetros retorna as informações de status para a última execução de configuração:

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```
O seguinte conjunto de parâmetros retorna as informações de status para todas as execuções de configuração anteriores:

```powershell
Get-DscConfigurationStatus  -All 
                            [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```

## Exemplo

```powershell
PS C:\> $Status = Get-DscConfigurationStatus 

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :   
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :   
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :   
InDesiredState          :   False
InitialState            :   
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```<!--HONumber=Mar16_HO2-->
