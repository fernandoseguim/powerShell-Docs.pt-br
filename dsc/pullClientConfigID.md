# Configurando um cliente de pull usando uma ID de configuração

> Aplica-se a: Windows PowerShell 5.0

Cada nó de destino deve ser instruído a usar o modo de pull e receber a URL em que possa contatar o servidor de pull para obter as configurações. Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias. Para configurar o LCM, é criado um tipo especial de configuração, com diminuição da potência com o atributo **DSCLocalConfigurationManager**. Para obter mais informações sobre como configurar o LCM, consulte [Configuring the Local Configuration Manager](metaConfig.md) (Configurando o Gerenciador de Configurações Local).

> **Observação**: este tópico se aplica ao PowerShell 5.0. Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md).

O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "CONTOSO-PullSrv".

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }      
    }
}
PullClientConfigID
```

No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull. O **ServerURL**

Depois de ser executado, esse script cria uma nova pasta de saída denominada **PullClientConfigID** e coloca um arquivo MOF de metaconfiguração nela. Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.

Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração. Por exemplo: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## ID de configuração

O script define a propriedade **ConfigurationID** do LCM para um GUID criado anteriormente para essa finalidade (você pode criar um GUID usando o cmdlet **New-Guid**). O **ConfigurationID** é usado pelo LCM para localizar a configuração apropriada no servidor de pull. O arquivo MOF de configuração no servidor de pull deve ser nomeado como _ConfigurationID_.mof, em que _ConfigurationID_ é o valor da propriedade **ConfigurationID** do nó de destino do LCM.

## Servidor de pull de SMB

Para configurar um cliente para efetuar o pull de configurações de um servidor SMB, use um bloco **ConfigurationRepositoryShare**. Em um bloco **ConfigurationRepositoryShare**, especifique o caminho para o servidor definindo a propriedade **SourcePath**. A metaconfiguração a seguir configura o nó de destino para efetuar o pull de um servidor de pull de SMB chamado **SMBPullServer**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## Servidores de recurso e relatório

Se você especificar apenas um bloco **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** em sua configuração LCM (como no exemplo anterior), o cliente de pull efetuará o pull 
de recursos do servidor especificado, mas não enviará relatórios a ele. Você pode usar um único servidor pull para emissão de relatórios, recursos e configurações, mas você precisa criar um 
bloco **ReportRepositoryWeb** para configurar os relatórios. 

O exemplo a seguir mostra uma metaconfiguração tem que configura um cliente para efetuar pull de recursos e configurações, além de enviar dados de relatórios para um único
servidor de pull.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

Também é possível especificar servidores de pull diferentes para recursos e relatórios. Para especificar um servidor de recursos, utilize um bloco **ResourceRepositoryWeb** (para um servidor de pull da Web) ou um 
bloco **ResourceRepositoryShare** (para um servidor de pull SMB).
Para especificar um servidor de relatório, utilize um bloco **ReportRepositoryWeb**. Um servidor de relatório não pode ser um servidor de SMB.
A metaconfiguração a seguir configura um cliente de pull para obter suas configurações de **CONTOSO PullSrv** e seus recursos de **CONTOSO ResourceSrv**, bem como enviar relatórios de status para **CONTOSO ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## Consulte Também

* [Configurando um cliente de pull com nomes de configuração](pullClientConfigNames.md)


<!--HONumber=May16_HO2-->


