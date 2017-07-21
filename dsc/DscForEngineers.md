---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Visão Geral da Configuração de Estado Desejado para Tomadores de Decisão"
ms.openlocfilehash: 50aaa407e02b8466a7df909711454e88b07c5c1f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="58db3-103">Visão Geral da Configuração de Estado Desejado para Engenheiros</span><span class="sxs-lookup"><span data-stu-id="58db3-103">Desired State Configuration Overview for Engineers</span></span> #

<span data-ttu-id="58db3-104">Elaboramos este documento para que as equipes de operações e os desenvolvedores possam compreender os benefícios da DSC (Configuração de Estado Desejado) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58db3-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="58db3-105">Para obter uma ideia mais abrangente do valor que a DSC fornece, confira o tópico [Visão Geral da Configuração de Estado Desejado para Tomadores de Decisão](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="58db3-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="58db3-106">Benefícios da Configuração de Estado Desejado</span><span class="sxs-lookup"><span data-stu-id="58db3-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="58db3-107">A DSC existe para:</span><span class="sxs-lookup"><span data-stu-id="58db3-107">DSC exists to:</span></span>
- <span data-ttu-id="58db3-108">Diminuir a complexidade da criação de scripts no Windows</span><span class="sxs-lookup"><span data-stu-id="58db3-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="58db3-109">Aumentar a velocidade de iteração</span><span class="sxs-lookup"><span data-stu-id="58db3-109">Increase the speed of iteration</span></span>

<span data-ttu-id="58db3-110">O conceito de "implantação contínua" está se tornando mais importante.</span><span class="sxs-lookup"><span data-stu-id="58db3-110">The concept of "continuous deployment" is becoming more important.</span></span> <span data-ttu-id="58db3-111">Implantação contínua significa a capacidade de implantar com frequência, possivelmente, várias vezes por dia.</span><span class="sxs-lookup"><span data-stu-id="58db3-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="58db3-112">A finalidade dessas implantações não é corrigir algo, mas sim publicar conteúdo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="58db3-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="58db3-113">Ao lançar novos recursos do desenvolvimento para as operações da forma mais tranquila e confiável possível, você aumenta o rendimento da nova lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="58db3-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="58db3-114">Existem duas tendências em jogo que aumentam essa necessidade de avançar rapidamente.</span><span class="sxs-lookup"><span data-stu-id="58db3-114">There are two trends at play which exacerbate this need to move quickly.</span></span> <span data-ttu-id="58db3-115">O avanço para a computação em nuvem implica uma mudança rápida, em escala, com uma ameaça constante de fracasso.</span><span class="sxs-lookup"><span data-stu-id="58db3-115">The move towards cloud computing implies rapid change, at scale, with a constant threat of failure.</span></span>
<span data-ttu-id="58db3-116">Em virtude dessas implicações, é necessário aumentar a automação.</span><span class="sxs-lookup"><span data-stu-id="58db3-116">These implications force automation in order to keep up.</span></span>
<span data-ttu-id="58db3-117">A criação da mentalidade "DevOps" é a solução para essas mudanças.</span><span class="sxs-lookup"><span data-stu-id="58db3-117">The creation of the "DevOps" mentality is a response to these changes.</span></span> 


<span data-ttu-id="58db3-118">A DSC é uma plataforma que fornece implantação, configuração e conformidade declarativas, autônomas e idempotentes (repetível).</span><span class="sxs-lookup"><span data-stu-id="58db3-118">DSC is a platform that provides declarative, autonomous and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="58db3-119">Na plataforma DSC, você garante que os componentes do datacenter tenham a configuração correta, evitando erros e falhas de implantação dispendiosas.</span><span class="sxs-lookup"><span data-stu-id="58db3-119">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="58db3-120">A DSC permite a implantação contínua, tratando as configurações DSC como parte do código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58db3-120">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="58db3-121">A configuração DSC deve ser atualizada como parte do aplicativo, garantindo que o conhecimento necessário para implantá-lo esteja sempre atualizado e pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="58db3-121">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>


## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="58db3-122">"Eu tenho o PowerShell, por que preciso da Configuração de Estado Desejado?"</span><span class="sxs-lookup"><span data-stu-id="58db3-122">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="58db3-123">As configurações DSC separam finalidade (ou seja, "o que eu quero fazer") de execução (isto é, "de que maneira eu quero fazê-lo").</span><span class="sxs-lookup"><span data-stu-id="58db3-123">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="58db3-124">Isso significa que a lógica de execução está incluída nos recursos.</span><span class="sxs-lookup"><span data-stu-id="58db3-124">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="58db3-125">Os usuários não precisam saber como implementar ou implantar um recurso quando um recurso DSC para este recurso está disponível.</span><span class="sxs-lookup"><span data-stu-id="58db3-125">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="58db3-126">Dessa forma, os usuários podem se concentrar na estrutura da implantação deles.</span><span class="sxs-lookup"><span data-stu-id="58db3-126">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="58db3-127">Por exemplo, os scripts do PowerShell devem ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="58db3-127">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="58db3-128">Esse script é fácil, simples e direto.</span><span class="sxs-lookup"><span data-stu-id="58db3-128">This script is simple, comprehensible, and straightforward.</span></span> <span data-ttu-id="58db3-129">No entanto, se tentar colocar o script em produção, você enfrentará vários problemas.</span><span class="sxs-lookup"><span data-stu-id="58db3-129">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="58db3-130">O que acontece se o script for executado duas vezes seguidas?</span><span class="sxs-lookup"><span data-stu-id="58db3-130">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="58db3-131">O que acontece se Diogo já tinha acesso completo ao compartilhamento?</span><span class="sxs-lookup"><span data-stu-id="58db3-131">What happens if Bob previously had Full Access to the share?</span></span> 

<span data-ttu-id="58db3-132">Para compensar esses problemas, uma versão "real" do script será mais parecida com a seguinte:</span><span class="sxs-lookup"><span data-stu-id="58db3-132">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="58db3-133">Esse script é mais complexo, com muita lógica e tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="58db3-133">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="58db3-134">O script é mais complexo porque você não informa mais o que pretende fazer, e sim *como fazê-lo*.</span><span class="sxs-lookup"><span data-stu-id="58db3-134">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="58db3-135">Na DSC, você pode informar o que pretende fazer e a lógica subjacente é simplificada.</span><span class="sxs-lookup"><span data-stu-id="58db3-135">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present" 
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"  
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
} 
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="58db3-136">Este script tem um formato simples e é fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="58db3-136">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="58db3-137">Os caminhos lógicos e o tratamento de erros continuam presentes na implementação [resource](resources.md), embora sejam invisíveis para o autor do script.</span><span class="sxs-lookup"><span data-stu-id="58db3-137">The logic paths and error handling are still present in the [resource](resources.md) implementation, but invisible to the script author.</span></span> 



