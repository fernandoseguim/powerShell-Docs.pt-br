# Usando um servidor de relatório de DSC

> Aplica-se a: Windows PowerShell 5.0

> **Observação:** o servidor de relatório descrito neste tópico não está disponível no PowerShell 4.0. Para relatórios no PowerShell 4.0, consulte Usando um servidor de conformidade de DSC.

O Gerenciador de Configurações Local (LCM) de um nó pode ser configurado para enviar relatórios sobre o status de configuração para um servidor de pull, que, por sua vez, pode ser consultado para recuperar dados. Cada vez que o nó verifica e aplica
uma configuração, envia um relatório para o servidor de relatório. Esses relatórios são armazenados em um banco de dados no servidor e podem ser recuperados chamando o serviço Web de relatórios. Cada relatório contém
informações como quais configurações foram aplicadas e se tiveram êxito, os recursos usados, os erros que foram lançados e os horários de início e término.

## Configurando um nó para enviar relatórios

Um nó é instruído a enviar relatórios para um servidor usando um bloco **ReportServerWeb** na configuração do LCM do nó (para obter informações sobre como configurar o LCM,
 consulte [Configurando o Gerenciador de Configurações Local](metaConfig.md)). O servidor ao qual o nó envia relatórios deve ser configurado como servidor de pull da Web (não é possível enviar relatórios
 para um compartilhamento SMB). Para obter informações sobre a configuração de um servidor de pull, consulte [Configurando um servidor de pull da Web de DSC](pullServer.md). O servidor de relatório pode ser o mesmo serviço do qual
 o nó efetua pull de configurações e obtém recursos ou pode ser um serviço diferente.
 
 No bloco **ReportServerWeb**, especifique a URL do serviço de pull
 e uma chave de registro que seja conhecida pelo servidor.
 
  A configuração a seguir define um nó para efetuar pull de configurações por meio de um serviço e enviar relatórios
 para um serviço em um servidor diferente. 
 
```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}
PullClientConfigID
```

## Obtendo dados de relatório

Relatórios enviados para o servidor de pull são inseridos em um banco de dados no servidor. Os relatórios estão disponíveis por meio de chamadas para o serviço Web. Para recuperar os relatórios de um nó específico, 
envie uma solicitação HTTP para o serviço Web no relatório a seguir:
`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentID = MyNodeAgentId)/Reports` 
em que `MyNodeAgentId` é a AgentId do nó para o qual você deseja obter relatórios. Pode-se obter a AgentID para um nó chamando [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
nesse nó.

Os relatórios são gerados como uma matriz de objetos JSON.

O script a seguir gera os relatórios para o nó no qual é executado:

```powershell
function GetReport
{
    param($AgentId = "$((glcm).AgentId)", $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCReportServer.svc")
    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```
    
## Exibindo dados de relatório

Se você definir uma variável como o resultado da função **GetReport**, poderá exibir os campos individuais em um elemento da matriz que é gerada:

```powershell
$reports = GetReport
$reports[1]

JobId                : 71515ae8-7294-40a3-8137-fc85bf4b678f
OperationType        : Consistency
RefreshMode          : 
Status               : 
ReportFormatVersion  : 1.0
ConfigurationVersion : 2.0.0
StartTime            : 02/08/2016 01:28:54
EndTime              : 02/08/2016 01:28:57
RebootRequested      : False
Errors               : {}
StatusData           : {{"NumberOfResources":"2","Locale":"en-US","ResourcesInDesiredState":[{"ResourceId":"[WindowsFeature]MyFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::4::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"},{"ResourceId":"[WindowsFeature]My2ndFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::8::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"}]}}
```

Observe que o campo **StatusData** é um objeto com três propriedades: **NumberOfResources**, **Locale** e **ResourcesInDesiredState**. A propriedade **ResourcesInDesiredState**
é uma matriz de objetos que têm um número de propriedades. O script a seguir usa um único relatório como parâmetro, itera por meio da sua matriz **ResourcesInDesiredState**
e escreve no console:
 
```powershell
function GetStatusData
{
    param ($Report)
    $statusData = $Report.StatusData | ConvertFrom-Json

    $Resources = $statusData.ResourcesInDesiredState

    Foreach ($Resource in $Resources)
    {
        Write-Host 'ResourceId: ' $Resource.ResourceId
        Write-Host 'SourceInfo: ' $Resource.SourceInfo
        Write-Host 'ModuleName: ' $Resource.ModuleName
        Write-Host 'ModuleVersion: ' $Resource.ModuleVersion
        Write-Host 'ConfigurationName: ' $Resource.ConfigurationName
        Write-Host 'ResourceName: ' $Resource.ResourceName
        Write-Host
    }
}
```

Este é um exemplo de saída depois de chamar a função **GetStatusData**:

```powershell
GetStatusData -Report $report[1]

ResourceId:  [WindowsFeature]MyFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::4::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature

ResourceId:  [WindowsFeature]My2ndFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::8::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature
```

Observe que esses exemplos destinam-se a dar uma ideia do que você pode fazer com os dados de relatório. Para obter uma introdução sobre como trabalhar com JSON no PowerShell, consulte
[Brincando com JSON e PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).

## Consulte Também
>[Configurando o Gerenciador de Configurações Local](metaConfig.md)
>[Configurando um servidor de pull da Web de DSC](pullServer.md)
>[Configurando um cliente de pull usando nomes de configuração](pullClientConfigNames.md)
<!--HONumber=Feb16_HO4-->
