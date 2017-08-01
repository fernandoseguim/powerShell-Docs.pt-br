---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: ARQUIVO LEIAME
ms.technology: powershell
ms.openlocfilehash: b0ef4ff685b82e1a4e9ab83a45736720df7b39a2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: pt-BR
---
# <a name="just-enough-administration"></a><span data-ttu-id="acda7-103">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="acda7-103">Just Enough Administration</span></span>
<span data-ttu-id="acda7-104">JEA (Just Enough Administration) é uma tecnologia de segurança que habilita o uso de administração delegada para qualquer coisa que pode ser gerenciada com o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="acda7-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything that can be managed with PowerShell.</span></span>
<span data-ttu-id="acda7-105">Com o JEA, você pode:</span><span class="sxs-lookup"><span data-stu-id="acda7-105">With JEA, you can:</span></span>
- <span data-ttu-id="acda7-106">**Reduzir o número de administradores em seus computadores** aproveitando contas virtuais que executam ações privilegiadas em nome dos usuários regulares.</span><span class="sxs-lookup"><span data-stu-id="acda7-106">**Reduce the number of administrators on your machines** by leveraging virtual accounts that perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="acda7-107">**Limitar o que os usuários podem fazer** especificando quais cmdlets, funções e comandos externos eles podem executar.</span><span class="sxs-lookup"><span data-stu-id="acda7-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="acda7-108">**Entender melhor o que seus usuários estão fazendo** com transcrições "Over The Shoulder” que mostram exatamente quais comandos um usuário executou durante uma sessão.</span><span class="sxs-lookup"><span data-stu-id="acda7-108">**Better understand what your users are doing** with "over the shoulder" transcriptions that show you exactly what commands a user executed during a session.</span></span>

<span data-ttu-id="acda7-109">**Por que isso é importante?**</span><span class="sxs-lookup"><span data-stu-id="acda7-109">**Why is this important?**</span></span>  
<span data-ttu-id="acda7-110">Considere o cenário comum em que os servidores DNS estão colocalizados com seus Controladores de Domínio do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="acda7-110">Consider the common scenario where your DNS servers are co-located with your Active Directory Domain Controllers.</span></span>
<span data-ttu-id="acda7-111">Os administradores DNS precisam ter privilégios de administrador local para corrigir problemas com o servidor DNS, porém para isso você precisa torná-los membros do grupo de segurança altamente privilegiado "Administradores do Domínio".</span><span class="sxs-lookup"><span data-stu-id="acda7-111">Your DNS administrators need to have local administrator privileges to fix issues with the DNS server, but in order to do so you have to make them members of the highly privileged "Domain Admins" security group.</span></span>
<span data-ttu-id="acda7-112">Essa abordagem concede de forma efetiva aos Administradores de DNS o controle todo o domínio e o acesso a todos os recursos nesse computador.</span><span class="sxs-lookup"><span data-stu-id="acda7-112">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="acda7-113">Com o JEA em vigor, você pode configurar uma função para seus administradores de DNS que concede acesso a todos os comandos que eles precisam para trabalhar, e nada mais.</span><span class="sxs-lookup"><span data-stu-id="acda7-113">With JEA in place, you can configure a role for your DNS administrators that gives them access to all the commands they need to get their job done, but nothing more.</span></span>
<span data-ttu-id="acda7-114">Isso significa que você pode fornecer o acesso apropriado para reparar um cache DNS inviabilizado sem acidentalmente conceder a eles direitos ao Active Directory, para navegar no sistema de arquivos ou para executar scripts potencialmente perigosos.</span><span class="sxs-lookup"><span data-stu-id="acda7-114">This means you can provide the appropriate access to repair a poisoned DNS cache without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span>
<span data-ttu-id="acda7-115">Melhor ainda, quando a sessão JEA está configurada para usar contas virtuais privilegiadas avulsas, seus administradores de DNS podem se conectar ao servidor usando credenciais *sem privilégios* e ainda poderão executar comandos privilegiados.</span><span class="sxs-lookup"><span data-stu-id="acda7-115">Better yet, when the JEA session is configured to use one-time privileged virtual accounts, your DNS administrators can connect to the server using *unprivileged* credentials and still be able to run privileged commands.</span></span>

## <a name="availability"></a><span data-ttu-id="acda7-116">Disponibilidade</span><span class="sxs-lookup"><span data-stu-id="acda7-116">Availability</span></span>
<span data-ttu-id="acda7-117">O JEA está sendo desenvolvido paralelamente ao Windows Server 2016 e está disponível em versões anteriores mais antigas do Windows por meio de atualizações do Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="acda7-117">JEA is being developed in parallel to Windows Server 2016, and is available on older versions of Windows through Windows Management Framework updates.</span></span>
<span data-ttu-id="acda7-118">A versão atual do JEA está disponível nas seguintes plataformas:</span><span class="sxs-lookup"><span data-stu-id="acda7-118">The current release of JEA is available on the following platforms:</span></span>

