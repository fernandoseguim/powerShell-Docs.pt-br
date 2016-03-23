# Configurar o nó com vários fragmentos de configuração (configurações parciais)

O WMF 5.0 ajuda a entregar documentos de configuração para um nó em fragmentos. Para que um nó receba vários fragmentos de um documento de configuração, o LCM (Gerenciador de Configurações Local) deve ser definido para especificar os fragmentos esperados, conforme mostrado neste exemplo.

```powershell
[DSCLocalConfigurationManager()]
configuration SQLServerDSCSettings
{
    Node localhost
    {
        Settings
        {
            ConfigurationModeFrequencyMins = 30
        }

        ConfigurationRepositoryWeb OSConfigServer
        {
            ServerURL = "https://corp.contoso.com/OSConfigServer/PSDSCPullServer.svc"
        }

        ConfigurationRepositoryWeb SQLConfigServer
        {
            ServerURL = "https://corp.contoso.com/SQLConfigServer/PSDSCPullServer.svc"
        }

        PartialConfiguration OSConfig
        {
            Description = 'Configuration for the Base OS'
            ExclusiveResources = 'PSDesiredStateConfiguration\*'
            ConfigurationSource = '[ConfigurationRepositoryWeb]OSConfigServer'
        }

        PartialConfiguration SQLConfig
        {
            Description = 'Configuration for the SQL Server'
            ConfigurationSource = '[ConfigurationRepositoryWeb]SQLConfigServer'
            DependsOn = '[PartialConfiguration]OSConfig'
        }
    }
}
```

Em uma configuração parcial, o nome da configuração deve corresponder ao que é definido no LCM. No exemplo acima, as configurações devem ser nomeadas `OSConfig` e `SQLConfig`.

Definir o LCM para configurações parciais permite a coordenação de configurações, mas NÃO fornece a funcionalidade de segurança.<!--HONumber=Mar16_HO2-->
