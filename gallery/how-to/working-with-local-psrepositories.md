---
ms.date: 11/06/2018
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery,psget
title: Trabalhando com PSRepositories local
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619189"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="a3d91-103">Trabalhando com repositórios locais do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a3d91-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="a3d91-104">Os repositórios de suporte do módulo PowerShellGet diferente na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3d91-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="a3d91-105">Esses cmdlets permitem que os cenários a seguir:</span><span class="sxs-lookup"><span data-stu-id="a3d91-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="a3d91-106">Dar suporte a um conjunto de módulos do PowerShell confiável e validado previamente para uso em seu ambiente</span><span class="sxs-lookup"><span data-stu-id="a3d91-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="a3d91-107">Teste de um pipeline de CI/CD que compila os módulos do PowerShell ou scripts</span><span class="sxs-lookup"><span data-stu-id="a3d91-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="a3d91-108">Fornecer módulos e scripts do PowerShell para sistemas que não é possível acessar a internet</span><span class="sxs-lookup"><span data-stu-id="a3d91-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="a3d91-109">Este artigo descreve como configurar um repositório local do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3d91-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="a3d91-110">O artigo também aborda a [OfflinePowerShellGetDeploy][] módulo disponível a partir da Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3d91-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="a3d91-111">Esse módulo contém cmdlets para instalar a versão mais recente do PowerShellGet no seu repositório local.</span><span class="sxs-lookup"><span data-stu-id="a3d91-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="a3d91-112">Tipos de repositório local</span><span class="sxs-lookup"><span data-stu-id="a3d91-112">Local repository types</span></span>

<span data-ttu-id="a3d91-113">Há duas maneiras de criar um local PSRepository: compartilhamento de arquivo ou de servidor do NuGet.</span><span class="sxs-lookup"><span data-stu-id="a3d91-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="a3d91-114">Cada tipo tem vantagens e desvantagens:</span><span class="sxs-lookup"><span data-stu-id="a3d91-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="a3d91-115">Servidor do NuGet</span><span class="sxs-lookup"><span data-stu-id="a3d91-115">NuGet Server</span></span>

| <span data-ttu-id="a3d91-116">Vantagens</span><span class="sxs-lookup"><span data-stu-id="a3d91-116">Advantages</span></span>| <span data-ttu-id="a3d91-117">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="a3d91-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="a3d91-118">Imita a funcionalidade de PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="a3d91-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="a3d91-119">Aplicativo de várias camadas requer planejamento de operações e suporte</span><span class="sxs-lookup"><span data-stu-id="a3d91-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="a3d91-120">O NuGet se integra com o Visual Studio, outras ferramentas</span><span class="sxs-lookup"><span data-stu-id="a3d91-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="a3d91-121">Modelo de autenticação e gerenciamento de contas do NuGet necessários</span><span class="sxs-lookup"><span data-stu-id="a3d91-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="a3d91-122">O NuGet dá suporte a metadados em `.Nupkg` pacotes</span><span class="sxs-lookup"><span data-stu-id="a3d91-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="a3d91-123">A publicação requer manutenção e gerenciamento de chave de API</span><span class="sxs-lookup"><span data-stu-id="a3d91-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="a3d91-124">Fornece pesquisa, administração de pacote, etc.</span><span class="sxs-lookup"><span data-stu-id="a3d91-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="a3d91-125">Comp. de Arquivos</span><span class="sxs-lookup"><span data-stu-id="a3d91-125">File Share</span></span>

| <span data-ttu-id="a3d91-126">Vantagens</span><span class="sxs-lookup"><span data-stu-id="a3d91-126">Advantages</span></span>| <span data-ttu-id="a3d91-127">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="a3d91-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="a3d91-128">Fácil de configurar, fazer backup e manter</span><span class="sxs-lookup"><span data-stu-id="a3d91-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="a3d91-129">Metadados usados pelo PowerShellGet não estão disponível</span><span class="sxs-lookup"><span data-stu-id="a3d91-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="a3d91-130">Modelo de segurança simples - permissões de usuário no compartilhamento</span><span class="sxs-lookup"><span data-stu-id="a3d91-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="a3d91-131">Nenhuma interface do usuário além do compartilhamento de arquivo básico</span><span class="sxs-lookup"><span data-stu-id="a3d91-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="a3d91-132">Não há restrições, como substituir itens existentes</span><span class="sxs-lookup"><span data-stu-id="a3d91-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="a3d91-133">Nenhuma gravação de quem atualiza o que e segurança limitada</span><span class="sxs-lookup"><span data-stu-id="a3d91-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="a3d91-134">PowerShellGet funciona com o tipo e dá suporte à localização de versões e a instalação da dependência.</span><span class="sxs-lookup"><span data-stu-id="a3d91-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="a3d91-135">No entanto, alguns recursos que funcionam para a Galeria do PowerShell não estão disponíveis para servidores de NuGet base ou compartilhamentos de arquivos.</span><span class="sxs-lookup"><span data-stu-id="a3d91-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="a3d91-136">Tudo o que é um pacote - nenhuma diferenciação de scripts, módulos, recursos de DSC ou recursos de função.</span><span class="sxs-lookup"><span data-stu-id="a3d91-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="a3d91-137">Servidores de compartilhamento de arquivos não podem ver os metadados do pacote, incluindo as marcas.</span><span class="sxs-lookup"><span data-stu-id="a3d91-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="a3d91-138">Criação de um repositório local</span><span class="sxs-lookup"><span data-stu-id="a3d91-138">Creating a local repository</span></span>

