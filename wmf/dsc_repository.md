# Separação de repositórios de configurações, recursos e relatórios

Nesta versão, permitimos que você tenha toda a flexibilidade necessária para efetuar pull e relatar para um ou mais servidores de recepção do DSC. Cada ponto de extremidade pode ser definido separadamente para que você possa efetuar pull das configurações de um local, dos recursos de outro e relatar ainda para outro local. A seguinte metaconfiguração faz exatamente isso.

```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
    }

    ConfigurationRepositoryWeb Configurations
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```

Além disso, é possível usar qualquer combinação desses elementos. A metaconfiguração a seguir define um nó de destino no modo push, porém, o nó efetuará pull de recursos que ele não tiver instalado por meio de um “servidor de recepção do DSC” e relatará seu status para outro “servidor de recepção do DSC”.


```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "Push";
        RebootNodeIfNeeded = $true;
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```<!--HONumber=Mar16_HO2-->
