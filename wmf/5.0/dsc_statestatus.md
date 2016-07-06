# Representação de estado e status consistente e unificada

Uma série de melhorias foram feitas nessa versão em relação ao estado do LCM e ao status do DSC internos das automações. Entre elas estão representações de estado e status consistentes e unificadas, propriedade datetime gerenciável de objetos de status retornados pelo cmdlet Get-DscConfigurationStatus e melhoria na propriedade de detalhes do estado do LCM retornada pelo cmdlet Get-DscLocalConfigurationManager.

A representação do estado do LCM e do status de operação do DSC foi revisitada e unificada de acordo com as seguintes regras:
1.  O recurso NotProcessed não afeta o estado do LCM e o status do DSC.
2.  O LCM interrompe o processamento de mais recursos quando encontra um recurso que solicita a reinicialização.
3.  Um recurso que solicita a reinicialização não fica no estado desejado até que realmente ocorra uma reinicialização.
4.  Depois de encontrar um recurso que falha, o LCM mantém o processamento de mais recursos desde que eles não sejam dependentes da primeira falha.
5.  O status geral retornado pelo cmdlet Get-DscConfigurationStatus é o superconjunto de todos os status de recursos.
6.  O estado de PendingReboot é um superconjunto do estado de PendingConfiguration.

A tabela abaixo ilustra as propriedades relacionadas a estado e status resultantes em alguns cenários típicos.

| **Cenário**                    | **LCMState\***       | **Status** | **Reinicialização solicitada**  | **ResourcesInDesiredState**  | **ResourcesNotInDesiredState** |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S**^**                          | Idle                 | Sucesso    | $false        | S                            | $null                          |
| F**^**                          | PendingConfiguration | Falha    | $false        | $null                        | F                              |
| S,F                             | PendingConfiguration | Falha    | $false        | S                            | F                              |
| F,S                             | PendingConfiguration | Falha    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Falha    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Falha    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Sucesso    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | Falha    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Sucesso    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Sucesso    | $true         | $null                        | r                              |

^
S<sub>i</sub>: uma série de recursos que são aplicadas com êxito F<sub>i</sub>: uma série de recursos que não são aplicados com êxito r: um recurso que exige reinicialização
\*

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## Melhorias no cmdlet Get-DscConfigurationStatus

Foram feitas algumas melhorias ao cmdlet Get-DscConfigurationStatus nesta versão. Anteriormente, a propriedade StartDate de objetos retornados pelo cmdlet era do tipo String. Agora, ela é do tipo Datetime, o que permite uma seleção e filtragem complexas, facilitando-as com base nas propriedades intrínsecas de um objeto Datetime.
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

Veja a seguir um exemplo que retorna todos os registros de operação do DSC ocorridos no mesmo dia da semana que hoje.
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Registros de operações que não fazem alterações à configuração do nó (ou seja, operações somente leitura) são eliminados. Portanto, as operações Test-DscConfiguration e Get-DscConfiguration são não mais adulteradas em objetos retornados pelo cmdlet Get-DscConfigurationStatus.
Registros da operação de definição de metaconfiguração são adicionados ao retorno pelo cmdlet Get-DscConfigurationStatus.

Apresentamos a seguir um exemplo de resultado retornado pelo cmdlet Get-DscConfigurationStatus –All.
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## Melhoria no cmdlet Get-DscLocalConfigurationManager
Um novo campo de LCMStateDetail é adicionado ao objeto retornado pelo cmdlet Get-DscLocalConfigurationManager. Este campo é populado quando LCMState é “Ocupado”. Ele pode ser recuperado pelo seguinte cmdlet:
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Veja a seguir um exemplo de saída de um monitoramento contínuo em uma configuração que exige duas reinicializações em um nó remoto.
```powershell
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```


<!--HONumber=Jun16_HO4-->


