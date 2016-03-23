# As frequências de RefreshMode e ConfigurationMode não precisam ser múltiplos um do outro

Na versão anterior do DSC, o LCM trataria `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` como múltiplos um do outro, conforme explicado [aqui](http://blogs.msdn.com/b/powershell/archive/2013/12/09/understanding-meta-configuration-in-windows-powershell-desired-state-configuration.aspx) no blog. No WMF 5.0 RTM, essas propriedades são processadas de forma independente uma da outra. As tabelas abaixo ilustram esse comportamento:

Comportamento no modo **PULL**: 

|                                  |**Valor na metaconfiguração**|**Valor após aplicação da metaconfiguração**|**Frequência com que o pull ocorre (em minutos)**|**Frequência com que a configuração é aplicada (em minutos)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |                                    |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |40                                  |                                                |

Comportamento no modo **PUSH**:

|                                  |**Valor na metaconfiguração**|**Valor após aplicação da metaconfiguração**|**Frequência com que a configuração é aplicada (em minutos)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |                                                |
<!--HONumber=Mar16_HO2-->
