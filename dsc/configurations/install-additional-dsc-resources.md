---
ms.date: 12/12/2018
keywords: DSC, powershell, recursos, da galeria, instalação
title: Instalar recursos adicionais do DSC
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400293"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="52183-103">Instalar recursos adicionais do DSC</span><span class="sxs-lookup"><span data-stu-id="52183-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="52183-104">PowerShell inclui vários recursos de Out-of-the-box para o Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="52183-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="52183-105">O **PSDesiredStateConfiguration** módulo contém todos os recursos de DSC OOB disponíveis em sua instância específica do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52183-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="52183-106">Esta é uma lista dos recursos OOB incluídos no PowerShell 4.0 e uma descrição dos recursos do recurso.</span><span class="sxs-lookup"><span data-stu-id="52183-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="52183-107">Isso é uma lista incompleta, como o número de recursos OOB cresceu com cada versão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52183-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="52183-108">Recurso</span><span class="sxs-lookup"><span data-stu-id="52183-108">Resource</span></span>  |<span data-ttu-id="52183-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="52183-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="52183-110">**File**</span><span class="sxs-lookup"><span data-stu-id="52183-110">**File**</span></span>|<span data-ttu-id="52183-111">Controla o estado de arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="52183-111">Controls the state of files and directories.</span></span> <span data-ttu-id="52183-112">Copia os arquivos de um **fonte** para um **destino** e as atualiza quando o **fonte** alterações comparando as datas, as somas de verificação e hashes.</span><span class="sxs-lookup"><span data-stu-id="52183-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="52183-113">**Archive**</span><span class="sxs-lookup"><span data-stu-id="52183-113">**Archive**</span></span>|<span data-ttu-id="52183-114">Desempacota os arquivos mortos e um local especificado.</span><span class="sxs-lookup"><span data-stu-id="52183-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="52183-115">Valida os arquivos com o determinado **soma de verificação**.</span><span class="sxs-lookup"><span data-stu-id="52183-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="52183-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="52183-116">**Environment**</span></span>|<span data-ttu-id="52183-117">Gerencia as variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="52183-117">Manages environment variables.</span></span>|
|<span data-ttu-id="52183-118">**Grupo**</span><span class="sxs-lookup"><span data-stu-id="52183-118">**Group**</span></span>|<span data-ttu-id="52183-119">Gerencia grupos locais e controla a associação de grupo.</span><span class="sxs-lookup"><span data-stu-id="52183-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="52183-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="52183-120">**Log**</span></span>|<span data-ttu-id="52183-121">Grava as mensagens para o `Microsoft-Windows-Desired State Configuration/Analytic` log de eventos.</span><span class="sxs-lookup"><span data-stu-id="52183-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="52183-122">**Pacote**</span><span class="sxs-lookup"><span data-stu-id="52183-122">**Package**</span></span>|<span data-ttu-id="52183-123">Instala ou desinstala pacotes usando **argumentos**, **LogPath**, **ReturnCode**, outras configurações.</span><span class="sxs-lookup"><span data-stu-id="52183-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="52183-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="52183-124">**Registry**</span></span>|<span data-ttu-id="52183-125">Gerencia os valores e chaves do registro.</span><span class="sxs-lookup"><span data-stu-id="52183-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="52183-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="52183-126">**Script**</span></span>|<span data-ttu-id="52183-127">Permite que você crie suas próprias [conjunto de teste get](../resources/get-test-set.md) blocos de script.</span><span class="sxs-lookup"><span data-stu-id="52183-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="52183-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="52183-128">**Service**</span></span>|<span data-ttu-id="52183-129">Configura os serviços do Windows.</span><span class="sxs-lookup"><span data-stu-id="52183-129">Configures Windows services.</span></span>|
|<span data-ttu-id="52183-130">**User**</span><span class="sxs-lookup"><span data-stu-id="52183-130">**User**</span></span> |<span data-ttu-id="52183-131">Gerencia usuários locais e atributos.</span><span class="sxs-lookup"><span data-stu-id="52183-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="52183-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="52183-132">**WindowsFeature**</span></span>|<span data-ttu-id="52183-133">Gerencia as funções e recursos.</span><span class="sxs-lookup"><span data-stu-id="52183-133">Manages roles and features.</span></span>|
|<span data-ttu-id="52183-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="52183-134">**WindowsProcess**</span></span>|<span data-ttu-id="52183-135">Configura os processos do Windows.</span><span class="sxs-lookup"><span data-stu-id="52183-135">Configures Windows processes.</span></span>|

