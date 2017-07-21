---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Install-Script
ms.openlocfilehash: 4c3fd9393ccb7ee5c3b010f1114b6596a74fdee2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="install-script"></a><span data-ttu-id="85fc4-103">Install-Script</span><span class="sxs-lookup"><span data-stu-id="85fc4-103">Install-Script</span></span>

<span data-ttu-id="85fc4-104">Instala arquivos de script do PowerShell de repositórios online no computador local.</span><span class="sxs-lookup"><span data-stu-id="85fc4-104">Installs the PowerShell script files from online repositories to the local computer.</span></span>


## <a name="description"></a><span data-ttu-id="85fc4-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="85fc4-105">Description</span></span>

<span data-ttu-id="85fc4-106">O cmdlet Install-Script adquire uma carga de script de um repositório, verifica se a carga é um script do PowerShell válido e copia o arquivo de script para um local de instalação especificado.</span><span class="sxs-lookup"><span data-stu-id="85fc4-106">The Install-Script cmdlet acquires a script payload from a repository, verifies that the payload is a valid PowerShell script, and copies the script file to a specified installation location.</span></span>

<span data-ttu-id="85fc4-107">Os repositórios padrão em que Install-Script opera podem ser configurados por meio dos cmdlets Register-PSRepository, Set-PSRepository, Unregister-PSRepository e Get-PSRepository.</span><span class="sxs-lookup"><span data-stu-id="85fc4-107">The default repositories Install-Script operates against are configurable through the Register-PSRepository, Set-PSRepository, Unregister-PSRepository, and Get-PSRepository cmdlets.</span></span> <span data-ttu-id="85fc4-108">Ao operar em vários repositórios, Install-Script instala o primeiro script correspondente aos critérios de pesquisa especificados (Name, MinimumVersion ou MaximumVersion) do primeiro repositório sem erros.</span><span class="sxs-lookup"><span data-stu-id="85fc4-108">When operating against multiple repositories, Install-Script installs the first script that matches the specified search criteria (Name, MinimumVersion, or MaximumVersion) from the first repository without any error.</span></span>


<span data-ttu-id="85fc4-109">O cmdlet Install-Script baixa um ou mais módulos de uma galeria online, valida-os e instala-os no computador local com o escopo de instalação especificado.</span><span class="sxs-lookup"><span data-stu-id="85fc4-109">Install-Script cmdlet downloads one or more modules from an online gallery, validates and installs them on the local computer to the specified installation scope.</span></span>

<span data-ttu-id="85fc4-110">O cmdlet Install-Script obtém um ou mais módulos que atendem aos critérios especificados de uma galeria online, verifica se os resultados da pesquisa são módulos válidos e copia pastas de módulo para o local de instalação.</span><span class="sxs-lookup"><span data-stu-id="85fc4-110">The Install-Script cmdlet gets one or more modules that meet specified criteria from an online gallery, verifies that search results are valid modules, and copies module folders to the installation location.</span></span>

<span data-ttu-id="85fc4-111">Quando nenhum escopo é definido ou quando o valor do parâmetro Scope é AllUsers, o módulo é instalado em %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="85fc4-111">When no scope is defined, or when the value of the Scope parameter is AllUsers, the module is installed to %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span></span> <span data-ttu-id="85fc4-112">Quando o valor de Scope é CurrentUser, o módulo é instalado em $home\Documents\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="85fc4-112">When the value of Scope is CurrentUser, the module is installed to $home\Documents\WindowsPowerShell\Modules.</span></span>

<span data-ttu-id="85fc4-113">Você pode filtrar os resultados com base nas versões mínima e exata dos módulos especificados.</span><span class="sxs-lookup"><span data-stu-id="85fc4-113">You can filter your results based on minimum and exact versions of specified modules.</span></span>

- <span data-ttu-id="85fc4-114">Não há suporte para a versão Lado a Lado para arquivos de Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="85fc4-114">No Side-by-side version support for PowerShell Script files</span></span>
- <span data-ttu-id="85fc4-115">Suporte para instalação de dependências de script</span><span class="sxs-lookup"><span data-stu-id="85fc4-115">Script dependency installation support</span></span>
- <span data-ttu-id="85fc4-116">**Prompt não confiável:** a aceitação do usuário é obrigatória para instalar os módulos de um repositório não confiável.</span><span class="sxs-lookup"><span data-stu-id="85fc4-116">**Untrusted prompt:** User acceptance is required for installing the modules from an untrusted repository.</span></span>
- <span data-ttu-id="85fc4-117">-Force reinstala o módulo instalado</span><span class="sxs-lookup"><span data-stu-id="85fc4-117">-Force reinstalls the installed module</span></span>
- <span data-ttu-id="85fc4-118">RequiredVersion instala a versão especificada no SxS com as versões existentes no PowerShell versão 5.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="85fc4-118">RequiredVersion installs the specified version in SxS with existing versions on PowerShell version 5.0 or newer.</span></span>

