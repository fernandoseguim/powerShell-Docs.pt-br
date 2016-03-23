# Configurar o LCM do DSC com o novo atributo de metaconfiguração

O atributo `DscLocalConfigurationManager` designa um bloco de configuração como uma metaconfiguração, que é usada para configurar o Gerenciador de Configurações Local do DSC. Esse atributo restringe uma configuração para que ela contenha somente os itens que configuram o Gerenciador de Configurações Local do DSC. Durante o processamento, essa configuração gera um arquivo `*.meta.mof` que é enviado para os nós de destino apropriados usando o cmdlet `Set-DscLocalConfigurationManager`.

```powershell
[DscLocalConfigurationManager()]
configuration meta
{
    Node localhost
    {
        Settings
        {
            ConfigurationMode = "ApplyAndAutocorrect"
            ConfigurationID = "5603f952-d6c6-4971-88c4-948636bf5c3f"
            RefreshMode = "Pull"
        }
        ConfigurationRepositoryWeb PullServer
        {
            ServerURL = "https://corp.contoso.com/PSDSCPullServer/PSDSCPullServer.svc"
        }
    }
}
```

O exemplo acima configura o modo de atualização para que o LCM use o modo pull, altera o modo de configuração para ApplyAndAutocorrect e define o tipo e o local do servidor de recepção.

Esse novo atributo de configuração substitui e estende a funcionalidade do recurso LocalConfigurationManager do PowerShell 4.0. Ainda há suporte para o LocalConfigurationManager em configurações sem esse atributo para compatibilidade com versões anteriores.

Metarrecursos:

| **Nome do Recurso**            | **Descrição**                                |
|------------------------------|------------------------------------------------|
| LocalConfigurationManager    | Várias configurações para a execução do mecanismo DSC      |
| PartialConfiguration         | Definições de configuração parcial                 |
| ConfigurationRepositoryWeb   | Repositório de configuração baseado na Web             |
| ConfigurationRepositoryShare | Repositório de configuração baseado em compartilhamento de arquivos      |
| ResourceRepositoryWeb        | Repositório de recursos baseado na Web                  |
| ResourceRepositoryShare      | Repositório de recursos baseado em arquivo                 |
| ReportServerWeb              | Ponto de extremidade de relatório baseado na Web para o cenário de pull |
<!--HONumber=Mar16_HO2-->
