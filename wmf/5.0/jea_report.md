---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 2af56be1915c148809f52cd9040c45da160ae0a2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="reporting-on-jea"></a><span data-ttu-id="e6a76-102">Relatando no JEA</span><span class="sxs-lookup"><span data-stu-id="e6a76-102">Reporting on JEA</span></span>
<span data-ttu-id="e6a76-103">Para relatar o estado da configuração JEA, é possível usar:</span><span class="sxs-lookup"><span data-stu-id="e6a76-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="e6a76-104">**Get-PSSessionConfiguration** para retornar uma lista de todos os pontos de extremidade registrados em determinado computador.</span><span class="sxs-lookup"><span data-stu-id="e6a76-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="e6a76-105">**Get-PSSessionCapability** para relatar as funcionalidades que determinado usuário tem em relação a um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="e6a76-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="e6a76-106">Aqui está um exemplo de **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="e6a76-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

<span data-ttu-id="e6a76-107">Para relatar as _ações_ executadas pelos usuários durante uma sessão JEA, é possível:</span><span class="sxs-lookup"><span data-stu-id="e6a76-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="e6a76-108">Habilitar as transcrições “over the shoulder” para o ponto de extremidade JEA e consultar o diretório de transcrições para obter um log completo das ações de cada usuário</span><span class="sxs-lookup"><span data-stu-id="e6a76-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="e6a76-109">Ativar o registro de módulo PowerShell e inspecionar os logs de eventos do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6a76-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>