---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,instalação
contributor: jianyunt, quoctruong
title: Melhorias ao Gerenciamento de Pacotes do WMF 5.1
ms.openlocfilehash: 30ef59ed9dc0d56636d85cc6e53523a9a73963a4
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794273"
---
# <a name="improvements-to-package-management-in-wmf-51"></a><span data-ttu-id="ecdd6-103">Melhorias ao Gerenciamento de Pacotes do WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="ecdd6-103">Improvements to Package Management in WMF 5.1</span></span>

## <a name="improvements-in-packagemanagement"></a><span data-ttu-id="ecdd6-104">Melhorias ao PackageManagement</span><span class="sxs-lookup"><span data-stu-id="ecdd6-104">Improvements in PackageManagement</span></span>

<span data-ttu-id="ecdd6-105">Veja a seguir as correções feitas no WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="ecdd6-105">The following are the fixes made in the WMF 5.1:</span></span>

### <a name="version-alias"></a><span data-ttu-id="ecdd6-106">Alias de versão</span><span class="sxs-lookup"><span data-stu-id="ecdd6-106">Version Alias</span></span>

<span data-ttu-id="ecdd6-107">**Cenário**: se tiver as versões 1.0 e 2.0 de um pacote, P1, instaladas em seu sistema e desejar desinstalar a versão 1.0, você executará `Uninstall-Package -Name P1 -Version 1.0` e esperará a versão 1.0 ser desinstalada após a execução do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-107">**Scenario**: If you have version 1.0 and 2.0 of a package, P1, installed on your system, and you want to uninstall version 1.0, you would run `Uninstall-Package -Name P1 -Version 1.0` and expect version 1.0 to be uninstalled after running the cmdlet.</span></span> <span data-ttu-id="ecdd6-108">No entanto o resultado é que a versão 2.0 é desinstalada.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-108">However the result is that version 2.0 gets uninstalled.</span></span>

<span data-ttu-id="ecdd6-109">Isso ocorre porque o parâmetro `-Version` é um alias do parâmetro `-MinimumVersion`.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-109">This occurs because the `-Version` parameter is an alias of the `-MinimumVersion` parameter.</span></span> <span data-ttu-id="ecdd6-110">Quando PackageManagement está procurando um pacote qualificado com a versão mínima de 1.0, ele retorna a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-110">When PackageManagement is looking for a qualified package with the minimum version of 1.0, it returns the latest version.</span></span> <span data-ttu-id="ecdd6-111">Esse comportamento é esperado em casos normais, pois encontrar a versão mais recente é geralmente o resultado desejado.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-111">This behavior is expected in normal cases because finding the latest version is usually the desired result.</span></span> <span data-ttu-id="ecdd6-112">No entanto, ele não deve se aplicar ao caso de `Uninstall-Package`.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-112">However, it should not apply to the `Uninstall-Package` case.</span></span>

