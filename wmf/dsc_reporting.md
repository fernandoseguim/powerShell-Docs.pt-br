# Relatar status de configuração para um local central

Informações detalhadas sobre o status da configuração DSC podem ser enviadas para um servidor com a execução do serviço DSC. As mesmas informações retornadas pelo cmdlet Get-DscConfigurationStatus são enviadas para o serviço DSC. Ao definir o servidor de relatório em uma metaconfiguração, esse status é enviado para o servidor quando ocorre um erro ou quando a configuração é concluída com êxito. Essas informações são enviadas quando um nó é configurado no modo pull ou push. Informações de status são armazenadas no banco de dados do serviço DSC.

## Metaconfiguração de exemplo para relatar o status
```PowerShell
[DscLocalConfigurationManager()]
Configuration ReportingClientMetaConfig
{
    Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PUSH"
            ConfigurationModeFrequencyMins = 15
            AllowModuleOverwrite = $true
        }

        ReportServerWeb ReportManager
        {
            ServerUrL = "http://localhost:8080/PSDSCPullServer/PSDSCPullserver.svc"
            AllowUnsecureConnection  = $true
        }           
}
```
Um novo ponto de extremidade OData é criado com o serviço DSC, que expõe essas informações de status. Ao passar uma ID de configuração ou de agente {$guid} para o ponto de extremidade, todos o status de um nó podem ser coletados e analisados.

## Solicitação da Web de exemplo para coletar o status de configuração 
```PowerShell
$statusReports = Invoke-WebRequest -Uri "[http://localhost:8080/PSDSCPullserver/PSDSCPullserver.svc/Node(ConfigurationId='$guid')/StatusReport](http://localhost:8080/PSDSCPullserver/psdscpullserver.svc/Node(ConfigurationId='$guid')/StatusReport)s" -UseBasicParsing -UseDefaultCredentials -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" -Headers @{Accept = "application/json"; ProtocolVersion = “1.1”}
```<!--HONumber=Mar16_HO2-->