<span data-ttu-id="acda7-119">**Windows Server**</span><span class="sxs-lookup"><span data-stu-id="acda7-119">**Windows Server**</span></span>
- <span data-ttu-id="acda7-120">Windows Server 2016 Technical Preview 4 e superior</span><span class="sxs-lookup"><span data-stu-id="acda7-120">Windows Server 2016 Technical Preview 4 and higher</span></span>
- <span data-ttu-id="acda7-121">Windows Server 2012 R2, 2012 e 2008 R2\* com [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) instalado</span><span class="sxs-lookup"><span data-stu-id="acda7-121">Windows Server 2012 R2, 2012, and 2008 R2\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="acda7-122">**Windows Client**</span><span class="sxs-lookup"><span data-stu-id="acda7-122">**Windows Client**</span></span>
- <span data-ttu-id="acda7-123">Windows 10 com a Atualização de Novembro (1511) instalada</span><span class="sxs-lookup"><span data-stu-id="acda7-123">Windows 10 with the November Update (1511) installed</span></span>
- <span data-ttu-id="acda7-124">Windows 8.1, 8 e 7\* com [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) instalado</span><span class="sxs-lookup"><span data-stu-id="acda7-124">Windows 8.1, 8, and 7\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="acda7-125">\* Suporte para contas virtuais em sessões JEA atualmente não está disponível no Windows Server 2008 R2 ou Windows 7.</span><span class="sxs-lookup"><span data-stu-id="acda7-125">\* Support for virtual accounts in JEA sessions is currently not available on Windows Server 2008 R2 or Windows 7.</span></span>


## <a name="explore-the-experience-guide"></a><span data-ttu-id="acda7-126">Explorar o guia de experiência</span><span class="sxs-lookup"><span data-stu-id="acda7-126">Explore the experience guide</span></span>
<span data-ttu-id="acda7-127">Pronto para aprender a criar, implantar e usar seu próprio ponto de extremidade JEA?</span><span class="sxs-lookup"><span data-stu-id="acda7-127">Ready to learn how to author, deploy, and use your own JEA endpoint?</span></span>

<span data-ttu-id="acda7-128">Este guia o familiariza rapidamente com um ponto de extremidade de JEA pré-criado para dar uma ideia de como é a experiência do usuário final, além de explicar a recriação de um ponto de extremidade do zero para ajudar a demonstrar conceitos como configurações de sessão e Recursos de Função.</span><span class="sxs-lookup"><span data-stu-id="acda7-128">This guide gets you started quickly with a pre-built JEA endpoint to get an idea of what the end-user experience is like, then walks you through recreating an endpoint from scratch to help demonstrate concepts like session configurations and Role Capabilities.</span></span>

1.  <span data-ttu-id="acda7-129">[Introdução](introduction.md) </span><span class="sxs-lookup"><span data-stu-id="acda7-129">[Introduction](introduction.md) </span></span>  
<span data-ttu-id="acda7-130">Examina rapidamente por que o JEA é importante</span><span class="sxs-lookup"><span data-stu-id="acda7-130">Briefly review why you should care about JEA</span></span>

2.  [<span data-ttu-id="acda7-131">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="acda7-131">Prerequisites</span></span>](prerequisites.md)  
<span data-ttu-id="acda7-132">Explica como configurar seu ambiente</span><span class="sxs-lookup"><span data-stu-id="acda7-132">Explains how to set up your environment</span></span>

3.  [<span data-ttu-id="acda7-133">Usando JEA</span><span class="sxs-lookup"><span data-stu-id="acda7-133">Using JEA</span></span>](using-jea.md)  
<span data-ttu-id="acda7-134">Ajuda a entender a experiência do operador com o JEA</span><span class="sxs-lookup"><span data-stu-id="acda7-134">Helps you start by understanding the operator experience of using JEA</span></span>

4.  [<span data-ttu-id="acda7-135">Recriar a demonstração</span><span class="sxs-lookup"><span data-stu-id="acda7-135">Remake the Demo</span></span>](remake-the-demo-endpoint.md)  
<span data-ttu-id="acda7-136">Criar uma configuração de sessão JEA do zero</span><span class="sxs-lookup"><span data-stu-id="acda7-136">Create a JEA Session Configuration from scratch</span></span>

5.  [<span data-ttu-id="acda7-137">Capacidades de Função</span><span class="sxs-lookup"><span data-stu-id="acda7-137">Role Capabilities</span></span>](role-capabilities.md)  
<span data-ttu-id="acda7-138">Saiba mais sobre como personalizar funcionalidades JEA com Arquivos de Funcionalidade de Função</span><span class="sxs-lookup"><span data-stu-id="acda7-138">Learn about how to customize JEA capabilities with Role Capability Files</span></span>

