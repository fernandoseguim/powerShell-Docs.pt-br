# As frequências de RefreshMode e ConfigurationMode não precisam ser múltiplos um do outro

Na versão anterior do DSC, o LCM trataria `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` como múltiplos um do outro. No WMF 5.0 RTM, essas propriedades são processadas de forma independente uma da outra. 

Para obter mais informações, veja [Configurando o Gerenciador de Configurações Local](../dsc/metaConfig.md).

<!--HONumber=Jun16_HO4-->


