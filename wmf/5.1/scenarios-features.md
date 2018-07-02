---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,instalação
title: Novos cenários e recursos no WMF 5.1
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: 50b66cada6943784b8d3c103cebc3c1e3e286a16
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37090356"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="06b7a-103">Novos cenários e recursos no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="06b7a-103">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="06b7a-104">Observação: essas informações são preliminares e estão sujeitas a alteração.</span><span class="sxs-lookup"><span data-stu-id="06b7a-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="06b7a-105">Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="06b7a-105">PowerShell Editions</span></span>

<span data-ttu-id="06b7a-106">A partir da versão 5.1, o PowerShell está disponível em diferentes edições que denotam os vários conjuntos de recursos e compatibilidades de plataforma.</span><span class="sxs-lookup"><span data-stu-id="06b7a-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="06b7a-107">**Desktop Edition:** criada no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows, como Server Core e Área de Trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="06b7a-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="06b7a-108">**Core Edition:** criada no .NET Core e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell executando em edições de superfície reduzida do Windows, como o Nano Server e Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="06b7a-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="06b7a-109">**Saiba mais sobre como usar as edições do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="06b7a-109">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="06b7a-110">Determinar a edição em execução do PowerShell usando $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="06b7a-110">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="06b7a-111">Filtrar resultados de Get-Module por CompatiblePSEditions usando o parâmetro PSEdition</span><span class="sxs-lookup"><span data-stu-id="06b7a-111">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="06b7a-112">Impedir a execução do script, a menos que seja ele executado em uma edição compatível do PowerShell</span><span class="sxs-lookup"><span data-stu-id="06b7a-112">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="06b7a-113">Declarar a compatibilidade de um módulo para versões específicas do PowerShell</span><span class="sxs-lookup"><span data-stu-id="06b7a-113">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a><span data-ttu-id="06b7a-114">Cmdlets de Catálogo</span><span class="sxs-lookup"><span data-stu-id="06b7a-114">Catalog Cmdlets</span></span>

<span data-ttu-id="06b7a-115">Dois novos cmdlets foram adicionados no módulo [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security); eles geram e validam os arquivos de catálogo do Windows.</span><span class="sxs-lookup"><span data-stu-id="06b7a-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; these generate and validate Windows catalog files.</span></span>

### <a name="new-filecatalog"></a><span data-ttu-id="06b7a-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="06b7a-116">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="06b7a-117">New-FileCatalog cria um arquivo de catálogo do Windows para o conjunto de arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="06b7a-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="06b7a-118">Este arquivo de catálogo contém hashes para todos os arquivos nos caminhos especificados.</span><span class="sxs-lookup"><span data-stu-id="06b7a-118">This catalog file contains hashes for all files in specified paths.</span></span>
<span data-ttu-id="06b7a-119">Os usuários podem distribuir o conjunto de pastas juntamente com o arquivo de catálogo correspondente que representa essas pastas.</span><span class="sxs-lookup"><span data-stu-id="06b7a-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span>
<span data-ttu-id="06b7a-120">Essas informações são úteis para validar se as alterações foram feitas nas pastas desde a hora de criação do catálogo.</span><span class="sxs-lookup"><span data-stu-id="06b7a-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="06b7a-121">Há suporte para as versões 1 e 2 do catálogo.</span><span class="sxs-lookup"><span data-stu-id="06b7a-121">Catalog versions 1 and 2 are supported.</span></span>
<span data-ttu-id="06b7a-122">A versão 1 usa o algoritmo de hash SHA1 para criar hashes de arquivo; a versão 2 usa SHA256.</span><span class="sxs-lookup"><span data-stu-id="06b7a-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span>
<span data-ttu-id="06b7a-123">Não há suporte para a versão 2 do catálogo no *Windows Server 2008 R2* ou no *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="06b7a-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span>
<span data-ttu-id="06b7a-124">Você deve usar a versão 2 do catálogo no *Windows 8*, no *Windows Server 2012* e nos sistemas operacionais posteriores.</span><span class="sxs-lookup"><span data-stu-id="06b7a-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="06b7a-125">Isso cria o arquivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="06b7a-125">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="06b7a-126">Para verificar a integridade do arquivo de catálogo (Pester.cat, no exemplo acima), assine-o usando o cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature).</span><span class="sxs-lookup"><span data-stu-id="06b7a-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span></span>

### <a name="test-filecatalog"></a><span data-ttu-id="06b7a-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="06b7a-127">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="06b7a-128">Test-FileCatalog valida o catálogo que representa um conjunto de pastas.</span><span class="sxs-lookup"><span data-stu-id="06b7a-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="06b7a-129">Este cmdlet compara todos os hashes de arquivos e seus caminhos relativos encontrados no *catálogo* com aqueles no *disco*.</span><span class="sxs-lookup"><span data-stu-id="06b7a-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span>
<span data-ttu-id="06b7a-130">Se detectar qualquer incompatibilidade entre os hashes e os caminhos de arquivo, o status será retornado como *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="06b7a-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span>
<span data-ttu-id="06b7a-131">Os usuários podem recuperar todas essas informações usando o parâmetro *-Detailed*.</span><span class="sxs-lookup"><span data-stu-id="06b7a-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span>
<span data-ttu-id="06b7a-132">Ele também exibe o status da assinatura do catálogo na propriedade *Signature*, que é equivalente a chamar o cmdlet [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) no arquivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="06b7a-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet on the catalog file.</span></span>
<span data-ttu-id="06b7a-133">Os usuários também podem ignorar qualquer arquivo durante a validação usando o parâmetro *-FilesToSkip*.</span><span class="sxs-lookup"><span data-stu-id="06b7a-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

