
---
<span data-ttu-id="f3f06-101">ms.date: 12/06/2017 colaborador: manikb ms.topic: palavras-chave de referência: galeria,powershell,cmdlet, título psget: Inicializando o NuGet</span><span class="sxs-lookup"><span data-stu-id="f3f06-101">ms.date :  06/12/2017 contributor:  manikb ms.topic:  reference keywords:  gallery,powershell,cmdlet,psget title:  Bootstrapping NuGet</span></span>
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="f3f06-102">Inicializar o provedor do NuGet e o NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="f3f06-102">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="f3f06-103">O NuGet.exe não está incluído no provedor do NuGet mais recente.</span><span class="sxs-lookup"><span data-stu-id="f3f06-103">NuGet.exe is not included in the latest NuGet provider.</span></span>
<span data-ttu-id="f3f06-104">Para operações de publicação de um módulo ou um de script, o PowerShellGet requer o NuGet.exe executável binário.</span><span class="sxs-lookup"><span data-stu-id="f3f06-104">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span>
<span data-ttu-id="f3f06-105">Somente o provedor do NuGet é necessário para todas as outras operações, incluindo *localizar*, *instalar*, *salvar* e *desinstalar*.</span><span class="sxs-lookup"><span data-stu-id="f3f06-105">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="f3f06-106">O PowerShellGet inclui a lógica para tratar a inicialização combinada do provedor do NuGet e do NuGet.exe ou a inicialização apenas do provedor do NuGet.</span><span class="sxs-lookup"><span data-stu-id="f3f06-106">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span>
<span data-ttu-id="f3f06-107">Em ambos os casos, apenas uma única mensagem de aviso deve ocorrer.</span><span class="sxs-lookup"><span data-stu-id="f3f06-107">In either case, only a single prompt message should occur.</span></span>
<span data-ttu-id="f3f06-108">Se o computador não estiver conectado à Internet, o usuário ou um administrador deverá copiar uma instância confiável do provedor do NuGet e/ou o arquivo NuGet.exe no computador desconectado.</span><span class="sxs-lookup"><span data-stu-id="f3f06-108">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

><span data-ttu-id="f3f06-109">**Observação**: a partir da versão 6, o provedor do NuGet é incluído na instalação do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3f06-109">**Note**: Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span> [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="f3f06-110">Resolvendo erro quando o provedor do NuGet não for instalado em um computador conectado à Internet</span><span class="sxs-lookup"><span data-stu-id="f3f06-110">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="f3f06-111">Resolvendo erro quando o provedor do NuGet está disponível e o NuGet.exe não está disponível durante a operação de publicação em um computador conectado à Internet</span><span class="sxs-lookup"><span data-stu-id="f3f06-111">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="f3f06-112">Resolução de erro quando o provedor do NuGet e o NuGet.exe não estão disponíveis durante a operação de publicação em um computador conectado à Internet</span><span class="sxs-lookup"><span data-stu-id="f3f06-112">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

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

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="f3f06-113">Inicializando manualmente o provedor do NuGet em um computador que não está conectado à Internet</span><span class="sxs-lookup"><span data-stu-id="f3f06-113">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="f3f06-114">Os processos demonstrados acima pressupõem que o computador está conectado à Internet e pode baixar arquivos de um local público.</span><span class="sxs-lookup"><span data-stu-id="f3f06-114">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span>
<span data-ttu-id="f3f06-115">Se isso não for possível, a única opção será inicializar um computador com os processos descritos acima e copiar manualmente o provedor para o nó isolado por meio de um processo confiável offline.</span><span class="sxs-lookup"><span data-stu-id="f3f06-115">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span>
<span data-ttu-id="f3f06-116">O caso de uso mais comum para esse cenário é quando uma galeria privada está disponível para dar suporte a um ambiente isolado.</span><span class="sxs-lookup"><span data-stu-id="f3f06-116">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="f3f06-117">Depois de seguir o processo acima para inicializar um computador conectado à Internet, você encontrará os arquivos do provedor no local:</span><span class="sxs-lookup"><span data-stu-id="f3f06-117">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

<span data-ttu-id="f3f06-118">A estrutura de pasta/arquivo do provedor do NuGet será (possivelmente com um número de versão diferente):</span><span class="sxs-lookup"><span data-stu-id="f3f06-118">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

