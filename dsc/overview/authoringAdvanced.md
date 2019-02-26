---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Noções básicas sobre a função da DSC em um pipeline de CI/CD
ms.openlocfilehash: 7aec414b3d8e61d1daa1ce796184ac34dbbb43ce
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803371"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="94639-103">Noções básicas sobre a função da DSC em um pipeline de CI/CD</span><span class="sxs-lookup"><span data-stu-id="94639-103">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="94639-104">Este artigo descreve os tipos de abordagens disponíveis para combinar configurações e recursos.</span><span class="sxs-lookup"><span data-stu-id="94639-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="94639-105">A meta para cada cenário é a mesma, para reduzir a complexidade quando várias configurações são preferíveis para acessar o estado final de implantação de um servidor.</span><span class="sxs-lookup"><span data-stu-id="94639-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="94639-106">Um exemplo disso seria várias equipes que contribuem para o resultado de uma implantação de servidor, como um proprietário de aplicativo que mantém o estado do aplicativo e uma equipe central liberar alterações em linhas de base de segurança.</span><span class="sxs-lookup"><span data-stu-id="94639-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="94639-107">As nuances de cada abordagem, incluindo benefícios e riscos, são descritas aqui.</span><span class="sxs-lookup"><span data-stu-id="94639-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Pipeline](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="94639-109">Tipos de técnicas de criação colaborativa</span><span class="sxs-lookup"><span data-stu-id="94639-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="94639-110">Há duas soluções internas no Configuration Manager Local para habilitar esse conceito:</span><span class="sxs-lookup"><span data-stu-id="94639-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="94639-111">Conceito</span><span class="sxs-lookup"><span data-stu-id="94639-111">Concept</span></span> | <span data-ttu-id="94639-112">Informações detalhadas</span><span class="sxs-lookup"><span data-stu-id="94639-112">Detailed Information</span></span>
|-|-
| <span data-ttu-id="94639-113">Configurações Parciais</span><span class="sxs-lookup"><span data-stu-id="94639-113">Partial Configurations</span></span> | [<span data-ttu-id="94639-114">Documentação</span><span class="sxs-lookup"><span data-stu-id="94639-114">Documentation</span></span>](../pull-server/partialConfigs.md)
| <span data-ttu-id="94639-115">Recursos de composição</span><span class="sxs-lookup"><span data-stu-id="94639-115">Composite Resources</span></span> | [<span data-ttu-id="94639-116">Documentação</span><span class="sxs-lookup"><span data-stu-id="94639-116">Documentation</span></span>](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="94639-117">Noções básicas sobre o impacto de cada abordagem</span><span class="sxs-lookup"><span data-stu-id="94639-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="94639-118">Qualquer uma dessas soluções pode ser usada para gerenciar o resultado de uma implantação de servidor.</span><span class="sxs-lookup"><span data-stu-id="94639-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="94639-119">No entanto, há uma diferença significativa no impacto do uso de cada abordagem.</span><span class="sxs-lookup"><span data-stu-id="94639-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="94639-120">Configurações Parciais</span><span class="sxs-lookup"><span data-stu-id="94639-120">Partial Configurations</span></span>

<span data-ttu-id="94639-121">Ao usar Configurações Parciais, o Configuration Manager Local é configurado para gerenciar várias configurações de forma independente.</span><span class="sxs-lookup"><span data-stu-id="94639-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="94639-122">As configurações são compiladas de forma independente e, em seguida, são atribuídas ao nó.</span><span class="sxs-lookup"><span data-stu-id="94639-122">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="94639-123">Isso exige que o LCM seja configurado com antecedência com o nome de cada configuração.</span><span class="sxs-lookup"><span data-stu-id="94639-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](../images/PartialConfiguration.jpg)

<span data-ttu-id="94639-125">As Configurações Parciais oferecem controle completo sobre a configuração de um servidor a duas ou mais equipes, geralmente sem o benefício da comunicação ou da colaboração.</span><span class="sxs-lookup"><span data-stu-id="94639-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="94639-126">Segundo os clientes, isso pode levar a conflitos de recursos, substituições não intencionais e, por fim, perda de controle da configuração do ativo.</span><span class="sxs-lookup"><span data-stu-id="94639-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="94639-127">Além disso, comentaram que ao usar esse modelo, é improvável que as alterações em cada configuração feita pelas equipes de controle sejam completamente testadas em um pipeline de lançamento, o que gera resultados inesperados na produção.</span><span class="sxs-lookup"><span data-stu-id="94639-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="94639-128">**É essencial que um único pipeline seja usado para avaliar o lançamento de todas as alterações nos servidores.**</span><span class="sxs-lookup"><span data-stu-id="94639-128">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="94639-129">Na ilustração abaixo, a Equipe B libera a configuração parcial para a Equipe A. Em seguida, a Equipe A executa seus testes em um servidor com ambas as configurações aplicadas.</span><span class="sxs-lookup"><span data-stu-id="94639-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="94639-130">Nesse modelo, somente uma autoridade tem permissão para fazer alterações na produção.</span><span class="sxs-lookup"><span data-stu-id="94639-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

