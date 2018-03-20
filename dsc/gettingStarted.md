---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Introdução à Configuração de Estado Desejado do PowerShell"
ms.openlocfilehash: 04404696bef128805e4f1c191711eaab33cf7e4c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="48b60-103">Introdução à Configuração de Estado Desejado do PowerShell</span><span class="sxs-lookup"><span data-stu-id="48b60-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="48b60-104">Este guia descreve como começar a criar documentos de Configuração de Estado Desejado do PowerShell e aplicá-los aos computadores.</span><span class="sxs-lookup"><span data-stu-id="48b60-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="48b60-105">Assume que há uma familiaridade básica com cmdlets, módulos e funções do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48b60-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span> 


## <a name="create-a-configuration"></a><span data-ttu-id="48b60-106">Criar uma configuração</span><span class="sxs-lookup"><span data-stu-id="48b60-106">Create a Configuration</span></span> ##

<span data-ttu-id="48b60-107">[**Configurações**](https://msdn.microsoft.com/powershell/dsc/configurations) são documentos que descrevem um ambiente.</span><span class="sxs-lookup"><span data-stu-id="48b60-107">[**Configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="48b60-108">Os ambientes consistem em "**nós**", que normalmente são máquinas virtuais ou físicas.</span><span class="sxs-lookup"><span data-stu-id="48b60-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span> 

<span data-ttu-id="48b60-109">As configurações podem vir de várias formas.</span><span class="sxs-lookup"><span data-stu-id="48b60-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="48b60-110">A maneira mais fácil de criar uma nova configuração é criar um arquivo .ps1 (script do PowerShell).</span><span class="sxs-lookup"><span data-stu-id="48b60-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="48b60-111">Para fazer isso, abra o editor escolhido por você.</span><span class="sxs-lookup"><span data-stu-id="48b60-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="48b60-112">O ISE do PowerShell é uma boa opção, pois entenda a DSC nativamente.</span><span class="sxs-lookup"><span data-stu-id="48b60-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="48b60-113">Salve o seguinte como um PS1:</span><span class="sxs-lookup"><span data-stu-id="48b60-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="48b60-114">Partes de uma Configuração</span><span class="sxs-lookup"><span data-stu-id="48b60-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="48b60-115">**Configuration** é uma palavra-chave que foi adicionada ao PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="48b60-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="48b60-116">Significa um tipo especial de função do PowerShell usado pela Configuração de Estado Desejado.</span><span class="sxs-lookup"><span data-stu-id="48b60-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="48b60-117">Neste exemplo, a função é chamada de myFirstConfiguration.</span><span class="sxs-lookup"><span data-stu-id="48b60-117">In this example, the function is named myFirstConfiguration.</span></span> 

<span data-ttu-id="48b60-118">A próxima linha é uma instrução de importação, semelhante à importação de um módulo.</span><span class="sxs-lookup"><span data-stu-id="48b60-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="48b60-119">Será discutida posteriormente.</span><span class="sxs-lookup"><span data-stu-id="48b60-119">It will be discussed later on.</span></span>

<span data-ttu-id="48b60-120">"Nó" define o nome do computador em que essa configuração vai agir.</span><span class="sxs-lookup"><span data-stu-id="48b60-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="48b60-121">Embora ela seja editada localmente, as configurações podem chegar a nós remotos e configurá-los.</span><span class="sxs-lookup"><span data-stu-id="48b60-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span> 

<span data-ttu-id="48b60-122">Os nós podem ser nomes ou endereços IP de computador.</span><span class="sxs-lookup"><span data-stu-id="48b60-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="48b60-123">Você pode ter vários nós em um único documento de configuração.</span><span class="sxs-lookup"><span data-stu-id="48b60-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="48b60-124">Usando [dados de configuração](https://msdn.microsoft.com/powershell/dsc/configdata), também é possível aplicar a mesma configuração a vários nós.</span><span class="sxs-lookup"><span data-stu-id="48b60-124">Using [configuration data](https://msdn.microsoft.com/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="48b60-125">Nesse caso, o nó é "localhost" - que significa o computador local.</span><span class="sxs-lookup"><span data-stu-id="48b60-125">In this case, the node is "localhost" - which means the local computer.</span></span> 

<span data-ttu-id="48b60-126">O próximo item é um [**recurso**](https://msdn.microsoft.com/powershell/dsc/resources).</span><span class="sxs-lookup"><span data-stu-id="48b60-126">The next item is a [**resource**](https://msdn.microsoft.com/powershell/dsc/resources).</span></span> <span data-ttu-id="48b60-127">Os recursos são blocos de construção de configurações.</span><span class="sxs-lookup"><span data-stu-id="48b60-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="48b60-128">Cada recurso é um módulo que define a lógica de implementação de um único aspecto de um computador.</span><span class="sxs-lookup"><span data-stu-id="48b60-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="48b60-129">Você pode exibir todos os recursos no seu computador executando **Get-DscResource** no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48b60-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="48b60-130">Os recursos devem estar presentes no computador local e ser importados antes que possam ser usados em uma configuração com **Import-DscResource**, que está na segunda linha dessa configuração.</span><span class="sxs-lookup"><span data-stu-id="48b60-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span> 

<span data-ttu-id="48b60-131">**Aplicando uma Configuração**</span><span class="sxs-lookup"><span data-stu-id="48b60-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="48b60-132">Se o script acima for salvo e executado, nenhuma saída será produzida.</span><span class="sxs-lookup"><span data-stu-id="48b60-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="48b60-133">Isso ocorre porque a configuração é apenas uma função e o script acima definiu a função, mas ainda não a executou.</span><span class="sxs-lookup"><span data-stu-id="48b60-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="48b60-134">Depois de ser definida, a função precisa ser chamada:</span><span class="sxs-lookup"><span data-stu-id="48b60-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="48b60-135">Quando executadas, as funções de configuração validam a configuração.</span><span class="sxs-lookup"><span data-stu-id="48b60-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="48b60-136">Ela não deve ter nenhum erro de sintaxe, os recursos devem ter todos os parâmetros obrigatórios definidos e todos os recursos devem ser importados antes da execução.</span><span class="sxs-lookup"><span data-stu-id="48b60-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="48b60-137">Depois de ser executada, a configuração cria uma pasta com seu nome contendo um **arquivo .MOF file** para cada nó na configuração.</span><span class="sxs-lookup"><span data-stu-id="48b60-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="48b60-138">O arquivo MOF é um formato de gerenciamento baseado em padrões que é usado pela DSC do PowerShell para se comunicar pela rede.</span><span class="sxs-lookup"><span data-stu-id="48b60-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="48b60-139">Para aplicar a configuração:</span><span class="sxs-lookup"><span data-stu-id="48b60-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="48b60-140">É criado um trabalho do PowerShell que atinge os nós na configuração e os configura.</span><span class="sxs-lookup"><span data-stu-id="48b60-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="48b60-141">Para ver a saída do trabalho, use -Wait.</span><span class="sxs-lookup"><span data-stu-id="48b60-141">To see the output of the job, use -Wait.</span></span> 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```