<span data-ttu-id="ecdd6-113">**Solução**: alias `-Version` removido inteiramente em PackageManagement (também conhecido como</span><span class="sxs-lookup"><span data-stu-id="ecdd6-113">**Solution**:removed `-Version` alias entirely in PackageManagement (a.k.a.</span></span> <span data-ttu-id="ecdd6-114">OneGet) e PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-114">OneGet) and PowerShellGet.</span></span>

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a><span data-ttu-id="ecdd6-115">Vários prompts para inicializar o provedor do NuGet</span><span class="sxs-lookup"><span data-stu-id="ecdd6-115">Multiple prompts for bootstrapping the NuGet provider</span></span>

<span data-ttu-id="ecdd6-116">**Cenário**: ao executar `Find-Module` ou `Install-Module` ou outros cmdlets PackageManagement em seu computador pela primeira vez, PackageManagement tenta inicializar o provedor de NuGet.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-116">**Scenario**: When you run `Find-Module` or `Install-Module` or other PackageManagement cmdlets on your computer for the first time, PackageManagement tries to bootstrap the NuGet provider.</span></span> <span data-ttu-id="ecdd6-117">Isso ocorre porque o provedor PowerShellGet também usa o provedor do NuGet para baixar os módulos do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-117">It does this because the PowerShellGet provider also uses the NuGet provider to download PowerShell modules.</span></span> <span data-ttu-id="ecdd6-118">Depois, o PackageManagement solicita permissão do usuário para instalar o provedor de NuGet.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-118">PackageManagement then prompts the user for permission to install the NuGet provider.</span></span> <span data-ttu-id="ecdd6-119">Após o usuário selecionar "sim" para a inicialização, a versão mais recente do provedor do NuGet será instalada.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-119">After the user selects "yes" for the bootstrapping, the latest version of the NuGet provider will be installed.</span></span>

<span data-ttu-id="ecdd6-120">No entanto, em alguns casos, quando há uma versão antiga do provedor de NuGet instalada em seu computador, a versão mais antiga do NuGet às vezes é carregada primeiro na sessão do PowerShell (ou seja, a condição de corrida no PackageManagement).</span><span class="sxs-lookup"><span data-stu-id="ecdd6-120">However, in some cases, when you have an old version of NuGet provider installed on your computer, the older version of NuGet sometimes gets loaded first into the PowerShell session (that's the race condition in PackageManagement).</span></span> <span data-ttu-id="ecdd6-121">No entanto, o PowerShellGet requer a versão mais recente do provedor de NuGet para funcionar, portanto, o PowerShellGet solicita que o PackageManagement inicialize o provedor de NuGet novamente.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-121">However PowerShellGet requires the later version of the NuGet provider to work, so PowerShellGet asks PackageManagement to bootstrap the NuGet provider again.</span></span> <span data-ttu-id="ecdd6-122">Isso resulta em vários prompts para inicializar o provedor do NuGet.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-122">This results in multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="ecdd6-123">**Solução**: no WMF 5.1, PackageManagement carrega a versão mais recente do provedor de NuGet para evitar vários prompts para inicialização do provedor de NuGet.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-123">**Solution**: In WMF5.1, PackageManagement loads the latest version of the NuGet provider to avoid multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="ecdd6-124">Você também pode utilizar uma solução alternativa para esse problema excluindo manualmente a versão antiga do provedor do NuGet (NuGet Anycpu.exe), caso ele exista, de $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span><span class="sxs-lookup"><span data-stu-id="ecdd6-124">You could also work around this issue by manually deleting the old version of the NuGet provider (NuGet-Anycpu.exe) if exists from $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span></span>


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a><span data-ttu-id="ecdd6-125">Suporte para PackageManagement em computadores somente com acesso à intranet</span><span class="sxs-lookup"><span data-stu-id="ecdd6-125">Support for PackageManagement on computers with Intranet access only</span></span>

<span data-ttu-id="ecdd6-126">**Cenário**: para o cenário empresarial, as pessoas estão trabalhando em um ambiente em que não há acesso à Internet, somente à intranet.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-126">**Scenario**: For the enterprise scenario, people are working under an environment where there is no Internet access but Intranet only.</span></span> <span data-ttu-id="ecdd6-127">O PackageManagement não dava suporte a esse caso no WMF 5.0.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-127">PackageManagement did not support this case in WMF 5.0.</span></span>

<span data-ttu-id="ecdd6-128">**Cenário**: no WMF 5.0, PackageManagement não dava suporte a computadores com acesso somente à intranet (e não à Internet).</span><span class="sxs-lookup"><span data-stu-id="ecdd6-128">**Scenario**: In WMF 5.0, PackageManagement did not support computers that have only Intranet (but not Internet) access.</span></span>

<span data-ttu-id="ecdd6-129">**Solução**: no WMF 5.1, você pode seguir estas etapas para permitir que computadores com intranet usem o PackageManagement:</span><span class="sxs-lookup"><span data-stu-id="ecdd6-129">**Solution**: In WMF 5.1, you can follow these steps to allow Intranet computers to use PackageManagement:</span></span>

1. <span data-ttu-id="ecdd6-130">Baixe o provedor de NuGet usando outro computador que tenha conexão com a Internet usando `Install-PackageProvider -Name NuGet`.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-130">Download the NuGet provider using another computer that has an Internet connection by using `Install-PackageProvider -Name NuGet`.</span></span>

2. <span data-ttu-id="ecdd6-131">Localize o provedor de NuGet em `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` ou `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-131">Find the NuGet provider under either `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget`  or  `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span></span>

3. <span data-ttu-id="ecdd6-132">Copie os binários para um local de compartilhamento de rede ou pasta que o computador com intranet possa acessar e, em seguida, instale o provedor de NuGet com `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-132">Copy the binaries to a folder or network share location that the Intranet computer can access, and then install the NuGet provider with `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span></span>


### <a name="event-logging-improvements"></a><span data-ttu-id="ecdd6-133">Aprimoramentos de registro em log de eventos</span><span class="sxs-lookup"><span data-stu-id="ecdd6-133">Event logging improvements</span></span>

<span data-ttu-id="ecdd6-134">Quando você instala pacotes, está alterando o estado do computador.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-134">When you install packages, you are changing the state of the computer.</span></span> <span data-ttu-id="ecdd6-135">No WMF 5.1, o PackageManagement agora registra eventos no log de eventos do Windows para atividades `Install-Package`, `Uninstall-Package` e `Save-Package`.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-135">In WMF 5.1, PackageManagement now logs events to the Windows event log for `Install-Package`, `Uninstall-Package`, and `Save-Package` activities.</span></span> <span data-ttu-id="ecdd6-136">O log de eventos é o mesmo do PowerShell, ou seja, `Microsoft-Windows-PowerShell, Operational`.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-136">The Event log  is the same as for PowerShell, that is, `Microsoft-Windows-PowerShell, Operational`.</span></span>

### <a name="support-for-basic-authentication"></a><span data-ttu-id="ecdd6-137">Suporte para autenticação básica</span><span class="sxs-lookup"><span data-stu-id="ecdd6-137">Support for basic authentication</span></span>

<span data-ttu-id="ecdd6-138">No WMF 5.1, o PackageManagement dá suporte para localizar e instalar pacotes de um repositório que requer autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-138">In WMF 5.1, PackageManagement supports finding and installing packages from a repository that requires basic authentication.</span></span> <span data-ttu-id="ecdd6-139">Você pode fornecer suas credenciais para os cmdlets `Find-Package` e `Install-Package`.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-139">You can supply your credentials to the `Find-Package` and `Install-Package` cmdlets.</span></span> <span data-ttu-id="ecdd6-140">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ecdd6-140">For example:</span></span>

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

### <a name="support-for-using-packagemanagement-behind-a-proxy"></a><span data-ttu-id="ecdd6-141">Suporte para usar o PackageManagement atrás de um proxy</span><span class="sxs-lookup"><span data-stu-id="ecdd6-141">Support for using PackageManagement behind a proxy</span></span>

<span data-ttu-id="ecdd6-142">No WMF 5.1, agora o PackageManagement leva novos parâmetros de proxy `-ProxyCredential` e `-Proxy`.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-142">In WMF 5.1, PackageManagement now takes new proxy parameters `-ProxyCredential` and `-Proxy`.</span></span> <span data-ttu-id="ecdd6-143">Usando esses parâmetros, você pode especificar a URL do proxy e as credenciais para cmdlets do PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-143">Using these parameters, you can specify the proxy URL and credentials to PackageManagement cmdlets.</span></span> <span data-ttu-id="ecdd6-144">Por padrão, as configurações de proxy do sistema são usadas.</span><span class="sxs-lookup"><span data-stu-id="ecdd6-144">By default, system proxy settings are used.</span></span> <span data-ttu-id="ecdd6-145">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ecdd6-145">For example:</span></span>

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
