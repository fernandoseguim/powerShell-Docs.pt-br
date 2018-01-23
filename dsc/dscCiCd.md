---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Criando um pipeline de integração contínua e implantação contínua com DSC"
ms.openlocfilehash: 5f7583fb93b69bbe4103b34b79b3a859c9cee8a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="df2e7-103">Criando um pipeline de integração contínua e implantação contínua com DSC</span><span class="sxs-lookup"><span data-stu-id="df2e7-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="df2e7-104">Este exemplo demonstra como criar um pipeline de CI/CD (implantação contínua/integração contínua) usando o PowerShell, a DSC, o Pester e o Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="df2e7-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="df2e7-105">Depois que o pipeline é criado e configurado, você pode usá-lo para implantar, configurar e testar completamente um servidor DNS e os registros de host associados.</span><span class="sxs-lookup"><span data-stu-id="df2e7-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span> <span data-ttu-id="df2e7-106">Esse processo simula a primeira parte de um pipeline que seria usado em um ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="df2e7-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="df2e7-107">Um pipeline de CI/CD automatizado ajuda a atualizar softwares com mais rapidez e confiança, garantir que todo o código seja testado e que um build atual do código esteja sempre disponível.</span><span class="sxs-lookup"><span data-stu-id="df2e7-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="df2e7-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="df2e7-108">Prerequisites</span></span>