<span data-ttu-id="85fc4-119">Não há suporte para curingas em -Name nos cmdlets Install-Module, Save-Module, Uninstall-Module, Install-Script, Save-Script e Uninstall-Script.</span><span class="sxs-lookup"><span data-stu-id="85fc4-119">Wildcards are not supported in -Name on Install-Module, Save-Module, Uninstall-Module, Install-Script, Save-Script, and Uninstall-Script cmdlets.</span></span>

### <a name="scope"></a><span data-ttu-id="85fc4-120">Escopo</span><span class="sxs-lookup"><span data-stu-id="85fc4-120">Scope</span></span>
<span data-ttu-id="85fc4-121">Especifica o escopo de instalação do módulo.</span><span class="sxs-lookup"><span data-stu-id="85fc4-121">Specifies the installation scope of the module.</span></span> <span data-ttu-id="85fc4-122">Os valores aceitáveis para este parâmetro são: AllUsers e CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="85fc4-122">The acceptable values for this parameter are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="85fc4-123">O escopo de instalação padrão é AllUsers.</span><span class="sxs-lookup"><span data-stu-id="85fc4-123">The default installation scope is AllUsers.</span></span>

<span data-ttu-id="85fc4-124">O escopo AllUsers permite que os módulos sejam instalados em um local que seja acessível para todos os usuários do computador, ou seja, "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".</span><span class="sxs-lookup"><span data-stu-id="85fc4-124">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".</span></span>

<span data-ttu-id="85fc4-125">O escopo CurrentUser permite que módulos ser instalado somente em "$home\Documents\WindowsPowerShell\Modules", de modo que o módulo fica disponível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="85fc4-125">The CurrentUser scope lets modules be installed only to "$home\Documents\WindowsPowerShell\Modules", so that the module is available only to the current user.</span></span>


<span data-ttu-id="85fc4-126">Especifica o escopo de instalação do script.</span><span class="sxs-lookup"><span data-stu-id="85fc4-126">Specifies the installation scope of the script.</span></span> <span data-ttu-id="85fc4-127">Os valores válidos são: AllUsers e CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="85fc4-127">Valid values are: AllUsers and CurrentUser.</span></span> <span data-ttu-id="85fc4-128">O padrão é CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="85fc4-128">The default is CurrentUser.</span></span>

<span data-ttu-id="85fc4-129">O escopo AllUsers especifica a instalação do script em %systemdrive%:\ProgramFiles\WindowsPowerShell\Scripts, de modo que o script fica disponível para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="85fc4-129">The AllUsers scope specifies to install a script to %systemdrive%:\ProgramFiles\WindowsPowerShell\Scripts so that the script is available to all users.</span></span> <span data-ttu-id="85fc4-130">O escopo CurrentUser especifica a instalação do script em $home\Documents\WindowsPowerShell\Scripts, de modo que o script fica disponível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="85fc4-130">The CurrentUser scope specifies to install the script in $home\Documents\WindowsPowerShell\Scripts so that the script is available only to the current user.</span></span>


## <a name="nopathupdate"></a><span data-ttu-id="85fc4-131">NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="85fc4-131">NoPathUpdate</span></span>

- <span data-ttu-id="85fc4-132">O parâmetro de opção NoPathUpdate no cmdlet Install-Script ignora o prompt para adicionar o local de instalação do script à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="85fc4-132">NoPathUpdate switch parameter on Install-Script cmdlet bypasses the prompt for adding the script install location to the PATH environment variable.</span></span>
- <span data-ttu-id="85fc4-133">Qualquer uso do comando COM – NoPathUpdate especificado não resultará em nenhum prompt e PATH NÃO será atualizado (Force pode ser ignorado aqui).</span><span class="sxs-lookup"><span data-stu-id="85fc4-133">Any use of the command WITH –NoPathUpdate specified will result in no prompt and the PATH NOT being updated (force is ignorable here).</span></span>
- <span data-ttu-id="85fc4-134">-Force sem –NoPathUpdate não resultará em nenhum prompt e PATH será atualizado.</span><span class="sxs-lookup"><span data-stu-id="85fc4-134">-Force without –NoPathUpdate will result in no prompt and the PATH will be updated.</span></span>
- <span data-ttu-id="85fc4-135">Se nem –Force nem – NoPathUpdate for especificado, o usuário verá o prompt.</span><span class="sxs-lookup"><span data-stu-id="85fc4-135">If neither –Force or –NoPathUpdate are specified, the user will see the prompt.</span></span>
- <span data-ttu-id="85fc4-136">Tudo isso se aplica apenas à primeira vez em que Inslatll-Script é usado em um determinado escopo.</span><span class="sxs-lookup"><span data-stu-id="85fc4-136">All of this only applies the first time Install-Script is used in a given scope.</span></span>


