# Solucionando problemas de DSC

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Este tópico descreve métodos para fazer seus scripts de Configuração de Estado Desejado (DSC) serem executados sem erros. Usando logs de forma eficiente para rastrear erros e entender como reciclar o cache para ver os resultados imediatos das alterações de recurso, você poderá solucionar problemas de DSC com mais eficiência. Essas técnicas são discutidas em duas seções:

* Meu script não funciona: Usando logs de DSC para diagnosticar erros de script
* Meus recursos não são atualizados: Como redefinir o cache

## Meu script não funciona: Usando logs de DSC para diagnosticar erros de script

Como todos os softwares do Windows, a DSC registra erros e eventos em logs que podem ser exibidos no Visualizador de Eventos. Um exame desses logs pode ajudá-lo a entender por que uma determinada operação falhou e como evitar falhas no futuro. Escrever scripts de configuração pode ser complicado; portanto, para facilitar o rastreamento de erros durante a criação, use o recurso de Log de DSC para acompanhar o progresso da sua configuração no log de eventos Analítico de DSC.

## Onde estão os logs de eventos de DSC?

No Visualizador de Eventos, os eventos de DSC estão em: Applications and Services Logs/Microsoft/Windows/Desired State Configuration

O cmdlet do PowerShell correspondente, Get-WinEvent, também pode ser executado para exibir os logs de eventos:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

Como mostrado acima, o nome do log primário da DSC é Microsoft->Windows->DSC (outros nomes de logs no Windows não são mostrados aqui por uma questão de brevidade). O nome primário é anexado ao nome do canal para criar o nome completo do log. O mecanismo de DSC escreve principalmente em três tipos de logs: logs Operacional, Analítico e de Depuração. Como os logs analítico e de depuração permanecem desligados por padrão, devem ser habilitados no Visualizador de Eventos. Para fazer isso, abra o Visualizador de Eventos digitando Show-EventLog no Windows PowerShell; ou clique no botão Iniciar, clique em Painel de Controle, em Ferramentas Administrativas e, em seguida, clique em Visualizador de Eventos. No menu Exibir do Visualizador de Eventos, clique em Mostrar Logs Analíticos e de Depuração. O nome do log para o canal analítico é Microsoft-Windows-Dsc/Analytic; para o canal de depuração é Microsoft-Windows-Dsc/Debug. Também é possível usar o utilitário wevtutil para habilitar os logs, conforme mostrado no exemplo a seguir.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## O que os logs de DSC contêm?

Os logs de DSC são divididos nos três canais de log com base na importância da mensagem. O log operacional na DSC contém todas as mensagens de erro e pode ser usado para identificar um problema. O log analítico tem um maior volume de eventos e pode identificar onde ocorreram erros. Esse canal também contém mensagens detalhadas (se houver). O log de depuração contém logs que podem ajudá-lo a entender como os erros ocorreram. As mensagens de eventos de DSC são estruturadas de modo que cada mensagem de evento comece com uma ID de trabalho que represente uma operação de DSC com exclusividade. O exemplo a seguir tenta obter a mensagem do primeiro evento registrado no log de DSC operacional.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

Os eventos de DSC são registrados em uma estrutura específica que permite que o usuário agregue eventos por meio de um trabalho de DSC. A estrutura é a seguinte:

ID do Trabalho: <Guid>
**<Event Message>**

## Coletando eventos de uma operação única de DSC

Os logs de eventos de DSC contêm os eventos gerados por várias operações de DSC. No entanto, você geralmente estará interessado nos detalhes sobre apenas uma operação específica. Todos os logs de DSC podem ser agrupados pela propriedade de ID do trabalho, que é exclusiva para cada operação de DSC. A ID do trabalho é exibida como o primeiro valor da propriedade em todos os eventos de DSC. As etapas a seguir explicam como acumular todos os eventos em uma estrutura de matriz agrupada.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>
 
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true
 
<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>
 
Get-DscLocalConfigurationManager
 
<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>
 