<span data-ttu-id="df2e7-109">Para usar este exemplo, você deve estar familiarizado com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="df2e7-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="df2e7-110">Os conceitos de CI-CD.</span><span class="sxs-lookup"><span data-stu-id="df2e7-110">CI-CD concepts.</span></span> <span data-ttu-id="df2e7-111">Uma boa referência pode ser encontrada em [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf) (O modelo de pipeline de versão).</span><span class="sxs-lookup"><span data-stu-id="df2e7-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="df2e7-112">O controle do código-fonte [Git](https://git-scm.com/)</span><span class="sxs-lookup"><span data-stu-id="df2e7-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="df2e7-113">A estrutura de testes [Pester](https://github.com/pester/Pester)</span><span class="sxs-lookup"><span data-stu-id="df2e7-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- <span data-ttu-id="df2e7-114">O [Team Foundation Server](https://www.visualstudio.com/tfs/)</span><span class="sxs-lookup"><span data-stu-id="df2e7-114">[Team Foundation Server](https://www.visualstudio.com/tfs/)</span></span>

## <a name="what-you-will-need"></a><span data-ttu-id="df2e7-115">O que será necessário</span><span class="sxs-lookup"><span data-stu-id="df2e7-115">What you will need</span></span>

<span data-ttu-id="df2e7-116">Para compilar e executar esse exemplo, você precisará de um ambiente com vários computadores e/ou máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="df2e7-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="df2e7-117">Remota</span><span class="sxs-lookup"><span data-stu-id="df2e7-117">Client</span></span>

<span data-ttu-id="df2e7-118">Este é o computador no qual você fará todo o trabalho de configurar e executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="df2e7-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="df2e7-119">O computador cliente deve ser um computador Windows com o seguinte instalado:</span><span class="sxs-lookup"><span data-stu-id="df2e7-119">The client computer must be a Windows computer with the following installed:</span></span>
- [<span data-ttu-id="df2e7-120">Git</span><span class="sxs-lookup"><span data-stu-id="df2e7-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="df2e7-121">um repositório git local clonado de https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="df2e7-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="df2e7-122">um editor de texto, como o [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="df2e7-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="df2e7-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="df2e7-123">TFSSrv1</span></span>

<span data-ttu-id="df2e7-124">O computador que hospeda o servidor do TFS no qual você definirá o build e a versão.</span><span class="sxs-lookup"><span data-stu-id="df2e7-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="df2e7-125">Este computador deve ter o [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) instalado.</span><span class="sxs-lookup"><span data-stu-id="df2e7-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="df2e7-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="df2e7-126">BuildAgent</span></span>

<span data-ttu-id="df2e7-127">O computador que executa o agente de build do Windows que compila o projeto.</span><span class="sxs-lookup"><span data-stu-id="df2e7-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="df2e7-128">Este computador deve ter um agente de build do Windows instalado e em execução.</span><span class="sxs-lookup"><span data-stu-id="df2e7-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="df2e7-129">Consulte [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) (Implantar um agente no Windows ) para obter instruções de como instalar e executar um agente de build do Windows.</span><span class="sxs-lookup"><span data-stu-id="df2e7-129">See [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="df2e7-130">Você também precisa instalar os módulos de DSC `xDnsServer` e `xNetworking` nesse computador.</span><span class="sxs-lookup"><span data-stu-id="df2e7-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="df2e7-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="df2e7-131">TestAgent1</span></span>

<span data-ttu-id="df2e7-132">Este é o computador que está configurado como um servidor DNS pela configuração DSC neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="df2e7-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="df2e7-133">O computador deve estar executando o [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="df2e7-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="df2e7-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="df2e7-134">TestAgent2</span></span>

<span data-ttu-id="df2e7-135">Este é o computador que hospeda o site, que este exemplo configura.</span><span class="sxs-lookup"><span data-stu-id="df2e7-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="df2e7-136">O computador deve estar executando o [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="df2e7-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> 

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="df2e7-137">Adicione o código no TFS</span><span class="sxs-lookup"><span data-stu-id="df2e7-137">Add the code to TFS</span></span>

<span data-ttu-id="df2e7-138">Vamos começar criando um repositório Git no TFS e importando o código de seu repositório local no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="df2e7-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="df2e7-139">Se você ainda não clonou o repositório Demo_CI no computador cliente, faça isso agora, executando o seguinte comando git:</span><span class="sxs-lookup"><span data-stu-id="df2e7-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="df2e7-140">No computador cliente, navegue até o servidor do TFS em um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="df2e7-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="df2e7-141">No TFS, [Crie um novo projeto de equipe](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) chamado Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="df2e7-141">In TFS, [Create a new team project](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) named Demo_CI.</span></span>

    <span data-ttu-id="df2e7-142">Verifique se o **Controle de versão** é definido como **Git**.</span><span class="sxs-lookup"><span data-stu-id="df2e7-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="df2e7-143">No computador cliente, adicione um remoto no repositório que você acabou de criar no TFS com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="df2e7-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

    `git remote add tfs <YourTFSRepoURL>`

    <span data-ttu-id="df2e7-144">Em que `<YourTFSRepoURL>` é a URL clone para o repositório do TFS que você criou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="df2e7-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

    <span data-ttu-id="df2e7-145">Se você não souber onde encontrar essa URL, consulte [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone) (Clonar um repositório Git existente).</span><span class="sxs-lookup"><span data-stu-id="df2e7-145">If you don't know where to find this URL, see [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span></span>
1. <span data-ttu-id="df2e7-146">Envie o código por push de seu repositório local para o repositório do TFS com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="df2e7-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

    `git push tfs --all`
1. <span data-ttu-id="df2e7-147">O repositório do TFS será preenchido com o código Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="df2e7-147">The TFS repository will be populated with the Demo_CI code.</span></span>

><span data-ttu-id="df2e7-148">**Observação:** este exemplo usa o código na ramificação `ci-cd-example` do repositório Git.</span><span class="sxs-lookup"><span data-stu-id="df2e7-148">**Note:** This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
><span data-ttu-id="df2e7-149">Assegure-se de especificar essa ramificação como a ramificação padrão em seu projeto do TFS e para os gatilhos de CI/CD que você criar.</span><span class="sxs-lookup"><span data-stu-id="df2e7-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="df2e7-150">Noções básicas sobre o código</span><span class="sxs-lookup"><span data-stu-id="df2e7-150">Understanding the code</span></span>

<span data-ttu-id="df2e7-151">Antes de criar os pipelines de build e implantação, vamos analisar parte do código para entender o que está acontecendo.</span><span class="sxs-lookup"><span data-stu-id="df2e7-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="df2e7-152">No computador cliente, abra o editor de texto favorito e navegue até a raiz do repositório Git Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="df2e7-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="df2e7-153">A configuração DSC</span><span class="sxs-lookup"><span data-stu-id="df2e7-153">The DSC configuration</span></span>

<span data-ttu-id="df2e7-154">Abra o arquivo `DNSServer.ps1` (da raiz do repositório local Demo_CI, `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="df2e7-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="df2e7-155">Este arquivo contém a configuração DSC que configura o servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="df2e7-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="df2e7-156">Aqui está ele por inteiro:</span><span class="sxs-lookup"><span data-stu-id="df2e7-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="df2e7-157">Observe a instrução `Node`:</span><span class="sxs-lookup"><span data-stu-id="df2e7-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="df2e7-158">Isso localiza todos os nós que foram definidos como tendo uma função de `DNSServer` nos [dados de configuração](configData.md), que são criados pelo script `DevEnv.ps1`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="df2e7-159">Usar dados de configuração para definir nós é importante ao fazer CI porque as informações do nó provavelmente serão alteradas entre os ambientes e usar dados de configuração permite fazer alterações facilmente nas informações do nó sem alterar o código de configuração.</span><span class="sxs-lookup"><span data-stu-id="df2e7-159">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="df2e7-160">No primeiro bloco de recurso, a configuração chama o [WindowsFeature](windowsFeatureResource.md) para garantir que o recurso DNS esteja habilitado.</span><span class="sxs-lookup"><span data-stu-id="df2e7-160">In the first resource block, the configuration calls the [WindowsFeature](windowsFeatureResource.md) to ensure that the DNS feature is enabled.</span></span> <span data-ttu-id="df2e7-161">Os blocos de recurso que seguem chamam recursos do módulo [xDnsServer](https://github.com/PowerShell/xDnsServer) para configurar os registros DNS e a zona primária.</span><span class="sxs-lookup"><span data-stu-id="df2e7-161">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="df2e7-162">Observe que os dois blocos `xDnsRecord` são encapsulados em loops `foreach` que iteram em matrizes nos dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="df2e7-162">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="df2e7-163">Novamente, os dados de configuração são criados pelo script `DevEnv.ps1`, o que veremos a seguir.</span><span class="sxs-lookup"><span data-stu-id="df2e7-163">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="df2e7-164">Dados de configuração</span><span class="sxs-lookup"><span data-stu-id="df2e7-164">Configuration data</span></span>

<span data-ttu-id="df2e7-165">O arquivo `DevEnv.ps1` (da raiz do repositório local Demo_CI, `./InfraDNS/DevEnv.ps1`) especifica os dados de configuração específicos ao ambiente em uma tabela de hash e, em seguida, passa essa tabela de hash para uma chamada da função `New-DscConfigurationDataDocument`, que é definida em `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="df2e7-165">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="df2e7-166">O arquivo `DevEnv.ps1`:</span><span class="sxs-lookup"><span data-stu-id="df2e7-166">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="df2e7-167">A função `New-DscConfigurationDataDocument` (definida em `\Assets\DscPipelineTools\DscPipelineTools.psm1`) cria programaticamente um documento de dados de configuração da tabela de hash (dados do nó) e da matriz (dados que não são do nó) que são passados como parâmetros `RawEnvData` e `OtherEnvData`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-167">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="df2e7-168">Em nosso caso, somente o parâmetro `RawEnvData` é usado.</span><span class="sxs-lookup"><span data-stu-id="df2e7-168">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="df2e7-169">O script de build psake</span><span class="sxs-lookup"><span data-stu-id="df2e7-169">The psake build script</span></span>

<span data-ttu-id="df2e7-170">O script de build [psake](https://github.com/psake/psake) definido em `Build.ps1` (da raiz do repositório Demo_CI, `./InfraDNS/Build.ps1`) define as tarefas que fazem parte do build.</span><span class="sxs-lookup"><span data-stu-id="df2e7-170">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="df2e7-171">Ele também define de quais outras tarefas cada tarefa depende.</span><span class="sxs-lookup"><span data-stu-id="df2e7-171">It also defines which other tasks each task depends on.</span></span> <span data-ttu-id="df2e7-172">Quando chamado, o script psake garante que a tarefa especificada (ou a tarefa chamada `Default` se não houver nenhuma especificada) seja executada e que todas as dependências também sejam executadas (isso é recursivo, para que as dependências das dependências sejam executadas e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="df2e7-172">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="df2e7-173">Neste exemplo, a tarefa `Default` é definida como:</span><span class="sxs-lookup"><span data-stu-id="df2e7-173">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="df2e7-174">A tarefa `Default` não tem nenhuma implementação em si, mas tem uma dependência da tarefa `CompileConfigs`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-174">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="df2e7-175">A cadeia de dependências de tarefa resultante garante que todas as tarefas no script de build sejam executadas.</span><span class="sxs-lookup"><span data-stu-id="df2e7-175">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="df2e7-176">Neste exemplo, o script psake é invocado por uma chamada para `Invoke-PSake` no arquivo `Initiate.ps1` (localizado na raiz do repositório Demo_CI):</span><span class="sxs-lookup"><span data-stu-id="df2e7-176">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="df2e7-177">Quando criarmos a definição de build para o nosso exemplo no TFS, forneceremos o arquivo de script psake como o parâmetro `fileName` para esse script.</span><span class="sxs-lookup"><span data-stu-id="df2e7-177">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="df2e7-178">O script de build define as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="df2e7-178">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="df2e7-179">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="df2e7-179">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="df2e7-180">Executa `DevEnv.ps1`, que gera o arquivo de dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="df2e7-180">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="df2e7-181">InstallModules</span><span class="sxs-lookup"><span data-stu-id="df2e7-181">InstallModules</span></span>

<span data-ttu-id="df2e7-182">Instala os módulos necessários para a configuração `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-182">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="df2e7-183">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="df2e7-183">ScriptAnalysis</span></span>

<span data-ttu-id="df2e7-184">Chama o [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="df2e7-184">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="df2e7-185">UnitTests</span><span class="sxs-lookup"><span data-stu-id="df2e7-185">UnitTests</span></span>

<span data-ttu-id="df2e7-186">Executa os testes de unidade do [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="df2e7-186">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="df2e7-187">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="df2e7-187">CompileConfigs</span></span>

<span data-ttu-id="df2e7-188">Compila a configuração (`DNSServer.ps1`) em um arquivo MOF, usando os dados de configuração gerados pela tarefa `GenerateEnvironmentFiles`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-188">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="df2e7-189">Clean</span><span class="sxs-lookup"><span data-stu-id="df2e7-189">Clean</span></span>

<span data-ttu-id="df2e7-190">Cria as pastas usadas para o exemplo e remove todos os resultados do teste, os arquivos de dados de configuração e os módulos das execuções anteriores.</span><span class="sxs-lookup"><span data-stu-id="df2e7-190">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="df2e7-191">O script de implantação psake</span><span class="sxs-lookup"><span data-stu-id="df2e7-191">The psake deploy script</span></span>

<span data-ttu-id="df2e7-192">O script de implantação [psake](https://github.com/psake/psake) definido em `Deploy.ps1` (da raiz do repositório Demo_CI, `./InfraDNS/Deploy.ps1`) define as tarefas que implantam e executam a configuração.</span><span class="sxs-lookup"><span data-stu-id="df2e7-192">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="df2e7-193">`Deploy.ps1` define as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="df2e7-193">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="df2e7-194">DeployModules</span><span class="sxs-lookup"><span data-stu-id="df2e7-194">DeployModules</span></span>

<span data-ttu-id="df2e7-195">Inicia uma sessão do PowerShell no `TestAgent1` e instala os módulos que contêm os recursos de DSC necessários para a configuração.</span><span class="sxs-lookup"><span data-stu-id="df2e7-195">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="df2e7-196">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="df2e7-196">DeployConfigs</span></span>

<span data-ttu-id="df2e7-197">Chama o cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) para executar a configuração em `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-197">Calls the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="df2e7-198">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="df2e7-198">IntegrationTests</span></span>

<span data-ttu-id="df2e7-199">Executa os testes de integração do [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="df2e7-199">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="df2e7-200">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="df2e7-200">AcceptanceTests</span></span>

<span data-ttu-id="df2e7-201">Executa os testes de aceitação do [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="df2e7-201">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="df2e7-202">Clean</span><span class="sxs-lookup"><span data-stu-id="df2e7-202">Clean</span></span>

<span data-ttu-id="df2e7-203">Remove todos os módulos instalados nas execuções anteriores e verifica se a pasta de resultados do teste exista.</span><span class="sxs-lookup"><span data-stu-id="df2e7-203">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="df2e7-204">Scripts de teste</span><span class="sxs-lookup"><span data-stu-id="df2e7-204">Test scripts</span></span>

<span data-ttu-id="df2e7-205">Os testes de unidade, integração e aceitação são definidos em scripts na pasta `Tests` (da raiz do repositório Demo_CI, `./InfraDNS/Tests`), cada um em arquivos denominados `DNSServer.tests.ps1` em suas respectivas pastas.</span><span class="sxs-lookup"><span data-stu-id="df2e7-205">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="df2e7-206">O teste de scripts usam as sintaxes [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="df2e7-206">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="df2e7-207">Testes de unidade</span><span class="sxs-lookup"><span data-stu-id="df2e7-207">Unit tests</span></span>

<span data-ttu-id="df2e7-208">Os testes de unidade testam as próprias configurações DSC para garantir que elas farão o que é esperado ao serem executadas.</span><span class="sxs-lookup"><span data-stu-id="df2e7-208">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="df2e7-209">O script de teste de unidade usa o [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="df2e7-209">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="df2e7-210">Testes de integração</span><span class="sxs-lookup"><span data-stu-id="df2e7-210">Integration tests</span></span>

<span data-ttu-id="df2e7-211">Os testes de integração testam a configuração do sistema para garantir que quando for integrado com outros componentes, o sistema esteja configurado como esperado.</span><span class="sxs-lookup"><span data-stu-id="df2e7-211">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="df2e7-212">Esses testes são executados no nó de destino depois que ele foi configurado com DSC.</span><span class="sxs-lookup"><span data-stu-id="df2e7-212">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="df2e7-213">O script de teste de integração usa uma combinação da sintaxe [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="df2e7-213">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="df2e7-214">Testes de aceitação</span><span class="sxs-lookup"><span data-stu-id="df2e7-214">Acceptance tests</span></span>

<span data-ttu-id="df2e7-215">Os testes de aceitação testam o sistema para garantir que ele se comporte como esperado.</span><span class="sxs-lookup"><span data-stu-id="df2e7-215">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="df2e7-216">Por exemplo, ele testa para garantir que uma página da Web retorne as informações corretas quando consultada.</span><span class="sxs-lookup"><span data-stu-id="df2e7-216">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="df2e7-217">Esses testes são executados remotamente do nó de destino para testar os cenários reais.</span><span class="sxs-lookup"><span data-stu-id="df2e7-217">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="df2e7-218">O script de teste de integração usa uma combinação da sintaxe [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="df2e7-218">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="df2e7-219">Definir o build</span><span class="sxs-lookup"><span data-stu-id="df2e7-219">Define the build</span></span>

<span data-ttu-id="df2e7-220">Agora que já carregado o código para o TFS e examinamos o que ele faz, vamos definir o build.</span><span class="sxs-lookup"><span data-stu-id="df2e7-220">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="df2e7-221">Aqui, vamos abordar apenas as etapas de build que você adicionará ao build.</span><span class="sxs-lookup"><span data-stu-id="df2e7-221">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="df2e7-222">Para obter instruções de como criar uma definição de build no TFS, consulte [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create) (Criar e enfileirar uma fila uma definição de build).</span><span class="sxs-lookup"><span data-stu-id="df2e7-222">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create).</span></span>

<span data-ttu-id="df2e7-223">Crie uma nova definição de build (selecione o modelo **Vazio**) denominado "InfraDNS".</span><span class="sxs-lookup"><span data-stu-id="df2e7-223">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="df2e7-224">Adicione as seguintes etapas em sua definição de build:</span><span class="sxs-lookup"><span data-stu-id="df2e7-224">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="df2e7-225">Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="df2e7-225">PowerShell Script</span></span>
- <span data-ttu-id="df2e7-226">Publicar resultados de teste</span><span class="sxs-lookup"><span data-stu-id="df2e7-226">Publish Test Results</span></span>
- <span data-ttu-id="df2e7-227">Copiar arquivos</span><span class="sxs-lookup"><span data-stu-id="df2e7-227">Copy Files</span></span>
- <span data-ttu-id="df2e7-228">Publicar artefato</span><span class="sxs-lookup"><span data-stu-id="df2e7-228">Publish Artifact</span></span>

<span data-ttu-id="df2e7-229">Depois de adicionar essas etapas de build, edite as propriedades de cada etapa da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="df2e7-229">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="df2e7-230">Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="df2e7-230">PowerShell Script</span></span>

1. <span data-ttu-id="df2e7-231">Defina a propriedade **Tipo** como `File Path`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-231">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="df2e7-232">Defina a propriedade **Caminho de script** como `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-232">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="df2e7-233">Adicione `-fileName build` na propriedade **Argumentos**.</span><span class="sxs-lookup"><span data-stu-id="df2e7-233">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="df2e7-234">Essa etapa de build executa o arquivo `initiate.ps1`, que chama o script de build psake.</span><span class="sxs-lookup"><span data-stu-id="df2e7-234">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="df2e7-235">Publicar resultados de teste</span><span class="sxs-lookup"><span data-stu-id="df2e7-235">Publish Test Results</span></span>

1. <span data-ttu-id="df2e7-236">Defina o **Formato de resultado do teste** para `NUnit`</span><span class="sxs-lookup"><span data-stu-id="df2e7-236">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="df2e7-237">Defina os **Arquivos de resultados de teste** para `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="df2e7-237">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="df2e7-238">Defina o **Título da execução de teste** para `Unit`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-238">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="df2e7-239">Verifique se as **Opções de controle** **Habilitado** e **Sempre executar** estão selecionadas.</span><span class="sxs-lookup"><span data-stu-id="df2e7-239">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="df2e7-240">Essa etapa de build executa os testes de unidade no script Pester que vimos anteriormente e armazena os resultados na pasta `InfraDNS/Tests/Results/*.xml`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-240">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="df2e7-241">Copiar arquivos</span><span class="sxs-lookup"><span data-stu-id="df2e7-241">Copy Files</span></span>

1. <span data-ttu-id="df2e7-242">Adicione cada uma das linhas a seguir em **Conteúdo**:</span><span class="sxs-lookup"><span data-stu-id="df2e7-242">Add each of the following lines to **Contents**:</span></span>

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. <span data-ttu-id="df2e7-243">Defina **TargetFolder** para `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="df2e7-243">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="df2e7-244">Esta etapa copia os scripts de build e de teste no diretório de preparo para que eles possam ser publicados como artefatos de build na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="df2e7-244">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="df2e7-245">Publicar artefato</span><span class="sxs-lookup"><span data-stu-id="df2e7-245">Publish Artifact</span></span>

1. <span data-ttu-id="df2e7-246">Defina o **Caminho para publicar** para `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="df2e7-246">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="df2e7-247">Defina o **Nome do artefato** para `Deploy`</span><span class="sxs-lookup"><span data-stu-id="df2e7-247">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="df2e7-248">Defina o **Tipo de artefato** para `Server`</span><span class="sxs-lookup"><span data-stu-id="df2e7-248">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="df2e7-249">Selecione `Enabled` em **Opções de controle**</span><span class="sxs-lookup"><span data-stu-id="df2e7-249">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="df2e7-250">Habilitar integração contínua</span><span class="sxs-lookup"><span data-stu-id="df2e7-250">Enable continuous integration</span></span>

<span data-ttu-id="df2e7-251">Agora vamos definir um gatilho que faz com que o projeto seja compilado sempre que uma alteração for verificada na ramificação `ci-cd-example` do repositório git.</span><span class="sxs-lookup"><span data-stu-id="df2e7-251">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="df2e7-252">No TFS, clique na guia **Build e versão**</span><span class="sxs-lookup"><span data-stu-id="df2e7-252">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="df2e7-253">Selecione a definição de build `DNS Infra` e, em seguida, clique em **Editar**</span><span class="sxs-lookup"><span data-stu-id="df2e7-253">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="df2e7-254">Clique na guia **Gatilhos**</span><span class="sxs-lookup"><span data-stu-id="df2e7-254">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="df2e7-255">Selecione **CI (integração contínua)** e selecione `refs/heads/ci-cd-example` na lista suspensa da ramificação</span><span class="sxs-lookup"><span data-stu-id="df2e7-255">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="df2e7-256">Clique em **Salvar** e em **OK**</span><span class="sxs-lookup"><span data-stu-id="df2e7-256">Click **Save** and then **OK**</span></span>

<span data-ttu-id="df2e7-257">Agora qualquer alteração no repositório git do TFS vai disparar um build automatizado.</span><span class="sxs-lookup"><span data-stu-id="df2e7-257">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="df2e7-258">Criar a definição de versão</span><span class="sxs-lookup"><span data-stu-id="df2e7-258">Create the release definition</span></span>

<span data-ttu-id="df2e7-259">Vamos criar uma definição de versão para que o projeto seja implantado no ambiente de desenvolvimento com cada verificação de código.</span><span class="sxs-lookup"><span data-stu-id="df2e7-259">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="df2e7-260">Para fazer isso, adicione uma nova definição de versão associada à definição de build `InfraDNS` que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="df2e7-260">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="df2e7-261">Assegure-se de selecionar **Implantação contínua** para que uma nova versão seja disparada sempre que um novo build for concluído.</span><span class="sxs-lookup"><span data-stu-id="df2e7-261">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="df2e7-262">[[How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions) (Instruções: trabalhar com definições de versão)] e configure da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="df2e7-262">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="df2e7-263">Adicione as seguintes etapas na definição de versão:</span><span class="sxs-lookup"><span data-stu-id="df2e7-263">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="df2e7-264">Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="df2e7-264">PowerShell Script</span></span>
- <span data-ttu-id="df2e7-265">Publicar resultados de teste</span><span class="sxs-lookup"><span data-stu-id="df2e7-265">Publish Test Results</span></span>
- <span data-ttu-id="df2e7-266">Publicar resultados de teste</span><span class="sxs-lookup"><span data-stu-id="df2e7-266">Publish Test Results</span></span>

<span data-ttu-id="df2e7-267">Edite as etapas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="df2e7-267">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="df2e7-268">Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="df2e7-268">PowerShell Script</span></span>

1. <span data-ttu-id="df2e7-269">Defina o campo **Caminho de script** para `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="df2e7-269">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="df2e7-270">Defina o campo **Argumentos** para `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="df2e7-270">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="df2e7-271">Primeiro publicar resultados de teste</span><span class="sxs-lookup"><span data-stu-id="df2e7-271">First Publish Test Results</span></span>

1. <span data-ttu-id="df2e7-272">Selecione `NUnit` para o campo **Formato de resultado do teste**</span><span class="sxs-lookup"><span data-stu-id="df2e7-272">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="df2e7-273">Defina o campo **Arquivos de resultados do teste** para `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="df2e7-273">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="df2e7-274">Defina o **Título da execução de teste** para `Integration`</span><span class="sxs-lookup"><span data-stu-id="df2e7-274">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="df2e7-275">Em **Opções de controle**, marque **Sempre executar**</span><span class="sxs-lookup"><span data-stu-id="df2e7-275">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="df2e7-276">Segundo publicar resultados de teste</span><span class="sxs-lookup"><span data-stu-id="df2e7-276">Second Publish Test Results</span></span>

1. <span data-ttu-id="df2e7-277">Selecione `NUnit` para o campo **Formato de resultado do teste**</span><span class="sxs-lookup"><span data-stu-id="df2e7-277">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="df2e7-278">Defina o campo **Arquivos de resultados do teste** para `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="df2e7-278">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="df2e7-279">Defina o **Título da execução de teste** para `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="df2e7-279">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="df2e7-280">Em **Opções de controle**, marque **Sempre executar**</span><span class="sxs-lookup"><span data-stu-id="df2e7-280">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="df2e7-281">Verifique os resultados</span><span class="sxs-lookup"><span data-stu-id="df2e7-281">Verify your results</span></span>

<span data-ttu-id="df2e7-282">Agora, sempre que você enviar alterações por push na ramificação `ci-cd-example` para o TFS, será iniciado um novo build.</span><span class="sxs-lookup"><span data-stu-id="df2e7-282">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="df2e7-283">Se o build for concluído com êxito, uma nova implantação será disparada.</span><span class="sxs-lookup"><span data-stu-id="df2e7-283">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="df2e7-284">Você pode verificar o resultado da implantação, abrindo um navegador no computador cliente e navegando para `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-284">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="df2e7-285">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="df2e7-285">Next steps</span></span>

<span data-ttu-id="df2e7-286">Este exemplo configura o servidor DNS `TestAgent1` para que a URL `www.contoso.com` seja resolvida para `TestAgent2`, mas na verdade isso não implanta um site.</span><span class="sxs-lookup"><span data-stu-id="df2e7-286">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="df2e7-287">O esqueleto para fazer isso é fornecido no repositório na pasta `WebApp`.</span><span class="sxs-lookup"><span data-stu-id="df2e7-287">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="df2e7-288">Você pode usar os stubs fornecidos para criar scripts psake, testes do Pester e configurações DSC para implantar seu próprio site.</span><span class="sxs-lookup"><span data-stu-id="df2e7-288">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>