## <a name="separating-environment-from-structure"></a><span data-ttu-id="58db3-138">Separando ambiente de estrutura</span><span class="sxs-lookup"><span data-stu-id="58db3-138">Separating Environment from Structure</span></span>

<span data-ttu-id="58db3-139">Um padrão comum na DevOps é usar vários ambientes de implantação.</span><span class="sxs-lookup"><span data-stu-id="58db3-139">A common pattern in DevOps is to have multiple environments for deployment.</span></span> <span data-ttu-id="58db3-140">Por exemplo, pode haver um ambiente de "desenvolvimento" para criar o protótipo de um novo código rapidamente.</span><span class="sxs-lookup"><span data-stu-id="58db3-140">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="58db3-141">O código do ambiente de "desenvolvimento" passa por um ambiente de "teste", no qual outras pessoas verificam a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="58db3-141">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="58db3-142">Por fim, o código passa para a "produção" ou o ambiente de produção de site ativo.</span><span class="sxs-lookup"><span data-stu-id="58db3-142">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="58db3-143">As configurações DSC acomodam esse pipeline de desenvolvimento/teste/produção, por meio do uso de [dados da configuração](configData.md).</span><span class="sxs-lookup"><span data-stu-id="58db3-143">DSC configurations accomodate this dev-test-prod pipeline through the use of [configuration data](configData.md).</span></span>
<span data-ttu-id="58db3-144">Isso simplifica ainda mais a diferença entre a estrutura da configuração e os nós gerenciados.</span><span class="sxs-lookup"><span data-stu-id="58db3-144">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="58db3-145">Por exemplo, você pode definir uma configuração que requer um SQL Server, um Servidor IIS e um servidor de camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="58db3-145">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span> <span data-ttu-id="58db3-146">Independentemente de quais nós recebem as diferentes partes dessa configuração, esses três elementos estarão sempre presentes.</span><span class="sxs-lookup"><span data-stu-id="58db3-146">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="58db3-147">Você pode usar dados de configuração para apontar todos os três elementos para o mesmo computador em um ambiente de desenvolvimento, separar os três elementos para três computadores diferentes em um ambiente de teste e, por fim, apontá-los para todos os servidores de produção no ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="58db3-147">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="58db3-148">Para implantar em diferentes ambientes, você pode invocar `Start-DscConfiguration` com os dados de configuração corretos para o ambiente de destino.</span><span class="sxs-lookup"><span data-stu-id="58db3-148">To deploy to the different environments, you can invoke `Start-DscConfiguration` with the correct configuration data for the environment you want to target.</span></span> 

## <a name="see-also"></a><span data-ttu-id="58db3-149">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="58db3-149">See Also</span></span>

[<span data-ttu-id="58db3-150">Configurações</span><span class="sxs-lookup"><span data-stu-id="58db3-150">Configurations</span></span>](configurations.md)

[<span data-ttu-id="58db3-151">Dados da Configuração</span><span class="sxs-lookup"><span data-stu-id="58db3-151">Configuration Data</span></span>](configData.md)

[<span data-ttu-id="58db3-152">Recursos</span><span class="sxs-lookup"><span data-stu-id="58db3-152">Resources</span></span>](resources.md)