<span data-ttu-id="94639-132">Quando a Equipe B requisitar alterações, ela deverá enviar uma solicitação de pull para o ambiente de controle do código-fonte da Equipe A.</span><span class="sxs-lookup"><span data-stu-id="94639-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="94639-133">Depois, a Equipe A examinará as alterações usando a automação de teste e liberará para a produção quando estiver certa de que as alterações não gerarão erros nos aplicativos ou serviços hospedados pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="94639-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="94639-134">Recursos de composição</span><span class="sxs-lookup"><span data-stu-id="94639-134">Composite Resources</span></span>

<span data-ttu-id="94639-135">Um recurso de composição é simplesmente uma configuração de DSC empacotada como um recurso.</span><span class="sxs-lookup"><span data-stu-id="94639-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="94639-136">Não há nenhum requisito especial para configurar o LCM para aceitar os recursos de composição.</span><span class="sxs-lookup"><span data-stu-id="94639-136">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="94639-137">Os recursos são usados dentro de uma nova configuração e uma única compilação resulta em um arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="94639-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](../images/CompositeResource.jpg)

<span data-ttu-id="94639-139">Há dois cenários comuns para recursos de composição.</span><span class="sxs-lookup"><span data-stu-id="94639-139">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="94639-140">O primeiro é reduzir a complexidade e os conceitos abstratos únicos.</span><span class="sxs-lookup"><span data-stu-id="94639-140">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="94639-141">O segundo é permitir que as linhas de base sejam empacotadas para uma equipe do aplicativo implantar com segurança por meio do pipeline de lançamento para produção após todos os testes serem aprovados.</span><span class="sxs-lookup"><span data-stu-id="94639-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="94639-142">Os recursos de composição promovem a composição e a colaboração usando um pipeline durante a criação de maturidade operacional</span><span class="sxs-lookup"><span data-stu-id="94639-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="94639-143">Você já pode estar usando recursos de composição sem perceber.</span><span class="sxs-lookup"><span data-stu-id="94639-143">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="94639-144">Um exemplo é **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="94639-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="94639-145">Esse recurso gerencia o estado dos vários serviços do Windows sem listá-los individualmente.</span><span class="sxs-lookup"><span data-stu-id="94639-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="94639-146">A propriedade Name aceita uma matriz de cadeias de caracteres para fornecer o nome de cada serviço.</span><span class="sxs-lookup"><span data-stu-id="94639-146">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="94639-147">Quando a configuração for compilada, o MOF conterá uma seção de Serviço exclusiva para cada um dos nomes passados para ServiceSet.</span><span class="sxs-lookup"><span data-stu-id="94639-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="94639-148">As organizações podem ter "agentes" ou "middleware" que devem ser instalados em todos os servidores.</span><span class="sxs-lookup"><span data-stu-id="94639-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="94639-149">Um recurso de composição é a melhor resposta para gerenciar as dependências, a instalação e a configuração de tais ferramentas e utilitários.</span><span class="sxs-lookup"><span data-stu-id="94639-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="94639-150">A pessoa ou a equipe responsável por soluções que abrangem vários servidores cria uma configuração que contém seus requisitos.</span><span class="sxs-lookup"><span data-stu-id="94639-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="94639-151">Em seguida, a configuração seria empacotada como um recurso de composição usando as instruções fornecidas na documentação do recurso de composição.</span><span class="sxs-lookup"><span data-stu-id="94639-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="94639-152">Por fim, o novo recurso de composição deve ser publicado em um local como um compartilhamento de arquivos ou feed do NuGet em que as equipes de aplicativo possam consumi-lo em suas configurações.</span><span class="sxs-lookup"><span data-stu-id="94639-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="94639-153">Toda vez que a equipe libera uma nova versão, o número de versão é aumentado no manifesto do módulo do recurso de composição.</span><span class="sxs-lookup"><span data-stu-id="94639-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="94639-154">As equipes de aplicativo incluem o recurso de composição na configuração que criam para gerenciar as dependências de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94639-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="94639-155">Quando as equipes de Operações/Segurança liberam uma nova versão do recurso, elas notificam as equipes de aplicativo sobre a nova alteração.</span><span class="sxs-lookup"><span data-stu-id="94639-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="94639-156">As equipes de aplicativo podem disparar uma versão para produção em que a única alteração é nas linhas de base.</span><span class="sxs-lookup"><span data-stu-id="94639-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="94639-157">No entanto, isso cria uma oportunidade de avaliar o impacto nos aplicativos antes do risco de uma interrupção de serviço.</span><span class="sxs-lookup"><span data-stu-id="94639-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="94639-158">Observação: nos comentários sobre o uso de recursos de composição, houve críticas sobre a necessidade de compilar e liberar um novo MOF ao fazer alterações.</span><span class="sxs-lookup"><span data-stu-id="94639-158">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="94639-159">Isso ocorre por design.</span><span class="sxs-lookup"><span data-stu-id="94639-159">This is by design.</span></span>
<span data-ttu-id="94639-160">Cada nova versão de configuração deve incluir uma referência estática a uma versão específica de cada recurso e ser validada por testes antes de chegar aos nós de servidor de produção.</span><span class="sxs-lookup"><span data-stu-id="94639-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="94639-161">O processo de teste e liberação de alterações do controle do código-fonte cria um ambiente seguro para liberar alterações em lotes pequenos, mas frequentes.</span><span class="sxs-lookup"><span data-stu-id="94639-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="94639-162">Para saber mais sobre como usar pipelines de lançamento para gerenciar a infraestrutura de núcleo, confira o white paper: [O modelo de pipeline de lançamento](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="94639-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