<span data-ttu-id="a3d91-139">O artigo a seguir lista as etapas para configurar seu próprio servidor do NuGet.</span><span class="sxs-lookup"><span data-stu-id="a3d91-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="a3d91-140">[NuGet. Server][]</span><span class="sxs-lookup"><span data-stu-id="a3d91-140">[NuGet.Server][]</span></span>

<span data-ttu-id="a3d91-141">Siga as etapas até o ponto de adição de pacotes.</span><span class="sxs-lookup"><span data-stu-id="a3d91-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="a3d91-142">As etapas para [publicando um pacote](#publishing-to-a-local-repository) são abordados neste artigo.</span><span class="sxs-lookup"><span data-stu-id="a3d91-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="a3d91-143">Para um repositório com base no compartilhamento de arquivo, certifique-se de que os usuários tenham permissões para acessar o compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="a3d91-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="a3d91-144">Registrando um repositório local</span><span class="sxs-lookup"><span data-stu-id="a3d91-144">Registering a local repository</span></span>

<span data-ttu-id="a3d91-145">Antes de um repositório pode ser usado, ele deve ser registrado usando o `Register-PSRepository` comando.</span><span class="sxs-lookup"><span data-stu-id="a3d91-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="a3d91-146">Nos exemplos a seguir, o **InstallationPolicy** é definido como *confiáveis*, supondo que você confia que o seu próprio repositório.</span><span class="sxs-lookup"><span data-stu-id="a3d91-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="a3d91-147">Tome nota da diferença entre como tratar os dois comandos **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="a3d91-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="a3d91-148">Para um repositórios baseados em compartilhamento de arquivo, o **SourceLocation** e **ScriptSourceLocation** devem corresponder.</span><span class="sxs-lookup"><span data-stu-id="a3d91-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="a3d91-149">Para um repositório baseado na web, eles devem ser diferentes, portanto, neste exemplo à direita "/" é adicionado para o **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="a3d91-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="a3d91-150">Se você quiser PSRepository recentemente criado para ser o repositório padrão, você deve cancelar o registro de todos os outros PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="a3d91-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="a3d91-151">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a3d91-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="a3d91-152">O nome do repositório 'PSGallery' é reservado para uso pela Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3d91-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="a3d91-153">Você pode cancelar o registro PSGallery, mas é possível reutilizar o nome PSGallery para qualquer outro repositório.</span><span class="sxs-lookup"><span data-stu-id="a3d91-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="a3d91-154">Se você precisar restaurar a PSGallery, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a3d91-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="a3d91-155">Publicação em um repositório local</span><span class="sxs-lookup"><span data-stu-id="a3d91-155">Publishing to a local repository</span></span>

<span data-ttu-id="a3d91-156">Depois que você registrou o PSRepository local, você pode publicar em seu local PSRepository.</span><span class="sxs-lookup"><span data-stu-id="a3d91-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="a3d91-157">Há dois cenários principais de publicação: publicar seu próprio módulo e publicação de um módulo de PSGallery.</span><span class="sxs-lookup"><span data-stu-id="a3d91-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="a3d91-158">Publicação de um módulo criado por você</span><span class="sxs-lookup"><span data-stu-id="a3d91-158">Publishing a module you authored</span></span>