<span data-ttu-id="52183-136">Os recursos OOB permitem que um bom ponto de partida para operações comuns.</span><span class="sxs-lookup"><span data-stu-id="52183-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="52183-137">Se os recursos OOB não atender às suas necessidades, você pode escrever seus próprios [recurso personalizado](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="52183-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="52183-138">Antes de escrever um recurso personalizado para resolver seu problema, você deve procurar por meio do grande número de recursos de DSC que já foram criados pela Microsoft e a comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52183-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="52183-139">Você pode encontrar recursos de DSC em ambos os [da Galeria do PowerShell](https://www.powershellgallery.com/) e [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="52183-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="52183-140">Você também pode instalar recursos de DSC diretamente do console do PowerShell usando [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="52183-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="52183-141">Instalando o PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="52183-141">Installing PowerShellGet</span></span>

<span data-ttu-id="52183-142">Para determinar se você já tiver **PowerShell** obter ou para obter ajuda para instalá-lo, consulte o guia a seguir: [Instalando o PowerShellGet](/powershell/gallery/installing-psget)</span><span class="sxs-lookup"><span data-stu-id="52183-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="52183-143">Localizar recursos de DSC usando o PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="52183-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="52183-144">Uma vez **PowerShellGet** é instalado em seu sistema, você pode localizar e instalar os recursos de DSC hospedados na [Galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="52183-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="52183-145">Primeiro, use o [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet para localizar recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="52183-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="52183-146">Quando você executa `Find-DSCResource` pela primeira vez, você verá o seguinte prompt para instalar o provedor do NuGet"".</span><span class="sxs-lookup"><span data-stu-id="52183-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="52183-147">Depois de pressionar 'y', o provedor "NuGet" é instalado, você ver uma lista de recursos de DSC que podem ser instalados da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52183-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="52183-148">Lista não é mostrada porque ela é muito grande.</span><span class="sxs-lookup"><span data-stu-id="52183-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="52183-149">Você também pode especificar o `-Name` parâmetro usando caracteres curinga, ou `-Filter` parâmetro sem caracteres curinga para restringir sua pesquisa.</span><span class="sxs-lookup"><span data-stu-id="52183-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="52183-150">Este exemplo tenta localizar um recurso de "Fuso horário" DSC usando caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="52183-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52183-151">Atualmente, há um bug na `Find-DSCResource` cmdlet que impeça o uso de curingas em ambos os `-Name` e `-Filter` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="52183-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="52183-152">O segundo exemplo abaixo mostra uma solução alternativa usando `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="52183-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="52183-153">Você também pode usar `Where-Object` para encontrar recursos DSC com filtragem mais granular.</span><span class="sxs-lookup"><span data-stu-id="52183-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="52183-154">Essa abordagem será mais lenta do que usando incorporado em parâmetros de filtragem.</span><span class="sxs-lookup"><span data-stu-id="52183-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="52183-155">Para obter mais informações sobre filtragem, consulte [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="52183-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="52183-156">Instalar recursos de DSC usando PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="52183-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="52183-157">Para instalar um recurso de DSC, use o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, especificando o nome do módulo mostrado sob **módulo** nome nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="52183-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="52183-158">O recurso de "Fuso horário" existe no módulo "ComputerManagementDSC", é assim que o módulo Este exemplo instala.</span><span class="sxs-lookup"><span data-stu-id="52183-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="52183-159">Se você não confiar na Galeria do PowerShell, você verá o aviso abaixo que pede confirmação, e instruindo como evitar avisos subsequentes em que você instala.</span><span class="sxs-lookup"><span data-stu-id="52183-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="52183-160">Pressione 'y' para continuar a instalação do módulo.</span><span class="sxs-lookup"><span data-stu-id="52183-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="52183-161">Após a instalação, verifique se o novo recurso é instalado usando [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="52183-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="52183-162">Você também pode exibir outros recursos em seu módulo recém-instalado, especificando o `-ModuleName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="52183-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="52183-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52183-163">See also</span></span>

- [<span data-ttu-id="52183-164">O que são recursos?</span><span class="sxs-lookup"><span data-stu-id="52183-164">What are Resources?</span></span>](../resources/resources.md)
