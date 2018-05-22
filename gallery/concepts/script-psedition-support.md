---
ms.date: 06/12/2017
contributor: manikb
keywords: galeria,powershell,cmdlet,psget
title: Script com edições compatíveis do PowerShell
ms.openlocfilehash: 27b50be4e99b6c6b8fa089d1d4a436a27eeb17c9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="512c6-103">Script com edições compatíveis do PowerShell</span><span class="sxs-lookup"><span data-stu-id="512c6-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="512c6-104">Da versão 5.1 em diante, o PowerShell está disponível nas edições diferentes que denotam diferentes conjuntos de recursos e compatibilidade de plataforma.</span><span class="sxs-lookup"><span data-stu-id="512c6-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="512c6-105">**Desktop Edition:** criada no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows, como Server Core e Área de Trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="512c6-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="512c6-106">**Core Edition:** criada no .NET Core e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell executando em edições de superfície reduzida do Windows, como o Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="512c6-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="512c6-107">A edição de execução do PowerShell é mostrada na propriedade PSEdition do $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="512c6-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="512c6-108">Os autores de scripts podem impedir que um script seja executado a menos que ele seja executado em uma edição compatível do PowerShell usando o parâmetro PSEdition em uma instrução #requires.</span><span class="sxs-lookup"><span data-stu-id="512c6-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a #requires statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="512c6-109">Os usuários da Galeria do PowerShell podem encontrar a lista de scripts com suporte em uma edição específica do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="512c6-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="512c6-110">Scripts sem PSEdition_Desktop e PSEditon_Core funcionam corretamente em edições do PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="512c6-110">Scripts without PSEdition_Desktop and PSEditon_Core are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core

```

## <a name="more-details"></a><span data-ttu-id="512c6-111">Mais detalhes</span><span class="sxs-lookup"><span data-stu-id="512c6-111">More details</span></span>

- [<span data-ttu-id="512c6-112">Módulos com PSEditions</span><span class="sxs-lookup"><span data-stu-id="512c6-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="512c6-113">Suporte do PSEditions na PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="512c6-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)