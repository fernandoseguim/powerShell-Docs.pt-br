---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Get-Test-Set
ms.openlocfilehash: 6d059518a49926bc5fb56e37e7d3d4d2c66bddec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676331"
---
# <a name="get-test-set"></a>Get-Test-Set

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

![Obter, testar e definir](/media/get-test-set.png)

PowerShell Desired State Configuration é construído ao redor de um **Obtenha**, **teste**, e **definir** processo. DSC [recursos](resources.md) cada contém métodos para concluir cada uma dessas operações. Em um [Configuration](../configurations/configurations.md), você define blocos de recursos para preencher as chaves que se tornam parâmetros para um recurso **obter**, **teste**, e **definido** métodos.

Esta é a sintaxe para uma **serviço** bloco de recurso. O **serviço** recursos configura os serviços do Windows.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

O **Obtenha**, **teste**, e **definir** métodos do **serviço** recurso terá blocos de parâmetro que aceitam esses valores.

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> Determina o idioma e o método usado para definir o recurso como o **Obtenha**, **teste**, e **definir** métodos serão definidos.

Porque o **Service** recurso só tem uma chave necessária (`Name`), uma **serviço** recurso de bloco pode ser tão simple como este:

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

Quando você compila a configuração acima, os valores especificados para uma chave são armazenados no arquivo ". MOF" que é gerado. Para obter mais informações, consulte [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

Quando aplicada, o [Gerenciador de configurações Local](../managing-nodes/metaConfig.md) lerá o valor "Spooler" do arquivo ". MOF" e passá-lo para o `-Name` parâmetro do **obter**, **teste**, e **definir** métodos para a instância de "MyService" das **Service** recursos.

## <a name="get"></a>Get

O **obter** método de um recurso, recupera o estado do recurso como está configurado no nó de destino. Esse estado é retornado como um [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables). As chaves do **hashtable** será configuráveis valores ou parâmetros, o recurso aceita.

O **Obtenha** método mapeia diretamente para o [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet. Quando você chama `Get-DSCConfiguration`, o LCM executa o **obter** método de cada recurso na configuração aplicada no momento. O LCM usa os valores de chave armazenados no arquivo ". MOF" como parâmetros para cada instância do recurso correspondente.

Isso é o exemplo de saída de um **serviço** recursos que configura o serviço "Spooler".

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

A saída mostra as propriedades atuais do valor configurável pela **serviço** recursos.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a>Teste

O **teste** método de um recurso determina se o nó de destino é atualmente compatível com o recurso *estado desejado*. O **teste** método retorna `$True` ou `$False` apenas para indicar se o nó está em conformidade.
Quando você chama [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), o LCM chama o **teste** método de cada recurso na configuração aplicada no momento. O LCM usa os valores de chave armazenados no arquivo ". MOF" como parâmetros para cada instância do recurso correspondente.

Se o resultado de qualquer recurso individual **teste** é `$False`, `Test-DSCConfiguration` retorna `$False` indicando que o nó não está em conformidade. Se todos os recursos **teste** métodos retornam `$True`, `Test-DSCConfiguration` retorna `$True` para indicar que o nó está em conformidade.

```powershell
Test-DSCConfiguration
```

```output
True
```

A partir do PowerShell 5.0, o `-Detailed` parâmetro foi adicionado. Especificando `-Detailed` faz com que `Test-DSCConfiguration` para retornar um objeto que contém conjuntos de resultados para os recursos compatíveis e incompatíveis.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Para obter mais informações, consulte [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Set

O **definir** método de um recurso tenta forçar o nó para ficarem em conformidade com o recurso *estado desejado*. O **definir** método deve ser **idempotente**, o que significa que **definir** poderia ser executado várias vezes e sempre obterá o mesmo resultado sem erros.  Quando você executa [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), os ciclos de LCM por meio de cada recurso na configuração aplicada no momento. O LCM recupera valores de chave para a instância atual do recurso do arquivo ". MOF" e usa-los como parâmetros para o **teste** método. Se o **teste** método retorna `$True`, o nó está em conformidade com o recurso atual e o **definir** método será ignorado. Se o **teste** retorna `$False`, o nó não está em conformidade.  O LCM passa o recurso de valores de chave da instância como parâmetros para o recurso **definir** método, restaurar o nó com a conformidade.

Especificando o `-Verbose` e `-Wait` parâmetros, você pode observar o progresso do `Start-DSCConfiguration` cmdlet. Neste exemplo, o nó já está em conformidade. O `Verbose` saída indica que o **definir** método foi ignorado.

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a>Consulte também

- [Visão geral do DSC de Automação do Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Configurando um servidor de pull da Web e SMB](../pull-server/pullServerSMB.md)
- [Configurando um cliente de pull](../pull-server/pullClientConfigID.md)
