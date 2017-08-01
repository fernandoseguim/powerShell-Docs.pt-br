---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: conceitos fundamentais usados neste guia
ms.technology: powershell
ms.openlocfilehash: 873ab19fdf43ec4ac41cc546aa94b64fbc607984
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: pt-BR
---
# <a name="key-concepts-used-throughout-this-guide"></a><span data-ttu-id="c10e6-103">Conceitos fundamentais usados em todo este guia</span><span class="sxs-lookup"><span data-stu-id="c10e6-103">Key Concepts Used Throughout This Guide</span></span>
<span data-ttu-id="c10e6-104">**O que exatamente é o JEA?**</span><span class="sxs-lookup"><span data-stu-id="c10e6-104">**What exactly is JEA?**</span></span>

<span data-ttu-id="c10e6-105">O JEA é uma extensão de [pontos de extremidade restritos](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) do PowerShell que adiciona definições de função, contas virtuais e vários outros aprimoramentos para facilitar ainda mais o bloqueio dos seus pontos de extremidade de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="c10e6-105">JEA is an extension of PowerShell [constrained endpoints](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) that adds in role definitions, virtual accounts, and several other improvements to make it even easier to lock down your management endpoints.</span></span>
<span data-ttu-id="c10e6-106">Um ponto de extremidade de JEA consiste em um arquivo de Configuração de Sessão do PowerShell e um ou mais arquivos de Capacidade de Função.</span><span class="sxs-lookup"><span data-stu-id="c10e6-106">A JEA endpoint consists of a PowerShell Session Configuration file and one or more Role Capability files.</span></span>

<span data-ttu-id="c10e6-107">**Oque são arquivos de Configuração de Sessão e Capacidade de Função?**</span><span class="sxs-lookup"><span data-stu-id="c10e6-107">**What are Session Configuration and Role Capability files?**</span></span>

<span data-ttu-id="c10e6-108">Arquivos de Configuração de Sessão do PowerShell (.pssc) definem *quem* pode se conectar a um ponto de extremidade do PowerShell e *como* ele é configurado.</span><span class="sxs-lookup"><span data-stu-id="c10e6-108">PowerShell Session Configuration files (.pssc) define *who* can connect to a PowerShell endpoint and *how* it is configured.</span></span>
<span data-ttu-id="c10e6-109">É aqui que os usuários e grupos de segurança são mapeados para funções específicas de gerenciamento e defina as configurações globais como contas virtuais e políticas de transcrição.</span><span class="sxs-lookup"><span data-stu-id="c10e6-109">This is where you would map users and security groups to specific management roles and configure global settings like virtual accounts and transcription policies.</span></span>
<span data-ttu-id="c10e6-110">Arquivos de configuração de sessão são específicos para cada computador, permitindo que você controle o acesso por computador, se desejado.</span><span class="sxs-lookup"><span data-stu-id="c10e6-110">Session configuration files are specific to each machine, which allows you to control access on a per-machine basis if desired.</span></span>

<span data-ttu-id="c10e6-111">Arquivos de Capacidade de Função do PowerShell (.psrc) definem o *que* os usuários que pertencem a uma função são capazes de fazer no sistema.</span><span class="sxs-lookup"><span data-stu-id="c10e6-111">PowerShell Role Capability files (.psrc) define *what* users belonging to a role are able to do on the system.</span></span>
<span data-ttu-id="c10e6-112">Aqui você pode restringir quais cmdlets, funções, provedores e programas externos um usuário pode usar em sua sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="c10e6-112">Here, you can restrict which cmdlets, functions, providers, and external programs a user may use in their JEA session.</span></span>
<span data-ttu-id="c10e6-113">Arquivos de Capacidade de Função geralmente são genéricos para a função atendida (administrador DNS, suporte técnico de nível 1, auditoria de inventário de somente leitura, etc.) e pertencem a módulos do PowerShell, facilitando compartilhá-los em seu ambiente e com outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="c10e6-113">Role Capability files are often generic for the role being served (DNS admin, level 1 helpdesk, read-only inventory auditing, etc.) and belong to PowerShell modules, making it easy to share them across your environment and with others.</span></span>

<span data-ttu-id="c10e6-114">**Como o JEA aproveita as contas virtuais?**</span><span class="sxs-lookup"><span data-stu-id="c10e6-114">**How does JEA leverage virtual accounts?**</span></span>

<span data-ttu-id="c10e6-115">No arquivo de Configuração de Sessão do PowerShell, você pode configurar sessões JEA para usar contas virtuais "Executar como".</span><span class="sxs-lookup"><span data-stu-id="c10e6-115">In the PowerShell Session Configuration file, you can configure JEA sessions to use virtual "run as" accounts.</span></span>
<span data-ttu-id="c10e6-116">As contas virtuais são contas privilegiadas avulsas geradas para o usuário específico da conexão nessa sessão específica na qual o contexto dos comandos do usuário são executados.</span><span class="sxs-lookup"><span data-stu-id="c10e6-116">Virtual accounts are one-time privileged accounts spun up for the specific connecting user in that specific session under which context the user's commands are executed.</span></span>
<span data-ttu-id="c10e6-117">Contas virtuais pertencem ao grupo de segurança "Administradores" por padrão, mas podem ser opcionalmente configuradas para pertencer somente aos grupos de segurança que você especificar.</span><span class="sxs-lookup"><span data-stu-id="c10e6-117">Virtual accounts belong to the local "Administrators" security group by default, but can optionally be configured to only belong to security groups you specify.</span></span>