6.  [<span data-ttu-id="acda7-139">Ponta a Ponta – Active Directory</span><span class="sxs-lookup"><span data-stu-id="acda7-139">End to End - Active Directory</span></span>](end-to-end---active-directory.md)  
<span data-ttu-id="acda7-140">Criar um novo ponto de extremidade para gerenciar o Active Directory</span><span class="sxs-lookup"><span data-stu-id="acda7-140">Make a whole new endpoint for managing Active Directory</span></span>

7.  [<span data-ttu-id="acda7-141">Manutenção e implantação de vários computadores</span><span class="sxs-lookup"><span data-stu-id="acda7-141">Multi-machine Deployment and Maintenance</span></span>](multi-machine-deployment-and-maintenance.md)  
<span data-ttu-id="acda7-142">Descobrir como a implantação e criação mudam com a escala</span><span class="sxs-lookup"><span data-stu-id="acda7-142">Discover how deployment and authoring changes with scale</span></span>

8.  [<span data-ttu-id="acda7-143">Relatando no JEA</span><span class="sxs-lookup"><span data-stu-id="acda7-143">Reporting on JEA</span></span>](reporting-on-jea.md)  
<span data-ttu-id="acda7-144">Descobrir como auditar e relatar todas as ações e a infraestrutura do JEA</span><span class="sxs-lookup"><span data-stu-id="acda7-144">Discover how to audit and report on all JEA actions and infrastructure</span></span>

9.  <span data-ttu-id="acda7-145">Apêndices</span><span class="sxs-lookup"><span data-stu-id="acda7-145">Appendixes</span></span>
  - [<span data-ttu-id="acda7-146">Conceitos fundamentais usados em todo este guia</span><span class="sxs-lookup"><span data-stu-id="acda7-146">Key Concepts Used Throughout This Guide</span></span>](key-concepts-used-throughout-this-guide.md)  
  -  [<span data-ttu-id="acda7-147">Criar um Controlador de Domínio</span><span class="sxs-lookup"><span data-stu-id="acda7-147">Creating a Domain Controller</span></span>](creating-a-domain-controller.md)  
  -  [<span data-ttu-id="acda7-148">Sobre lista de bloqueios</span><span class="sxs-lookup"><span data-stu-id="acda7-148">On Blacklisting</span></span>](on-blacklisting.md)  
  -  [<span data-ttu-id="acda7-149">Considerações sobre a limitação de comandos</span><span class="sxs-lookup"><span data-stu-id="acda7-149">Considerations When Limiting Commands</span></span>](considerations-when-limiting-commands.md)  
  -  [<span data-ttu-id="acda7-150">Armadilhas comuns de Capacidade de Função</span><span class="sxs-lookup"><span data-stu-id="acda7-150">Common Role Capability Pitfalls</span></span>](common-role-capability-pitfalls.md)

## <a name="start-authoring-your-own-jea-endpoints"></a><span data-ttu-id="acda7-151">Começar a criar seus próprios pontos de extremidade de JEA</span><span class="sxs-lookup"><span data-stu-id="acda7-151">Start authoring your own JEA endpoints</span></span>
<span data-ttu-id="acda7-152">É fácil criar um ponto de extremidade de JEA, tudo o que você precisa é um sistema habilitado para JEA e um editor de texto (como o ISE do PowerShell).</span><span class="sxs-lookup"><span data-stu-id="acda7-152">It's easy to author a JEA endpoint -- all you need is a JEA-enabled system and a text editor (like PowerShell ISE).</span></span>
<span data-ttu-id="acda7-153">Uma dica útil para começar é criar arquivos esqueleto usando [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) e [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) sem outros argumentos.</span><span class="sxs-lookup"><span data-stu-id="acda7-153">One helpful tip to get started is to create skeleton files using [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) and [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) without any other arguments.</span></span>
<span data-ttu-id="acda7-154">Esses arquivos de esqueleto contêm todos os campos de configuração aplicáveis juntamente com comentários úteis para explicar a finalidade de cada campo.</span><span class="sxs-lookup"><span data-stu-id="acda7-154">These skeleton files contain all of the applicable configuration fields along with helpful comments to explain what each field can be used for.</span></span>

<span data-ttu-id="acda7-155">Para tornar a criação dos pontos de extremidade de JEA ainda mais fácil, confira o [Auxiliar do Kit de Ferramentas JEA](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) que fornece uma interface gráfica com a qual você pode criar arquivos de Configuração de Sessão e de Capacidade de Função.</span><span class="sxs-lookup"><span data-stu-id="acda7-155">To make authoring JEA endpoints even easier, check out the [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) which provides a GUI with which you can author Session Configuration and Role Capability files.</span></span>
<span data-ttu-id="acda7-156">Ela ainda dão suporte à geração de Capacidades de Função com base nos logs do PowerShell para dar os primeiros passos nos comandos que os usuários executam regularmente para trabalhar.</span><span class="sxs-lookup"><span data-stu-id="acda7-156">It even supports generating Role Capabilities based on PowerShell logs to start you off with the commands your users regularly run to get their jobs done.</span></span>

