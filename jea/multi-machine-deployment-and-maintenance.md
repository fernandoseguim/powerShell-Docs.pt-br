---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "manutenção e implantação de vários computadores"
ms.technology: powershell
ms.openlocfilehash: 8117d0d12c062b460cb7117b54c138c8db5a1d0c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: pt-BR
---
# <a name="multi-machine-deployment-and-maintenance"></a><span data-ttu-id="e2b4d-103">Manutenção e implantação de vários computador</span><span class="sxs-lookup"><span data-stu-id="e2b4d-103">Multi-machine Deployment and Maintenance</span></span>
<span data-ttu-id="e2b4d-104">Neste ponto, você já implantou o JEA para sistemas locais várias vezes.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-104">At this point, you have deployed JEA to local systems several times.</span></span>
<span data-ttu-id="e2b4d-105">Como seu ambiente de produção provavelmente consiste em mais de um computador, é importante seguir as etapas essenciais no processo de implantação que deve ser repetido em cada computador.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-105">Because your production environment probably consists of more than one machine, it's important to walk through the critical steps in the deployment process that must be repeated on each machine.</span></span>

## <a name="high-level-steps"></a><span data-ttu-id="e2b4d-106">Etapas de alto nível:</span><span class="sxs-lookup"><span data-stu-id="e2b4d-106">High Level Steps:</span></span>
1.  <span data-ttu-id="e2b4d-107">Copie seus módulos (com Capacidades de Função) para cada nó.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-107">Copy your modules (with Role Capabilities) to each node.</span></span>
2.  <span data-ttu-id="e2b4d-108">Copie os arquivos de configuração de sessão para cada nó.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-108">Copy your session configuration files to each node.</span></span>
3.  <span data-ttu-id="e2b4d-109">Execute `Register-PSSessionConfiguration` com sua sessão de configuração.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-109">Run `Register-PSSessionConfiguration` with your session configuration.</span></span>
4.  <span data-ttu-id="e2b4d-110">Mantenha uma cópia da sua configuração de sessão e kits de ferramentas em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-110">Keep a copy of your session configuration and toolkits in a secure location.</span></span>
<span data-ttu-id="e2b4d-111">Ao fazer modificações, é recomendável ter uma "única fonte verdadeira".</span><span class="sxs-lookup"><span data-stu-id="e2b4d-111">As you make modifications, it's good to have a "single source of truth."</span></span>

## <a name="example-script"></a><span data-ttu-id="e2b4d-112">Script de Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2b4d-112">Example Script</span></span>
<span data-ttu-id="e2b4d-113">Veja este exemplo de script de implantação.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-113">Here's an example script for deployment.</span></span>
<span data-ttu-id="e2b4d-114">Para usá-lo em seu ambiente, você terá que usar os nomes ou caminhos de compartilhamentos de arquivo reais e módulos.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-114">To use it in your environment, you'll have to use the names/paths of real file shares and modules.</span></span>
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## <a name="modifying-capabilities"></a><span data-ttu-id="e2b4d-115">Modificar Capacidades</span><span class="sxs-lookup"><span data-stu-id="e2b4d-115">Modifying Capabilities</span></span>
<span data-ttu-id="e2b4d-116">Ao lidar com vários computadores, é importante que as modificações sejam distribuídas de maneira consistente.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-116">When dealing with many machines, it's important that modifications are rolled out in a consistent manner.</span></span>
<span data-ttu-id="e2b4d-117">Uma vez que JEA tem um recurso de DSC, isso ajuda a garantir que seu ambiente esteja sincronizado.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-117">Once JEA has a DSC Resource, this will help ensure your environment is in sync.</span></span>
<span data-ttu-id="e2b4d-118">Até lá, é altamente recomendável manter uma cópia mestra de suas configurações de sessão e implantar novamente cada vez que fizer uma alteração.</span><span class="sxs-lookup"><span data-stu-id="e2b4d-118">Until that time, we highly recommend you keep a master copy of your session configurations and re-deploy each time you make a modification.</span></span>

## <a name="removing-capabilities"></a><span data-ttu-id="e2b4d-119">Remover Capacidades</span><span class="sxs-lookup"><span data-stu-id="e2b4d-119">Removing Capabilities</span></span>
<span data-ttu-id="e2b4d-120">Para remover a configuração de JEA de seus sistemas, use o seguinte comando em cada computador:</span><span class="sxs-lookup"><span data-stu-id="e2b4d-120">To remove your JEA configuration from your systems, use the following command on each machine:</span></span>
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```