$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)
 
 
<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}  
```

Aqui, a variável `$SeparateDscOperations` contém logs agrupados pelas IDs de trabalho. Cada elemento da matriz dessa variável representa um grupo de eventos registrados por uma operação de DSC diferente, permitindo o acesso a mais informações sobre os logs.

```
PS C:\> $SeparateDscOperations
 
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...       
```

Você pode extrair os dados na variável `$SeparateDscOperations` usando Where-Object. Seguem cinco cenários em que talvez você queira extrair dados para solucionar problemas de DSC:

### 1: Falhas em operações

Todos os eventos têm níveis de gravidade. Essas informações podem ser usadas para identificar os eventos de erro:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### 2: Detalhes das operações executadas na última meia hora

`TimeCreated`, uma propriedade de todos os eventos do Windows, indica o horário em que o evento foi criado. A comparação dessa propriedade com um objeto de data/hora específico pode ser usada para filtrar todos os eventos:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### 3: Mensagens da operação mais recente

A operação mais recente é armazenada no primeiro índice do grupo de matriz `$SeparateDscOperations`. Uma consulta às mensagens do grupo para o índice 0 gera todas as mensagens referentes à operação mais recente:

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Consistency check completed. 
```

### 4: Mensagens de erro registradas para falhas em operações recentes

`$SeparateDscOperations[0].Group` contém um conjunto de eventos para a operação mais recente. Execute o cmdlet `Where-Object` para filtrar os eventos com base em seu nome de exibição de nível. Os resultados são armazenados na variável `$myFailedEvent`, que ainda pode ser examinada para obter a mensagem de evento:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### 5: Todos os eventos gerados para uma ID de trabalho específica.

`$SeparateDscOperations` é uma matriz de grupos, sendo que cada um deles tem o nome como a ID exclusiva do trabalho. Ao executar o cmdlet `Where-Object`, você pode extrair esses grupos de eventos que têm uma ID de trabalho específica:

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC
 
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...  
```

## Usando xDscDiagnostics para analisar logs de DSC

xDscDiagnostics é um módulo do PowerShell que consiste em duas funções simples que podem ajudar a analisar falhas de DSC em seu computador: `Get-xDscOperation` e `Trace-xDscOperation`. Essas funções podem ajudá-lo a identificar todos os eventos locais de operações anteriores de DSC ou eventos de DSC em computadores remotos (com credenciais válidas). Aqui, o termo operação de DSC é usado para definir uma única execução de DSC desde o início até o fim. Por exemplo, `Test-DscConfiguration` seria uma operação de DSC separada. Da mesma forma, cada outro cmdlet na DSC (como `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) pode ser identificado como operações de DSC separadas. As duas funções são explicadas no módulo xDscDiagnostics do PowerShell (Kit de Recursos de DSC) e em mais detalhes abaixo. A ajuda está disponível executando `Get-Help <cmdlet name>`.

## Get-xDscOperation

Essa função permite que você localize os resultados das operações de DSC que são executadas em um ou vários computadores e gera um objeto que contém a coleção de eventos produzidos por cada operação de DSC. Por exemplo, na seguinte saída, três comandos foram executados. O primeiro deles passou e os outros dois falharam. Esses resultados estão resumidos na saída de `Get-xDscOperation`.

TODO: Substituir esta imagem que mostra a saída de Get-xDscOperation

### Parâmetros

* Newest: aceita um valor inteiro para indicar o número de operações que devem ser exibidas. Por padrão, gera as 10 operações mais recentes. Por exemplo,
  TODO: Mostrar Get-xDscOperation -Newest 5
