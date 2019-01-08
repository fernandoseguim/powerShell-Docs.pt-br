---
ms.date: 06/12/2017
contributor: manikb
keywords: galeria,powershell,cmdlet,psget
title: Script com edições compatíveis do PowerShell
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655269"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="32deb-103">Script com edições compatíveis do PowerShell</span><span class="sxs-lookup"><span data-stu-id="32deb-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="32deb-104">Da versão 5.1 em diante, o PowerShell está disponível nas edições diferentes que denotam diferentes conjuntos de recursos e compatibilidade de plataforma.</span><span class="sxs-lookup"><span data-stu-id="32deb-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="32deb-105">Desktop Edition Baseado no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows como núcleo de servidor e área de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="32deb-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="32deb-106">**Core Edition:** Baseada no .NET Core e fornece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de volume reduzido do Windows, como o Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="32deb-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="32deb-107">A edição de execução do PowerShell é mostrada na propriedade PSEdition do $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="32deb-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

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

<span data-ttu-id="32deb-108">Os autores de scripts podem impedir que um script seja executado a menos que ele seja executado em uma edição compatível do PowerShell usando o parâmetro PSEdition em uma instrução `#requires`.</span><span class="sxs-lookup"><span data-stu-id="32deb-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="32deb-109">Os usuários da Galeria do PowerShell podem encontrar a lista de scripts com suporte em uma edição específica do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32deb-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="32deb-110">Scripts sem as marcas PSEdition_Desktop e PSEdition_Core funcionam corretamente na edição do PowerShell Desktop.</span><span class="sxs-lookup"><span data-stu-id="32deb-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="32deb-111">Mais detalhes</span><span class="sxs-lookup"><span data-stu-id="32deb-111">More details</span></span>

- [<span data-ttu-id="32deb-112">Módulos com PSEditions</span><span class="sxs-lookup"><span data-stu-id="32deb-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="32deb-113">Suporte do PSEditions na PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="32deb-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)
