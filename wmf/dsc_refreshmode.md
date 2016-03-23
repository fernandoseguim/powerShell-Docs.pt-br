# Valor adicional para a propriedade de RefreshMode

Esta versão apresenta um novo valor `RefreshMode`, **Disabled**. Quando esse modo é definido, o LCM não faz o gerenciamento de documentos. Esse modo pode ser usado quando uma ferramenta de gerenciamento de configuração de terceiros é usada em vez do DSC, ao mesmo tempo que ainda usa os recursos DSC com o cmdlet `Invoke-DscResource`, ou caso precise apenas interromper o processamento do DSC por qualquer motivo.

```powershell
Configuration LCMSettings
{
    Node localhost
    {
        LocalConfigurationManager
        {
           RefreshMode = 'Disabled'
        }
    }
}

LCMSettings -OutputPath .\LCMSettings
Set-DscLocalConfigurationManager -Path .\LCMSettings -Verbose -ComputerName localhost
```
<!--HONumber=Mar16_HO2-->