* ComputerName: parâmetro que aceita uma matriz de cadeias de caracteres, cada uma contendo o nome de um computador do qual você deseja coletar dados de log de eventos de DSC. Por padrão, ele coleta dados do computador local. Para habilitar esse recurso, você deve executar o seguinte comando em computadores remotos, no modo elevado, para permitir a coleta de eventos
```powershell
  New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
* Credential: parâmetro que é do tipo PSCredential, que pode ajudar a acessar os computadores especificados no parâmetro ComputerName.

### Objeto gerado

O cmdlet gera uma matriz de objetos do tipo Microsoft.PowerShell.xDscDiagnostics.GroupedEvents. Cada objeto nessa matriz se refere a uma operação de DSC diferente. A exibição padrão para este objeto tem as seguintes propriedades
* SequenceID: especifica o número incremental atribuído à operação de DSC com base no tempo. Por exemplo, a última operação executada teria SequenceID como 1, a penúltima operação de DSC teria SequenceID de 2 e assim por diante. Esse número é outro identificador para cada objeto na matriz gerada.
* TimeCreated: um valor DateTime que indica quando a operação de DSC começou.
* ComputerName: o nome do computador em que os resultados estão agregados.
* Result: uma cadeia de caracteres com o valor Failure ou Success que indica se a operação de DSC sofreu um erro ou não, respectivamente.
* AllEvents: um objeto que representa uma coleção de eventos produzidos pela operação de DSC.

Por exemplo, a saída a seguir mostra os resultados da última operação de vários computadores:
  TODO: Substituir imagem para Get-xDscOperation para exibir logs do computador remoto

## Trace-xDscOperation

Esse cmdlet gera um objeto que contém uma coleção de eventos, os tipos de evento e a saída de mensagem gerada por meio de uma determinada operação de DSC. Normalmente, quando uma falha é encontrada em qualquer uma das operações usando `Get-xDscOperation`, você rastrearia a operação para descobrir quais dos eventos causaram uma falha.

### Parâmetros

* SequenceID: esse é o valor inteiro atribuído a qualquer operação, referente a um computador específico. Ao especificar uma ID de sequência de 4, por exemplo, o rastreamento para a operação de DSC que ficou em 4º lugar a partir do último será gerado

Trace-xDscOperation com ID de sequência especificada
* JobID: esse é o valor GUID atribuído pelo xDscOperation do LCM para identificar exclusivamente uma operação. Quando um JobID é especificado, o rastreamento da operação de DSC correspondente é a saída.
  TODO: Substituir a imagem para Trace-xDscOperation usando JobID como parâmetro
* ComputerName e Credential: esses parâmetros permitem que o rastreamento seja coletado de computadores remotos:
```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
  TODO: substituir a imagem para Trace-xDscOperation executado em um computador diferente

Observe que, como `Trace-xDscOperation` agrega eventos dos logs Operacional, Analítico e de Depuração, ele solicitará a habilitação desses logs, conforme descrito acima.

### Objeto gerado

O cmdlet gera uma matriz de objetos, cada um do tipo `Microsoft.PowerShell.xDscDiagnostics.TraceOutput`. Cada objeto nessa matriz contém os seguintes campos:
* ComputerName: o nome do computador do qual os logs estão sendo coletados.
* EventType: é um campo do tipo de enumerador que contém informações sobre o tipo de evento. Pode ser um dos seguintes:
  - Operational: o evento é do log operacional.
  - Analytic: do evento é do log analítico.
  - Debug: o evento é do log de depuração.
  - Verbose: saída de eventos como mensagens detalhadas durante a execução. As mensagens detalhadas facilitam a identificação da sequência de eventos que são publicados.
  - Error: eventos de erro. Ao procurar os eventos de erro, em geral é possível encontrar rapidamente o motivo da falha.
* TimeCreated: um valor DateTime que indica quando o evento foi registrado pela DSC.
* Message: a mensagem que foi registrada pela DSC nos logs de eventos.

A seguir estão campos nesse objeto que podem ser usados para obter mais informações sobre o evento, mas não são exibidos por padrão:

* JobID: a ID do trabalho (formato GUID) específica para essa operação de DSC.
* SequenceID: a SequenceID exclusiva para essa operação de DSC nesse computador.
* Event: o evento real registrado pela DSC, do tipo `System.Diagnostics.Eventing.Reader.EventLogRecord`. Também pode ser obtido por execução do cmdlet `Get-WinEvent`. Ele contém mais informações, como a tarefa, a eventID e o nível do evento.

Como alternativa, você pode reunir informações sobre os eventos salvando a saída de `Trace-xDscOperation` em uma variável. Pode-se usar o comando a seguir para exibir todos os eventos de uma determinada operação de DSC:

```powershell
(Trace-xDscOperation -SequenceID 3).Event
```

Isso exibirá os mesmos resultados que o cmdlet `Get-WinEvent`, como a saída abaixo:
  TODO: Qual saída?

Idealmente, em primeiro lugar, use `Get-xDscOperation` para listar as últimas execuções da configuração DSC nos seus computadores. Depois disso, você pode examinar qualquer operação única (usando sua SequenceID ou JobID) com `Trace-xDscOperation` para descobrir o que ela fazia em segundo plano.