<span data-ttu-id="a3d91-159">Use `Publish-Module` e `Publish-Script` para publicar seu módulo em seu local PSRepository da mesma maneira que faria para a Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3d91-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="a3d91-160">Especifique o local para seu código</span><span class="sxs-lookup"><span data-stu-id="a3d91-160">Specify the location for your code</span></span>
- <span data-ttu-id="a3d91-161">Forneça uma chave de API</span><span class="sxs-lookup"><span data-stu-id="a3d91-161">Supply an API key</span></span>
- <span data-ttu-id="a3d91-162">Especifique o nome do repositório.</span><span class="sxs-lookup"><span data-stu-id="a3d91-162">Specify the repository name.</span></span> <span data-ttu-id="a3d91-163">Por exemplo, `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="a3d91-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="a3d91-164">Você deve criar uma conta no servidor do NuGet e entrar para gerar e salvar a chave de API.</span><span class="sxs-lookup"><span data-stu-id="a3d91-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="a3d91-165">Para um compartilhamento de arquivos, use qualquer cadeia de caracteres não vazia para o valor de NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="a3d91-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="a3d91-166">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="a3d91-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="a3d91-167">Para garantir a segurança, as chaves de API não devem ser codificado em scripts.</span><span class="sxs-lookup"><span data-stu-id="a3d91-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="a3d91-168">Use um sistema de gerenciamento de chaves seguro.</span><span class="sxs-lookup"><span data-stu-id="a3d91-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="a3d91-169">Publicação de um módulo de PSGallery</span><span class="sxs-lookup"><span data-stu-id="a3d91-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="a3d91-170">Para publicar um módulo do PSGallery para seu local PSRepository, você pode usar o cmdlet 'Save-Package'.</span><span class="sxs-lookup"><span data-stu-id="a3d91-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="a3d91-171">Especifique o nome do pacote</span><span class="sxs-lookup"><span data-stu-id="a3d91-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="a3d91-172">Especifique 'NuGet' como o provedor</span><span class="sxs-lookup"><span data-stu-id="a3d91-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="a3d91-173">Especifique o local de PSGallery como o código-fonte (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="a3d91-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="a3d91-174">Especifique o caminho para seu repositório local</span><span class="sxs-lookup"><span data-stu-id="a3d91-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="a3d91-175">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a3d91-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="a3d91-176">Se o seu local PSRepository é baseado na web, ele requer uma etapa adicional que usa nuget.exe para publicar.</span><span class="sxs-lookup"><span data-stu-id="a3d91-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="a3d91-177">Consulte a documentação para usar [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="a3d91-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="a3d91-178">Instalar o PowerShellGet em um sistema desconectado</span><span class="sxs-lookup"><span data-stu-id="a3d91-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="a3d91-179">Implantar o PowerShellGet é difícil em ambientes que exigem sistemas para ser desconectado da internet.</span><span class="sxs-lookup"><span data-stu-id="a3d91-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="a3d91-180">O PowerShellGet tem um processo de inicialização que instala a versão mais recente na primeira vez que ele é usado.</span><span class="sxs-lookup"><span data-stu-id="a3d91-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="a3d91-181">O módulo OfflinePowerShellGetDeploy na Galeria do PowerShell fornece cmdlets que oferecem suporte a esse processo de inicialização.</span><span class="sxs-lookup"><span data-stu-id="a3d91-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="a3d91-182">Para inicializar uma implantação offline, você precisa:</span><span class="sxs-lookup"><span data-stu-id="a3d91-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="a3d91-183">Baixe e instale o sistema OfflinePowerShellGetDeploy seu conectados à internet e seus sistemas desconectados</span><span class="sxs-lookup"><span data-stu-id="a3d91-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="a3d91-184">Baixe o PowerShellGet e suas dependências no sistema conectado à internet usando o `Save-PowerShellGetForOffline` cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3d91-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="a3d91-185">Copiar PowerShellGet e suas dependências de sistema conectado à internet para o sistema desconectado</span><span class="sxs-lookup"><span data-stu-id="a3d91-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="a3d91-186">Use o `Install-PowerShellGetOffline` no sistema desconectado para colocar PowerShellGet e suas dependências nas pastas apropriadas</span><span class="sxs-lookup"><span data-stu-id="a3d91-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="a3d91-187">Os seguintes comandos use `Save-PowerShellGetForOffline` colocar todos os componentes em uma pasta `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="a3d91-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="a3d91-188">Neste ponto, você deve fazer o conteúdo de `F:\OfflinePowerShellGet` disponíveis para seus sistemas desconectados.</span><span class="sxs-lookup"><span data-stu-id="a3d91-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="a3d91-189">Execute o `Install-PowerShellGetOffline` cmdlet para instalar o PowerShellGet no sistema desconectado.</span><span class="sxs-lookup"><span data-stu-id="a3d91-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="a3d91-190">É importante que você não executar o PowerShellGet na sessão do PowerShell antes de executar esses comandos.</span><span class="sxs-lookup"><span data-stu-id="a3d91-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="a3d91-191">Depois que o PowerShellGet está carregado na sessão, os componentes não podem ser atualizados.</span><span class="sxs-lookup"><span data-stu-id="a3d91-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="a3d91-192">Se você iniciar o PowerShellGet por engano, saia e reinicie o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3d91-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="a3d91-193">Depois de executar esses comandos, você está pronto para publicar o PowerShellGet em seu repositório local.</span><span class="sxs-lookup"><span data-stu-id="a3d91-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="a3d91-194">Para garantir a segurança, as chaves de API não devem ser codificado em scripts.</span><span class="sxs-lookup"><span data-stu-id="a3d91-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="a3d91-195">Use um sistema de gerenciamento de chaves seguro.</span><span class="sxs-lookup"><span data-stu-id="a3d91-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[NuGet. Server]: /nuget/hosting-packages/nuget-server
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[NuGet.exe]: /nuget/tools/nuget-exe-cli-reference
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
