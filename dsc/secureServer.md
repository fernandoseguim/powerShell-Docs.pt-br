---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Práticas recomendadas do servidor de pull"
ms.openlocfilehash: 66b97f4edb43926866b39731d720a2dc8c91eb2e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="efb05-103">Práticas recomendadas do servidor de pull</span><span class="sxs-lookup"><span data-stu-id="efb05-103">Pull server best practices</span></span>

><span data-ttu-id="efb05-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="efb05-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="efb05-105">Resumo: este documento destina-se a incluir processo e extensibilidade para ajudar os engenheiros que estão se preparando para a solução.</span><span class="sxs-lookup"><span data-stu-id="efb05-105">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="efb05-106">Os detalhes devem fornecer as práticas recomendadas, como identificadas por clientes e, em seguida, validadas pela equipe de produto para garantir que as recomendações sejam voltadas para o futuro e consideradas estáveis.</span><span class="sxs-lookup"><span data-stu-id="efb05-106">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="efb05-107">Informações do documento</span><span class="sxs-lookup"><span data-stu-id="efb05-107">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="efb05-108">Autor</span><span class="sxs-lookup"><span data-stu-id="efb05-108">Author</span></span> | <span data-ttu-id="efb05-109">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="efb05-109">Michael Greene</span></span>  
<span data-ttu-id="efb05-110">Revisores</span><span class="sxs-lookup"><span data-stu-id="efb05-110">Reviewers</span></span> | <span data-ttu-id="efb05-111">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="efb05-111">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>  
<span data-ttu-id="efb05-112">Publicado</span><span class="sxs-lookup"><span data-stu-id="efb05-112">Published</span></span> | <span data-ttu-id="efb05-113">Abril de 2015</span><span class="sxs-lookup"><span data-stu-id="efb05-113">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="efb05-114">Resumo</span><span class="sxs-lookup"><span data-stu-id="efb05-114">Abstract</span></span>

<span data-ttu-id="efb05-115">Este documento foi criado para fornecer diretrizes oficiais para qualquer pessoa que esteja planejando uma implementação de um servidor de pull de Configuração de Estado Desejado do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efb05-115">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="efb05-116">Um servidor de pull é um serviço simples que deve levar apenas alguns minutos para implantar.</span><span class="sxs-lookup"><span data-stu-id="efb05-116">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="efb05-117">Embora ofereça diretrizes técnicas passo a passo que podem ser usadas em uma implantação, o valor desse documento está em servir como uma referência para as práticas recomendadas e no que se deve refletir antes da implantação.</span><span class="sxs-lookup"><span data-stu-id="efb05-117">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="efb05-118">Os leitores devem ter uma familiaridade básica com o DSC e com os termos usados para descrever os componentes que estão incluídos em uma implantação de DSC.</span><span class="sxs-lookup"><span data-stu-id="efb05-118">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="efb05-119">Para obter mais informações, consulte o tópico [Visão Geral da Configuração de Estado Desejado do Windows PowerShell](https://technet.microsoft.com/en-us/library/dn249912.aspx).</span><span class="sxs-lookup"><span data-stu-id="efb05-119">For more information, see the [Windows PowerShell Desired State Configuration Overview](https://technet.microsoft.com/en-us/library/dn249912.aspx)  topic.</span></span>
<span data-ttu-id="efb05-120">Como é esperado que o DSC evolua em uma cadência de nuvem, espera-se também que a tecnologia subjacente, incluindo o servidor de pull, evolua e introduza novos recursos.</span><span class="sxs-lookup"><span data-stu-id="efb05-120">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="efb05-121">Este documento inclui uma tabela de versão no apêndice que fornece referências a versões anteriores e referências a soluções futuras para incentivar designs inovadores.</span><span class="sxs-lookup"><span data-stu-id="efb05-121">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="efb05-122">As duas seções principais deste documento:</span><span class="sxs-lookup"><span data-stu-id="efb05-122">The two major sections of this document:</span></span>

 - <span data-ttu-id="efb05-123">Planejamento de Configuração</span><span class="sxs-lookup"><span data-stu-id="efb05-123">Configuration Planning</span></span>
 - <span data-ttu-id="efb05-124">Guia de instalação</span><span class="sxs-lookup"><span data-stu-id="efb05-124">Installation Guide</span></span>
 
### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="efb05-125">Versões do Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="efb05-125">Versions of the Windows Management Framework</span></span> 
<span data-ttu-id="efb05-126">As informações neste documento destinam-se ao Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="efb05-126">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="efb05-127">Embora o WMF 5.0 não seja necessário para a implantação e operação de um servidor de pull, o foco deste documento é a versão 5.0.</span><span class="sxs-lookup"><span data-stu-id="efb05-127">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="efb05-128">Configuração do Estado Desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="efb05-128">Windows PowerShell Desired State Configuration</span></span>
<span data-ttu-id="efb05-129">A DSC (Configuração do Estado Desejado) é uma plataforma de gerenciamento que habilita a implantação e gerenciamento de dados de configuração, usando uma sintaxe do setor chamada de MOF (Managed Object Format) para descrever o CIM (modelo CIM).</span><span class="sxs-lookup"><span data-stu-id="efb05-129">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="efb05-130">Existe um projeto de software livre, o OMI (Open Management Infrastructure), para promover o desenvolvimento desses padrões entre plataformas, incluindo Linux e sistemas operacionais de hardware de rede.</span><span class="sxs-lookup"><span data-stu-id="efb05-130">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="efb05-131">Para obter mais informações, consulte a [página DMTF com vínculo para as especificações de MOF](http://dmtf.org/standards/cim) e [Documentos e Fonte do OMI](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="efb05-131">For more information, see the [DMTF page linking to MOF specifications](http://dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="efb05-132">O Windows PowerShell fornece um conjunto de extensões de linguagem para a Configuração de Estado Desejado que podem ser usadas para criar e gerenciar configurações declarativas.</span><span class="sxs-lookup"><span data-stu-id="efb05-132">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="efb05-133">Função de servidor de pull</span><span class="sxs-lookup"><span data-stu-id="efb05-133">Pull server role</span></span>  
<span data-ttu-id="efb05-134">Um servidor de pull oferece um serviço centralizado para armazenar configurações que estarão acessíveis aos nós de destino.</span><span class="sxs-lookup"><span data-stu-id="efb05-134">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>
 
<span data-ttu-id="efb05-135">A função de servidor de pull pode ser implantada como uma instância de servidor Web ou um compartilhamento de arquivos SMB.</span><span class="sxs-lookup"><span data-stu-id="efb05-135">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="efb05-136">A capacidade de servidor Web inclui uma interface de OData e, opcionalmente, pode incluir recursos para que os nós de destino reportem a confirmação de êxito ou de falha conforme as configurações são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="efb05-136">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="efb05-137">Essa funcionalidade é útil em ambientes em que há um grande número de nós de destino.</span><span class="sxs-lookup"><span data-stu-id="efb05-137">This functionality is useful in environments where there are a large number of target nodes.</span></span> <span data-ttu-id="efb05-138">Depois de configurar um nó de destino (também conhecido como um cliente) para apontar para o servidor de pull, os dados de configuração mais recentes e os scripts necessários são baixados e aplicados.</span><span class="sxs-lookup"><span data-stu-id="efb05-138">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="efb05-139">Isso pode ser feito como uma implantação única ou como um trabalho recorrente, o que também torna o servidor de pull um ativo importante para o gerenciamento de alteração em grande escala.</span><span class="sxs-lookup"><span data-stu-id="efb05-139">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="efb05-140">Para obter mais informações, consulte [Servidores de Pull de Configuração de Estado Desejado do Windows PowerShell](https://technet.microsoft.com/en-us/library/dn249913.aspx) e [Modos de Configuração de Push e Pull](https://technet.microsoft.com/en-us/library/dn249913.aspx).</span><span class="sxs-lookup"><span data-stu-id="efb05-140">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](https://technet.microsoft.com/en-us/library/dn249913.aspx) and [Push and Pull Configuration Modes](https://technet.microsoft.com/en-us/library/dn249913.aspx).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="efb05-141">Planejamento de configuração</span><span class="sxs-lookup"><span data-stu-id="efb05-141">Configuration planning</span></span>

<span data-ttu-id="efb05-142">Para qualquer implantação de software empresarial há informações que podem ser coletadas com antecedência para ajudar a planejar a arquitetura correta e se preparar para as etapas necessárias para concluir a implantação.</span><span class="sxs-lookup"><span data-stu-id="efb05-142">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="efb05-143">As seções a seguir fornecem informações sobre como se preparar e as conexões organizacionais que provavelmente precisarão acontecer com antecedência.</span><span class="sxs-lookup"><span data-stu-id="efb05-143">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="efb05-144">Requisitos de software</span><span class="sxs-lookup"><span data-stu-id="efb05-144">Software requirements</span></span>

<span data-ttu-id="efb05-145">A implantação de um servidor de pull requer o recurso de Serviço DSC do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="efb05-145">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="efb05-146">Esse recurso foi introduzido no Windows Server 2012 e foi atualizado por meio das versões em andamento do WMF (Windows Management Framework).</span><span class="sxs-lookup"><span data-stu-id="efb05-146">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="efb05-147">Downloads de software</span><span class="sxs-lookup"><span data-stu-id="efb05-147">Software downloads</span></span>

<span data-ttu-id="efb05-148">Além de instalar o conteúdo mais recente do Windows Update, há dois downloads que são considerados como práticas recomendadas para implantar um servidor de pull de DSC: a versão mais recente do Windows Management Framework e um módulo de DSC para automatizar o provisionamento do servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="efb05-148">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="efb05-149">WINDOWS MANAGEMENT FRAMEWORK</span><span class="sxs-lookup"><span data-stu-id="efb05-149">WMF</span></span>

<span data-ttu-id="efb05-150">O Windows Server 2012 R2 inclui um recurso chamado de serviço DSC.</span><span class="sxs-lookup"><span data-stu-id="efb05-150">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="efb05-151">O recurso de serviço DSC fornece a funcionalidade do servidor de pull, incluindo os binários que oferecem suporte ao ponto de extremidade OData.</span><span class="sxs-lookup"><span data-stu-id="efb05-151">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span> <span data-ttu-id="efb05-152">O WMF está incluído no Windows Server e é atualizado em uma cadência ágil entre as versões do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="efb05-152">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="efb05-153">[Novas versões do WMF 5.0](http://aka.ms/wmf5latest) podem incluir atualizações do recurso de Serviço DSC.</span><span class="sxs-lookup"><span data-stu-id="efb05-153">[New versions of WMF 5.0](http://aka.ms/wmf5latest)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="efb05-154">Por esse motivo, é uma prática recomendada baixar a versão mais recente do WMF e examinar as notas de versão para determinar se a versão inclui uma atualização do recurso de serviço DSC.</span><span class="sxs-lookup"><span data-stu-id="efb05-154">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="efb05-155">Também é necessário examinar a seção das notas de versão que indica se o status de design para uma atualização ou cenário está listado como estável ou experimental.</span><span class="sxs-lookup"><span data-stu-id="efb05-155">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span> <span data-ttu-id="efb05-156">Para permitir um ciclo de lançamento ágil, recursos individuais podem ser declarados estáveis, o que indica que o recurso está pronto para ser usado em um ambiente de produção ainda que o WMF esteja lançado como visualização.</span><span class="sxs-lookup"><span data-stu-id="efb05-156">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="efb05-157">Outros recursos que têm sido historicamente atualizados por versões do WMF (consulte as Notas de Versão do WMF para obter mais detalhes):</span><span class="sxs-lookup"><span data-stu-id="efb05-157">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

 - <span data-ttu-id="efb05-158">Windows PowerShell, ISE (Ambiente de Script Integrado) do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="efb05-158">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
 - <span data-ttu-id="efb05-159">Serviços Web do Windows PowerShell (Extensão do IIS do Management OData)</span><span class="sxs-lookup"><span data-stu-id="efb05-159">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
 - <span data-ttu-id="efb05-160">DSC (Configuração de Estado Desejado) do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="efb05-160">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
 - <span data-ttu-id="efb05-161">WinRM (Gerenciamento Remoto do Windows) WMI (Instrumentação de Gerenciamento do Windows)</span><span class="sxs-lookup"><span data-stu-id="efb05-161">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="efb05-162">Recurso DSC</span><span class="sxs-lookup"><span data-stu-id="efb05-162">DSC resource</span></span>

<span data-ttu-id="efb05-163">Uma implantação de servidor de pull pode ser simplificada através do provisionamento do serviço com o uso de um script de configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="efb05-163">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="efb05-164">Este documento inclui scripts de configuração que podem ser usados para implantar um nó de servidor pronto para produção.</span><span class="sxs-lookup"><span data-stu-id="efb05-164">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="efb05-165">Para usar os scripts de configuração, é necessário um módulo de DSC que não está incluído no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="efb05-165">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="efb05-166">O nome do módulo necessário é **xPSDesiredStateConfiguration**, que inclui o recurso de DSC **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="efb05-166">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="efb05-167">O módulo xPSDesiredStateConfiguration pode ser baixado [aqui](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="efb05-167">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="efb05-168">Use o cmdlet **Install-Module** do módulo **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="efb05-168">Use the **Install-Module** cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="efb05-169">O módulo **PowerShellGet** baixará o módulo em:</span><span class="sxs-lookup"><span data-stu-id="efb05-169">The **PowerShellGet** module will download the module to:</span></span> 

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="efb05-170">Tarefa de planejamento</span><span class="sxs-lookup"><span data-stu-id="efb05-170">Planning task</span></span>|
---|
<span data-ttu-id="efb05-171">Você tem acesso aos arquivos de instalação do Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="efb05-171">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="efb05-172">O ambiente de implantação terá acesso à Internet para baixar o módulo e o WMF da galeria online?</span><span class="sxs-lookup"><span data-stu-id="efb05-172">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="efb05-173">Como você instalará as atualizações mais recentes de segurança depois de instalar o sistema operacional?</span><span class="sxs-lookup"><span data-stu-id="efb05-173">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="efb05-174">O ambiente terá acesso à Internet para obter atualizações ou terá um servidor local do WSUS (Windows Server Update Services)?</span><span class="sxs-lookup"><span data-stu-id="efb05-174">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="efb05-175">Você tem acesso aos arquivos de instalação do Windows Server que já contêm atualizações por meio de injeção offline?</span><span class="sxs-lookup"><span data-stu-id="efb05-175">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="efb05-176">Requisitos de hardware</span><span class="sxs-lookup"><span data-stu-id="efb05-176">Hardware requirements</span></span>

<span data-ttu-id="efb05-177">As implantações de servidor de pull têm suporte em servidores físicos e virtuais.</span><span class="sxs-lookup"><span data-stu-id="efb05-177">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="efb05-178">Os requisitos de dimensionamento para o servidor de pull estão alinhados com os requisitos do Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="efb05-178">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="efb05-179">CPU: processador de 1,4 GHz e 64 bits</span><span class="sxs-lookup"><span data-stu-id="efb05-179">CPU: 1.4 GHz 64-bit processor</span></span>  
<span data-ttu-id="efb05-180">Memória: 512 MB</span><span class="sxs-lookup"><span data-stu-id="efb05-180">Memory: 512 MB</span></span>  
<span data-ttu-id="efb05-181">Espaço em disco: 32 GB</span><span class="sxs-lookup"><span data-stu-id="efb05-181">Disk Space: 32 GB</span></span>  
<span data-ttu-id="efb05-182">Rede: Adaptador Gigabit Ethernet</span><span class="sxs-lookup"><span data-stu-id="efb05-182">Network: Gigabit Ethernet Adapter</span></span>  

<span data-ttu-id="efb05-183">Tarefa de planejamento</span><span class="sxs-lookup"><span data-stu-id="efb05-183">Planning task</span></span>|
---|
<span data-ttu-id="efb05-184">Você implantará em hardware físico ou em uma plataforma de virtualização?</span><span class="sxs-lookup"><span data-stu-id="efb05-184">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="efb05-185">Qual é o processo de solicitação de um novo servidor para seu ambiente de destino?</span><span class="sxs-lookup"><span data-stu-id="efb05-185">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="efb05-186">Qual é o tempo médio de resposta para que um servidor fique disponível?</span><span class="sxs-lookup"><span data-stu-id="efb05-186">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="efb05-187">Qual tamanho de servidor você solicitará?</span><span class="sxs-lookup"><span data-stu-id="efb05-187">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="efb05-188">Contas</span><span class="sxs-lookup"><span data-stu-id="efb05-188">Accounts</span></span>

<span data-ttu-id="efb05-189">Não há nenhum requisito de conta de serviço para implantar uma instância de servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="efb05-189">There are no service account requirements to deploy a pull server instance.</span></span> <span data-ttu-id="efb05-190">No entanto, há situações em que o site pode ser executado em um contexto de uma conta de usuário local.</span><span class="sxs-lookup"><span data-stu-id="efb05-190">However, there are scenarios where the website could run in the context of a local user account.</span></span> <span data-ttu-id="efb05-191">Por exemplo, se houver a necessidade de acessar um compartilhamento de armazenamento de conteúdo do site e o Windows Server ou o dispositivo que hospeda o compartilhamento de armazenamento não estiverem associados ao domínio.</span><span class="sxs-lookup"><span data-stu-id="efb05-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="efb05-192">Registros DNS</span><span class="sxs-lookup"><span data-stu-id="efb05-192">DNS records</span></span>

<span data-ttu-id="efb05-193">Será necessário um nome do servidor para ser usado durante a configuração de clientes para trabalhar com um ambiente de servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="efb05-193">You will need a server name to use when configuring clients to work with a pull server environment.</span></span> <span data-ttu-id="efb05-194">Em ambientes de teste, normalmente será usado o nome do host do servidor ou poderá ser usado o endereço IP para o servidor se a resolução de nomes DNS não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="efb05-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span> <span data-ttu-id="efb05-195">Em ambientes de produção ou em um ambiente de laboratório que pretende representar uma implantação de produção, a prática recomendada é criar um registro DNS CNAME.</span><span class="sxs-lookup"><span data-stu-id="efb05-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="efb05-196">Um DNS CNAME permite a criação de um alias para se referir ao seu registro de host (A).</span><span class="sxs-lookup"><span data-stu-id="efb05-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span> <span data-ttu-id="efb05-197">O objetivo do registro de nome adicional é o aumento da flexibilidade, caso uma alteração seja necessária no futuro.</span><span class="sxs-lookup"><span data-stu-id="efb05-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span> <span data-ttu-id="efb05-198">Um CNAME pode ajudar a isolar a configuração do cliente de maneira que as alterações no ambiente de servidor, como a substituição de um servidor de pull ou adição de servidores de pull, não exijam uma alteração correspondente na configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="efb05-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="efb05-199">Ao escolher um nome para o registro DNS, lembre-se da arquitetura da solução.</span><span class="sxs-lookup"><span data-stu-id="efb05-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span> <span data-ttu-id="efb05-200">Se estiver usando o balanceamento de carga, o certificado usado para proteger o tráfego por meio de HTTPS precisará compartilhar o mesmo nome do registro DNS.</span><span class="sxs-lookup"><span data-stu-id="efb05-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span> 

<span data-ttu-id="efb05-201">Cenário</span><span class="sxs-lookup"><span data-stu-id="efb05-201">Scenario</span></span> |<span data-ttu-id="efb05-202">Prática recomendada</span><span class="sxs-lookup"><span data-stu-id="efb05-202">Best Practice</span></span>
:---|:---
<span data-ttu-id="efb05-203">Ambiente de Teste</span><span class="sxs-lookup"><span data-stu-id="efb05-203">Test Environment</span></span> |<span data-ttu-id="efb05-204">Reproduzir o ambiente de produção planejado, se possível.</span><span class="sxs-lookup"><span data-stu-id="efb05-204">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="efb05-205">Um nome do host do servidor é adequado para configurações simples.</span><span class="sxs-lookup"><span data-stu-id="efb05-205">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="efb05-206">Se o DNS não estiver disponível, um endereço IP poderá ser usado no lugar do nome do host.</span><span class="sxs-lookup"><span data-stu-id="efb05-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="efb05-207">Implantação de Nó único</span><span class="sxs-lookup"><span data-stu-id="efb05-207">Single Node Deployment</span></span> |<span data-ttu-id="efb05-208">Criar um registro DNS CNAME que aponta para o nome do host do servidor.</span><span class="sxs-lookup"><span data-stu-id="efb05-208">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="efb05-209">Para obter mais informações, consulte [Configuração de Round Robin de DNS no Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="efb05-209">For more information, see [Configuring DNS Round Robin in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span></span>

<span data-ttu-id="efb05-210">Tarefa de planejamento</span><span class="sxs-lookup"><span data-stu-id="efb05-210">Planning task</span></span>|
---|
<span data-ttu-id="efb05-211">Você sabe quem contatar para que os registros DNS sejam criados e alterados?</span><span class="sxs-lookup"><span data-stu-id="efb05-211">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="efb05-212">Qual é o tempo médio de resposta para uma solicitação de um registro DNS?</span><span class="sxs-lookup"><span data-stu-id="efb05-212">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="efb05-213">Você precisa solicitar registros de nome do host (A) estáticos para servidores?</span><span class="sxs-lookup"><span data-stu-id="efb05-213">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="efb05-214">O que você solicitará como um CNAME?</span><span class="sxs-lookup"><span data-stu-id="efb05-214">What will you request as a CNAME?</span></span>|
<span data-ttu-id="efb05-215">Se necessário, qual tipo de solução de Balanceamento de Carga você utilizará?</span><span class="sxs-lookup"><span data-stu-id="efb05-215">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="efb05-216">(consulte a seção intitulada Balanceamento de Carga para obter mais detalhes)</span><span class="sxs-lookup"><span data-stu-id="efb05-216">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="efb05-217">Infraestrutura de chave pública</span><span class="sxs-lookup"><span data-stu-id="efb05-217">Public Key Infrastructure</span></span>

<span data-ttu-id="efb05-218">A maioria das organizações atuais exige que o tráfego de rede, especialmente o tráfego que inclui dados confidenciais como a maneira que os servidores são configurados, seja validado e/ou criptografado durante o trânsito.</span><span class="sxs-lookup"><span data-stu-id="efb05-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span> <span data-ttu-id="efb05-219">Embora seja possível implantar um servidor de pull usando HTTP, o que facilita as solicitações de clientes em texto não criptografado, é uma prática recomendada proteger o tráfego usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="efb05-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="efb05-220">O serviço pode ser configurado para usar HTTPS por meio de um conjunto de parâmetros no recurso de DSC **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="efb05-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="efb05-221">Os requisitos de certificado para proteger o tráfego HTTPS do servidor de pull não são diferentes da proteção de qualquer outro site HTTPS.</span><span class="sxs-lookup"><span data-stu-id="efb05-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="efb05-222">O modelo de **servidor Web** dos Serviços de Certificado do Windows Server satisfaz os recursos necessários.</span><span class="sxs-lookup"><span data-stu-id="efb05-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="efb05-223">Tarefa de planejamento</span><span class="sxs-lookup"><span data-stu-id="efb05-223">Planning task</span></span>|
---|
<span data-ttu-id="efb05-224">Se as solicitações de certificado não são automatizadas, quem você precisará contatar para solicitar um certificado?</span><span class="sxs-lookup"><span data-stu-id="efb05-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="efb05-225">Qual é o tempo médio de resposta para a solicitação?</span><span class="sxs-lookup"><span data-stu-id="efb05-225">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="efb05-226">Como o arquivo de certificado será transferido para você?</span><span class="sxs-lookup"><span data-stu-id="efb05-226">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="efb05-227">Como a chave privada do certificado será transferida para você?</span><span class="sxs-lookup"><span data-stu-id="efb05-227">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="efb05-228">Qual é o tempo de expiração padrão?</span><span class="sxs-lookup"><span data-stu-id="efb05-228">How long is the default expiration time?</span></span>|
<span data-ttu-id="efb05-229">Você estabeleceu um nome DNS para o ambiente de servidor de pull que pode ser usado para o nome do certificado?</span><span class="sxs-lookup"><span data-stu-id="efb05-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="efb05-230">Escolha de uma arquitetura</span><span class="sxs-lookup"><span data-stu-id="efb05-230">Choosing an architecture</span></span>

<span data-ttu-id="efb05-231">Um servidor de pull pode ser implantado usando um serviço Web hospedado no IIS ou em um compartilhamento de arquivos SMB.</span><span class="sxs-lookup"><span data-stu-id="efb05-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="efb05-232">Na maioria das situações, a opção de serviço Web fornecerá maior flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="efb05-232">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="efb05-233">Não é incomum que o tráfego HTTPS atravesse os limites da rede, enquanto que o tráfego SMB é geralmente filtrado ou bloqueado entre redes.</span><span class="sxs-lookup"><span data-stu-id="efb05-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="efb05-234">O serviço Web também oferece a opção de incluir um Servidor de Conformidade ou um Reporting Manager da Web (esses dois tópicos serão abordados em uma versão futura deste documento) que fornecem um mecanismo para os clientes reportarem o status a um servidor para uma visibilidade centralizada.</span><span class="sxs-lookup"><span data-stu-id="efb05-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span> <span data-ttu-id="efb05-235">O SMB fornece uma opção para ambientes em que a política determina que um servidor Web não deve ser utilizado e para outros requisitos de ambientes em que uma função de servidor Web não é desejada.</span><span class="sxs-lookup"><span data-stu-id="efb05-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span> <span data-ttu-id="efb05-236">Em ambos os casos, lembre-se de avaliar os requisitos para assinatura e criptografia de tráfego.</span><span class="sxs-lookup"><span data-stu-id="efb05-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="efb05-237">O HTTPS, a assinatura SMB e as políticas IPSEC são opções que vale a pena considerar.</span><span class="sxs-lookup"><span data-stu-id="efb05-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="efb05-238">Balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="efb05-238">Load balancing</span></span>  
<span data-ttu-id="efb05-239">Os clientes interagindo com o serviço Web fazem uma solicitação de informações que é retornada em uma única resposta.</span><span class="sxs-lookup"><span data-stu-id="efb05-239">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="efb05-240">Não são necessárias solicitações sequenciais, portanto, não é necessário que a plataforma de balanceamento de carga garanta que as sessões sejam mantidas em um único servidor em qualquer ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="efb05-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="efb05-241">Tarefa de planejamento</span><span class="sxs-lookup"><span data-stu-id="efb05-241">Planning task</span></span>|
---|
<span data-ttu-id="efb05-242">Qual solução será usada para o tráfego de balanceamento de carga entre servidores?</span><span class="sxs-lookup"><span data-stu-id="efb05-242">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="efb05-243">Se estiver usando um balanceador de carga de hardware, quem receberá uma solicitação para adicionar uma nova configuração ao dispositivo?</span><span class="sxs-lookup"><span data-stu-id="efb05-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="efb05-244">Qual é o tempo médio de resposta de uma solicitação para configurar um novo serviço Web com balanceamento de carga?</span><span class="sxs-lookup"><span data-stu-id="efb05-244">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="efb05-245">Quais informações serão necessárias para a solicitação?</span><span class="sxs-lookup"><span data-stu-id="efb05-245">What information will be required for the request?</span></span>|
<span data-ttu-id="efb05-246">Você precisará solicitar um IP adicional ou a equipe responsável pelo balanceamento de carga cuidará disso?</span><span class="sxs-lookup"><span data-stu-id="efb05-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="efb05-247">Você tem os registros DNS necessários e isso será solicitado pela equipe responsável por configurar a solução de balanceamento de carga?</span><span class="sxs-lookup"><span data-stu-id="efb05-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="efb05-248">A solução de balanceamento de carga necessita que o PKI seja manipulado pelo dispositivo ou ele pode balancear a carga de tráfego HTTPS desde que não haja requisitos de sessão?</span><span class="sxs-lookup"><span data-stu-id="efb05-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="efb05-249">Configurações e módulos de preparo no servidor de pull</span><span class="sxs-lookup"><span data-stu-id="efb05-249">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="efb05-250">Como parte do planejamento da configuração, será necessário pensar sobre quais módulos de DSC e configurações serão hospedadas pelo servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="efb05-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="efb05-251">Para fins de planejamento de configuração, é importante ter um entendimento básico de como preparar e implantar conteúdo em um servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="efb05-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span> 

<span data-ttu-id="efb05-252">No futuro, esta seção será expandida e incluída em um Guia de Operações para Servidor de Pull da DSC.</span><span class="sxs-lookup"><span data-stu-id="efb05-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="efb05-253">O guia discutirá o processo diário do gerenciamento de módulos e das configurações ao longo do tempo, com automação.</span><span class="sxs-lookup"><span data-stu-id="efb05-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span> 

#### <a name="dsc-modules"></a><span data-ttu-id="efb05-254">Módulos de DSC</span><span class="sxs-lookup"><span data-stu-id="efb05-254">DSC modules</span></span>  
<span data-ttu-id="efb05-255">Os clientes que solicitam uma configuração precisarão dos módulos necessários de DSC.</span><span class="sxs-lookup"><span data-stu-id="efb05-255">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="efb05-256">Automatizar a distribuição por demanda dos módulos de DSC para clientes é uma funcionalidade do servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="efb05-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="efb05-257">Se estiver implantando um servidor de pull pela primeira vez, talvez como um laboratório ou prova de conceito, você provavelmente vai depender de módulos de DSC que estão disponíveis em repositórios públicos, como a Galeria do PowerShell ou os repositórios PowerShell.org do GitHub para módulos de DSC.</span><span class="sxs-lookup"><span data-stu-id="efb05-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="efb05-258">É importante lembrar que mesmo para as fontes confiáveis online como a Galeria do PowerShell, qualquer módulo que é baixado de um repositório público deve ser revisado por alguém com experiência com PowerShell e conhecimento sobre o ambiente em que os módulos serão usados antes de serem usados em produção.</span><span class="sxs-lookup"><span data-stu-id="efb05-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="efb05-259">Durante a conclusão dessa tarefa é um bom momento para verificar se há qualquer conteúdo adicional no módulo que pode ser removido, como documentação e scripts de exemplo.</span><span class="sxs-lookup"><span data-stu-id="efb05-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="efb05-260">Isso reduz a largura de banda da rede por cliente em sua primeira solicitação, quando os módulos serão baixados do servidor para o cliente através da rede.</span><span class="sxs-lookup"><span data-stu-id="efb05-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="efb05-261">Cada módulo deve ser empacotado em um formato específico, um arquivo ZIP denominado ModuleName_Version.zip que contém o conteúdo do módulo.</span><span class="sxs-lookup"><span data-stu-id="efb05-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="efb05-262">Depois que o arquivo for copiado para o servidor, um arquivo de soma de verificação deve ser criado.</span><span class="sxs-lookup"><span data-stu-id="efb05-262">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="efb05-263">Quando os clientes se conectam ao servidor, a soma de verificação é usada para verificar se o conteúdo do módulo de DSC não foi alterado desde que foi publicado.</span><span class="sxs-lookup"><span data-stu-id="efb05-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="efb05-264">Tarefa de planejamento</span><span class="sxs-lookup"><span data-stu-id="efb05-264">Planning task</span></span>|
---|
<span data-ttu-id="efb05-265">Se você estiver planejando um ambiente de laboratório ou de teste, quais cenários serão fundamentais para validar?</span><span class="sxs-lookup"><span data-stu-id="efb05-265">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="efb05-266">Há módulos disponíveis publicamente que contêm recursos para cobrir tudo o que é necessário ou você precisará criar seus próprios recursos?</span><span class="sxs-lookup"><span data-stu-id="efb05-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="efb05-267">Seu ambiente terá acesso à Internet para recuperar os módulos públicos?</span><span class="sxs-lookup"><span data-stu-id="efb05-267">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="efb05-268">Quem será responsável por examinar os módulos de DSC?</span><span class="sxs-lookup"><span data-stu-id="efb05-268">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="efb05-269">Se você estiver planejando um ambiente de produção, o que será usado como repositório local para armazenar os módulos de DSC?</span><span class="sxs-lookup"><span data-stu-id="efb05-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="efb05-270">Uma equipe central aceitará módulos de DSC das equipes de aplicativo?</span><span class="sxs-lookup"><span data-stu-id="efb05-270">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="efb05-271">Qual será o processo?</span><span class="sxs-lookup"><span data-stu-id="efb05-271">What will the process be?</span></span>|
<span data-ttu-id="efb05-272">O empacotamento, a cópia e a criação do seu repositório de origem, de uma soma de verificação para módulos de DSC prontos para a produção no servidor, será automatizada?</span><span class="sxs-lookup"><span data-stu-id="efb05-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="efb05-273">Sua equipe também será responsável pelo gerenciamento da plataforma de automação?</span><span class="sxs-lookup"><span data-stu-id="efb05-273">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="efb05-274">Configurações DSC</span><span class="sxs-lookup"><span data-stu-id="efb05-274">DSC configurations</span></span>

<span data-ttu-id="efb05-275">A finalidade de um servidor de pull é fornecer um mecanismo centralizado para a distribuição de configurações DSC aos nós de cliente.</span><span class="sxs-lookup"><span data-stu-id="efb05-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="efb05-276">As configurações são armazenadas no servidor como documentos MOF.</span><span class="sxs-lookup"><span data-stu-id="efb05-276">The configurations are stored on the server as MOF documents.</span></span> <span data-ttu-id="efb05-277">Cada documento será nomeado com um GUID exclusivo.</span><span class="sxs-lookup"><span data-stu-id="efb05-277">Each document will be named with a unique GUID.</span></span> <span data-ttu-id="efb05-278">Quando os clientes são configurados para se conectar com um servidor de pull, também recebem o GUID para a configuração que devem solicitar.</span><span class="sxs-lookup"><span data-stu-id="efb05-278">When clients are configured to connect with a pull server, they are also given the GUID for the configuration they should request.</span></span> <span data-ttu-id="efb05-279">Esse sistema de referenciar configurações por GUID garante a exclusividade global e é flexível, de modo que uma configuração possa ser aplicada com granularidade por nó ou como uma configuração de função que abrange vários servidores que devem ter configurações idênticas.</span><span class="sxs-lookup"><span data-stu-id="efb05-279">This system of referencing configurations by GUID guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="efb05-280">GUIDs</span><span class="sxs-lookup"><span data-stu-id="efb05-280">GUIDs</span></span>

<span data-ttu-id="efb05-281">O planejamento de GUIDs de configuração merece atenção adicional quando se pensa em uma implantação de servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="efb05-281">Planning for configuration GUIDs is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="efb05-282">Não há nenhum requisito específico para manipular GUIDs e é provável que o processo seja exclusivo para cada ambiente.</span><span class="sxs-lookup"><span data-stu-id="efb05-282">There is no specific requirement for how to handle GUIDs and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="efb05-283">O processo pode variar de simples a complexo: um arquivo CSV armazenado centralmente, uma tabela SQL simples, um CMDB ou uma solução complexa que exige integração com outra solução de ferramenta ou de software.</span><span class="sxs-lookup"><span data-stu-id="efb05-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="efb05-284">Há duas abordagens gerais:</span><span class="sxs-lookup"><span data-stu-id="efb05-284">There are two general approaches:</span></span>

 - <span data-ttu-id="efb05-285">**Atribuição de GUIDs por servidor** — Fornece uma medida de garantia de que todas as configurações de servidor sejam controladas individualmente.</span><span class="sxs-lookup"><span data-stu-id="efb05-285">**Assigning GUIDs per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="efb05-286">Isso fornece um nível de precisão em relação às atualizações e pode funcionar bem em ambientes com poucos servidores.</span><span class="sxs-lookup"><span data-stu-id="efb05-286">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
 - <span data-ttu-id="efb05-287">**Atribuição de GUIDs por função de servidor** — Todos os servidores que executam a mesma função, como servidores Web, usam o mesmo GUID para fazer referência aos dados de configuração necessários.</span><span class="sxs-lookup"><span data-stu-id="efb05-287">**Assigning GUIDs per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="efb05-288">Lembre-se de que se vários servidores compartilham o mesmo GUID, todos eles serão atualizados simultaneamente quando as configurações forem alteradas.</span><span class="sxs-lookup"><span data-stu-id="efb05-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

<span data-ttu-id="efb05-289">O GUID é algo que deve ser considerado como dado confidencial, porque ele pode ser aproveitado por alguém mal-intencionado para obter informações sobre como os servidores estão implantados e configurados no seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="efb05-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="efb05-290">Para obter mais informações, consulte [Alocar GUIDs com segurança no Modo Pull da Configuração de Estado Desejado do PowerShell](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span><span class="sxs-lookup"><span data-stu-id="efb05-290">For more information, see [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span></span>

<span data-ttu-id="efb05-291">Tarefa de planejamento</span><span class="sxs-lookup"><span data-stu-id="efb05-291">Planning task</span></span>|
---|
<span data-ttu-id="efb05-292">Quem será responsável pela cópia de configurações na pasta do servidor de pull quando elas estiverem prontas?</span><span class="sxs-lookup"><span data-stu-id="efb05-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="efb05-293">Se as configurações são criadas por uma equipe de aplicativos, qual será o processo para entregá-las?</span><span class="sxs-lookup"><span data-stu-id="efb05-293">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="efb05-294">Você utilizará um repositório para armazenar configurações conforme elas são criadas entre as equipes?</span><span class="sxs-lookup"><span data-stu-id="efb05-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="efb05-295">Você automatizará o processo de copiar as configurações para o servidor e criar uma soma de verificação quando estiverem prontas?</span><span class="sxs-lookup"><span data-stu-id="efb05-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="efb05-296">Como você mapeará os GUIDs aos servidores ou às funções e onde isso será armazenado?</span><span class="sxs-lookup"><span data-stu-id="efb05-296">How will you map GUIDs to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="efb05-297">O que será usado como processo para configurar computadores cliente e como isso se integrará ao seu processo de criação e armazenamento de GUIDs de Configuração?</span><span class="sxs-lookup"><span data-stu-id="efb05-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration GUIDs?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="efb05-298">Guia de instalação</span><span class="sxs-lookup"><span data-stu-id="efb05-298">Installation Guide</span></span>

<span data-ttu-id="efb05-299">*Os scripts fornecidos neste documento são exemplos estáveis. Sempre examine os scripts cuidadosamente antes de executá-los em um ambiente de produção.*</span><span class="sxs-lookup"><span data-stu-id="efb05-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="efb05-300">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="efb05-300">Prerequisites</span></span>

<span data-ttu-id="efb05-301">Para verificar a versão do PowerShell no seu servidor use o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="efb05-301">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="efb05-302">Se possível, atualize para a versão mais recente do Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="efb05-302">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="efb05-303">Em seguida, baixe o módulo `xPsDesiredStateConfiguration` usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="efb05-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>


```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="efb05-304">O comando solicitará sua aprovação antes de baixar o módulo.</span><span class="sxs-lookup"><span data-stu-id="efb05-304">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="efb05-305">Scripts de instalação e configuração</span><span class="sxs-lookup"><span data-stu-id="efb05-305">Installation and configuration scripts</span></span>
-

<span data-ttu-id="efb05-306">O melhor método para implantar um servidor de pull de DSC é usar um script de configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="efb05-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="efb05-307">Este documento apresentará scripts que incluem as configurações básicas que configurariam apenas o serviço Web da DSC e as configurações avançadas, que configurariam um Windows Server de ponta a ponta, incluindo o serviço Web da DSC.</span><span class="sxs-lookup"><span data-stu-id="efb05-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="efb05-308">Observação: atualmente o módulo `xPSDesiredStateConfiguation` da DSC exige que o servidor seja de localidade EN-US.</span><span class="sxs-lookup"><span data-stu-id="efb05-308">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="efb05-309">Configuração básica para Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="efb05-309">Basic configuration for Windows Server 2012</span></span>
-------------------------------------------
```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="efb05-310">Configuração avançada para Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="efb05-310">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS
    
param (
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $Credential
    )
    
Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {
            
        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }
    
        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }
    
        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }
    
        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }
        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }
        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }
        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }
        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }
    
        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }
    
        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }
    
        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    
        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        { 
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        { 
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
    
        # Stop the default website
        xWebsite StopDefaultSite  
        { 
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}
$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }
PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
    
# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share' 
```


### <a name="verify-pull-server-functionality"></a><span data-ttu-id="efb05-311">Verificar a funcionalidade do servidor de pull</span><span class="sxs-lookup"><span data-stu-id="efb05-311">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN' 

Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="efb05-312">Configurar clientes</span><span class="sxs-lookup"><span data-stu-id="efb05-312">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager 
                { 
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15; 
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}
PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```


## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="efb05-313">Exemplos, trechos de código e referências adicionais</span><span class="sxs-lookup"><span data-stu-id="efb05-313">Additional references, snippets, and examples</span></span>

<span data-ttu-id="efb05-314">Este exemplo mostra como iniciar manualmente uma conexão de cliente (requer WMF5) para teste.</span><span class="sxs-lookup"><span data-stu-id="efb05-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span> 

```powershell
Update-DSCConfiguration –Wait -Verbose
```

<span data-ttu-id="efb05-315">O cmdlet [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) é usado para adicionar um tipo de registro CNAME em uma zona DNS.</span><span class="sxs-lookup"><span data-stu-id="efb05-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span> 

<span data-ttu-id="efb05-316">A função do PowerShell para [Criar uma soma de verificação e publicar o MOF da DSC em um servidor de pull de SMB](http://bit.ly/1E46BhI) gera automaticamente a soma de verificação necessária e, em seguida, copia a configuração do MOF e os arquivos de soma de verificação para o servidor de pull de SMB.</span><span class="sxs-lookup"><span data-stu-id="efb05-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](http://bit.ly/1E46BhI) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="efb05-317">Apêndice – Noções básicas sobre tipos de arquivo de dados do serviço ODATA</span><span class="sxs-lookup"><span data-stu-id="efb05-317">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="efb05-318">Um arquivo de dados é armazenado para criar informações durante a implantação de um servidor de pull que inclui o serviço Web OData.</span><span class="sxs-lookup"><span data-stu-id="efb05-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="efb05-319">O tipo de arquivo depende do sistema operacional, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="efb05-319">The type of file depends on the operating system, as described below.</span></span>

 - <span data-ttu-id="efb05-320">**Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="efb05-320">**Windows Server 2012**</span></span>  
<span data-ttu-id="efb05-321">O tipo de arquivo sempre será .mdb</span><span class="sxs-lookup"><span data-stu-id="efb05-321">The file type will always be   .mdb</span></span>
 - <span data-ttu-id="efb05-322">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="efb05-322">**Windows Server 2012 R2**</span></span>  
<span data-ttu-id="efb05-323">O tipo de arquivo padrão será .edb, a menos que um .mdb seja especificado na configuração</span><span class="sxs-lookup"><span data-stu-id="efb05-323">The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="efb05-324">No [Script de exemplo avançado](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) para a instalação de um Servidor de Pull, você também encontrará um exemplo de como controlar automaticamente as configurações do arquivo web.config para evitar qualquer possibilidade de erro causado pelo tipo de arquivo.</span><span class="sxs-lookup"><span data-stu-id="efb05-324">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>