## <a name="notes"></a><span data-ttu-id="85fc4-137">Observações</span><span class="sxs-lookup"><span data-stu-id="85fc4-137">Notes</span></span>

<span data-ttu-id="85fc4-138">Esse cmdlet é executado no Windows PowerShell 3.0 ou em versões posteriores do Windows PowerShell, no Windows 7 ou no Windows 2008 R2 e em versões posteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="85fc4-138">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="85fc4-139">Se um módulo instalado não puder ser importado (ou seja, se ele não tiver um .psm1, .psd1 ou .dll com o mesmo nome dentro da pasta), a instalação falhará, a menos que você adicione o parâmetro Force ao comando.</span><span class="sxs-lookup"><span data-stu-id="85fc4-139">If an installed module cannot be imported (that is, if it does not have a .psm1, .psd1, or .dll of the same name within the folder), installation fails unless you add the Force parameter to your command.</span></span>

<span data-ttu-id="85fc4-140">Se uma versão do módulo no computador corresponder ao valor especificado para o parâmetro Name e você não tiver adicionado o parâmetro MinimumVersion ou RequiredVersion, o Install-Script continuará silenciosamente sem instalar o módulo.</span><span class="sxs-lookup"><span data-stu-id="85fc4-140">If a version of the module on the computer matches the value specified for the Name parameter, and you have not added the MinimumVersion or RequiredVersion parameter, Install-Script silently continues without installing that module.</span></span> <span data-ttu-id="85fc4-141">Se os parâmetros MinimumVersion ou RequiredVersion forem especificados e o módulo existente não corresponder aos valores no parâmetro, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="85fc4-141">If the MinimumVersion or RequiredVersion parameters are specified, and the existing module does not match the values in that parameter, then an error occurs.</span></span> <span data-ttu-id="85fc4-142">Para ser mais específico: se a versão do módulo instalada atualmente for inferior ao valor do parâmetro MinimumVersion ou for diferente do valor do parâmetro RequiredVersion, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="85fc4-142">To be more specific: if the version of the currently-installed module is either lower than the value of the MinimumVersion parameter, or not equal to the value of the RequiredVersion parameter, an error occurs.</span></span> <span data-ttu-id="85fc4-143">Se a versão do módulo instalado for maior que o valor do parâmetro MinimumVersion ou igual ao valor do parâmetro RequiredVersion, Install-Script continuará silenciosamente sem instalar o módulo.</span><span class="sxs-lookup"><span data-stu-id="85fc4-143">If the version of the installed module is greater than the value of the MinimumVersion parameter, or equal to the value of the RequiredVersion parameter, Install-Script silently continues without installing that module.</span></span>

<span data-ttu-id="85fc4-144">Install-Script retornará um erro se não existir na galeria online nenhum módulo correspondente ao nome especificado.</span><span class="sxs-lookup"><span data-stu-id="85fc4-144">Install-Script returns an error if no module exists in the online gallery that matches the specified name.</span></span>

<span data-ttu-id="85fc4-145">Para instalar vários módulos, especifique uma matriz de nomes de módulo, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="85fc4-145">To install multiple modules, specify an array of the module names, separated by commas.</span></span> <span data-ttu-id="85fc4-146">Não será possível adicionar MinimumVersion ou RequiredVersion se você especificar vários nomes de módulo.</span><span class="sxs-lookup"><span data-stu-id="85fc4-146">You cannot add MinimumVersion or RequiredVersion if you specify multiple module names.</span></span>