## Meus recursos não são atualizados: como redefinir o cache

O mecanismo de DSC armazena em cache os recursos implementados como um módulo do PowerShell para fins de eficiência. No entanto, isso pode causar problemas quando você está criando um recurso e testando-o simultaneamente, porque DSC carregará a versão armazenada em cache até o processo ser reiniciado. A única maneira de fazer a DSC carregar a versão mais recente é eliminar explicitamente o processo que hospeda o mecanismo de DSC.

Da mesma forma, quando você executa `Start-DscConfiguration`, depois de adicionar e modificar um recurso personalizado, a modificação pode não ser executada a menos que, ou até que, o computador seja reinicializado. Isso ocorre porque a DSC é executada no Processo de Host do provedor WMI (WmiPrvSE) e, geralmente, há muitas instâncias do WmiPrvSE em execução ao mesmo tempo. Quando você reinicializa, o processo de host é reiniciado e o cache é limpo.

Para conseguir reciclar a configuração e limpar o cache sem reinicialização, você deve parar e reiniciar o processo de host. Isso pode ser feito por instância, ou seja, você identifica o processo, interrompe-o e reinicia-o. Ou pode usar `DebugMode`, conforme demonstrado abaixo, para recarregar o recurso de DSC do PowerShell.

Para identificar o processo que está hospedando o mecanismo de DSC e interrompê-lo por instância, é possível listar a ID do processo do WmiPrvSE que está hospedando o mecanismo de DSC. Em seguida, para atualizar o provedor, interrompa o processo WmiPrvSE usando os comandos abaixo; depois, execute Start-DscConfiguration novamente.

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers | 
Where-Object {$_.provider -like 'dsccore'} | 
Select-Object -ExpandProperty HostProcessIdentifier 

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## Usando o DebugMode

Você pode configurar o Gerenciador de Configurações Local (LCM) de DSC para usar `DebugMode` para sempre limpar o cache quando o processo de host for reiniciado. Quando definido como TRUE, faz com que o mecanismo sempre recarregue o recurso de DSC do PowerShell. Depois de escrever seu recurso, você pode defini-lo como FALSE e o mecanismo será revertido para o comportamento de armazenamento em cache dos módulos.

Segue uma demonstração para mostrar como `DebugMode` pode atualizar o cache automaticamente. Primeiro, vamos examinar a configuração padrão:

```
PS C:\> Get-DscLocalConfigurationManager
 
 
AllowModuleOverwrite           : False
CertificateID                  : 
ConfigurationID                : 
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     : 
DebugMode                      : False
DownloadManagerCustomData      : 
DownloadManagerName            : 
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :  
```

Pode-se ver que `DebugMode` foi definido como FALSE.

Para configurar a demonstração `DebugMode`, use o seguinte recurso do PowerShell:

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
} 
```

Agora, crie uma configuração usando o recurso acima chamado `TestProviderDebugMode`:

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

Você verá que o conteúdo do arquivo: “$env:SystemDrive\OutputFromTestProviderDebugMode.txt” é 1.

Agora, atualize o código do provedor usando o script a seguir:

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

Esse script gera um número aleatório e atualiza o código do provedor correspondentemente. Com `DebugMode` definido como false, o conteúdo do arquivo “$env:SystemDrive\OutputFromTestProviderDebugMode.txt” nunca é alterado.

Agora, defina `DebugMode` como TRUE no script de configuração:

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

Quando você executar novamente o script acima, verá que o conteúdo do arquivo é diferente em cada ocasião. (É possível executar `Get-DscConfiguration` para verificar). Abaixo está o resultado de duas execuções adicionais (os resultados podem ser diferentes quando você executar o script):

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
20                                      localhost                              
 
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
14                                      localhost
```

## Consulte Também

### Referência
* [Recurso Log de DSC](logResource.md)

### Conceitos
* [Criar recursos personalizados de configuração de estado desejado do Windows PowerShell](authoringResource.md)

### Outros recursos
* [Cmdlets de Configuração de Estado Desejado do Windows PowerShell](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)


<!--HONumber=Mar16_HO1-->


