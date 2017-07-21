---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: 69188738333a853a16e6ea68689ecba5dc632225
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="c6c7b-102">Suporte à versão lado a lado no PowerShell 5.0 ou mais recente</span><span class="sxs-lookup"><span data-stu-id="c6c7b-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="c6c7b-103">Agora há suporte à versão do módulo SxS (lado a lado) nos cmdlets Install-Module, Update-Module e Publish-Module executados no Windows PowerShell 5.0 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="c6c7b-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="c6c7b-104">Além disso, adicionamos um parâmetro -RequiredVersion ao cmdlet Publish-Module para especificar a versão a ser publicada.</span><span class="sxs-lookup"><span data-stu-id="c6c7b-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="c6c7b-105">O parâmetro Path agora dá suporte ao caminho base do módulo com a pasta de versão.</span><span class="sxs-lookup"><span data-stu-id="c6c7b-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="c6c7b-106">**Exemplos de Install-Module:**</span><span class="sxs-lookup"><span data-stu-id="c6c7b-106">**Install-Module examples:**</span></span>
```powershell
PS C:\\windows\\system32&gt; Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
PS C:\\windows\\system32&gt; Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase
Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

PS C:\\windows\\system32&gt; Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
PS C:\\windows\\system32&gt; Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase
Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

PS C:\\windows\\system32&gt; Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Type       Repository           Description            
-------    ----                                ----       ----------           -----------            
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```