<span data-ttu-id="85fc4-147">Por padrão, os módulos são instalados na pasta Arquivos de Programas, para evitar confusão ao instalar recursos de DSC (Configuração de Estado Desejado) do Windows PowerShell. É possível redirecionar vários objetos PSGetItemInfo para Install-Script; esta é outra maneira de especificar vários módulos para serem instalados em um único comando.</span><span class="sxs-lookup"><span data-stu-id="85fc4-147">By default, modules are installed to the Program Files folder, to prevent confusion when you are installing Windows PowerShell Desired State Configuration (DSC) resources.You can pipe multiple PSGetItemInfo objects to Install-Script; this is another way of specifying multiple modules to install in a single command.</span></span>

<span data-ttu-id="85fc4-148">Para ajudar a evitar a execução de módulos que contêm código mal-intencionado, os módulos instalados não são importados automaticamente pela instalação.</span><span class="sxs-lookup"><span data-stu-id="85fc4-148">To help prevent running modules that contain malicious code, installed modules are not automatically imported by installation.</span></span> <span data-ttu-id="85fc4-149">Como mellhor prática de segurança, avalie o código do módulo antes de executar cmdlets ou funções em um módulo pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="85fc4-149">As a security best practice, evaluate module code before running any cmdlets or functions in a module for the first time.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="85fc4-150">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="85fc4-150">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Install-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="85fc4-151">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="85fc4-151">Cmdlet online help reference</span></span>

[<span data-ttu-id="85fc4-152">Install-Script</span><span class="sxs-lookup"><span data-stu-id="85fc4-152">Install-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619784)

## <a name="example-commands"></a><span data-ttu-id="85fc4-153">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="85fc4-153">Example commands</span></span>

```powershell


# Piping Find-Script output to Install-Script cmdlet

Find-Script -Repository Local1 -Name Required-Script2

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script2                    local1               Description for the Required-Script2 script


Find-Script -Repository Local1 -Name Required-Script2 | Install-Script

Get-Command Required-Script2

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
ExternalScript  Required-Script2.ps1                                2.0       C:\Users\manikb\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1


Get-InstalledScript Required-Script2

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script2                    local1               Description for the Required-Script2 script


Get-InstalledScript Required-Script2 | fl * -Force


Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : manikb
CompanyName                :
Copyright                  : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://manikb-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\manikb\Documents\WindowsPowerShell\Scripts


# Installing a script to AllUsers scope

Install-Script -Repository Local1 -Name Required-Script3 -Scope AllUsers
Get-InstalledScript -Name Required-Script3

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Get-InstalledScript -Name Required-Script3  | fl * -Force


Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : manikb
CompanyName                :
Copyright                  : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://manikb-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


# Installing a script with dependent scripts and modules

Find-Script -Repository Local1 -Name Script-WithDependencies2 -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0        Script-WithDependencies2            local1               Description for the Script-WithDependencies2 script
2.5        RequiredModule1                     local1               RequiredModule1 module
2.5        RequiredModule2                     local1               RequiredModule2 module
2.5        RequiredModule3                     local1               RequiredModule3 module
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Install-Script -Repository Local1 -Name Script-WithDependencies2
Get-InstalledScript

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script
2.0        Script-WithDependencies2            local1               Description for the Script-WithDependencies2 script


Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        RequiredModule1                     local1               RequiredModule1 module
2.5        RequiredModule2                     local1               RequiredModule2 module
2.5        RequiredModule3                     local1               RequiredModule3 module


Find-Script -Repository Local1 -Name Required-Script*

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Install-Script -Repository Local1 -Name Required-Script*

Get-InstalledScript

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


# Find a script and install it

# The first command finds the script named Required-Script2 from the Local1 repository and displays the results.
# The second command finds the Required-Script2 script, and then uses the pipeline operator to pass it to the Install-Script cmdlet to install it.
# The third command uses the Get-Command cmdlet to get Required-Script2, and then displays the results.
# The fourth command uses the Get-InstalledScript cmdlet to get Required-Script2 and display the results.
# The fifth command gets RequiredScript2 and uses the pipeline operator to pass it to the Format-List cmdlet to format the output.

Find-Script -Repository "Local1" -Name "Required-Script2"

Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
Get-Command -Name "Required-Script2"

Get-InstalledScript -Name "Required-Script2"

Get-InstalledScript -Name "Required-Script2" | Format-List * 


# Install a script with AllUsers scope

# The first command installs the script named Required-Script3 and assigns it AllUsers scope.
# The second command gets the installed script Required-Script3 and displays information about it.
# The third command gets Required-Script3 and uses the pipeline operator to pass it to the Format-List cmdlet to format the output.

Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
Get-InstalledScript -Name "Required-Script3"
Get-InstalledScript -Name "Required-Script3" | Format-List * 


# Install a script with its dependent scripts and modules

# The first command finds the script named Script-WithDependencies2 and its dependencies in the Local1 repository and displays the results.
# The second command installs Script-WithDependencies2.
# The third command uses the Get-InstalledScript script cmdlet to get installed scripts and display the results.
# The fourth command uses the Get-InstalledModule cmdlet to get installed modules and display the results.
# The fifth command uses the Find-Script cmdlet to find scripts where the name begins with Required-Script and display the results.
# The sixth command installs the scripts where the name begins with Required-Script in the Local1 repository. 
# The final command gets installed scripts and displays the results.

Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
Get-InstalledScript
Get-InstalledModule
Find-Script -Repository "Local1" -Name "Required-Script*"
Install-Script -Repository "Local1" -Name "Required-Script*"
Get-InstalledScript

```