<span data-ttu-id="f3f06-119">NuGet</span><span class="sxs-lookup"><span data-stu-id="f3f06-119">NuGet</span></span><br>
<span data-ttu-id="f3f06-120">--2.8.5.208</span><span class="sxs-lookup"><span data-stu-id="f3f06-120">--2.8.5.208</span></span><br>
<span data-ttu-id="f3f06-121">----Microsoft.PackageManagement.NuGetProvider.dll</span><span class="sxs-lookup"><span data-stu-id="f3f06-121">----Microsoft.PackageManagement.NuGetProvider.dll</span></span>

<span data-ttu-id="f3f06-122">Copie essas pastas e arquivos para os computadores offline usando um processo confiável.</span><span class="sxs-lookup"><span data-stu-id="f3f06-122">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="f3f06-123">Inicializando manualmente o NuGet.exe para dar suporte a operações de publicação em um computador que não está conectado à Internet</span><span class="sxs-lookup"><span data-stu-id="f3f06-123">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="f3f06-124">Além de processo para inicializar manualmente o provedor do NuGet, se o computador for usado para publicar scripts ou módulos em uma galeria privada usando os cmdlets *Publish-Module* ou *Publish-Script*, o arquivo executável binário NuGet.exe será necessário.</span><span class="sxs-lookup"><span data-stu-id="f3f06-124">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the *Publish-Module* or *Publish-Script* cmdlets, the NuGet.exe binary executable file will be required.</span></span>
<span data-ttu-id="f3f06-125">O caso de uso mais comum para esse cenário é quando uma galeria privada está disponível para dar suporte a um ambiente isolado.</span><span class="sxs-lookup"><span data-stu-id="f3f06-125">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>
<span data-ttu-id="f3f06-126">Há duas opções para obter o arquivo NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="f3f06-126">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="f3f06-127">Uma opção é inicializar um computador que esteja conectado à Internet e copiar os arquivos para os computadores offline usando um processo confiável.</span><span class="sxs-lookup"><span data-stu-id="f3f06-127">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span>
<span data-ttu-id="f3f06-128">Após inicializar o computador conectado à Internet, o binário NuGet.exe estará localizado em uma das duas pastas:</span><span class="sxs-lookup"><span data-stu-id="f3f06-128">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="f3f06-129">Se os cmdlets *Publish-Module* ou *Publish-Script* foram executados com permissões elevadas (como um administrador):</span><span class="sxs-lookup"><span data-stu-id="f3f06-129">If the *Publish-Module* or *Publish-Script* cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="f3f06-130">Se os cmdlets foram executados como um usuário sem permissões elevadas:</span><span class="sxs-lookup"><span data-stu-id="f3f06-130">If the cmdlets were executed as a user without elevated permissions:</span></span>

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="f3f06-131">Uma segunda opção é baixar o NuGet.exe do site NuGet.Org: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span><span class="sxs-lookup"><span data-stu-id="f3f06-131">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span></span><br>
<span data-ttu-id="f3f06-132">Ao selecionar uma versão NugGet para computadores de produção, verifique se ela é posterior à 2.8.5.208 e identifique a versão rotulada como "recomendada".</span><span class="sxs-lookup"><span data-stu-id="f3f06-132">When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span>
<span data-ttu-id="f3f06-133">Lembre-se de desbloquear o arquivo se ele tiver sido baixado usando um navegador.</span><span class="sxs-lookup"><span data-stu-id="f3f06-133">Remember to unblock the file if it was downloaded using a browser.</span></span>
<span data-ttu-id="f3f06-134">Isso pode ser feito usando o cmdlet *Unblock-File*.</span><span class="sxs-lookup"><span data-stu-id="f3f06-134">This can be performed by using the *Unblock-File* cmdlet.</span></span>

<span data-ttu-id="f3f06-135">Em ambos os casos, o arquivo NuGet.exe pode ser copiado para qualquer local em *$env:path*, mas os locais padrão são:</span><span class="sxs-lookup"><span data-stu-id="f3f06-135">In either case, the NuGet.exe file can be copied to any location in *$env:path*, but the standard locations are:</span></span>

<span data-ttu-id="f3f06-136">Para disponibilizar o executável para que todos os usuários possam usar os cmdlets *Publish-Module* e *Publish-Script*:</span><span class="sxs-lookup"><span data-stu-id="f3f06-136">To make the executable available so that all users can use *Publish-Module* and *Publish-Script* cmdlets:</span></span>

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="f3f06-137">Para disponibilizar o executável para apenas um usuário específico, copie para o local apenas dentro desse perfil de usuário:</span><span class="sxs-lookup"><span data-stu-id="f3f06-137">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```