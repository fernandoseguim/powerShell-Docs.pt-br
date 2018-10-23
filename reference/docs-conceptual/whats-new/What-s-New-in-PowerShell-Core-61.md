---
title: Novidades no PowerShell Core 6.1
description: Novos recursos e alterações liberados no PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 4e39780a0ff446993005bba6284741f3b4b02549
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851300"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="82e14-103">Novidades no PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="82e14-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="82e14-104">Abaixo está uma seleção de alguns dos principais recursos novos e alterações que foram introduzidos no PowerShell Core 6.1.</span><span class="sxs-lookup"><span data-stu-id="82e14-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="82e14-105">Também há **toneladas** de "coisas chatas" que tornam o PowerShell mais rápido e mais estável (além de muitas e muitas correções de bugs)!</span><span class="sxs-lookup"><span data-stu-id="82e14-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="82e14-106">Para obter uma lista completa de alterações, confira nosso [log de alterações no GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="82e14-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="82e14-107">Apesar de citarmos alguns nomes abaixo, obrigado a [todos os colaboradores da comunidade](https://github.com/PowerShell/PowerShell/graphs/contributors) que possibilitaram esta versão.</span><span class="sxs-lookup"><span data-stu-id="82e14-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="82e14-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="82e14-108">.NET Core 2.1</span></span>

<span data-ttu-id="82e14-109">O PowerShell Core 6.1 migrou para o .NET Core 2.1 depois de ter sido [liberado em maio](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resultando em muitas melhorias no PowerShell, incluindo:</span><span class="sxs-lookup"><span data-stu-id="82e14-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="82e14-110">aprimoramentos de desempenho (veja [abaixo](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="82e14-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="82e14-111">Suporte a Alpine Linux (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="82e14-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="82e14-112">[Suporte à ferramenta global .NET](/dotnet/core/tools/global-tools) – em breve no PowerShell</span><span class="sxs-lookup"><span data-stu-id="82e14-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="82e14-113">Pacote de compatibilidade do Windows para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="82e14-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="82e14-114">No Windows, a equipe do .NET enviou o [pacote de compatibilidade do Windows para o .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), um conjunto de assemblies que devolve algumas APIs removidas ao .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="82e14-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="82e14-115">Adicionamos o pacote de compatibilidade do Windows à versão do PowerShell Core 6.1 para que os módulos ou scripts que usam essas APIs possam acreditar que estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="82e14-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="82e14-116">O pacote de compatibilidade do Windows permite que o PowerShell Core use **mais de 1900 cmdlets que acompanham a atualização de outubro de 2018 do Windows 10 e o Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="82e14-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="82e14-117">Suporte à lista de permissões de aplicativos</span><span class="sxs-lookup"><span data-stu-id="82e14-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="82e14-118">O PowerShell Core 6.1 tem paridade com o Windows PowerShell 5.1, com suporte para lista de permissões de aplicativos do [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) e do [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control).</span><span class="sxs-lookup"><span data-stu-id="82e14-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span>
<span data-ttu-id="82e14-119">A lista de permissões de aplicativos permite um controle granular de quais binários podem ser executados, usado com o [modo de linguagem restrita](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82e14-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="82e14-120">Aprimoramentos do desempenho</span><span class="sxs-lookup"><span data-stu-id="82e14-120">Performance improvements</span></span>

<span data-ttu-id="82e14-121">O PowerShell Core 6.0 fez alguns aprimoramentos significativos no desempenho.</span><span class="sxs-lookup"><span data-stu-id="82e14-121">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="82e14-122">O PowerShell Core 6.1 continua aumentando a velocidade de determinadas operações.</span><span class="sxs-lookup"><span data-stu-id="82e14-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="82e14-123">Por exemplo, `Group-Object` foi acelerado em 66%:</span><span class="sxs-lookup"><span data-stu-id="82e14-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="82e14-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="82e14-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="82e14-125">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="82e14-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="82e14-126">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="82e14-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="82e14-127">Tempo (s)</span><span class="sxs-lookup"><span data-stu-id="82e14-127">Time (sec)</span></span>   | <span data-ttu-id="82e14-128">25,178</span><span class="sxs-lookup"><span data-stu-id="82e14-128">25.178</span></span>                 | <span data-ttu-id="82e14-129">19,653</span><span class="sxs-lookup"><span data-stu-id="82e14-129">19.653</span></span>              | <span data-ttu-id="82e14-130">6,641</span><span class="sxs-lookup"><span data-stu-id="82e14-130">6.641</span></span>               |
| <span data-ttu-id="82e14-131">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="82e14-131">Speed-up (%)</span></span> | <span data-ttu-id="82e14-132">N/D</span><span class="sxs-lookup"><span data-stu-id="82e14-132">N/A</span></span>                    | <span data-ttu-id="82e14-133">21,9%</span><span class="sxs-lookup"><span data-stu-id="82e14-133">21.9%</span></span>               | <span data-ttu-id="82e14-134">66,2%</span><span class="sxs-lookup"><span data-stu-id="82e14-134">66.2%</span></span>               |

<span data-ttu-id="82e14-135">Da mesma forma, a classificação de cenários como este melhorou em mais de 15%:</span><span class="sxs-lookup"><span data-stu-id="82e14-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="82e14-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="82e14-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="82e14-137">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="82e14-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="82e14-138">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="82e14-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="82e14-139">Tempo (s)</span><span class="sxs-lookup"><span data-stu-id="82e14-139">Time (sec)</span></span>   | <span data-ttu-id="82e14-140">12,170</span><span class="sxs-lookup"><span data-stu-id="82e14-140">12.170</span></span>                 | <span data-ttu-id="82e14-141">8,493</span><span class="sxs-lookup"><span data-stu-id="82e14-141">8.493</span></span>               | <span data-ttu-id="82e14-142">7,08</span><span class="sxs-lookup"><span data-stu-id="82e14-142">7.08</span></span>                |
| <span data-ttu-id="82e14-143">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="82e14-143">Speed-up (%)</span></span> | <span data-ttu-id="82e14-144">N/D</span><span class="sxs-lookup"><span data-stu-id="82e14-144">N/A</span></span>                    | <span data-ttu-id="82e14-145">30,2%</span><span class="sxs-lookup"><span data-stu-id="82e14-145">30.2%</span></span>               | <span data-ttu-id="82e14-146">16,6%</span><span class="sxs-lookup"><span data-stu-id="82e14-146">16.6%</span></span>               |

<span data-ttu-id="82e14-147">`Import-Csv` também acelerou significativamente após uma regressão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82e14-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="82e14-148">O exemplo a seguir usa um CSV de teste com 26.616 linhas e seis colunas:</span><span class="sxs-lookup"><span data-stu-id="82e14-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="82e14-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="82e14-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="82e14-150">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="82e14-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="82e14-151">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="82e14-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="82e14-152">Tempo (s)</span><span class="sxs-lookup"><span data-stu-id="82e14-152">Time (sec)</span></span>   | <span data-ttu-id="82e14-153">0,441</span><span class="sxs-lookup"><span data-stu-id="82e14-153">0.441</span></span>                  | <span data-ttu-id="82e14-154">1,069</span><span class="sxs-lookup"><span data-stu-id="82e14-154">1.069</span></span>               | <span data-ttu-id="82e14-155">0,268</span><span class="sxs-lookup"><span data-stu-id="82e14-155">0.268</span></span>                  |
| <span data-ttu-id="82e14-156">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="82e14-156">Speed-up (%)</span></span> | <span data-ttu-id="82e14-157">N/D</span><span class="sxs-lookup"><span data-stu-id="82e14-157">N/A</span></span>                    | <span data-ttu-id="82e14-158">-142,4%</span><span class="sxs-lookup"><span data-stu-id="82e14-158">-142.4%</span></span>             | <span data-ttu-id="82e14-159">74,9% (39,2% de WPS)</span><span class="sxs-lookup"><span data-stu-id="82e14-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="82e14-160">Por fim, a conversão de JSON em `PSObject` acelerou em mais de 50% desde o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82e14-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="82e14-161">O exemplo a seguir usa um arquivo JSON de teste de cerca de 2MB:</span><span class="sxs-lookup"><span data-stu-id="82e14-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="82e14-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="82e14-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="82e14-163">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="82e14-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="82e14-164">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="82e14-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="82e14-165">Tempo (s)</span><span class="sxs-lookup"><span data-stu-id="82e14-165">Time (sec)</span></span>   | <span data-ttu-id="82e14-166">0,259</span><span class="sxs-lookup"><span data-stu-id="82e14-166">0.259</span></span>                  | <span data-ttu-id="82e14-167">0,577</span><span class="sxs-lookup"><span data-stu-id="82e14-167">0.577</span></span>               | <span data-ttu-id="82e14-168">0,125</span><span class="sxs-lookup"><span data-stu-id="82e14-168">0.125</span></span>                  |
| <span data-ttu-id="82e14-169">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="82e14-169">Speed-up (%)</span></span> | <span data-ttu-id="82e14-170">N/D</span><span class="sxs-lookup"><span data-stu-id="82e14-170">N/A</span></span>                    | <span data-ttu-id="82e14-171">-122,8%</span><span class="sxs-lookup"><span data-stu-id="82e14-171">-122.8%</span></span>             | <span data-ttu-id="82e14-172">78,3% (51,7% de WPS)</span><span class="sxs-lookup"><span data-stu-id="82e14-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="82e14-173">Verificar `system32` se há módulos de caixa de entrada compatíveis no Windows</span><span class="sxs-lookup"><span data-stu-id="82e14-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="82e14-174">Na atualização 1809 do Windows 10 e no Windows Server 2019, atualizamos alguns módulos do PowerShell na caixa de entrada para marcá-los como compatíveis com o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="82e14-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="82e14-175">Quando o PowerShell Core 6.1 for iniciado, ele incluirá `$windir\System32` automaticamente como parte da variável de ambiente `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="82e14-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="82e14-176">No entanto, expõe módulos somente para `Get-Module` e `Import-Module` se seu `CompatiblePSEdition` está marcado como compatível `Core`.</span><span class="sxs-lookup"><span data-stu-id="82e14-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="82e14-177">Você pode ver diferentes módulos disponíveis dependendo de quais funções e recursos estão instalados.</span><span class="sxs-lookup"><span data-stu-id="82e14-177">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="82e14-178">Pode substituir esse comportamento para mostrar todos os módulos usando o parâmetro de opção `-SkipEditionCheck`.</span><span class="sxs-lookup"><span data-stu-id="82e14-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="82e14-179">Também adicionamos uma propriedade `PSEdition` à saída de tabela.</span><span class="sxs-lookup"><span data-stu-id="82e14-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="82e14-180">Para obter mais informações sobre esse comportamento, confira [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="82e14-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="82e14-181">Cmdlets de markdown e renderização</span><span class="sxs-lookup"><span data-stu-id="82e14-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="82e14-182">O markdown é um padrão para a criação de documentos de texto não criptografado legíveis com formatação básica que possam ser renderizados em HTML.</span><span class="sxs-lookup"><span data-stu-id="82e14-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="82e14-183">Adicionamos alguns cmdlets em um 6.1 o que permite converter e renderizar documentos de Markdown no console, incluindo:</span><span class="sxs-lookup"><span data-stu-id="82e14-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="82e14-184">Por exemplo, `Show-Markdown` renderiza um arquivo markdown no console:</span><span class="sxs-lookup"><span data-stu-id="82e14-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Exemplo de Markdown do show](./images/markdown_example.png)

<span data-ttu-id="82e14-186">Para obter mais informações sobre como esses cmdlets funcionam, confira [essa RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="82e14-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="82e14-187">Sinalizadores de recursos experimentais</span><span class="sxs-lookup"><span data-stu-id="82e14-187">Experimental feature flags</span></span>

<span data-ttu-id="82e14-188">Com os sinalizadores de recursos experimentais, os usuários podem habilitar recursos que não foram finalizados.</span><span class="sxs-lookup"><span data-stu-id="82e14-188">Experimental feature flags enable users to turn on features that haven't been finalized.</span></span>
<span data-ttu-id="82e14-189">Esses recursos experimentais não têm suporte e podem conter bugs.</span><span class="sxs-lookup"><span data-stu-id="82e14-189">These experimental features aren't supported and may have bugs.</span></span>

<span data-ttu-id="82e14-190">Você pode aprender mais sobre esse recurso no [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="82e14-190">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="82e14-191">Aprimoramentos do cmdlet da Web</span><span class="sxs-lookup"><span data-stu-id="82e14-191">Web cmdlet improvements</span></span>

<span data-ttu-id="82e14-192">Graças a [@markekraus](https://github.com/markekraus), uma grande quantidade de melhorias foi feita em nossos cmdlets da Web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="82e14-192">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="82e14-193">e [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="82e14-193">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="82e14-194">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) – conjunto de codificação padrão para UTF-8 para respostas `application-json`</span><span class="sxs-lookup"><span data-stu-id="82e14-194">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="82e14-195">Parâmetro [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` para permitir cabeçalhos `Content-Type` que não estão em conformidade com as regras</span><span class="sxs-lookup"><span data-stu-id="82e14-195">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="82e14-196">Parâmetro [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` para dar suporte ao suporte `multipart/form-data` simplificado</span><span class="sxs-lookup"><span data-stu-id="82e14-196">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="82e14-197">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) – Em conformidade, tratamento de chaves de relação sem distinção entre maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="82e14-197">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="82e14-198">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) – Adicionar parâmetro `-Resume` para cmdlets da Web</span><span class="sxs-lookup"><span data-stu-id="82e14-198">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="82e14-199">Aprimoramentos na comunicação remota</span><span class="sxs-lookup"><span data-stu-id="82e14-199">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="82e14-200">O PowerShell Direct para Contêineres tenta usar primeiro o PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="82e14-200">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="82e14-201">O [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) é um recurso do PowerShell e do Hyper-V que permite que você se conecte a uma VM ou Contêiner do Hyper-V sem conectividade de rede ou outros serviços de gerenciamento remoto.</span><span class="sxs-lookup"><span data-stu-id="82e14-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="82e14-202">No passado, o PowerShell Direct era conectado usando a instância do Windows PowerShell de caixa de entrada no Contêiner.</span><span class="sxs-lookup"><span data-stu-id="82e14-202">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span>
<span data-ttu-id="82e14-203">Agora, o PowerShell Direct primeiro tenta se conectar usando algum `pwsh.exe` disponível na variável de ambiente `PATH`.</span><span class="sxs-lookup"><span data-stu-id="82e14-203">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="82e14-204">Se `pwsh.exe` não estiver disponível, o PowerShell Direct voltará a usar `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="82e14-204">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="82e14-205">`Enable-PSRemoting` já cria pontos de extremidade de comunicação remota separados para versões prévias</span><span class="sxs-lookup"><span data-stu-id="82e14-205">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="82e14-206">`Enable-PSRemoting` já cria duas configurações de sessão de comunicação remota:</span><span class="sxs-lookup"><span data-stu-id="82e14-206">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="82e14-207">Uma para a versão principal do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82e14-207">One for the major version of PowerShell.</span></span> <span data-ttu-id="82e14-208">Por exemplo, `PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="82e14-208">For example,`PowerShell.6`.</span></span> <span data-ttu-id="82e14-209">Esse ponto de extremidade que pode ser utilizado em versões secundárias é atualizado como a configuração de sessão do PowerShell 6 "para todo o sistema"</span><span class="sxs-lookup"><span data-stu-id="82e14-209">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="82e14-210">Uma configuração de sessão específica da versão, por exemplo: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="82e14-210">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="82e14-211">Esse comportamento será útil se você quiser ter várias versões do PowerShell 6 instaladas e acessíveis no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="82e14-211">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="82e14-212">Além disso, as versões prévias do PowerShell já têm suas próprias configurações de sessão de comunicação remota depois de executar o cmdlet `Enable-PSRemoting`:</span><span class="sxs-lookup"><span data-stu-id="82e14-212">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="82e14-213">A saída poderá ser diferente se você ainda não tiver configurado o WinRM.</span><span class="sxs-lookup"><span data-stu-id="82e14-213">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="82e14-214">Em seguida, pode ver as configurações de sessão separadas do PowerShell para a versão prévia e builds estáveis do PowerShell 6, assim como para cada versão específica.</span><span class="sxs-lookup"><span data-stu-id="82e14-214">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="82e14-215">Sintaxe `user@host:port` com suporte para o SSH</span><span class="sxs-lookup"><span data-stu-id="82e14-215">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="82e14-216">Os clientes do SSH geralmente dão suporte a uma cadeia de conexão no formato `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="82e14-216">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="82e14-217">Com a adição de SSH como um protocolo de comunicação remota do PowerShell, adicionamos suporte para esse formato de cadeia de conexão:</span><span class="sxs-lookup"><span data-stu-id="82e14-217">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="82e14-218">Opção de MSI para adicionar o menu de contexto de shell do Explorer no Windows</span><span class="sxs-lookup"><span data-stu-id="82e14-218">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="82e14-219">Graças a [@bergmeister](https://github.com/bergmeister), já é possível habilitar um menu de contexto no Windows.</span><span class="sxs-lookup"><span data-stu-id="82e14-219">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="82e14-220">Agora, você pode abrir a instalação do PowerShell 6.1 para todo o sistema por meio de qualquer pasta no Windows Explorer:</span><span class="sxs-lookup"><span data-stu-id="82e14-220">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Menu de contexto do shell do PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="82e14-222">Coisas boas</span><span class="sxs-lookup"><span data-stu-id="82e14-222">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="82e14-223">"Executar como administrador" na lista de atalhos do Windows</span><span class="sxs-lookup"><span data-stu-id="82e14-223">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="82e14-224">Graças a [@bergmeister](https://github.com/bergmeister), a lista de atalhos do PowerShell Core passou a incluir "Executar como administrador":</span><span class="sxs-lookup"><span data-stu-id="82e14-224">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Executar como administrador na lista de atalhos do PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="82e14-226">`cd -` retorna ao diretório anterior</span><span class="sxs-lookup"><span data-stu-id="82e14-226">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="82e14-227">Ou no Linux:</span><span class="sxs-lookup"><span data-stu-id="82e14-227">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="82e14-228">Além, `cd` e `cd --` mudam para `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="82e14-228">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="82e14-229">Graças a [@iSazonov](https://github.com/iSazonov), o [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet foi movido para o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="82e14-229">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="82e14-230">`Update-Help` como não administrador</span><span class="sxs-lookup"><span data-stu-id="82e14-230">`Update-Help` as non-admin</span></span>

<span data-ttu-id="82e14-231">Por demanda popular, `Update-Help` não precisa mais ser executado como um administrador.</span><span class="sxs-lookup"><span data-stu-id="82e14-231">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
<span data-ttu-id="82e14-232">Agora, o padrão de `Update-Help` é salvar a ajuda em uma pasta no escopo do usuário.</span><span class="sxs-lookup"><span data-stu-id="82e14-232">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="82e14-233">Novos métodos/propriedades em `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="82e14-233">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="82e14-234">Graças a [@iSazonov](https://github.com/iSazonov), incluímos novos métodos e propriedades em `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="82e14-234">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span>
<span data-ttu-id="82e14-235">`PSCustomObject` agora inclui uma propriedade `Count`/`Length` como outros objetos.</span><span class="sxs-lookup"><span data-stu-id="82e14-235">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="82e14-236">Esse trabalho também inclui os métodos `ForEach` e `Where`, que permitem que você utilize e filtre os itens `PSCustomObject`:</span><span class="sxs-lookup"><span data-stu-id="82e14-236">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="82e14-237">Graças a @SimonWahlin, incluímos o parâmetro `-Not` em `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="82e14-237">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="82e14-238">Agora, é possível filtrar um objeto no pipeline por inexistência de uma propriedade ou um valor de propriedade nula/vazia.</span><span class="sxs-lookup"><span data-stu-id="82e14-238">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="82e14-239">Por exemplo, esse comando retorna todos os serviços que não têm serviços dependentes definidos:</span><span class="sxs-lookup"><span data-stu-id="82e14-239">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="82e14-240">`New-ModuleManifest` cria um documento de UTF-8 sem marca de ordem de byte</span><span class="sxs-lookup"><span data-stu-id="82e14-240">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="82e14-241">Dada nossa migração para UTF-8 sem marca de ordem de byte no PowerShell 6.0, atualizamos o cmdlet `New-ModuleManifest` para criar um documento UTF-8 sem marca de ordem de byte ao invés de um UTF-16.</span><span class="sxs-lookup"><span data-stu-id="82e14-241">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="82e14-242">Conversões de PSMethod para delegado</span><span class="sxs-lookup"><span data-stu-id="82e14-242">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="82e14-243">Graças a [@powercode](https://github.com/powercode), passamos a dar suporte para a conversão de `PSMethod` em um delegado.</span><span class="sxs-lookup"><span data-stu-id="82e14-243">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="82e14-244">Assim, é possível fazer coisas como passar `PSMethod` `[M]::DoubleStrLen` como valor delegado para `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="82e14-244">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="82e14-245">Para obter mais informações sobre essa alteração, confira [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="82e14-245">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="82e14-246">Desvio padrão em `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="82e14-246">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="82e14-247">Graças a [@CloudyDino](https://github.com/CloudyDino), incluímos uma propriedade `StandardDeviation` em `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="82e14-247">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="82e14-248">Graças a [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` passou a ter o parâmetro `Password`, que pega um `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="82e14-248">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="82e14-249">Assim, você pode usá-lo de forma não interativa:</span><span class="sxs-lookup"><span data-stu-id="82e14-249">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="82e14-250">Remoção da função `more`</span><span class="sxs-lookup"><span data-stu-id="82e14-250">Removal of the `more` function</span></span>

<span data-ttu-id="82e14-251">No passado, o PowerShell enviou uma função no Windows chamada `more`, que encapsulou `more.com`.</span><span class="sxs-lookup"><span data-stu-id="82e14-251">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="82e14-252">Essa função foi removida.</span><span class="sxs-lookup"><span data-stu-id="82e14-252">That function has now been removed.</span></span>

<span data-ttu-id="82e14-253">Além disso, a função `help` foi alterada para usar `more.com` no Windows ou o pager padrão do sistema especificado por `$env:PAGER` em plataformas não Windows.</span><span class="sxs-lookup"><span data-stu-id="82e14-253">Also the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="82e14-254">Agora, `cd DriveName:` retorna os usuários para o diretório de trabalho atual na unidade</span><span class="sxs-lookup"><span data-stu-id="82e14-254">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="82e14-255">Anteriormente, o uso de `Set-Location` ou `cd` para retornar para um PSDrive enviava aos usuários ao local padrão para essa unidade.</span><span class="sxs-lookup"><span data-stu-id="82e14-255">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="82e14-256">Graças a [@mcbobke](https://github.com/mcbobke), os usuários são enviados ao último diretório de trabalho atual conhecido para a sessão.</span><span class="sxs-lookup"><span data-stu-id="82e14-256">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="82e14-257">Aceleradores de tipo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="82e14-257">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="82e14-258">No Windows PowerShell, incluímos os seguintes aceleradores de tipo para facilitar o trabalho com os respectivos tipos:</span><span class="sxs-lookup"><span data-stu-id="82e14-258">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="82e14-259">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="82e14-259">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="82e14-260">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="82e14-260">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="82e14-261">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="82e14-261">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="82e14-262">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="82e14-262">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="82e14-263">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="82e14-263">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="82e14-264">Esses aceleradores de tipo não foram incluídos no PowerShell 6, mas foram incluídos no PowerShell 6.1 em execução no Windows.</span><span class="sxs-lookup"><span data-stu-id="82e14-264">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="82e14-265">Esses tipos são úteis para construir objetos AD e WMI facilmente.</span><span class="sxs-lookup"><span data-stu-id="82e14-265">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="82e14-266">É possível, por exemplo, consultar usando LDAP:</span><span class="sxs-lookup"><span data-stu-id="82e14-266">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="82e14-267">O exemplo a seguir cria um objeto CIM Win32_OperatingSystem:</span><span class="sxs-lookup"><span data-stu-id="82e14-267">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="82e14-268">Esse exemplo retorna um objeto ManagementClass para a classe Win32_OperatingSystem.</span><span class="sxs-lookup"><span data-stu-id="82e14-268">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="82e14-269">Alias `-lp` para todos os parâmetros `-LiteralPath`</span><span class="sxs-lookup"><span data-stu-id="82e14-269">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="82e14-270">Graças a [@kvprasoon](https://github.com/kvprasoon), passamos a ter um alias de parâmetro `-lp` para todos os cmdlets internos do PowerShell que têm um parâmetro `-LiteralPath`.</span><span class="sxs-lookup"><span data-stu-id="82e14-270">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="82e14-271">Alterações da falha</span><span class="sxs-lookup"><span data-stu-id="82e14-271">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="82e14-272">Caminhos de instalação baseada em MSI no Windows</span><span class="sxs-lookup"><span data-stu-id="82e14-272">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="82e14-273">No Windows, o pacote MSI passou a ser instalado neste caminho:</span><span class="sxs-lookup"><span data-stu-id="82e14-273">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="82e14-274">`$env:ProgramFiles\PowerShell\6\` para a instalação estável do 6.x</span><span class="sxs-lookup"><span data-stu-id="82e14-274">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="82e14-275">`$env:ProgramFiles\PowerShell\6-preview\` para a instalação da versão prévia do 6.x</span><span class="sxs-lookup"><span data-stu-id="82e14-275">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="82e14-276">Essa alteração garante que o PowerShell Core possa ser atualizado/atendido pelo Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="82e14-276">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="82e14-277">Para obter mais informações, confira [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="82e14-277">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="82e14-278">A telemetria só pode ser desabilitada com uma variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="82e14-278">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="82e14-279">O PowerShell Core envia dados telemétricos básicos à Microsoft quando é iniciado.</span><span class="sxs-lookup"><span data-stu-id="82e14-279">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="82e14-280">Os dados incluem o nome do sistema operacional, a versão do sistema operacional e a versão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82e14-280">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="82e14-281">Com esses dados, podemos entender melhor os ambientes nos quais o PowerShell é usado, além de priorizar novos recursos e correções.</span><span class="sxs-lookup"><span data-stu-id="82e14-281">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="82e14-282">Para recusar essa telemetria, defina a variável de ambiente `POWERSHELL_TELEMETRY_OPTOUT` para `true`, `yes` ou `1`.</span><span class="sxs-lookup"><span data-stu-id="82e14-282">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="82e14-283">Não damos mais suporte à exclusão do arquivo `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` para desabilitar a telemetria.</span><span class="sxs-lookup"><span data-stu-id="82e14-283">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="82e14-284">Autenticação básica não permitida por HTTP na Comunicação Remota do PowerShell em plataformas Unix</span><span class="sxs-lookup"><span data-stu-id="82e14-284">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="82e14-285">Para evitar o uso de tráfego não criptografado, a Comunicação Remota do PowerShell em plataformas Unix agora exige o uso de NTLM/Negotiate ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="82e14-285">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="82e14-286">Para obter mais informações sobre essas alterações, confira [Problema #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span><span class="sxs-lookup"><span data-stu-id="82e14-286">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="82e14-287">`VisualBasic` removido como linguagem com suporte em Add-Type</span><span class="sxs-lookup"><span data-stu-id="82e14-287">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="82e14-288">No passado, era possível compilar o código do Visual Basic usando o cmdlet `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="82e14-288">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="82e14-289">O Visual Basic raramente era usado com `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="82e14-289">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="82e14-290">Removemos esse recurso para reduzir o tamanho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82e14-290">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="82e14-291">Usos limpos de `CommandTypes.Workflow` e `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="82e14-291">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="82e14-292">Para obter mais informações sobre essas alterações, confira [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="82e14-292">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>