<span data-ttu-id="85fc4-154">Também é possível usar Get-Command –Name <InstalledScriptFileName> para obtê-lo.</span><span class="sxs-lookup"><span data-stu-id="85fc4-154">You can also use Get-Command –Name <InstalledScriptFileName> to get it.</span></span> <span data-ttu-id="85fc4-155">Dois locais de instalação são adicionados à variável de ambiente PATH na primeira utilização de um escopo especificado.</span><span class="sxs-lookup"><span data-stu-id="85fc4-155">Two install locations are added to the PATH environment variable on first use of a specified scope.</span></span>
```powershell
$env:Path -split ';'| Where-Object {$\_} | Select-Object -Last 2
C:\\Program Files\\WindowsPowerShell\\Scripts
C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Get-Command Required-Script2
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script2.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Required-Script2.ps1
```

```powershell

# Install a module by name
Install-Script -Name MyDscModule

# Install multiple modules
Install-Script ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Script -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Script -Name ContosoServer -RequiredVersion 1.1.3

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Script -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Script ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Script ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Script ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Script ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Script ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Script ContosoClient -Force

# Install a module with dependencies
Install-Script -Name 


# Install a script from the registered repository with ScriptSourceLocation
Install-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Install-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Install-Script -Name *Azure*

# Find all versions of a script
Install-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion. 
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Install-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Install-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Install-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Installing a script to default AllUsers scope and with RequiredVersion
Install-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script from the specified repository
Install-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Install-Script

# Find available scripts from few registered repositories
Install-Script -Repository PSGallery, PrivatePSGallery

```

```powershell
 Added the logic for checking and failing the install script operation when there is a command with same name is already available on the system.
Also updated the prompt message.

 Examples:
PS C:\WINDOWS\system32> install-script get-childitem -Repository localrepo
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:1
+ install-script get-childitem -Repository localrepo
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script

 
 
 PS C:\WINDOWS\system32> install-script get-childitem,contosos -Repository localrepo
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:1
+ install-script get-childitem,contosos -Repository localrepo
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script

 PackageManagement\Install-Package : No match was found for the specified search criteria and script name 'contosos'. Try Get-ScriptRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\powershellget\1.0.0.1\PSModule.psm1:2891 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : ObjectNotFound: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], Exception
     + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage

 PS C:\WINDOWS\system32>

 
 
 PS C:\WINDOWS\system32> find-script get-childitem -Repository localrepo | install-script
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:51
+ find-script get-childitem -Repository localrepo | install-script
+                                                   ~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script

 
 PS C:\WINDOWS\system32>

 PS C:\WINDOWS\system32> Install-Package -Name Get-ChildItem -source LocalRepo  -ProviderName powershellget -Type Script
WARNING: A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.

```

```powershell

Prompt ONCE per USER and per SCOPE for adding the script installation location to PATH environment variable.

- Prompt message for CurrentUser scope: (Complete message will be scrubbed later)

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):


- Prompt message for –AllUsers scope is same as above with $env:ProgramFiles\WindowsPowerShell\Scripts .

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Program Files\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Program Files\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Program Files\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):


- To prompt only once per scope, user acceptance for PATH variable change will be added to the user specific settings file under %localappdata%\Microsoft\windows\PowerShell\PowerShellGet
%localappdata%\Microsoft\windows\PowerShell\PowerShellGet\PowerShellGetSettings.XML. 
This settings file will be used to not prompt again.

After prompting for CurrentUser scope: 
    true or false for CurrentUserScope_AllowPATHChangeForScripts key based on user input.

After prompting for AllUsers scope: 
    true or false for AllUsersScope_AllowPATHChangeForScripts key based on user input.

- If user accepts the prompt
                Check and add $home\Documents\WindowsPowerShell\Scripts to user specific PATH environment variable.
                Check and add $env:ProgramFiles\WindowsPowerShell\Scripts to system specific PATH environment variable only when Install-Script cmdlet is used in an administrator process.
                Check and add above two paths to $env:PATH variable of the current process.

- If user denies the prompt, script installation will be proceeded without making any changes to the PATH environment variable.



Example:             
PS C:\windows\system32> Install-Script -Name $scriptName -Repository $repositoryName -Scope $Scope -Verbose

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Program Files\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Program Files\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Program Files\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n


```

