# Configurando um cliente de pull usando nomes de configuração

> Aplica-se a: Windows PowerShell 5.0

Cada nó de destino deve ser instruído a usar o modo de pull e receber a URL em que possa contatar o servidor de pull para obter as configurações. Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias. Para configurar o LCM, crie um tipo especial de configuração, decorada com o atributo **DSCLocalConfigurationManager**. Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local](metaConfig.md).

> **Observação**: este tópico se aplica ao PowerShell 5.0. Para obter informações sobre como configurar um cliente de pull no PowerShell 4.0, consulte [Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0](pullClientConfigID4.md).

O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "CONTOSO-PullSrv":

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
            
        }      
    }
}
PullClientConfigID
```

No script, o bloco **ConfigurationRepositoryWeb** define o servidor de pull. A propriedade **ServerURL** especifica o ponto de extremidade para o servidor de pull.

A propriedade **RegistrationKey** é uma chave compartilhada entre todos os nós de cliente para um servidor de pull e esse servidor de pull. O mesmo valor é armazenado em um arquivo no servidor de pull. A propriedade **ConfigurationNames** especifica o nome da configuração destinada ao nó do cliente. No servidor de pull, o arquivo MOF de configuração para esse nó do cliente deve ser nomeado *ConfigurationNames*.mof, em que *ConfigurationNames* corresponde ao valor da propriedade **ConfigurationNames** definida nessa metaconfiguração.

Depois de ser executado, esse script cria uma nova pasta de saída denominada **PullClientConfigID** e coloca um arquivo MOF de metaconfiguração nela. Nesse caso, o arquivo MOF de metaconfiguração será nomeado `localhost.meta.mof`.

Para aplicar a configuração, chame o cmdlet **Set-DscLocalConfigurationManager**, com **Path** definido como a localização do arquivo MOF de metaconfiguração. Por exemplo: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

> **Observação**: as chaves de registro funcionam apenas com servidores de pull da Web. Você ainda deve usar **ConfigurationID** com um servidor de pull de SMB. Para obter informações sobre como configurar um servidor de pull usando **ConfigurationID**, consulte [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigID.md)

## Servidores de recurso e relatório

Por padrão, o nó do cliente obtém os recursos necessários do servidor de pull de configuração e informa o status para ele. No entanto, é possível especificar servidores de pull diferentes para recursos e relatórios.
Para especificar um servidor de recurso, utilize um bloco **ResourceRepositoryWeb** (para um servidor de pull da Web) ou um bloco **ResourceRepositoryShare** (para um servidor de pull de SMB).
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
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
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

* [Configurando um cliente de pull com uma ID de configuração](pullClientConfigID.md)
* [Configurando um servidor de pull da Web de DSC](pullServer.md)
<!--HONumber=Feb16_HO4-->
