# <a name="detailed-information-about-lcm-state"></a>Informações detalhadas sobre o estado do LCM

Fizemos melhorias na exposição de detalhes sobre o estado do LCM. O LCMState retornado por Get-DscLocalConfigurationManager agora pode conter os seguintes valores:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Também adicionamos uma propriedade de LCMStateDetail que contém mais informações sobre o estado.