## <a name="install-script-cmdlet-in-pipeline-operations"></a><span data-ttu-id="85fc4-156">Cmdlet Install-Script em operações de pipeline</span><span class="sxs-lookup"><span data-stu-id="85fc4-156">Install-Script cmdlet in pipeline operations</span></span>

```powershell

# Find a module and install it
Find-Script -Name "MyDSC*" | Install-Script

# Find a module and install it to the CurrentUser scope
Find-Script -Name "MyDSC*" | Install-Script -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Script to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Script
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Script cmdlet by using the pipeline operator. The Install-Script cmdlet installs the module for the resource. 
# If you pipe multiple resources to the Install-Script cmdlet from the same module, Install-Script attempts to install the module only once. 
Find-DscResource -Name "MyResource" | Install-Script
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Script
Get-InstalledModule

```

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="85fc4-157">Suporte à versão lado a lado no PowerShell 5.0 ou mais recente</span><span class="sxs-lookup"><span data-stu-id="85fc4-157">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="85fc4-158">O PowerShellGet dá suporte à versão SxS (lado a lado) do módulo nos cmdlets Install-Script, Update-Script e Publish-Script executados no Windows PowerShell 5.0 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="85fc4-158">PowerShellGet supports the side-by-side (SxS) module version support in Install-Script, Update-Script, and Publish-Script cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>

### <a name="install-script-examples"></a><span data-ttu-id="85fc4-159">Exemplos de Install-Script</span><span class="sxs-lookup"><span data-stu-id="85fc4-159">Install-Script examples</span></span>

```powershell
# Install a version of the module
Install-Script -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Script -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Script -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Script -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## <a name="install-module-with-its-dependencies"></a><span data-ttu-id="85fc4-160">Instalar um módulo com dependências</span><span class="sxs-lookup"><span data-stu-id="85fc4-160">Install module with its dependencies</span></span>

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Script -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## <a name="error-scenarios"></a><span data-ttu-id="85fc4-161">Cenários de erro</span><span class="sxs-lookup"><span data-stu-id="85fc4-161">Error scenarios</span></span>

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Script'
Install-Script ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Script'
Install-Script ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Script'
Install-Script ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Script'
Install-Script ContosoClient,ContosoServer -MinimumVersion 2.0

```

## <a name="installing-a-script-with-dependent-scripts-and-modules"></a><span data-ttu-id="85fc4-162">Instalando um script com módulos e scripts dependentes</span><span class="sxs-lookup"><span data-stu-id="85fc4-162">Installing a script with dependent scripts and modules</span></span>

```powershell
# Installing a script with dependent scripts and modules
Find-Script -Repository GalleryINT -Name Script-WithDependencies2 -IncludeDependencies
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.5 Required-Script3 Script GalleryINT Description for the Required-Script3 script

Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
Get-InstalledModule
Install-Script -Repository GalleryINT -Name Script-WithDependencies2 -Scope CurrentUser
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
Get-InstalledModule
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module

# Contents of Script-WithDependencies2 file.
<#PSScriptInfo
.VERSION 2.0
.GUID 90082fa1-0b84-49fb-a00e-0a624fbb6584
.AUTHOR manikb
.COMPANYNAME Microsoft Corporation
.COPYRIGHT (c) 2015 Microsoft Corporation. All rights reserved.
.TAGS Tag1 Tag2 Tag-Script-WithDependencies2-2.0
.LICENSEURI http://script-withdependencies2.com/license
.PROJECTURI http://script-withdependencies2.com/
.ICONURI http://script-withdependencies2.com/icon
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS Required-Script1,Required-Script2,Required-Script3
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
Script-WithDependencies2 release notes
#>
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'}
#Requires -Module @{RequiredVersion = '2.5'; ModuleName = 'RequiredModule3'}
#Requires -Module @{ModuleVersion = '1.1'; ModuleName = 'RequiredModule4'; MaximumVersion = '2.0'}
#Requires -Module @{MaximumVersion = '1.5'; ModuleName = 'RequiredModule5'}
<#
.DESCRIPTION
Description for the Script-WithDependencies2 script
#>
Param()
Function Test-FunctionFromScript\_Script-WithDependencies2 { Get-Date }
Workflow Test-WorkflowFromScript\_Script-WithDependencies2 { Get-Date }
```