## <a name="module-analysis-cache"></a><span data-ttu-id="06b7a-134">Cache de análise do módulo</span><span class="sxs-lookup"><span data-stu-id="06b7a-134">Module Analysis Cache</span></span>

<span data-ttu-id="06b7a-135">Do WMF 5.1 em diante, o PowerShell fornece controle sobre o arquivo que é usado para cache de dados sobre um módulo, como os comandos que exporta.</span><span class="sxs-lookup"><span data-stu-id="06b7a-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="06b7a-136">Por padrão, esse cache é armazenado no arquivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="06b7a-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="06b7a-137">O cache normalmente é lido na inicialização ao procurar um comando e é gravado em um thread em segundo plano em algum momento após a importação de um módulo.</span><span class="sxs-lookup"><span data-stu-id="06b7a-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="06b7a-138">Para alterar o local padrão do cache, defina a variável de ambiente `$env:PSModuleAnalysisCachePath` antes de iniciar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06b7a-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span>
<span data-ttu-id="06b7a-139">As alterações a esta variável de ambiente afetarão apenas processos filhos.</span><span class="sxs-lookup"><span data-stu-id="06b7a-139">Changes to this environment variable will only affect children processes.</span></span>
<span data-ttu-id="06b7a-140">O valor deve nomear um caminho completo (incluindo nome do arquivo) em que o PowerShell tenha permissão para criar e gravar arquivos.</span><span class="sxs-lookup"><span data-stu-id="06b7a-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>
<span data-ttu-id="06b7a-141">Para desabilitar o cache de arquivo, defina esse valor para um local inválido, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="06b7a-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="06b7a-142">Isso define o caminho para um dispositivo inválido.</span><span class="sxs-lookup"><span data-stu-id="06b7a-142">This sets the path to an invalid device.</span></span>
<span data-ttu-id="06b7a-143">Se o PowerShell não conseguir gravar no caminho, nenhum erro será retornado, mas você poderá ver relatórios de erro usando um rastreamento:</span><span class="sxs-lookup"><span data-stu-id="06b7a-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="06b7a-144">Ao gravar o cache, o PowerShell verificará se há módulos que não existem mais para evitar um cache desnecessariamente grande.</span><span class="sxs-lookup"><span data-stu-id="06b7a-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="06b7a-145">Às vezes, essas verificações não são desejáveis, o que, nesse caso, você pode desativá-las configurando:</span><span class="sxs-lookup"><span data-stu-id="06b7a-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="06b7a-146">Definir essa variável de ambiente entrará em vigor imediatamente no processo atual.</span><span class="sxs-lookup"><span data-stu-id="06b7a-146">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="06b7a-147">Especificando a versão do módulo</span><span class="sxs-lookup"><span data-stu-id="06b7a-147">Specifying module version</span></span>

<span data-ttu-id="06b7a-148">No WMF 5.1, o `using module` comporta-se da mesma maneira que outras construções relacionadas ao módulo no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06b7a-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="06b7a-149">Anteriormente, não era possível especificar uma versão de módulo específica; se houvesse várias versões presentes, isso resultaria em um erro.</span><span class="sxs-lookup"><span data-stu-id="06b7a-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="06b7a-150">No WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="06b7a-150">In WMF 5.1:</span></span>

- <span data-ttu-id="06b7a-151">Você pode usar o [Construtor ModuleSpecification (tabela de hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="06b7a-151">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="06b7a-152">Essa tabela de hash tem o mesmo formato que `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="06b7a-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="06b7a-153">**Exemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="06b7a-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="06b7a-154">Se houver várias versões do módulo, o PowerShell usará a **mesma lógica de resolução** que `Import-Module` e não retornará um erro – o mesmo comportamento que `Import-Module` e `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="06b7a-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="06b7a-155">Melhorias no Pester</span><span class="sxs-lookup"><span data-stu-id="06b7a-155">Improvements to Pester</span></span>

<span data-ttu-id="06b7a-156">No WMF 5.1, a versão do Pester fornecida com o PowerShell foi atualizada do 3.3.5 para 3.4.0, com a adição da confirmação https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, que permite um comportamento melhor do Pester no Nano Server.</span><span class="sxs-lookup"><span data-stu-id="06b7a-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="06b7a-157">Você pode revisar as alterações nas versões 3.3.5 a 3.4.0 inspecionando o arquivo ChangeLog.md em: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="06b7a-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>
