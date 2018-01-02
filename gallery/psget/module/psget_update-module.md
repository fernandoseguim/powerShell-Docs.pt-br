---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Update-Module
ms.openlocfilehash: 66535cd5b1f44e108c2bc47fa343c77c86bb21dc
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2017
---
# <a name="update-module"></a><span data-ttu-id="7d902-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="7d902-103">Update-Module</span></span>

<span data-ttu-id="7d902-104">Baixa e instala a versão mais recente dos módulos especificados de uma galeria online para o computador local.</span><span class="sxs-lookup"><span data-stu-id="7d902-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="7d902-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="7d902-105">Description</span></span>

<span data-ttu-id="7d902-106">O cmdlet Update-Module instala uma versão mais recente de um módulo do Windows PowerShell que foi instalado da galeria online executando Install-Module no computador local.</span><span class="sxs-lookup"><span data-stu-id="7d902-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="7d902-107">Por padrão, a versão mais recente do módulo especificado disponível na galeria online é instalada, a menos que você especifique uma versão obrigatória.</span><span class="sxs-lookup"><span data-stu-id="7d902-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="7d902-108">Você pode atualizar um módulo existente instalado especificando o nome do módulo. Update-Module procura pelo $env:PSModulePath do módulo que você deseja atualizar.</span><span class="sxs-lookup"><span data-stu-id="7d902-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="7d902-109">Executar Update-Module sem o parâmetro de nome atualiza todos os módulos que podem ser atualizados no computador local.</span><span class="sxs-lookup"><span data-stu-id="7d902-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="7d902-110">Observações</span><span class="sxs-lookup"><span data-stu-id="7d902-110">Notes</span></span>

- <span data-ttu-id="7d902-111">Esse cmdlet é executado no Windows PowerShell 3.0 ou em versões posteriores do Windows PowerShell, no Windows 7 ou no Windows 2008 R2 e em versões posteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="7d902-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="7d902-112">Se o módulo especificado com o parâmetro de nome não tiver sido instalado usando Install-Module, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="7d902-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="7d902-113">Você só pode executar Update-Module em módulos que foram instalados da galeria online executando Install-Module.</span><span class="sxs-lookup"><span data-stu-id="7d902-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="7d902-114">Se Update-Module tentar atualizar binários que estão em uso, ele retornará um erro que identifica os processos com problema e instruirá o usuário a repetir Update-Module depois de interromper os processos.</span><span class="sxs-lookup"><span data-stu-id="7d902-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="7d902-115">No PowerShell 5.0 ou em versões mais recentes, quando Update-Module atualiza um módulo, ele adiciona a versão mais recente (ou especificada) do módulo, portanto, as versões mais antigas e mais recentes ficam lado a lado no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="7d902-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="7d902-116">Seria útil dizer isso e mostrar um exemplo da saída desses comandos.</span><span class="sxs-lookup"><span data-stu-id="7d902-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="7d902-117">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="7d902-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="7d902-118">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="7d902-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="7d902-119">Update-Module</span><span class="sxs-lookup"><span data-stu-id="7d902-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="7d902-120">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="7d902-120">Example commands</span></span>

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a><span data-ttu-id="7d902-121">Atualizar o módulo com uma versão de pré-lançamento, requer o sinalizador -AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="7d902-121">Update the module with a prerelease version, requires -AllowPrerelease flag</span></span>
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="7d902-122">Atualize o módulo TestDepWithNestedRequiredModules1 com dependências.</span><span class="sxs-lookup"><span data-stu-id="7d902-122">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```