## <a name="install-script-and-get-installedscript-cmdlets"></a><span data-ttu-id="85fc4-163">Cmdlets Install-Script e Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="85fc4-163">Install-Script and Get-InstalledScript cmdlets</span></span>
<span data-ttu-id="85fc4-164">O cmdlet Install-Script permite instalar um arquivo de script específico junto com suas dependências no escopo especificado.</span><span class="sxs-lookup"><span data-stu-id="85fc4-164">Install-Script cmdlet lets you to install a specific script file along with its dependencies to the specified scope.</span></span> <span data-ttu-id="85fc4-165">Por padrão, os scripts são instalados no escopo AllUsers.</span><span class="sxs-lookup"><span data-stu-id="85fc4-165">By default, scripts are installed to the AllUsers scope.</span></span> <span data-ttu-id="85fc4-166">O cmdlet Get-InstalledScript permite obter a lista de arquivos de script que foram instalados com o cmdlet Install-Script.</span><span class="sxs-lookup"><span data-stu-id="85fc4-166">Get-InstalledScript cmdlet lets you to get the list of script files which were installed using Install-Script cmdlet.</span></span>

<span data-ttu-id="85fc4-167">Observação de uso: para permitir o gerenciamento e a localização dos scripts quando eles forem instalados, Install-Script criará uma pasta padrão para armazenar scripts em $home\Documents\WindowsPowerShell\Scripts e adicionará essa pasta ao seu ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="85fc4-167">Use note: To allow management and locating of scripts once they are installed, Install-script will create a default folder for storing scripts at $home\Documents\WindowsPowerShell\Scripts, and add that folder to your PATH environment.</span></span> <span data-ttu-id="85fc4-168">Caso a modificação do caminho seja uma preocupação, use Save-Script em vez de Install-Script.</span><span class="sxs-lookup"><span data-stu-id="85fc4-168">If modifying the path is a concern, use Save-Script instead of Install-Script.</span></span> <span data-ttu-id="85fc4-169">Get-InstalledScripts e Uninstall-Script só podem funcionar com scripts colocados no sistema usando Install-Script.</span><span class="sxs-lookup"><span data-stu-id="85fc4-169">Get-InstalledScripts and Uninstall-Script can only work with scripts placed on the system using Install-Script.</span></span>
```powershell
# Install locations for scripts:
# Default scope is AllUsers.
# AllUsers scope --> "$env:ProgramFiles\\WindowsPowerShell\\Scripts"
# CurrentUser scope -->; "$env:USERPROFILE\\Documents\\WindowsPowerShell\\Scripts"

# Piping Find-Script output to Install-Script cmdlet
Find-Script -Repository GalleryINT -Name Required-Script2 | Install-Script -Scope CurrentUser -Verbose
VERBOSE: Repository details, Name = 'GalleryINT', Location = 'https://customgallery.cloudapp.net/api/v2/'; IsTrusted = 'True'; IsRegistered = 'True'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.5' of script 'Required-Script2'".
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'GalleryINT'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://customgallery.cloudapp.net/api/v2/items/psscript/' and PackageManagementProvider is 'NuGet'.
VERBOSE: Searching repository 'https://customgallery.cloudapp.net/api/v2/items/psscript/FindPackagesById()?id='Required-Script2'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'Required-Script2'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.5' of script 'Required-Script2'".
VERBOSE: The installation scope is specified to be 'CurrentUser'.
VERBOSE: The specified script will be installed in 'C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts' and its dependent modules will be installed in
'C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading script 'Required-Script2' with version '2.5' from the repository 'https://customgallery.cloudapp.net/api/v2/items/psscript/'.
VERBOSE: Script 'Required-Script2' was installed successfully.

Get-InstalledScript Required-Scri\*
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script

Get-InstalledScript Required-Script2 | Format-List \* -Force
Name : Required-Script2
Version : 2.5
Type : Script
Description : Description for the Required-Script2 script
Author : manikb
CompanyName :
Copyright : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate : 10/30/2015 1:25:15 AM
LicenseUri : http://required-script2.com/license
ProjectUri : http://required-script2.com/
IconUri : http://required-script2.com/icon
Tags : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript}
Includes : {Function, DscResource, Cmdlet, Workflow...}
PowerShellGetFormatVersion :
ReleaseNotes : Required-Script2 release notes
Dependencies : {}
RepositorySourceLocation : https://customgallery.cloudapp.net/api/v2/
Repository : GalleryINT
PackageManagementProvider : NuGet
AdditionalMetadata : {Type, releaseNotes, copyright, PackageManagementProvider...}
InstalledLocation : C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Installed script file is immediately available for usage.
```

