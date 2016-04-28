# Configurando um cliente de pull usando uma ID de configuração no PowerShell 4.0

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Cada nó de destino deve ser instruído a usar o modo de pull e receber a URL em que possa contatar o servidor de pull para obter as configurações. Para fazer isso, você precisa configurar o Gerenciador de Configurações Local (LCM) com as informações necessárias. Para configurar o LCM, é criado um tipo especial de configuração conhecido como "metaconfiguração". Para obter mais informações sobre como configurar o LCM, consulte [Gerenciador de Configurações Local de Configuração de Estado Desejado do Windows PowerShell 4.0](metaConfig4.md)

O script a seguir configura o LCM para efetuar o pull de configurações de um servidor chamado "PullServer":

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 15;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

No script, **DownloadManagerCustomData** passa a URL do servidor de pull e (para esse exemplo) autoriza uma conexão não segura. 

Depois de ser executado, esse script cria uma nova pasta de saída denominada **SimpleMetaConfigurationForPull** e coloca um arquivo MOF de metaconfiguração nela.

Para aplicar a configuração, use **Set-DscLocalConfigurationManager** com parâmetros para **ComputerName** (use "localhost") e **Path** (o caminho até o local do arquivo localhost.meta.mof do nó de destino). Por exemplo: 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## ID de configuração
O script define a propriedade **ConfigurationID** do LCM para um GUID criado anteriormente para essa finalidade (você pode criar um GUID usando o cmdlet **New-Guid**). O **ConfigurationID** é usado pelo LCM para localizar a configuração apropriada no servidor de pull. O arquivo MOF de configuração no servidor de pull deve ser nomeado como `ConfigurationID.mof`, em que *ConfigurationID* é o valor da propriedade **ConfigurationID** do nó de destino do LCM.

## Efetuando pull de um servidor de SMB

Se o servidor de pull é configurado como um compartilhamento de arquivos SMB em vez de como um serviço Web, especifique o **DscFileDownloadManager** em vez de **WebDownLoadManager**.
O **DscFileDownloadManager** usa uma propriedade **SourcePath** em vez de **ServerUrl**. O script a seguir configura o LCM para efetuar o pull de configurações de um compartilhamento de SMB chamado
"SmbDscShare" em um servidor chamado "CONTOSO-SERVER":

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 15;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

## Consulte Também

- [Configurando um servidor de pull da Web de DSC](pullServer.md)
- [Configurando um servidor de pull de SMB para DSC](pullServerSMB.md)

<!--HONumber=Mar16_HO2-->


