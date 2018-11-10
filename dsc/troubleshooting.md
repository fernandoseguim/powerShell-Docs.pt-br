---
ms.date: 10/30/2018
keywords: DSC,powershell,configuração,instalação
title: Solucionando problemas de DSC
ms.openlocfilehash: 04fb1e9016c508d0e514b51b3cfd6e6f6d5c4974
ms.sourcegitcommit: 9cabc119f4d59598e12d4a36238a311349082ff0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410007"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="ab3ff-103">Solucionando problemas de DSC</span><span class="sxs-lookup"><span data-stu-id="ab3ff-103">Troubleshooting DSC</span></span>

<span data-ttu-id="ab3ff-104">_Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="ab3ff-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="ab3ff-105">Este tópico descreve maneiras de solucionar o DSC quando surgem problemas.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="ab3ff-106">Dependência do WinRM</span><span class="sxs-lookup"><span data-stu-id="ab3ff-106">WinRM Dependency</span></span>

<span data-ttu-id="ab3ff-107">O DSC (Configuração de Estado Desejado) do Windows PowerShell depende do WinRM.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="ab3ff-108">O WinRM não é habilitado por padrão no Windows Server 2008 R2 nem no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="ab3ff-109">Execute `Set-WSManQuickConfig`, em uma sessão de privilégios elevados do Windows PowerShell, para habilitar o WinRM.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="ab3ff-110">Usando Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="ab3ff-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="ab3ff-111">O cmdlet [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) obtém informações sobre o status de configuração de um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-111">The [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="ab3ff-112">Será retornado um objeto avançado, que inclui informações de alto nível sobre se a execução da configuração foi bem-sucedida ou não.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="ab3ff-113">É possível examinar o objeto para descobrir detalhes sobre a execução da configuração como:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="ab3ff-114">Todos os recursos que falharam</span><span class="sxs-lookup"><span data-stu-id="ab3ff-114">All of the resources that failed</span></span>
- <span data-ttu-id="ab3ff-115">Qualquer recurso que solicitou uma reinicialização</span><span class="sxs-lookup"><span data-stu-id="ab3ff-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="ab3ff-116">Definições de metaconfiguração em tempo de execução da configuração</span><span class="sxs-lookup"><span data-stu-id="ab3ff-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="ab3ff-117">Etc.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-117">Etc.</span></span>

<span data-ttu-id="ab3ff-118">O seguinte conjunto de parâmetros retorna as informações de status para a última execução de configuração:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="ab3ff-119">O seguinte conjunto de parâmetros retorna as informações de status para todas as execuções de configuração anteriores:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="ab3ff-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab3ff-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ReosurceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="ab3ff-121">Meu script não funciona: usar logs de DSC para diagnosticar erros de script</span><span class="sxs-lookup"><span data-stu-id="ab3ff-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="ab3ff-122">Como todos os softwares do Windows, a DSC registra erros e eventos em [logs](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) que podem ser exibidos no [Visualizador de Eventos](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span><span class="sxs-lookup"><span data-stu-id="ab3ff-122">Like all Windows software, DSC records errors and events in [logs](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) that can be viewed from the [Event Viewer](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span></span>
<span data-ttu-id="ab3ff-123">Um exame desses logs pode ajudá-lo a entender por que uma determinada operação falhou e como evitar falhas no futuro.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="ab3ff-124">Escrever scripts de configuração pode ser complicado; portanto, para facilitar o rastreamento de erros durante a criação, use o recurso de Log de DSC para acompanhar o progresso da sua configuração no log de eventos Analítico de DSC.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="ab3ff-125">Onde estão os logs de eventos de DSC?</span><span class="sxs-lookup"><span data-stu-id="ab3ff-125">Where are DSC event logs?</span></span>

<span data-ttu-id="ab3ff-126">No Visualizador de Eventos, os eventos de DSC estão em: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="ab3ff-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="ab3ff-127">O cmdlet do PowerShell correspondente, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), também pode ser executado para exibir os logs de eventos:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-127">The corresponding PowerShell cmdlet, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="ab3ff-128">Como mostrado acima, o nome do log primário da DSC é **Microsoft->Windows->DSC** (outros nomes de logs no Windows não são mostrados aqui por uma questão de brevidade).</span><span class="sxs-lookup"><span data-stu-id="ab3ff-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="ab3ff-129">O nome primário é anexado ao nome do canal para criar o nome completo do log.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="ab3ff-130">O mecanismo de DSC escreve principalmente em três tipos de logs: [logs Operacional, Analítico e de Depuração](https://technet.microsoft.com/library/cc722404.aspx).</span><span class="sxs-lookup"><span data-stu-id="ab3ff-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](https://technet.microsoft.com/library/cc722404.aspx).</span></span> <span data-ttu-id="ab3ff-131">Como os logs analítico e de depuração permanecem desligados por padrão, devem ser habilitados no Visualizador de Eventos.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="ab3ff-132">Para fazer isso, abra o Visualizador de Eventos digitando Show-EventLog no Windows PowerShell; ou clique no botão **Iniciar**, clique em **Painel de Controle**, em **Ferramentas Administrativas** e, em seguida, clique em **Visualizador de Eventos**.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="ab3ff-133">No menu **Exibir** no Visualizador de Eventos, clique em **Mostrar Logs Analítico e de Depuração**.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="ab3ff-134">O nome do log para o canal analítico **Microsoft-Windows-Dsc/Analytic**; para o canal de depuração é **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="ab3ff-135">Também é possível usar o utilitário [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) para habilitar os logs, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-135">You could also use the [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="ab3ff-136">O que os logs de DSC contêm?</span><span class="sxs-lookup"><span data-stu-id="ab3ff-136">What do DSC logs contain?</span></span>

<span data-ttu-id="ab3ff-137">Os logs de DSC são divididos nos três canais de log com base na importância da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="ab3ff-138">O log operacional na DSC contém todas as mensagens de erro e pode ser usado para identificar um problema.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="ab3ff-139">O log analítico tem um maior volume de eventos e pode identificar onde ocorreram erros.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="ab3ff-140">Esse canal também contém mensagens detalhadas (se houver).</span><span class="sxs-lookup"><span data-stu-id="ab3ff-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="ab3ff-141">O log de depuração contém logs que podem ajudá-lo a entender como os erros ocorreram.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="ab3ff-142">As mensagens de eventos de DSC são estruturadas de modo que cada mensagem de evento comece com uma ID de trabalho que represente uma operação de DSC com exclusividade.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="ab3ff-143">O exemplo a seguir tenta obter a mensagem do primeiro evento registrado no log de DSC operacional.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="ab3ff-144">Os eventos de DSC são registrados em uma estrutura específica que permite que o usuário agregue eventos por meio de um trabalho de DSC.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="ab3ff-145">A estrutura é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="ab3ff-146">Coletando eventos de uma operação única de DSC</span><span class="sxs-lookup"><span data-stu-id="ab3ff-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="ab3ff-147">Os logs de eventos de DSC contêm os eventos gerados por várias operações de DSC.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="ab3ff-148">No entanto, você geralmente estará interessado nos detalhes sobre apenas uma operação específica.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="ab3ff-149">Todos os logs de DSC podem ser agrupados pela propriedade de ID do trabalho, que é exclusiva para cada operação de DSC.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="ab3ff-150">A ID do trabalho é exibida como o primeiro valor da propriedade em todos os eventos de DSC.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="ab3ff-151">As etapas a seguir explicam como acumular todos os eventos em uma estrutura de matriz agrupada.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

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

<span data-ttu-id="ab3ff-152">Aqui, a variável `$SeparateDscOperations` contém logs agrupados pelas IDs de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="ab3ff-153">Cada elemento da matriz dessa variável representa um grupo de eventos registrados por uma operação de DSC diferente, permitindo o acesso a mais informações sobre os logs.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

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

<span data-ttu-id="ab3ff-154">Você pode extrair os dados na variável `$SeparateDscOperations` usando [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span><span class="sxs-lookup"><span data-stu-id="ab3ff-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span></span> <span data-ttu-id="ab3ff-155">Seguem cinco cenários em que talvez você queira extrair dados para solucionar problemas de DSC:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="ab3ff-156">1: Falhas em operações</span><span class="sxs-lookup"><span data-stu-id="ab3ff-156">1: Operations failures</span></span>

<span data-ttu-id="ab3ff-157">Todos os eventos têm [níveis de gravidade](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ab3ff-157">All events have [severity levels](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span></span> <span data-ttu-id="ab3ff-158">Essas informações podem ser usadas para identificar os eventos de erro:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="ab3ff-159">2: Detalhes das operações executadas na última meia hora</span><span class="sxs-lookup"><span data-stu-id="ab3ff-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="ab3ff-160">`TimeCreated`, uma propriedade de todos os eventos do Windows, indica o horário em que o evento foi criado.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="ab3ff-161">A comparação dessa propriedade com um objeto de data/hora específico pode ser usada para filtrar todos os eventos:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="ab3ff-162">3: Mensagens da operação mais recente</span><span class="sxs-lookup"><span data-stu-id="ab3ff-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="ab3ff-163">A operação mais recente é armazenada no primeiro índice do grupo de matriz `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="ab3ff-164">Uma consulta às mensagens do grupo para o índice 0 gera todas as mensagens referentes à operação mais recente:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

```powershell
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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="ab3ff-165">4: Mensagens de erro registradas para falhas em operações recentes</span><span class="sxs-lookup"><span data-stu-id="ab3ff-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="ab3ff-166">`$SeparateDscOperations[0].Group` contém um conjunto de eventos para a operação mais recente.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="ab3ff-167">Execute o cmdlet `Where-Object` para filtrar os eventos com base em seu nome de exibição de nível.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="ab3ff-168">Os resultados são armazenados na variável `$myFailedEvent`, que ainda pode ser examinada para obter a mensagem de evento:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="ab3ff-169">5: Todos os eventos gerados para uma ID de trabalho específica.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="ab3ff-170">`$SeparateDscOperations` é uma matriz de grupos, sendo que cada um deles tem o nome como a ID exclusiva do trabalho.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="ab3ff-171">Ao executar o cmdlet `Where-Object`, você pode extrair esses grupos de eventos que têm uma ID de trabalho específica:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="ab3ff-172">Usando xDscDiagnostics para analisar logs de DSC</span><span class="sxs-lookup"><span data-stu-id="ab3ff-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="ab3ff-173">**xDscDiagnostics** é um módulo do PowerShell que consiste em várias funções que podem ajudar a analisar falhas de DSC em seu computador.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="ab3ff-174">Essas funções podem ajudá-lo a identificar todos os eventos locais de operações anteriores de DSC ou eventos de DSC em computadores remotos (com credenciais válidas).</span><span class="sxs-lookup"><span data-stu-id="ab3ff-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="ab3ff-175">Aqui, o termo operação de DSC é usado para definir uma única execução de DSC desde o início até o fim.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="ab3ff-176">Por exemplo, `Test-DscConfiguration` seria uma operação de DSC separada.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="ab3ff-177">Da mesma forma, cada outro cmdlet na DSC (como `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) pode ser identificado como operações de DSC separadas.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="ab3ff-178">As funções são explicadas em [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="ab3ff-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="ab3ff-179">A ajuda está disponível executando `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="ab3ff-180">Obtendo detalhes das operações de DSC</span><span class="sxs-lookup"><span data-stu-id="ab3ff-180">Getting details of DSC operations</span></span>

<span data-ttu-id="ab3ff-181">A função `Get-xDscOperation` permite encontrar os resultados das operações de DSC executadas em um ou vários computadores e retorna um objeto que contém a coleção de eventos produzidos por cada operação de DSC.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="ab3ff-182">Por exemplo, na seguinte saída, três comandos foram executados.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="ab3ff-183">O primeiro deles passou e os outros dois falharam.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="ab3ff-184">Esses resultados estão resumidos na saída de `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="ab3ff-185">Você também pode especificar que deseja apenas obter resultados para as operações mais recentes usando o parâmetro `Newest`:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="ab3ff-186">Obtendo detalhes de eventos de DSC</span><span class="sxs-lookup"><span data-stu-id="ab3ff-186">Getting details of DSC events</span></span>

<span data-ttu-id="ab3ff-187">O cmdlet `Trace-xDscOperation` gera um objeto que contém uma coleção de eventos, os tipos de evento e a saída de mensagem gerada por meio de uma operação de DSC específica.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="ab3ff-188">Normalmente, quando uma falha é encontrada em qualquer uma das operações usando `Get-xDscOperation`, você rastrearia a operação para descobrir quais dos eventos causaram uma falha.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="ab3ff-189">Use o parâmetro `SequenceID` para obter os eventos de uma operação específica referente a um computador específico.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="ab3ff-190">Por exemplo, se você especificar um `SequenceID` de 9, `Trace-xDscOperaion` obterá o rastreamento para a operação de DSC que foi a 9ª da última operação:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="ab3ff-191">Passe o **GUID** atribuído a uma operação de DSC específica (conforme retornado pelo cmdlet `Get-xDscOperation`) para obter os detalhes do evento para a operação de DSC:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmldet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="ab3ff-192">Observe que, como `Trace-xDscOperation` agrega eventos dos logs Operacional, Analítico e de Depuração, ele solicitará a habilitação desses logs, conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="ab3ff-193">Como alternativa, você pode reunir informações sobre os eventos salvando a saída de `Trace-xDscOperation` em uma variável.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="ab3ff-194">Pode-se usar o comando a seguir para exibir todos os eventos de determinada operação de DSC.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="ab3ff-195">Isso exibirá os mesmos resultados que o cmdlet `Get-WinEvent`, como a saída abaixo:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="ab3ff-196">Idealmente, em primeiro lugar, use `Get-xDscOperation` para listar as últimas execuções da configuração DSC nos seus computadores.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="ab3ff-197">Depois disso, você pode examinar qualquer operação única (usando sua SequenceID ou JobID) com `Trace-xDscOperation` para descobrir o que ela fazia em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="ab3ff-198">Obtendo eventos de um computador remoto</span><span class="sxs-lookup"><span data-stu-id="ab3ff-198">Getting events for a remote computer</span></span>

<span data-ttu-id="ab3ff-199">Use o parâmetro `ComputerName` do cmdlet `Trace-xDscOperation` para obter os detalhes de evento em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="ab3ff-200">Antes de poder fazer isso, é necessário criar uma regra de firewall para permitir a administração remota no computador remoto:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="ab3ff-201">Agora você pode especificar o computador em sua chamada para `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="ab3ff-202">Meus recursos não são atualizados: como redefinir o cache</span><span class="sxs-lookup"><span data-stu-id="ab3ff-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="ab3ff-203">O mecanismo de DSC armazena em cache os recursos implementados como um módulo do PowerShell para fins de eficiência.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="ab3ff-204">No entanto, isso pode causar problemas quando você está criando um recurso e testando-o simultaneamente, porque DSC carregará a versão armazenada em cache até o processo ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="ab3ff-205">A única maneira de fazer a DSC carregar a versão mais recente é eliminar explicitamente o processo que hospeda o mecanismo de DSC.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="ab3ff-206">Da mesma forma, quando você executa `Start-DscConfiguration`, depois de adicionar e modificar um recurso personalizado, a modificação pode não ser executada a menos que, ou até que, o computador seja reinicializado.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="ab3ff-207">Isso ocorre porque a DSC é executada no Processo de Host do provedor WMI (WmiPrvSE) e, geralmente, há muitas instâncias do WmiPrvSE em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="ab3ff-208">Quando você reinicializa, o processo de host é reiniciado e o cache é limpo.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="ab3ff-209">Para conseguir reciclar a configuração e limpar o cache sem reinicialização, você deve parar e reiniciar o processo de host.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="ab3ff-210">Isso pode ser feito por instância, ou seja, você identifica o processo, interrompe-o e reinicia-o.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="ab3ff-211">Ou pode usar `DebugMode`, conforme demonstrado abaixo, para recarregar o recurso de DSC do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="ab3ff-212">Para identificar o processo que está hospedando o mecanismo de DSC e interrompê-lo por instância, é possível listar a ID do processo do WmiPrvSE que está hospedando o mecanismo de DSC.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="ab3ff-213">Em seguida, para atualizar o provedor, interrompa o processo WmiPrvSE usando os comandos abaixo; depois, execute **Start-DscConfiguration** novamente.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

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

## <a name="using-debugmode"></a><span data-ttu-id="ab3ff-214">Usando o DebugMode</span><span class="sxs-lookup"><span data-stu-id="ab3ff-214">Using DebugMode</span></span>

<span data-ttu-id="ab3ff-215">Você pode configurar o Gerenciador de Configurações Local (LCM) de DSC para usar `DebugMode` para sempre limpar o cache quando o processo de host for reiniciado.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="ab3ff-216">Quando definido como **TRUE**, faz com que o mecanismo sempre recarregue o recurso de DSC do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="ab3ff-217">Depois de escrever seu recurso, você pode defini-lo como **FALSE** e o mecanismo será revertido para o comportamento de armazenamento em cache dos módulos.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="ab3ff-218">Segue uma demonstração para mostrar como `DebugMode` pode atualizar o cache automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="ab3ff-219">Primeiro, vamos examinar a configuração padrão:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-219">First, let's look at the default configuration:</span></span>

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="ab3ff-220">Pode-se ver que `DebugMode` foi definido como **"None"**.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="ab3ff-221">Para configurar a demonstração `DebugMode`, use o seguinte recurso do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

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

<span data-ttu-id="ab3ff-222">Agora, crie uma configuração usando o recurso acima chamado `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

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

<span data-ttu-id="ab3ff-223">Você verá que o conteúdo do arquivo: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` é **1**.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="ab3ff-224">Agora, atualize o código do provedor usando o script a seguir:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-224">Now, update the provider code using the following script:</span></span>

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

<span data-ttu-id="ab3ff-225">Esse script gera um número aleatório e atualiza o código do provedor correspondentemente.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="ab3ff-226">Com `DebugMode` definido como falso, o conteúdo do arquivo "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" nunca é alterado.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="ab3ff-227">Agora, defina `DebugMode` como **"ForceModuleImport"** no script de configuração:</span><span class="sxs-lookup"><span data-stu-id="ab3ff-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="ab3ff-228">Quando você executar novamente o script acima, verá que o conteúdo do arquivo é diferente em cada ocasião.</span><span class="sxs-lookup"><span data-stu-id="ab3ff-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="ab3ff-229">(É possível executar `Get-DscConfiguration` para verificar).</span><span class="sxs-lookup"><span data-stu-id="ab3ff-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="ab3ff-230">Abaixo está o resultado de duas execuções adicionais (os resultados podem ser diferentes quando você executar o script):</span><span class="sxs-lookup"><span data-stu-id="ab3ff-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ab3ff-231">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ab3ff-231">See Also</span></span>

### <a name="reference"></a><span data-ttu-id="ab3ff-232">Referência</span><span class="sxs-lookup"><span data-stu-id="ab3ff-232">Reference</span></span>

- [<span data-ttu-id="ab3ff-233">Recurso Log de DSC</span><span class="sxs-lookup"><span data-stu-id="ab3ff-233">DSC Log Resource</span></span>](logResource.md)

### <a name="concepts"></a><span data-ttu-id="ab3ff-234">Conceitos</span><span class="sxs-lookup"><span data-stu-id="ab3ff-234">Concepts</span></span>

- [<span data-ttu-id="ab3ff-235">Criar recursos personalizados de configuração de estado desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab3ff-235">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="ab3ff-236">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="ab3ff-236">Other Resources</span></span>

- <span data-ttu-id="ab3ff-237">[Cmdlets de Configuração de Estado Desejado do Windows PowerShell](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="ab3ff-237">[Windows PowerShell Desired State Configuration Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span></span>