<span data-ttu-id="85fc4-170">Também é possível usar Get-Command –Name <InstalledScriptFileName> para obtê-lo.</span><span class="sxs-lookup"><span data-stu-id="85fc4-170">You can also use Get-Command –Name <InstalledScriptFileName> to get it.</span></span> <span data-ttu-id="85fc4-171">Dois locais de instalação são adicionados à variável de ambiente PATH na primeira utilização de um escopo especificado.</span><span class="sxs-lookup"><span data-stu-id="85fc4-171">Two install locations are added to the PATH environment variable on first use of a specified scope.</span></span>
```powershell
$env:Path -split ';'| Where-Object {$\_} | Select-Object -Last 2
C:\\Program Files\\WindowsPowerShell\\Scripts
C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Get-Command Required-Script2
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script2.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Required-Script2.ps1

Find-Script -Repository LocalRepo1 -Name Demo-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script LocalRepo1 Script file description goes here

Find-Script -Repository LocalRepo1 -Name Demo-Script | Install-Script -Scope CurrentUser
Untrusted repository
You are installing the scripts from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the scripts from 'C:\\MyLocalRepo'?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"): Y

Get-InstalledScript Demo-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script LocalRepo1 Script file description goes here

Get-Command Demo-Script
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Demo-Script.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Demo-Script.ps1

# Using the installed script
Demo-Script
Demo-ScriptFunction
Demo-ScriptWorkflow

# Installing a script to default AllUsers scope and with RequiredVersion
Install-Script -Repository GalleryINT -Name Required-Script3 -RequiredVersion 2.0
Get-InstalledScript -Name Required-Script3

Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
Get-InstalledScript -Name Required-Script3 | Format-List Name,InstalledLocation -Force
Name : Required-Script3
InstalledLocation : C:\\Program Files\\WindowsPowerShell\\Scripts

Get-Command Required-Script3
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script3.ps1 C:\\Program Files\\WindowsPowerShell\\Scripts\\Required-Script3.ps1

# Installing a script with dependent scripts and modules
Find-Script -Repository GalleryINT -Name Script-WithDependencies2 -IncludeDependencies
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.5 Required-Script3 Script GalleryINT Description for the Required-Script3 script

Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
Get-InstalledModule
Install-Script -Repository GalleryINT -Name Script-WithDependencies2 -Scope CurrentUser
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
Get-InstalledModule
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module

# Contents of Script-WithDependencies2 file.
<#PSScriptInfo
.VERSION 2.0
.GUID 90082fa1-0b84-49fb-a00e-0a624fbb6584
.AUTHOR manikb
.COMPANYNAME Microsoft Corporation
.COPYRIGHT (c) 2015 Microsoft Corporation. All rights reserved.
.TAGS Tag1 Tag2 Tag-Script-WithDependencies2-2.0
.LICENSEURI http://script-withdependencies2.com/license
.PROJECTURI http://script-withdependencies2.com/
.ICONURI http://script-withdependencies2.com/icon
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS Required-Script1,Required-Script2,Required-Script3
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
Script-WithDependencies2 release notes
#>
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'}
#Requires -Module @{RequiredVersion = '2.5'; ModuleName = 'RequiredModule3'}
#Requires -Module @{ModuleVersion = '1.1'; ModuleName = 'RequiredModule4'; MaximumVersion = '2.0'}
#Requires -Module @{MaximumVersion = '1.5'; ModuleName = 'RequiredModule5'}
<#
.DESCRIPTION
Description for the Script-WithDependencies2 script
#>
Param()
Function Test-FunctionFromScript\_Script-WithDependencies2 { Get-Date }
Workflow Test-WorkflowFromScript\_Script-WithDependencies2 { Get-Date }
```

