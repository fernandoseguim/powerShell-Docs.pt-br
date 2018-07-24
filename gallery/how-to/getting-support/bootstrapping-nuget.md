---
ms.date: 06/12/2017
contributor: manikb
keywords: galeria,powershell,cmdlet,psget
title: Inicializando o NuGet
ms.openlocfilehash: 2d321097fda201c0d8f843b2194a161eceabe4e1
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094010"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="e385b-103">Inicializar o provedor do NuGet e o NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="e385b-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="e385b-104">O NuGet.exe não está incluído no provedor do NuGet mais recente.</span><span class="sxs-lookup"><span data-stu-id="e385b-104">NuGet.exe is not included in the latest NuGet provider.</span></span>
<span data-ttu-id="e385b-105">Para operações de publicação de um módulo ou um de script, o PowerShellGet requer o NuGet.exe executável binário.</span><span class="sxs-lookup"><span data-stu-id="e385b-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span>
<span data-ttu-id="e385b-106">Somente o provedor do NuGet é necessário para todas as outras operações, incluindo *localizar*, *instalar*, *salvar* e *desinstalar*.</span><span class="sxs-lookup"><span data-stu-id="e385b-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="e385b-107">O PowerShellGet inclui a lógica para tratar a inicialização combinada do provedor do NuGet e do NuGet.exe ou a inicialização apenas do provedor do NuGet.</span><span class="sxs-lookup"><span data-stu-id="e385b-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span>
<span data-ttu-id="e385b-108">Em ambos os casos, apenas uma única mensagem de aviso deve ocorrer.</span><span class="sxs-lookup"><span data-stu-id="e385b-108">In either case, only a single prompt message should occur.</span></span>
<span data-ttu-id="e385b-109">Se o computador não estiver conectado à Internet, o usuário ou um administrador deverá copiar uma instância confiável do provedor do NuGet e/ou o arquivo NuGet.exe no computador desconectado.</span><span class="sxs-lookup"><span data-stu-id="e385b-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="e385b-110">A partir da versão 6, o provedor do NuGet é incluído na instalação do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e385b-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span> [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="e385b-111">Resolvendo erro quando o provedor do NuGet não for instalado em um computador conectado à Internet</span><span class="sxs-lookup"><span data-stu-id="e385b-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="e385b-112">Resolvendo erro quando o provedor do NuGet está disponível e o NuGet.exe não está disponível durante a operação de publicação em um computador conectado à Internet</span><span class="sxs-lookup"><span data-stu-id="e385b-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="e385b-113">Resolução de erro quando o provedor do NuGet e o NuGet.exe não estão disponíveis durante a operação de publicação em um computador conectado à Internet</span><span class="sxs-lookup"><span data-stu-id="e385b-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="e385b-114">Inicializando manualmente o provedor do NuGet em um computador que não está conectado à Internet</span><span class="sxs-lookup"><span data-stu-id="e385b-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="e385b-115">Os processos demonstrados acima pressupõem que o computador está conectado à Internet e pode baixar arquivos de um local público.</span><span class="sxs-lookup"><span data-stu-id="e385b-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span>
<span data-ttu-id="e385b-116">Se isso não for possível, a única opção será inicializar um computador com os processos descritos acima e copiar manualmente o provedor para o nó isolado por meio de um processo confiável offline.</span><span class="sxs-lookup"><span data-stu-id="e385b-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span>
<span data-ttu-id="e385b-117">O caso de uso mais comum para esse cenário é quando uma galeria privada está disponível para dar suporte a um ambiente isolado.</span><span class="sxs-lookup"><span data-stu-id="e385b-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="e385b-118">Depois de seguir o processo acima para inicializar um computador conectado à Internet, você encontrará os arquivos do provedor no local:</span><span class="sxs-lookup"><span data-stu-id="e385b-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

<span data-ttu-id="e385b-119">A estrutura de pasta/arquivo do provedor do NuGet será (possivelmente com um número de versão diferente):</span><span class="sxs-lookup"><span data-stu-id="e385b-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="e385b-120">Copie essas pastas e arquivos para os computadores offline usando um processo confiável.</span><span class="sxs-lookup"><span data-stu-id="e385b-120">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="e385b-121">Inicializando manualmente o NuGet.exe para dar suporte a operações de publicação em um computador que não está conectado à Internet</span><span class="sxs-lookup"><span data-stu-id="e385b-121">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="e385b-122">Além de processo para inicializar manualmente o provedor do NuGet, se o computador for usado para publicar scripts ou módulos em uma galeria privada usando os cmdlets `Publish-Module` ou `Publish-Script`, o arquivo executável binário NuGet.exe será necessário.</span><span class="sxs-lookup"><span data-stu-id="e385b-122">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="e385b-123">O caso de uso mais comum para esse cenário é quando uma galeria privada está disponível para dar suporte a um ambiente isolado.</span><span class="sxs-lookup"><span data-stu-id="e385b-123">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>
<span data-ttu-id="e385b-124">Há duas opções para obter o arquivo NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="e385b-124">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="e385b-125">Uma opção é inicializar um computador que esteja conectado à Internet e copiar os arquivos para os computadores offline usando um processo confiável.</span><span class="sxs-lookup"><span data-stu-id="e385b-125">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span>
<span data-ttu-id="e385b-126">Após inicializar o computador conectado à Internet, o binário NuGet.exe estará localizado em uma das duas pastas:</span><span class="sxs-lookup"><span data-stu-id="e385b-126">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="e385b-127">Se os cmdlets `Publish-Module` ou `Publish-Script` foram executados com permissões elevadas (como um administrador):</span><span class="sxs-lookup"><span data-stu-id="e385b-127">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="e385b-128">Se os cmdlets foram executados como um usuário sem permissões elevadas:</span><span class="sxs-lookup"><span data-stu-id="e385b-128">If the cmdlets were executed as a user without elevated permissions:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="e385b-129">Uma segunda opção é fazer o download do NuGet.exe do site NuGet.Org: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) Ao selecionar uma versão NugGet para computadores de produção, verifique se ela é posterior à 2.8.5.208 e identifique a versão rotulada como "recomendada".</span><span class="sxs-lookup"><span data-stu-id="e385b-129">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span>
<span data-ttu-id="e385b-130">Lembre-se de desbloquear o arquivo se ele tiver sido baixado usando um navegador.</span><span class="sxs-lookup"><span data-stu-id="e385b-130">Remember to unblock the file if it was downloaded using a browser.</span></span>
<span data-ttu-id="e385b-131">Isso pode ser feito usando o cmdlet `Unblock-File`.</span><span class="sxs-lookup"><span data-stu-id="e385b-131">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="e385b-132">Em ambos os casos, o arquivo NuGet.exe pode ser copiado para qualquer local em `$env:path`, mas os locais padrão são:</span><span class="sxs-lookup"><span data-stu-id="e385b-132">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

<span data-ttu-id="e385b-133">Para disponibilizar o executável para que todos os usuários possam usar os cmdlets `Publish-Module` e `Publish-Script`:</span><span class="sxs-lookup"><span data-stu-id="e385b-133">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="e385b-134">Para disponibilizar o executável para apenas um usuário específico, copie para o local apenas dentro desse perfil de usuário:</span><span class="sxs-lookup"><span data-stu-id="e385b-134">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```