<span data-ttu-id="c10e6-118">**Comunicação Remota do PowerShell**: a comunicação remota do PowerShell permite que você execute comandos do PowerShell em computadores remotas.</span><span class="sxs-lookup"><span data-stu-id="c10e6-118">**PowerShell Remoting**: PowerShell remoting allows you to run PowerShell commands against remote machines.</span></span>
<span data-ttu-id="c10e6-119">Você pode operar em um ou vários computadores e usar conexões temporárias ou persistentes.</span><span class="sxs-lookup"><span data-stu-id="c10e6-119">You can operate against one or many computers, and use either temporary or persistent connections.</span></span>
<span data-ttu-id="c10e6-120">Nesta demonstração, você acessará remotamente seu computador local com uma sessão interativa.</span><span class="sxs-lookup"><span data-stu-id="c10e6-120">In this demo, you remoted into your local machine with an interactive session.</span></span>
<span data-ttu-id="c10e6-121">O JEA restringe a funcionalidade disponível por meio de comunicação remota do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c10e6-121">JEA restricts the functionality available through PowerShell remoting.</span></span>
<span data-ttu-id="c10e6-122">Para obter mais informações sobre a conexão remota do PowerShell, execute `Get-Help about_Remote`.</span><span class="sxs-lookup"><span data-stu-id="c10e6-122">For more information about PowerShell remoting, run `Get-Help about_Remote`.</span></span>

<span data-ttu-id="c10e6-123">**Usuário "RunAs"**: ao usar JEA, um não administrador "é executado como" uma conta com privilégios de "Conta Virtual".</span><span class="sxs-lookup"><span data-stu-id="c10e6-123">**"RunAs" User**: When using JEA, a non-administrator "runs as" a privileged "Virtual Account."</span></span>
<span data-ttu-id="c10e6-124">A Conta Virtual dura apenas pela duração da sessão remota.</span><span class="sxs-lookup"><span data-stu-id="c10e6-124">The Virtual Account only lasts the duration of the remote session.</span></span>
<span data-ttu-id="c10e6-125">Isso significa que ela é criada quando um usuário se conecta ao ponto de extremidade e é destruída quando o usuário encerra a sessão.</span><span class="sxs-lookup"><span data-stu-id="c10e6-125">That is to say, it is created when a user connects to the endpoint, and destroyed when the user ends the session.</span></span>
<span data-ttu-id="c10e6-126">Por padrão, a Conta Virtual é um membro do grupo Administradores local.</span><span class="sxs-lookup"><span data-stu-id="c10e6-126">By default, the Virtual Account is a member of the local Administrators group.</span></span>
<span data-ttu-id="c10e6-127">Em um controlador de domínio, ele é um membro do grupo Administradores de Domínio.</span><span class="sxs-lookup"><span data-stu-id="c10e6-127">On a domain controller, it is a member of Domain Admins.</span></span>
<span data-ttu-id="c10e6-128">Contas Virtuais são locais no computador no qual são criadas e não têm permissões fora desse computador.</span><span class="sxs-lookup"><span data-stu-id="c10e6-128">Virtual Accounts are local to the machine on which they are created, and do not have permissions outside of that machine.</span></span>
<span data-ttu-id="c10e6-129">Isso significa que eles não são registrados no Active Directory (nenhum RID atribuído).</span><span class="sxs-lookup"><span data-stu-id="c10e6-129">This means that they are not registered in Active Directory (no RID is assigned).</span></span>
<span data-ttu-id="c10e6-130">Além disso, se um comando/script permitido tentar acessar recursos fora do computador local, ele acessará esses recursos com a identidade do computador, não da Conta Virtual.</span><span class="sxs-lookup"><span data-stu-id="c10e6-130">Additionally, if an allowed command/script tries to access resources outside of the local machine, it will be accessing those resources under the machine's identity, not the Virtual Account identity.</span></span>

<span data-ttu-id="c10e6-131">**Usuário "Conectado"**: o usuário não administrador que se conecta ao ponto de extremidade JEA e ao qual são atribuídas as funções.</span><span class="sxs-lookup"><span data-stu-id="c10e6-131">**"Connected" User**: The non-administrator user who connects to the JEA endpoint and to whom roles are assigned.</span></span>
<span data-ttu-id="c10e6-132">Quaisquer comandos executado por esse usuário são executados sob o contexto do usuário RunAs ou conta virtual.</span><span class="sxs-lookup"><span data-stu-id="c10e6-132">Any commands this user runs are run under the context of the RunAs User or virtual account.</span></span>

