---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: instalar e usar o windows powershell web access
ms.openlocfilehash: a860f7c22829da46f0458ea729fa0afd1fe4fb6f
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
#  <a name="install-and-use-windows-powershell-web-access"></a><span data-ttu-id="df311-103">Instalar e usar o Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="df311-103">Install and Use Windows PowerShell Web Access</span></span>

<span data-ttu-id="df311-104">Atualizado em: 5 de novembro de 2013</span><span class="sxs-lookup"><span data-stu-id="df311-104">Updated: November 5, 2013</span></span>

<span data-ttu-id="df311-105">Aplica-se a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="df311-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="df311-106">Windows PowerShell® Web Access, introduzido no Windows Server® 2012, atua como um gateway do Windows PowerShell, oferecendo um console baseado na Web do Windows PowerShell, destinado a um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="df311-106">Windows PowerShell® Web Access, first introduced in Windows Server® 2012, acts as a Windows PowerShell gateway, providing a web-based Windows PowerShell console that is targeted at a remote computer.</span></span> <span data-ttu-id="df311-107">Ele permite aos profissionais de TI executar comandos e scripts no console do Windows PowerShell em um navegador da Web, sem necessidade de instalar o Windows PowerShell, software de gerenciamento remoto ou plug-in de navegador no dispositivo cliente.</span><span class="sxs-lookup"><span data-stu-id="df311-107">It enables IT Pros to run Windows PowerShell commands and scripts from a Windows PowerShell console in a web browser, with no Windows PowerShell, remote management software, or browser plug-in installation necessary on the client device.</span></span> <span data-ttu-id="df311-108">Para executar o console do Windows PowerShell baseado na Web, basta um gateway do Windows PowerShell Web Access devidamente configurado e um navegador de dispositivo cliente que dê suporte a JavaScript® e aceite cookies.</span><span class="sxs-lookup"><span data-stu-id="df311-108">All that is required to run the web-based Windows PowerShell console is a properly-configured Windows PowerShell Web Access gateway, and a client device browser that supports JavaScript® and accepts cookies.</span></span>

<span data-ttu-id="df311-109">Exemplos de dispositivos clientes: laptops, computadores pessoais não usados para trabalho, computadores emprestados, tablets, quiosques Web, computadores que não executam sistemas operacionais baseados em Windows e navegadores de celulares.</span><span class="sxs-lookup"><span data-stu-id="df311-109">Examples of client devices include laptops, non-work personal computers, borrowed computers, tablet computers, web kiosks, computers that are not running a Windows-based operating system, and cell phone browsers.</span></span> <span data-ttu-id="df311-110">Os profissionais de TI podem realizar tarefas essenciais de gerenciamento em servidores remotos baseados em Windows a partir de dispositivos com acesso a uma conexão com a Internet e um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="df311-110">IT Pros can perform critical management tasks on remote Windows-based servers from devices that have access to an Internet connection and a web browser.</span></span>

<span data-ttu-id="df311-111">Depois de instalar e configurar o gateway com sucesso, os usuários podem acessar um console do Windows PowerShell usando um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="df311-111">After successful gateway setup and configuration, users can access a Windows PowerShell console by using a web browser.</span></span> <span data-ttu-id="df311-112">Quando os usuários abrem o site seguro do Windows PowerShell Web Access, eles podem executar um console do Windows PowerShell baseado na Web após autenticação bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="df311-112">When users open the secured Windows PowerShell Web Access website, they can run a web-based Windows PowerShell console after successful authentication.</span></span>

<span data-ttu-id="df311-113">O processo de instalação e configuração do Windows PowerShell Web Access inclui três etapas:</span><span class="sxs-lookup"><span data-stu-id="df311-113">Windows PowerShell Web Access setup and configuration is a three-step process:</span></span>

1.  <span data-ttu-id="df311-114">Instalando o Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="df311-114">Installing Windows PowerShell Web Access</span></span>

2.  <span data-ttu-id="df311-115">Configurando o gateway</span><span class="sxs-lookup"><span data-stu-id="df311-115">Configuring the gateway</span></span>

3.  <span data-ttu-id="df311-116">Configurando regras de autorização que permitem acesso de usuários ao console do Windows PowerShell baseado na Web</span><span class="sxs-lookup"><span data-stu-id="df311-116">Configuring authorization rules that allow users access to the web-based Windows PowerShell console</span></span>

<span data-ttu-id="df311-117">Antes de instalar e configurar o Windows PowerShell Web Access, recomendamos ler todo este guia, o qual inclui instruções sobre como instalar, proteger e desinstalar o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-117">Before you install and configure Windows PowerShell Web Access, we recommend that you read this entire guide, which includes instructions about how to install, secure, and uninstall Windows PowerShell Web Access.</span></span> <span data-ttu-id="df311-118">O tópico [Usar o console do Windows PowerShell baseado na Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) descreve como os usuários entram no console baseado na Web, além de abordar limitações e as diferenças entre o console do Windows PowerShell baseado na web e o console **powershell.exe**.</span><span class="sxs-lookup"><span data-stu-id="df311-118">The [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) topic describes how users sign in to the web-based console, and covers limitations and differences between the web-based Windows PowerShell console and the **powershell.exe** console.</span></span> <span data-ttu-id="df311-119">Os usuários finais do console baseado na Web devem ler o artigo [Usar o console do Windows PowerShell baseado na Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), mas não precisam ler o restante do guia.</span><span class="sxs-lookup"><span data-stu-id="df311-119">End users of the web-based console should read [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), but do not need to read the rest of this guide.</span></span>

<span data-ttu-id="df311-120">Este tópico não fornece diretrizes detalhadas de operações do Servidor Web (IIS). Ele contém apenas as etapas necessárias para configurar o gateway do Windows PowerShell Web Access, como descrito neste tópico.</span><span class="sxs-lookup"><span data-stu-id="df311-120">This topic does not provide in-depth Web Server (IIS) operations guidance; only those steps required to configure the Windows PowerShell Web Access gateway are described in this topic.</span></span> <span data-ttu-id="df311-121">Para obter mais informações sobre como configurar e proteger sites no IIS, consulte os recursos da documentação do IIS na seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="df311-121">For more information about configuring and securing websites in IIS, see the IIS documentation resources in the See Also section.</span></span>

<span data-ttu-id="df311-122">O diagrama a seguir mostra como funciona o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-122">The following diagram shows how Windows PowerShell Web Access works.</span></span>

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

<span data-ttu-id="df311-123">Neste tópico:</span><span class="sxs-lookup"><span data-stu-id="df311-123">In this topic:</span></span>

-   [<span data-ttu-id="df311-124">Requisitos para execução do Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="df311-124">Requirements for running Windows PowerShell Web Access</span></span>](#BKMK_reqs)

-   [<span data-ttu-id="df311-125">Suporte a navegadores e dispositivos cliente</span><span class="sxs-lookup"><span data-stu-id="df311-125">Browser and client device support</span></span>](#BKMK_browser)

-   [<span data-ttu-id="df311-126">Implantação (rápida) recomendada</span><span class="sxs-lookup"><span data-stu-id="df311-126">Recommended (quick) deployment</span></span>](#BKMK_recm)

-   [<span data-ttu-id="df311-127">Implantação personalizada</span><span class="sxs-lookup"><span data-stu-id="df311-127">Custom deployment</span></span>](#BKMK_custom)

-   [<span data-ttu-id="df311-128">Configurar um certificado original</span><span class="sxs-lookup"><span data-stu-id="df311-128">Configure a genuine certificate</span></span>](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<span data-ttu-id="df311-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisitos para execução do Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="df311-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requirements for running Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-130">O Windows PowerShell Web Access requer um servidor Web (IIS), .NET Framework 4.5 e o Windows PowerShell 3.0 ou Windows PowerShell 4.0 em execução no servidor no qual você deseja executar o gateway.</span><span class="sxs-lookup"><span data-stu-id="df311-130">Windows PowerShell Web Access requires Web Server (IIS), .NET Framework 4.5, and Windows PowerShell 3.0 or Windows PowerShell 4.0 to be running on the server on which you want to run the gateway.</span></span> <span data-ttu-id="df311-131">Você pode instalar o Windows PowerShell Web Access em um servidor que está executando o Windows Server 2012 R2 ou o Windows Server 2012 usando o Assistente Adicionar Funções e Recursos no Gerenciador do Servidor ou cmdlets de implantação do Windows PowerShell para o Gerenciador do Servidor.</span><span class="sxs-lookup"><span data-stu-id="df311-131">You can install Windows PowerShell Web Access on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either the Add Roles and Features Wizard in Server Manager, or Windows PowerShell deployment cmdlets for Server Manager.</span></span> <span data-ttu-id="df311-132">Quando você instala o Windows PowerShell Web Access usando o Gerenciador do Servidor ou seus cmdlets de implantação, as funções e os recursos necessários são automaticamente adicionados como parte do processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="df311-132">When you install Windows PowerShell Web Access by using Server Manager or its deployment cmdlets, required roles and features are automatically added as part of the installation process.</span></span>

<span data-ttu-id="df311-133">O Windows PowerShell Web Access permite que usuários remotos acessem computadores em sua organização usando o Windows PowerShell em um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="df311-133">Windows PowerShell Web Access allows remote users to access computers in your organization by using Windows PowerShell in a web browser.</span></span> <span data-ttu-id="df311-134">Embora o Windows PowerShell Web Access seja uma ferramenta de gerenciamento avançada e conveniente, o acesso baseado na Web impõe riscos à segurança e deve ser configurado da maneira mais segura possível.</span><span class="sxs-lookup"><span data-stu-id="df311-134">Although Windows PowerShell Web Access is a convenient and powerful management tool, the web-based access poses security risks, and should be configured as securely as possible.</span></span> <span data-ttu-id="df311-135">Recomendamos que os administradores que configuram o gateway do Windows PowerShell Web Access usem as camadas de segurança disponíveis, as regras de autorização baseadas em cmdlets incluídas no Windows PowerShell Web Access e as camadas de segurança disponíveis no Servidor Web (IIS) e em aplicativos de terceiros.</span><span class="sxs-lookup"><span data-stu-id="df311-135">We recommend that administrators who configure the Windows PowerShell Web Access gateway use available security layers, both the cmdlet-based authorization rules included with Windows PowerShell Web Access, and security layers that are available in Web Server (IIS) and third-party applications.</span></span> <span data-ttu-id="df311-136">Esta documentação inclui exemplos desprotegidos, recomendados apenas para ambientes de teste, além de exemplos recomendados para implantações seguras.</span><span class="sxs-lookup"><span data-stu-id="df311-136">This documentation includes both unsecure examples that are only recommended for test environments, as well as examples that are recommended for secure deployments.</span></span>

<a href="" id="BKMK_browser"></a>

<span data-ttu-id="df311-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Suporte a navegadores e dispositivos cliente</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="df311-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser and client device support</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-138">O Windows PowerShell Web Access dá suporte aos seguintes navegadores da Internet.</span><span class="sxs-lookup"><span data-stu-id="df311-138">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="df311-139">Embora navegadores móveis não tenham suporte oficialmente, muitos poderão executar o console do Windows PowerShell baseado na Web.</span><span class="sxs-lookup"><span data-stu-id="df311-139">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="df311-140">É provável que outros navegadores que aceitam cookies, executam JavaScript e abrem sites HTTPS funcionam, mas não foram oficialmente testados.</span><span class="sxs-lookup"><span data-stu-id="df311-140">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="df311-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navegadores de computador desktop compatíveis</span></a></span><span class="sxs-lookup"><span data-stu-id="df311-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="df311-142">Windows® Internet Explorer® para Microsoft Windows® 8.0, 9.0, 10.0 e 11.0</span><span class="sxs-lookup"><span data-stu-id="df311-142">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="df311-143">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="df311-143">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="df311-144">Google Chrome™ 17.0.963.56m para Windows</span><span class="sxs-lookup"><span data-stu-id="df311-144">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="df311-145">Apple Safari® 5.1.2 para Windows</span><span class="sxs-lookup"><span data-stu-id="df311-145">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="df311-146">Apple Safari 5.1.2 para Mac OS®</span><span class="sxs-lookup"><span data-stu-id="df311-146">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="df311-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navegadores ou dispositivos móveis minimamente testados</span></a></span><span class="sxs-lookup"><span data-stu-id="df311-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="df311-148">Windows Phone 7 e 7.5</span><span class="sxs-lookup"><span data-stu-id="df311-148">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="df311-149">Navegador Google Android WebKit 3.1 Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="df311-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="df311-150">Apple Safari para iPhone com sistema operacional 5.0.1</span><span class="sxs-lookup"><span data-stu-id="df311-150">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="df311-151">Apple Safari para iPad 2 com sistema operacional 5.0.1</span><span class="sxs-lookup"><span data-stu-id="df311-151">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="df311-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisitos de navegador</span></a></span><span class="sxs-lookup"><span data-stu-id="df311-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-153">Para usar o console do Windows PowerShell Web Access baseado na Web, os navegadores devem executar os procedimentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="df311-153">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="df311-154">Permitir cookies do site do gateway do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-154">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="df311-155">Ser capazes de abrir e ler páginas HTTPS.</span><span class="sxs-lookup"><span data-stu-id="df311-155">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="df311-156">Abrir e executar sites que usam JavaScript.</span><span class="sxs-lookup"><span data-stu-id="df311-156">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_recm"></a>

<span data-ttu-id="df311-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Implantação (rápida) recomendada</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="df311-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-158">Você pode instalar o gateway do Windows PowerShell Web Access em um servidor que está executando o Windows Server 2012 R2 ou o Windows Server 2012 usando o cmdlets do Windows PowerShell ou o assistente Adicionar Funções e Recursos que é aberto no Gerenciador do Servidor.</span><span class="sxs-lookup"><span data-stu-id="df311-158">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either Windows PowerShell cmdlets, or by using the Add Roles and Features Wizard that is opened from within Server Manager.</span></span> <span data-ttu-id="df311-159">Para rápida instalação e configuração, use os cmdlets do Windows PowerShell, conforme descrito nesta seção.</span><span class="sxs-lookup"><span data-stu-id="df311-159">For quick installation and configuration, use Windows PowerShell cmdlets, as described in this section.</span></span>

-   [<span data-ttu-id="df311-160">Etapa 1: instalar o Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="df311-160">Step 1: Install Windows PowerShell Web Access</span></span>](#BKMK_step1)

-   [<span data-ttu-id="df311-161">Etapa 2: configurar o gateway</span><span class="sxs-lookup"><span data-stu-id="df311-161">Step 2: Configure the gateway</span></span>](#BKMK_step2)

-   [<span data-ttu-id="df311-162">Etapa 3: configurar uma regra de autorização restritiva</span><span class="sxs-lookup"><span data-stu-id="df311-162">Step 3: Configure a restrictive authorization rule</span></span>](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<span data-ttu-id="df311-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 1: instalar o Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="df311-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="df311-164">Para instalar o Windows PowerShell Web Access usando cmdlets do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="df311-164">To install Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="df311-165">Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados.</span><span class="sxs-lookup"><span data-stu-id="df311-165">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="df311-166">Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="df311-166">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="df311-167">Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="df311-167">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="df311-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Observação </span></span><span class="sxs-lookup"><span data-stu-id="df311-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="df311-169">No Windows PowerShell 3.0 e 4.0, não é preciso importar o módulo de cmdlet do Gerenciador do Servidor para a sessão do Windows PowerShell antes de executar os cmdlets que fazem parte do módulo.</span><span class="sxs-lookup"><span data-stu-id="df311-169">In Windows PowerShell 3.0 and 4.0, there is no need to import the Server Manager cmdlet module into the Windows PowerShell session before running cmdlets that are part of the module.</span></span> <span data-ttu-id="df311-170">Um módulo é importado automaticamente durante a primeira execução de um cmdlet que faça parte do módulo.</span><span class="sxs-lookup"><span data-stu-id="df311-170">A module is automatically imported the first time you run a cmdlet that is part of the module.</span></span> <span data-ttu-id="df311-171">Além disso, os cmdlets do Windows PowerShell não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="df311-171">Also, Windows PowerShell cmdlets are not case-sensitive.</span></span></p></td>
    </tr>
    </tbody>
    </table>

2.  <span data-ttu-id="df311-172">Digite o seguinte e pressione **Enter**, em que *computer_name* representa um computador remoto no qual você deseja instalar o Windows PowerShell Web Access, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="df311-172">Type the following, and then press **Enter**, where *computer_name* represents a remote computer on which you want to install Windows PowerShell Web Access, if applicable.</span></span> <span data-ttu-id="df311-173">O parâmetro <span class="code">Reiniciar</span> reinicia automaticamente os servidores de destino, se necessário.</span><span class="sxs-lookup"><span data-stu-id="df311-173">The <span class="code">Restart</span> parameter automatically restarts destination servers if required.</span></span>

    [<span data-ttu-id="df311-174">Cópia</span><span class="sxs-lookup"><span data-stu-id="df311-174">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "Copy to clipboard.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="df311-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Observação </span></span><span class="sxs-lookup"><span data-stu-id="df311-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="df311-176">A instalação do Windows PowerShell Web Access usando cmdlets do Windows PowerShell não adiciona ferramentas de gerenciamento do Servidor Web (IIS) por padrão.</span><span class="sxs-lookup"><span data-stu-id="df311-176">Installing Windows PowerShell Web Access by using Windows PowerShell cmdlets does not add Web Server (IIS) management tools by default.</span></span> <span data-ttu-id="df311-177">Para instalar ferramentas de gerenciamento no mesmo servidor que o gateway do Windows PowerShell Web Access, adicione o parâmetro <span class="code">IncludeManagementTools</span> ao comando de instalação (como fornecido nesta etapa).</span><span class="sxs-lookup"><span data-stu-id="df311-177">If you want to install the management tools on the same server as the Windows PowerShell Web Access gateway, add the <span class="code">IncludeManagementTools</span> parameter to the installation command (as provided in this step).</span></span> <span data-ttu-id="df311-178">Se você estiver gerenciando o site do Windows PowerShell Web Access de um computador remoto, instale o snap-in Gerenciador do IIS ao instalar as <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Ferramentas de Administração de Servidor Remoto do Windows 8.1</a> ou as <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Ferramentas de Administração de Servidor Remoto para Windows 8</a> no computador do qual você quer gerenciar o gateway.</span><span class="sxs-lookup"><span data-stu-id="df311-178">If you are managing the Windows PowerShell Web Access website from a remote computer, install the IIS Manager snap-in by installing <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Remote Server Administration Tools for Windows 8.1</a> or <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Remote Server Administration Tools for Windows 8</a> on the computer from which you want to manage the gateway.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="df311-179">Para instalar funções e recursos em um VHD offline, adicione os parâmetros <span class="code">ComputerName</span> e <span class="code">VHD</span>.</span><span class="sxs-lookup"><span data-stu-id="df311-179">To install roles and features on an offline VHD, you must add both the <span class="code">ComputerName</span> parameter and the <span class="code">VHD</span> parameter.</span></span> <span data-ttu-id="df311-180">O parâmetro <span class="code">ComputerName</span> contém o nome do servidor em que será montado o VHD e o parâmetro <span class="code">VHD</span> contém o caminho para o arquivo VHD no servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="df311-180">The <span class="code">ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="df311-181">Cópia</span><span class="sxs-lookup"><span data-stu-id="df311-181">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "Copy to clipboard.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  <span data-ttu-id="df311-182">Quando a instalação for concluída, verifique se o Windows PowerShell Web Access foi instalado nos servidores de destino executando o cmdlet **Get-WindowsFeature** em um servidor de destino, em um console do Windows PowerShell que foi aberto com direitos do usuário elevados.</span><span class="sxs-lookup"><span data-stu-id="df311-182">When installation is complete, verify that Windows PowerShell Web Access was installed on destination servers by running the **Get-WindowsFeature** cmdlet on a destination server, in a Windows PowerShell console that has been opened with elevated user rights.</span></span> <span data-ttu-id="df311-183">Também será possível verificar se o Windows PowerShell Web Access foi instalado no console do Gerenciador do Servidor, selecionando um servidor de destino na página **Todos os Servidores** e exibindo o bloco **Funções e Recursos** do servidor selecionado.</span><span class="sxs-lookup"><span data-stu-id="df311-183">You can also verify that Windows PowerShell Web Access was installed in the Server Manager console, by selecting a destination server on the **All Servers** page, and then viewing the **Roles and Features** tile for the selected server.</span></span> <span data-ttu-id="df311-184">Você também pode exibir o arquivo Leiame para o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-184">You can also view the readme file for Windows PowerShell Web Access.</span></span>

4.  <span data-ttu-id="df311-185">Após a instalação do Windows PowerShell Web Access, você será solicitado a examinar o arquivo Leiame, que contém instruções de configuração básicas e necessárias para o gateway.</span><span class="sxs-lookup"><span data-stu-id="df311-185">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="df311-186">Essas instruções de instalação também estão incluídas na seção a seguir, [Etapa 2: Configurar o gateway](#BKMK_step2).</span><span class="sxs-lookup"><span data-stu-id="df311-186">These setup instructions are also in the following section, [Step 2: Configure the gateway](#BKMK_step2).</span></span> <span data-ttu-id="df311-187">O caminho para o arquivo Leiame é <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span><span class="sxs-lookup"><span data-stu-id="df311-187">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

<a href="" id="BKMK_step2"></a>
###

<span data-ttu-id="df311-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 2: configurar o gateway</span></a></span><span class="sxs-lookup"><span data-stu-id="df311-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-189">O cmdlet **Install-PswaWebApplication** é uma maneira rápida de configurar o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-189">The **Install-PswaWebApplication** cmdlet is a quick way to get Windows PowerShell Web Access configured.</span></span> <span data-ttu-id="df311-190">Embora seja possível adicionar o parâmetro <span class="code">UseTestCertificate</span> ao cmdlet <span class="code">Install-PswaWebApplication</span> para instalar um certificado SSL autoassinado para fins de teste, isso não é seguro. Para um ambiente de produção seguro, sempre use um certificado SSL válido assinado por uma AC (autoridade de certificação).</span><span class="sxs-lookup"><span data-stu-id="df311-190">Although you can add the <span class="code">UseTestCertificate</span> parameter to the <span class="code">Install-PswaWebApplication</span> cmdlet to install a self-signed SSL certificate for test purposes, this is not secure; for a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="df311-191">Os administradores podem substituir o certificado de teste por um certificado assinado de sua preferência usando o console do Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="df311-191">Administrators can replace the test certificate with a signed certificate of their choice by using the IIS Manager console.</span></span>

<span data-ttu-id="df311-192">Você pode concluir a configuração do aplicativo Web Windows PowerShell Web Access executando o cmdlet <span class="code">Install-PswaWebApplication</span> ou seguindo as etapas de configuração baseada em GUI no Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="df311-192">You can complete Windows PowerShell Web Access web application configuration either by running the <span class="code">Install-PswaWebApplication</span> cmdlet or by performing GUI-based configuration steps in IIS Manager.</span></span> <span data-ttu-id="df311-193">Por padrão, o cmdlet instala o aplicativo Web, o **pswa** (e um pool de aplicativos para ele, **pswa_pool**), no contêiner **Site Padrão**, como mostrado no Gerenciador do IIS. Se quiser, você poderá instruir o cmdlet a alterar o contêiner do site padrão do aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="df311-193">By default, the cmdlet installs the web application, **pswa** (and an application pool for it, **pswa_pool**), in the **Default Web Site** container, as shown in IIS Manager; if desired, you can instruct the cmdlet to change the default site container of the web application.</span></span> <span data-ttu-id="df311-194">O Gerenciador do IIS oferece opções de configuração disponíveis para aplicativos Web, como alteração do número da porta ou do certificado SSL (Secure Sockets Layer).</span><span class="sxs-lookup"><span data-stu-id="df311-194">IIS Manager offers configuration options that are available for web applications, such as changing the port number or the Secure Sockets Layer (SSL) certificate.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="df311-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Observação de Segurança </span></span><span class="sxs-lookup"><span data-stu-id="df311-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="df311-196">Recomendamos enfaticamente que os administradores configurem o gateway para usar um certificado válido assinado por uma CA.</span><span class="sxs-lookup"><span data-stu-id="df311-196">We strongly recommend that administrators configure the gateway to use a valid certificate that has been signed by a CA.</span></span></p></td>
</tr>
</tbody>
</table>

-   [<span data-ttu-id="df311-197">Para configurar o gateway do Windows PowerShell Web Access com um certificado de teste usando Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="df311-197">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>](#BKMK_testcert)

-   [<span data-ttu-id="df311-198">Para configurar o gateway do Windows PowerShell Web Access com um certificado original usando o Install-PswaWebApplication e o Gerenciador do IIS</span><span class="sxs-lookup"><span data-stu-id="df311-198">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>](#BKMK_gencert)

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a><span data-ttu-id="df311-199">Para configurar o gateway do Windows PowerShell Web Access com um certificado de teste usando Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="df311-199">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>

1.  <span data-ttu-id="df311-200">Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df311-200">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="df311-201">Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="df311-201">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="df311-202">Na tela **Iniciar** do Windows, clique em **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="df311-202">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="df311-203">Digite o seguinte e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="df311-203">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="df311-204">**Install-PswaWebApplication -UseTestCertificate**</span><span class="sxs-lookup"><span data-stu-id="df311-204">**Install-PswaWebApplication -UseTestCertificate**</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="df311-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Observação de Segurança </span></span><span class="sxs-lookup"><span data-stu-id="df311-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="df311-206">O parâmetro <span class="code">UseTestCertificate</span> só deve ser usado em um ambiente de teste privado.</span><span class="sxs-lookup"><span data-stu-id="df311-206">The <span class="code">UseTestCertificate</span> parameter should only be used in a private test environment.</span></span> <span data-ttu-id="df311-207">Para um ambiente de produção seguro, recomendamos usar um certificado válido assinado por uma AC.</span><span class="sxs-lookup"><span data-stu-id="df311-207">For a secure production environment, we recommend using a valid certificate that has been signed by a CA.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="df311-208">Quando o cmdlet é executado, o aplicativo web Windows PowerShell Web Access é instalado no contêiner Site Padrão do IIS.</span><span class="sxs-lookup"><span data-stu-id="df311-208">Running the cmdlet installs the Windows PowerShell Web Access web application within the IIS Default Web Site container.</span></span> <span data-ttu-id="df311-209">O cmdlet cria a infraestrutura necessária para executar o Windows PowerShell Web Access no site padrão, https://&lt;nome_do_servidor&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="df311-209">The cmdlet creates the infrastructure required to run Windows PowerShell Web Access on the default website, https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="df311-210">Para instalar o aplicativo Web em outro site, forneça o nome do site adicionando o parâmetro <span class="code">WebSiteName</span>.</span><span class="sxs-lookup"><span data-stu-id="df311-210">To install the web application in a different website, provide the website name by adding the <span class="code">WebSiteName</span> parameter.</span></span> <span data-ttu-id="df311-211">Para alterar o nome do aplicativo Web (o padrão é <span class="code">pswa</span>), adicione o parâmetro <span class="code">WebApplicationName</span>.</span><span class="sxs-lookup"><span data-stu-id="df311-211">To change the name of the web application (the default is <span class="code">pswa</span>), add the <span class="code">WebApplicationName</span> parameter.</span></span>

    <span data-ttu-id="df311-212">As configurações a seguir são feitas executando o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df311-212">The following settings are configured by running the cmdlet.</span></span> <span data-ttu-id="df311-213">Você pode alterá-las manualmente no console do Gerenciador do IIS, se desejado.</span><span class="sxs-lookup"><span data-stu-id="df311-213">You can change these manually in the IIS Manager console, if desired.</span></span>

    -   <span data-ttu-id="df311-214">Caminho: /pswa</span><span class="sxs-lookup"><span data-stu-id="df311-214">Path: /pswa</span></span>

    -   <span data-ttu-id="df311-215">ApplicationPool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="df311-215">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="df311-216">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="df311-216">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="df311-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="df311-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

    <span data-ttu-id="df311-218"><span class="label">Exemplo:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span><span class="sxs-lookup"><span data-stu-id="df311-218"><span class="label">Example:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span></span>

    <span data-ttu-id="df311-219">Neste exemplo, o site resultante do Windows PowerShell Web Access é https://&lt;*nome_do_servidor*&gt;/myWebApp.</span><span class="sxs-lookup"><span data-stu-id="df311-219">In this example, the resulting website for Windows PowerShell Web Access is https://&lt; *server_name*&gt;/myWebApp.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="df311-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Observação </span></span><span class="sxs-lookup"><span data-stu-id="df311-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="df311-221">Você não poderá fazer logon até que todos os usuários tenham obtido acesso ao site adicionando regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="df311-221">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="df311-222">Para saber mais, confira <a href="#BKMK_step3">Etapa 3: Configurar uma regra de autorização restritiva</a> e <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Regras de autorização e recursos de segurança do Windows PowerShell Web Access</a>.</span><span class="sxs-lookup"><span data-stu-id="df311-222">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a><span data-ttu-id="df311-223">Para configurar o gateway do Windows PowerShell Web Access com um certificado original usando o Install-PswaWebApplication e o Gerenciador do IIS</span><span class="sxs-lookup"><span data-stu-id="df311-223">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>

1.  <span data-ttu-id="df311-224">Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df311-224">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="df311-225">Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="df311-225">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="df311-226">Na tela **Iniciar** do Windows, clique em **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="df311-226">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="df311-227">Digite o seguinte e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="df311-227">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="df311-228">**Install-PswaWebApplication**</span><span class="sxs-lookup"><span data-stu-id="df311-228">**Install-PswaWebApplication**</span></span>

    <span data-ttu-id="df311-229">As configurações de gateway a seguir são feitas executando o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df311-229">The following gateway settings are configured by running the cmdlet.</span></span> <span data-ttu-id="df311-230">Você pode alterá-las manualmente no console do Gerenciador do IIS, se desejado.</span><span class="sxs-lookup"><span data-stu-id="df311-230">You can change these manually in the IIS Manager console, if desired.</span></span> <span data-ttu-id="df311-231">Você também pode especificar valores para os parâmetros <span class="code">WebsiteName</span> e <span class="code">WebApplicationName</span> do cmdlet <span class="code">Install-PswaWebApplication</span>.</span><span class="sxs-lookup"><span data-stu-id="df311-231">You can also specify values for the <span class="code">WebsiteName</span> and <span class="code">WebApplicationName</span> parameters of the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span>

    -   <span data-ttu-id="df311-232">Caminho: /pswa</span><span class="sxs-lookup"><span data-stu-id="df311-232">Path: /pswa</span></span>

    -   <span data-ttu-id="df311-233">ApplicationPool: pswa_pool</span><span class="sxs-lookup"><span data-stu-id="df311-233">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="df311-234">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="df311-234">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="df311-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="df311-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

3.  <span data-ttu-id="df311-236">Abra o console do Gerenciador do IIS seguindo um destes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="df311-236">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="df311-237">Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="df311-237">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="df311-238">No menu **Ferramentas** no Gerenciador do Servidor, clique em **Gerenciador do IIS (Serviços de Informações da Internet)**.</span><span class="sxs-lookup"><span data-stu-id="df311-238">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="df311-239">Na tela **Iniciar** do Windows, clique em **Gerenciador do Servidor**.</span><span class="sxs-lookup"><span data-stu-id="df311-239">On the Windows **Start** screen, click **Server Manager**.</span></span>

4.  <span data-ttu-id="df311-240">No painel de árvore do Gerenciador do IIS, expanda o nó do servidor no qual o Windows PowerShell Web Access está instalado até que a pasta **Sites** fique visível.</span><span class="sxs-lookup"><span data-stu-id="df311-240">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="df311-241">Expanda a pasta **Sites**.</span><span class="sxs-lookup"><span data-stu-id="df311-241">Expand the **Sites** folder.</span></span>

5.  <span data-ttu-id="df311-242">Selecione o site no qual você instalou o aplicativo Web Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-242">Select the website in which you have installed the Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="df311-243">No painel **Ações**, clique em **Associações**.</span><span class="sxs-lookup"><span data-stu-id="df311-243">In the **Actions** pane, click **Bindings**.</span></span>

6.  <span data-ttu-id="df311-244">Na caixa de diálogo **Associação do Site**, clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="df311-244">In the **Site Binding** dialog box, click **Add**.</span></span>

7.  <span data-ttu-id="df311-245">Na caixa de diálogo **Adicionar Associação do Site**, no campo **Tipo**, escolha **https**.</span><span class="sxs-lookup"><span data-stu-id="df311-245">In the **Add Site Binding** dialog box, in the **Type** field, select **https**.</span></span>

8.  <span data-ttu-id="df311-246">No campo **Certificado SSL**, selecione o certificado assinado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="df311-246">In the **SSL certificate** field, select your signed certificate from the drop-down menu.</span></span> <span data-ttu-id="df311-247">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="df311-247">Click **OK**.</span></span> <span data-ttu-id="df311-248">Consulte [Para configurar um certificado SSL no Gerenciador do IIS](#BKMK_cert) neste tópico para obter mais informações sobre como obter um certificado.</span><span class="sxs-lookup"><span data-stu-id="df311-248">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

    <span data-ttu-id="df311-249">O aplicativo web Windows PowerShell Web Access agora está configurado para usar seu certificado SSL assinado.</span><span class="sxs-lookup"><span data-stu-id="df311-249">The Windows PowerShell Web Access web application is now configured to use your signed SSL certificate.</span></span> <span data-ttu-id="df311-250">Você pode acessar o Windows PowerShell Web Access ao abrir https://&lt;nome_do_servidor&gt;/pswa em uma janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="df311-250">You can access Windows PowerShell Web Access by opening https://&lt;server_name&gt;/pswa in a browser window.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="df311-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Observação </span></span><span class="sxs-lookup"><span data-stu-id="df311-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="df311-252">Você não poderá fazer logon até que todos os usuários tenham obtido acesso ao site adicionando regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="df311-252">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="df311-253">Para saber mais, confira <a href="#BKMK_step3">Etapa 3: Configurar uma regra de autorização restritiva</a> e <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Regras de autorização e recursos de segurança do Windows PowerShell Web Access</a>.</span><span class="sxs-lookup"><span data-stu-id="df311-253">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="df311-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 3: Configurar uma regra de autorização restritiva</span></a></span><span class="sxs-lookup"><span data-stu-id="df311-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-255">Depois que o Windows PowerShell Web Access for instalado e o gateway configurado, os usuários poderão abrir a página de entrada em um navegador, mas só poderão entrar depois que o administrador do Windows PowerShell Web Access conceder a eles acesso explicitamente.</span><span class="sxs-lookup"><span data-stu-id="df311-255">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="df311-256">O controle de acesso do Windows PowerShell Web Access é gerenciado por meio de um conjunto de cmdlets do Windows PowerShell descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="df311-256">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="df311-257">Não há uma GUI comparável para adicionar ou gerenciar regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="df311-257">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="df311-258">Para saber mais sobre os cmdlets do Windows PowerShell Web Access, confira os tópicos de referência de cmdlet [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx) (Cmdlets do Windows PowerShell Web Access).</span><span class="sxs-lookup"><span data-stu-id="df311-258">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="df311-259">Para obter mais detalhes sobre as regras e a segurança de autorização do Windows PowerShell Web Access, confira [Authorization Rules and Security Features of Windows PowerShell Web Access (Recursos de segurança e regras de autorização do Windows PowerShell Web Access)](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="df311-259">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="df311-260">Para adicionar uma regra de autorização restritiva</span><span class="sxs-lookup"><span data-stu-id="df311-260">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="df311-261">Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados.</span><span class="sxs-lookup"><span data-stu-id="df311-261">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="df311-262">Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="df311-262">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="df311-263">Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="df311-263">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="df311-264"><span class="label">Etapa opcional para restringir o acesso dos usuários por meio de configurações de sessão:</span> verifique se as configurações de sessão que você deseja usar em suas regras já existem.</span><span class="sxs-lookup"><span data-stu-id="df311-264"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="df311-265">Se elas ainda não foram criadas, siga as instruções sobre como criar configurações de sessão em [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) no MSDN.</span><span class="sxs-lookup"><span data-stu-id="df311-265">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="df311-266">Digite o seguinte e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="df311-266">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="df311-267">Cópia</span><span class="sxs-lookup"><span data-stu-id="df311-267">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="df311-268">Essa regra de autorização permite que um usuário específico acesse um computador na rede ao qual tipicamente tem acesso, com acesso a uma configuração de sessão específica, voltada para as necessidades típicas de script e cmdlet do usuário.</span><span class="sxs-lookup"><span data-stu-id="df311-268">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="df311-269">No exemplo a seguir, um usuário nomeado <span class="code">JSmith</span> no domínio <span class="code">Contoso</span> ganha acesso para gerenciar o computador <span class="code">Contoso_214</span> e usa uma configuração de sessão nomeada <span class="code">NewAdminsOnly</span>.</span><span class="sxs-lookup"><span data-stu-id="df311-269">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="df311-270">Cópia</span><span class="sxs-lookup"><span data-stu-id="df311-270">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="df311-271">Verifique se a regra foi criada ao executar o cmdlet **Get-PswaAuthorizationRule** ou **Test-PswaAuthorizationRule -UserName &lt;domínio\\usuário | computador\\usuário&gt; -ComputerName** &lt;nome_do_computador&gt;.</span><span class="sxs-lookup"><span data-stu-id="df311-271">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="df311-272">Por exemplo, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span><span class="sxs-lookup"><span data-stu-id="df311-272">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="df311-273">Depois de configurar uma regra de autorização, você está pronto para que os usuários autorizados entrem no console baseado na web e comecem a usar o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-273">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_custom"></a>

<span data-ttu-id="df311-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Implantação personalizada</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="df311-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-275">Você pode instalar o gateway do Windows PowerShell Web Access em um servidor que está executando o Windows Server 2012 R2 ou o Windows Server 2012 usando o assistente Adicionar Funções e Recursos no Gerenciador do Servidor.</span><span class="sxs-lookup"><span data-stu-id="df311-275">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using the Add Roles and Features Wizard in Server Manager.</span></span> <span data-ttu-id="df311-276">Depois de instalar o Windows PowerShell Web Access, você pode personalizar a configuração do gateway no Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="df311-276">After Windows PowerShell Web Access is installed, you can customize the configuration of the gateway in IIS Manager.</span></span>

<a href="" id="BKMK_custom1"></a>
###

<span data-ttu-id="df311-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 1: instalar o Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="df311-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a><span data-ttu-id="df311-278">Para instalar o Windows PowerShell Web Access usando o Assistente para Adicionar Funções e Recursos</span><span class="sxs-lookup"><span data-stu-id="df311-278">To install Windows PowerShell Web Access by using the Add Roles and Features Wizard</span></span>

1.  <span data-ttu-id="df311-279">Se o Gerenciador do Servidor já estiver aberto, vá para a etapa seguinte.</span><span class="sxs-lookup"><span data-stu-id="df311-279">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="df311-280">Se o Gerenciador do Servidor ainda não estiver aberto, abra-o de uma das maneiras a seguir.</span><span class="sxs-lookup"><span data-stu-id="df311-280">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="df311-281">Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="df311-281">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="df311-282">Na tela **Iniciar** do Windows, clique em **Gerenciador do Servidor**.</span><span class="sxs-lookup"><span data-stu-id="df311-282">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="df311-283">No menu **Gerenciar**, clique em **Adicionar Funções e Recursos**.</span><span class="sxs-lookup"><span data-stu-id="df311-283">On the **Manage** menu, click **Add Roles and Features**.</span></span>

3.  <span data-ttu-id="df311-284">Na página **Selecionar tipo de instalação**, selecione **Instalação baseada em função ou recurso**.</span><span class="sxs-lookup"><span data-stu-id="df311-284">On the **Select installation type** page, select **Role-based or feature-based installation**.</span></span> <span data-ttu-id="df311-285">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="df311-285">Click **Next**.</span></span>

4.  <span data-ttu-id="df311-286">Na página **Selecionar servidor de destino**, escolha um servidor no pool de servidores ou um VHD offline.</span><span class="sxs-lookup"><span data-stu-id="df311-286">On the **Select destination server** page, select a server from the server pool, or select an offline VHD.</span></span> <span data-ttu-id="df311-287">Para selecionar um VHD offline como servidor de destino, primeiro selecione o servidor no qual deseja montar o VHD e selecione o arquivo VHD.</span><span class="sxs-lookup"><span data-stu-id="df311-287">To select an offline VHD as your destination server, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="df311-288">Para obter informações sobre como adicionar servidores ao pool de servidores, consulte a Ajuda do Gerenciador do Servidor.</span><span class="sxs-lookup"><span data-stu-id="df311-288">For information about how to add servers to your server pool, see the Server Manager Help.</span></span> <span data-ttu-id="df311-289">Após selecionar o servidor de destino, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="df311-289">After you have selected the destination server, click **Next**.</span></span>

5.  <span data-ttu-id="df311-290">Na página **Selecionar recursos** do assistente, expanda **Windows PowerShell** e escolha **Windows PowerShell Web Access**.</span><span class="sxs-lookup"><span data-stu-id="df311-290">On the **Select features** page of the wizard, expand **Windows PowerShell**, and then select **Windows PowerShell Web Access**.</span></span>

6.  <span data-ttu-id="df311-291">O sistema solicitará a adição dos recursos obrigatórios, como o .NET Framework 4.5 e os serviços de função do Servidor Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="df311-291">Note that you are prompted to add required features, such as .NET Framework 4.5, and role services of Web Server (IIS).</span></span> <span data-ttu-id="df311-292">Adicione os recursos obrigatórios e continue.</span><span class="sxs-lookup"><span data-stu-id="df311-292">Add required features and continue.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="df311-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Observação </span></span><span class="sxs-lookup"><span data-stu-id="df311-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="df311-294">A instalação do Windows PowerShell Web Access usando o assistente Adicionar Funções e Recursos também instala o servidor Web (IIS), incluindo o snap-in Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="df311-294">Installing Windows PowerShell Web Access by using the Add Roles and Features Wizard also installs Web Server (IIS), including the IIS Manager snap-in.</span></span> <span data-ttu-id="df311-295">O snap-in e outras ferramentas de gerenciamento do IIS são instalados por padrão quando o assistente Adicionar Funções e Recursos é usado.</span><span class="sxs-lookup"><span data-stu-id="df311-295">The snap-in and other IIS management tools are installed by default if you use Add Roles and Features Wizard.</span></span> <span data-ttu-id="df311-296">Se você instalar o Windows PowerShell Web Access usando cmdlets do Windows PowerShell, como descrito no procedimento a seguir, as ferramentas de gerenciamento não serão adicionadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="df311-296">If you install Windows PowerShell Web Access by using Windows PowerShell cmdlets as described in the following procedure, management tools are not added by default.</span></span></p></td>
    </tr>
    </tbody>
    </table>

7.  <span data-ttu-id="df311-297">Na página **Confirmar seleções de instalação**, se os arquivos de recursos do Windows PowerShell Web Access não estiverem armazenados no servidor de destino selecionado na etapa 4, clique em **Especificar um caminho de origem alternativo** e forneça o caminho para os arquivos de recursos.</span><span class="sxs-lookup"><span data-stu-id="df311-297">On the **Confirm installation selections** page, if the feature files for Windows PowerShell Web Access are not stored on the destination server that you selected in step 4, click **Specify an alternate source path**, and provide the path to the feature files.</span></span> <span data-ttu-id="df311-298">Caso contrário, clique em **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="df311-298">Otherwise, click **Install**.</span></span>

8.  <span data-ttu-id="df311-299">Depois que você clicar em **Instalar**, a página **Progresso da instalação** exibirá o progresso, os resultados e mensagens da instalação, como avisos, falhas ou as etapas de configuração pós-instalação necessárias ao Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-299">After you click **Install**, the **Installation progress** page displays installation progress, results, and messages such as warnings, failures, or post-installation configuration steps that are required for Windows PowerShell Web Access.</span></span> <span data-ttu-id="df311-300">Após a instalação do Windows PowerShell Web Access, você será solicitado a examinar o arquivo Leiame, que contém instruções de configuração básicas e necessárias para o gateway.</span><span class="sxs-lookup"><span data-stu-id="df311-300">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="df311-301">Essas instruções também estão incluídas neste tópico.</span><span class="sxs-lookup"><span data-stu-id="df311-301">These instructions are also included in this topic.</span></span> <span data-ttu-id="df311-302">O caminho para o arquivo Leiame é <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span><span class="sxs-lookup"><span data-stu-id="df311-302">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

###

<span data-ttu-id="df311-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 2: configurar o gateway</span></a></span><span class="sxs-lookup"><span data-stu-id="df311-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-304">As instruções nesta seção referem-se à instalação do aplicativo Web Windows PowerShell Web Access em um subdiretório do seu site e não no diretório raiz.</span><span class="sxs-lookup"><span data-stu-id="df311-304">Instructions in this section are for installing the Windows PowerShell Web Access web application in a subdirectory—and not in the root directory—of your website.</span></span> <span data-ttu-id="df311-305">Esse procedimento é o equivalente baseado em GUI das ações executadas pelo cmdlet <span class="code">Install-PswaWebApplication</span>.</span><span class="sxs-lookup"><span data-stu-id="df311-305">This procedure is the GUI-based equivalent of the actions performed by the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span> <span data-ttu-id="df311-306">Esta seção também inclui instruções sobre como usar o Gerenciador do IIS para configurar o gateway do Windows PowerShell Web Access como um site raiz.</span><span class="sxs-lookup"><span data-stu-id="df311-306">This section also includes instructions for how to use IIS Manager to configure the Windows PowerShell Web Access gateway as a root website.</span></span>

-   [<span data-ttu-id="df311-307">Para usar o Gerenciador do IIS a fim de configurar um gateway em um site existente</span><span class="sxs-lookup"><span data-stu-id="df311-307">To use IIS Manager to configure the gateway in an existing website</span></span>](#BKMK_configman)

-   [<span data-ttu-id="df311-308">Para usar o Gerenciador do IIS a fim de configurar o gateway como site raiz com um certificado de teste</span><span class="sxs-lookup"><span data-stu-id="df311-308">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>](#BKMK_configroot)

-   

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a><span data-ttu-id="df311-309">Para usar o Gerenciador do IIS a fim de configurar um gateway em um site existente</span><span class="sxs-lookup"><span data-stu-id="df311-309">To use IIS Manager to configure the gateway in an existing website</span></span>

1.  <span data-ttu-id="df311-310">Abra o console do Gerenciador do IIS seguindo um destes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="df311-310">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="df311-311">Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="df311-311">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="df311-312">No menu **Ferramentas** no Gerenciador do Servidor, clique em **Gerenciador do IIS (Serviços de Informações da Internet)**.</span><span class="sxs-lookup"><span data-stu-id="df311-312">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="df311-313">Na tela **Iniciar** do Windows, digite qualquer parte do nome **Gerenciador do IIS (Serviços de Informações da Internet)**.</span><span class="sxs-lookup"><span data-stu-id="df311-313">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="df311-314">Clique no atalho quando ele for exibido nos resultados de **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="df311-314">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="df311-315">Crie um novo pool de aplicativos para o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-315">Create a new application pool for Windows PowerShell Web Access.</span></span> <span data-ttu-id="df311-316">Expanda o nó do servidor de gateway no painel de árvore do Gerenciador do IIS, selecione **Pools de Aplicativos** e clique em **Adicionar Pool de Aplicativos** no painel **Ações**.</span><span class="sxs-lookup"><span data-stu-id="df311-316">Expand the node of the gateway server in the IIS Manager tree pane, select **Application Pools**, and click **Add Application Pool** in the **Actions** pane.</span></span>

3.  <span data-ttu-id="df311-317">Adicione um novo pool de aplicativos com o nome **pswa_pool** ou forneça outro nome.</span><span class="sxs-lookup"><span data-stu-id="df311-317">Add a new application pool with the name **pswa_pool**, or provide another name.</span></span> <span data-ttu-id="df311-318">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="df311-318">Click **OK**.</span></span>

4.  <span data-ttu-id="df311-319">No painel de árvore do Gerenciador do IIS, expanda o nó do servidor no qual o Windows PowerShell Web Access está instalado até que a pasta **Sites** fique visível.</span><span class="sxs-lookup"><span data-stu-id="df311-319">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="df311-320">Selecione a pasta **Sites**.</span><span class="sxs-lookup"><span data-stu-id="df311-320">Select the **Sites** folder.</span></span>

5.  <span data-ttu-id="df311-321">Clique com o botão direito do mouse no site (por exemplo, **Site Padrão**) ao qual você deseja adicionar o site do Windows PowerShell Web Access e clique em **Adicionar Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="df311-321">Right-click the website (for example, **Default Web Site**) to which you would like to add the Windows PowerShell Web Access website, and then click **Add Application**.</span></span>

6.  <span data-ttu-id="df311-322">No campo **Alias**, digite pswa ou forneça outro alias.</span><span class="sxs-lookup"><span data-stu-id="df311-322">In the **Alias** field, type pswa, or provide another alias.</span></span> <span data-ttu-id="df311-323">O alias vira o nome do diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="df311-323">The alias becomes the virtual directory name.</span></span> <span data-ttu-id="df311-324">Por exemplo, o **pswa** na URL a seguir, representa o alias especificado nesta etapa: https://&lt;nome_do_servidor&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="df311-324">For example, **pswa** in the following URL represents the alias specified in this step: https://&lt;server_name&gt;/pswa.</span></span>

7.  <span data-ttu-id="df311-325">No campo **Pool de Aplicativos**, selecione o pool de aplicativos criado na etapa 3.</span><span class="sxs-lookup"><span data-stu-id="df311-325">In the **Application pool** field, select the application pool that you created in step 3.</span></span>

8.  <span data-ttu-id="df311-326">No campo **Caminho físico**, procure a localização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df311-326">In the **Physical path** field, browse for the location of the application.</span></span> <span data-ttu-id="df311-327">Você pode usar a localização padrão, %windir%/Web/PowerShellWebAccess/wwwroot.</span><span class="sxs-lookup"><span data-stu-id="df311-327">You can use the default location, %windir%/Web/PowerShellWebAccess/wwwroot.</span></span> <span data-ttu-id="df311-328">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="df311-328">Click **OK**.</span></span>

9.  <span data-ttu-id="df311-329">Siga as etapas no procedimento [Para configurar um certificado SSL no Gerenciador do IIS](#BKMK_cert) neste tópico.</span><span class="sxs-lookup"><span data-stu-id="df311-329">Follow the steps in the procedure [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic.</span></span>

10. <span data-ttu-id="df311-330"><span class="label">Etapa opcional de segurança:</span> com o site selecionado no painel de árvore, clique duas vezes em **Configurações de SSL** no painel de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="df311-330"><span class="label">Optional security step:</span> With the website selected in the tree pane, double-click **SSL Settings** in the content pane.</span></span> <span data-ttu-id="df311-331">Selecione **Exigir SSL** e, no painel **Ações**, clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="df311-331">Select **Require SSL**, and then in the **Actions** pane, click **Apply**.</span></span> <span data-ttu-id="df311-332">Opcionalmente, no painel **Configurações de SSL**, você pode exigir que os usuários que se conectem ao site do Windows PowerShell Web Access tenham certificados de cliente.</span><span class="sxs-lookup"><span data-stu-id="df311-332">Optionally, in the **SSL Settings** pane, you can require that users connecting to the Windows PowerShell Web Access website have client certificates.</span></span> <span data-ttu-id="df311-333">Os certificados de cliente ajudam a verificar a identidade de um usuário de dispositivo cliente.</span><span class="sxs-lookup"><span data-stu-id="df311-333">Client certificates help to verify the identity of a client device user.</span></span> <span data-ttu-id="df311-334">Para obter mais informações sobre como exigir certificados de cliente que podem aumentar a segurança do Windows PowerShell Web Access, consulte [Regras de autorização e recursos de segurança do Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) neste guia.</span><span class="sxs-lookup"><span data-stu-id="df311-334">For more information about how requiring client certificates can increase the security of Windows PowerShell Web Access, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in this guide.</span></span>

11. <span data-ttu-id="df311-335">Abra uma sessão de navegador em um dispositivo cliente.</span><span class="sxs-lookup"><span data-stu-id="df311-335">Open a browser session on a client device.</span></span> <span data-ttu-id="df311-336">Para obter mais informações sobre navegadores e dispositivos com suporte, consulte [Suporte para navegadores e dispositivos cliente](#BKMK_browser) neste tópico.</span><span class="sxs-lookup"><span data-stu-id="df311-336">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this topic.</span></span>

12. <span data-ttu-id="df311-337">Abra o novo site do Windows PowerShell Web Access, https://&lt; *nome_do_servidor_do_gateway*&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="df311-337">Open the new Windows PowerShell Web Access website, https://&lt; *gateway_server_name*&gt;/pswa.</span></span>

    <span data-ttu-id="df311-338">O navegador exibirá a página de entrada do console do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-338">The browser should display the Windows PowerShell Web Access console sign-in page.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="df311-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Observação </span></span><span class="sxs-lookup"><span data-stu-id="df311-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="df311-340">Você não poderá fazer logon até que todos os usuários tenham obtido acesso ao site adicionando regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="df311-340">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

13. <span data-ttu-id="df311-341">Em uma sessão do Windows PowerShell, aberta com direitos de usuário elevados (Executar como Administrador), execute o script a seguir, no qual *application_pool_name* representa o nome do pool de aplicativos criado na etapa 3, para conferir ao pool de aplicativos direitos de acesso ao arquivo de autorização.</span><span class="sxs-lookup"><span data-stu-id="df311-341">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 3, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="df311-342">Cópia</span><span class="sxs-lookup"><span data-stu-id="df311-342">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "Copy to clipboard.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="df311-343">Para exibir os direitos de acesso existentes relativos ao arquivo de autorização, execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="df311-343">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="df311-344">Cópia</span><span class="sxs-lookup"><span data-stu-id="df311-344">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "Copy to clipboard.")

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a><span data-ttu-id="df311-345">Para usar o Gerenciador do IIS a fim de configurar o gateway como site raiz com um certificado de teste</span><span class="sxs-lookup"><span data-stu-id="df311-345">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>

1.  <span data-ttu-id="df311-346">Abra o console do Gerenciador do IIS seguindo um destes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="df311-346">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="df311-347">Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="df311-347">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="df311-348">No menu **Ferramentas** no Gerenciador do Servidor, clique em **Gerenciador do IIS (Serviços de Informações da Internet)**.</span><span class="sxs-lookup"><span data-stu-id="df311-348">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="df311-349">Na tela **Iniciar** do Windows, digite qualquer parte do nome **Gerenciador do IIS (Serviços de Informações da Internet)**.</span><span class="sxs-lookup"><span data-stu-id="df311-349">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="df311-350">Clique no atalho quando ele for exibido nos resultados de **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="df311-350">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="df311-351">No painel de árvore do Gerenciador do IIS, expanda o nó do servidor no qual o Windows PowerShell Web Access está instalado até que a pasta **Sites** fique visível.</span><span class="sxs-lookup"><span data-stu-id="df311-351">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="df311-352">Selecione a pasta **Sites**.</span><span class="sxs-lookup"><span data-stu-id="df311-352">Select the **Sites** folder.</span></span>

3.  <span data-ttu-id="df311-353">No painel **Ações**, clique em **Adicionar Site**.</span><span class="sxs-lookup"><span data-stu-id="df311-353">In the **Actions** pane, click **Add Website**.</span></span>

4.  <span data-ttu-id="df311-354">Digite um nome para o site, por exemplo, **Windows PowerShell Web Access**.</span><span class="sxs-lookup"><span data-stu-id="df311-354">Type a name for the website, such as **Windows PowerShell Web Access**.</span></span>

5.  <span data-ttu-id="df311-355">Um pool de aplicativos será criado automaticamente para o novo site.</span><span class="sxs-lookup"><span data-stu-id="df311-355">An application pool is automatically created for the new website.</span></span> <span data-ttu-id="df311-356">Para usar outro pool de aplicativos, clique em **Selecionar** para selecionar um pool de aplicativos a ser associado ao novo site.</span><span class="sxs-lookup"><span data-stu-id="df311-356">To use a different application pool, click **Select** to select an application pool to associate with the new website.</span></span> <span data-ttu-id="df311-357">Escolha o pool de aplicativos alternativo na caixa de diálogo **Selecionar Pool de Aplicativos** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="df311-357">Select the alternate application pool in the **Select Application Pool** dialog box, and then click **OK**.</span></span>

6.  <span data-ttu-id="df311-358">Na caixa de texto **Caminho físico**, navegue até %*windir*%/Web/PowerShellWebAccess/wwwroot.</span><span class="sxs-lookup"><span data-stu-id="df311-358">In the **Physical path** text box, navigate to %*windir*%/Web/PowerShellWebAccess/wwwroot.</span></span>

7.  <span data-ttu-id="df311-359">No campo **Tipo** da área **Associação**, escolha **https**.</span><span class="sxs-lookup"><span data-stu-id="df311-359">In the **Type** field of the **Binding** area, select **https**.</span></span>

8.  <span data-ttu-id="df311-360">Atribua um número de porta a um site que ainda não seja usado por outro site ou aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df311-360">Assign a port number to the website that is not already in use by another site or application.</span></span> <span data-ttu-id="df311-361">Para localizar portas abertas, você pode executar o comando **netstat** em uma janela de Prompt de Comando.</span><span class="sxs-lookup"><span data-stu-id="df311-361">To locate open ports, you can run the **netstat** command in a Command Prompt window.</span></span> <span data-ttu-id="df311-362">O número de porta padrão é 443.</span><span class="sxs-lookup"><span data-stu-id="df311-362">The default port number is 443.</span></span>

    <span data-ttu-id="df311-363">Altere a porta padrão se outro site já estiver usando 443 ou se tiver outros motivos relativos à segurança para alterar esse número.</span><span class="sxs-lookup"><span data-stu-id="df311-363">Change the default port if another website is already using 443, or if you have other security reasons for changing the port number.</span></span> <span data-ttu-id="df311-364">Se outro site em execução no seu servidor de gateway estiver usando a porta selecionada, um aviso será exibido quando você clicar em **OK** na caixa de diálogo **Adicionar Site**.</span><span class="sxs-lookup"><span data-stu-id="df311-364">If another website that is running on your gateway server is using your selected port, a warning is displayed when you click **OK** in the **Add Website** dialog box.</span></span> <span data-ttu-id="df311-365">Você deve usar uma porta não utilizada para executar o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-365">You must use an unused port to run Windows PowerShell Web Access.</span></span>

9.  <span data-ttu-id="df311-366">Opcionalmente, se necessário para sua organização, especifique um nome de host que faça sentido para a organização e para os usuários, como **www.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="df311-366">Optionally, if needed for your organization, specify a host name that makes sense to your organization and users, such as **www.contoso.com**.</span></span> <span data-ttu-id="df311-367">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="df311-367">Click **OK**.</span></span>

10. <span data-ttu-id="df311-368">Para um ambiente de produção mais seguro, recomendamos enfaticamente fornecer um certificado válido assinado por uma AC.</span><span class="sxs-lookup"><span data-stu-id="df311-368">For a more secure production environment, we strongly recommend providing a valid certificate that has been signed by a CA.</span></span> <span data-ttu-id="df311-369">Forneça um certificado SSL, pois os usuários só podem se conectar ao Windows PowerShell Web Access por meio de um site HTTPS.</span><span class="sxs-lookup"><span data-stu-id="df311-369">You must provide an SSL certificate, because users can only connect to Windows PowerShell Web Access through an HTTPS website.</span></span> <span data-ttu-id="df311-370">Consulte [Para configurar um certificado SSL no Gerenciador do IIS](#BKMK_cert) neste tópico para obter mais informações sobre como obter um certificado.</span><span class="sxs-lookup"><span data-stu-id="df311-370">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

11. <span data-ttu-id="df311-371">Clique em **OK** para fechar a caixa de diálogo **Adicionar Site**.</span><span class="sxs-lookup"><span data-stu-id="df311-371">Click **OK** to close the **Add Website** dialog box.</span></span>

12. <span data-ttu-id="df311-372">Em uma sessão do Windows PowerShell, aberta com direitos de usuário elevados (Executar como Administrador), execute o script a seguir, no qual *application_pool_name* representa o nome do pool de aplicativos criado na etapa 4, para conferir ao pool de aplicativos direitos de acesso ao arquivo de autorização.</span><span class="sxs-lookup"><span data-stu-id="df311-372">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 4, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="df311-373">Cópia</span><span class="sxs-lookup"><span data-stu-id="df311-373">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "Copy to clipboard.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="df311-374">Para exibir os direitos de acesso existentes relativos ao arquivo de autorização, execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="df311-374">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="df311-375">Cópia</span><span class="sxs-lookup"><span data-stu-id="df311-375">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "Copy to clipboard.")

        c:\windows\system32\icacls.exe $authorizationFile

13. <span data-ttu-id="df311-376">Com o novo site selecionado no painel de árvore do Gerenciador do IIS, clique em **Iniciar** no painel **Ações** para iniciar o site.</span><span class="sxs-lookup"><span data-stu-id="df311-376">With the new website selected in the IIS Manager tree pane, click **Start** in the **Actions** pane to start the website.</span></span>

14. <span data-ttu-id="df311-377">Abra uma sessão de navegador em um dispositivo cliente.</span><span class="sxs-lookup"><span data-stu-id="df311-377">Open a browser session on a client device.</span></span> <span data-ttu-id="df311-378">Para obter mais informações sobre navegadores e dispositivos com suporte, consulte [Suporte para navegador e dispositivo cliente](#BKMK_browser) neste documento.</span><span class="sxs-lookup"><span data-stu-id="df311-378">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this document.</span></span>

15. <span data-ttu-id="df311-379">Abra o novo site do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-379">Open the new Windows PowerShell Web Access website.</span></span>

    <span data-ttu-id="df311-380">Como o site raiz aponta para a pasta do Windows PowerShell Web Access, o navegador exibirá a página de entrada do Windows PowerShell Web Access quando você abrir https://&lt; *nome_do_servidor_do_gateway*&gt;.</span><span class="sxs-lookup"><span data-stu-id="df311-380">Because the root website points to the Windows PowerShell Web Access folder, the browser should display the Windows PowerShell Web Access sign-in page when you open https://&lt; *gateway_server_name*&gt;.</span></span> <span data-ttu-id="df311-381">Não será preciso adicionar **/pswa** à URL.</span><span class="sxs-lookup"><span data-stu-id="df311-381">You should not need to add **/pswa** to the URL.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="df311-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Observação </span></span><span class="sxs-lookup"><span data-stu-id="df311-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="df311-383">Você não poderá fazer logon até que todos os usuários tenham obtido acesso ao site adicionando regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="df311-383">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="df311-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 3: configurar uma regra de autorização restritiva</span></a></span><span class="sxs-lookup"><span data-stu-id="df311-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-385">Depois que o Windows PowerShell Web Access for instalado e o gateway configurado, os usuários poderão abrir a página de entrada em um navegador, mas só poderão entrar depois que o administrador do Windows PowerShell Web Access conceder a eles acesso explicitamente.</span><span class="sxs-lookup"><span data-stu-id="df311-385">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="df311-386">O controle de acesso do Windows PowerShell Web Access é gerenciado por meio de um conjunto de cmdlets do Windows PowerShell descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="df311-386">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="df311-387">Não há uma GUI comparável para adicionar ou gerenciar regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="df311-387">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="df311-388">Para saber mais sobre os cmdlets do Windows PowerShell Web Access, confira os tópicos de referência de cmdlet [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx) (Cmdlets do Windows PowerShell Web Access).</span><span class="sxs-lookup"><span data-stu-id="df311-388">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="df311-389">Para obter mais detalhes sobre as regras e a segurança de autorização do Windows PowerShell Web Access, confira [Authorization Rules and Security Features of Windows PowerShell Web Access (Recursos de segurança e regras de autorização do Windows PowerShell Web Access)](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="df311-389">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="df311-390">Para adicionar uma regra de autorização restritiva</span><span class="sxs-lookup"><span data-stu-id="df311-390">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="df311-391">Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados.</span><span class="sxs-lookup"><span data-stu-id="df311-391">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="df311-392">Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="df311-392">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="df311-393">Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="df311-393">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="df311-394"><span class="label">Etapa opcional para restringir o acesso dos usuários por meio de configurações de sessão:</span> verifique se as configurações de sessão que você deseja usar em suas regras já existem.</span><span class="sxs-lookup"><span data-stu-id="df311-394"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="df311-395">Se elas ainda não foram criadas, siga as instruções sobre como criar configurações de sessão em [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) no MSDN.</span><span class="sxs-lookup"><span data-stu-id="df311-395">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="df311-396">Digite o seguinte e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="df311-396">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="df311-397">Cópia</span><span class="sxs-lookup"><span data-stu-id="df311-397">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="df311-398">Essa regra de autorização permite que um usuário específico acesse um computador na rede ao qual tipicamente tem acesso, com acesso a uma configuração de sessão específica, voltada para as necessidades típicas de script e cmdlet do usuário.</span><span class="sxs-lookup"><span data-stu-id="df311-398">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="df311-399">No exemplo a seguir, um usuário nomeado <span class="code">JSmith</span> no domínio <span class="code">Contoso</span> ganha acesso para gerenciar o computador <span class="code">Contoso_214</span> e usa uma configuração de sessão nomeada <span class="code">NewAdminsOnly</span>.</span><span class="sxs-lookup"><span data-stu-id="df311-399">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="df311-400">Cópia</span><span class="sxs-lookup"><span data-stu-id="df311-400">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "Copy to clipboard.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="df311-401">Verifique se a regra foi criada ao executar o cmdlet **Get-PswaAuthorizationRule** ou **Test-PswaAuthorizationRule -UserName &lt;domínio\\usuário | computador\\usuário&gt; -ComputerName** &lt;nome_do_computador&gt;.</span><span class="sxs-lookup"><span data-stu-id="df311-401">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="df311-402">Por exemplo, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span><span class="sxs-lookup"><span data-stu-id="df311-402">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="df311-403">Depois de configurar uma regra de autorização, você está pronto para que os usuários autorizados entrem no console baseado na web e comecem a usar o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="df311-403">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_configcert"></a>

<span data-ttu-id="df311-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configurar um certificado original</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="df311-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configure a genuine certificate</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-405">Para um ambiente de produção seguro, sempre use um certificado SSL válido que foi assinado por uma AC (autoridade de certificação).</span><span class="sxs-lookup"><span data-stu-id="df311-405">For a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="df311-406">O procedimento nesta seção descreve como obter e aplicar um certificado SSL válido por meio de uma AC.</span><span class="sxs-lookup"><span data-stu-id="df311-406">The procedure in this section describes how to obtain and apply a valid SSL certificate from a CA.</span></span>

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a><span data-ttu-id="df311-407">Para configurar um certificado SSL no Gerenciador do IIS</span><span class="sxs-lookup"><span data-stu-id="df311-407">To configure an SSL certificate in IIS Manager</span></span>

1.  <span data-ttu-id="df311-408">No painel da árvore Gerenciador do IIS, selecione o servidor no qual o Windows PowerShell Web Access está instalado.</span><span class="sxs-lookup"><span data-stu-id="df311-408">In the IIS Manager tree pane, select the server on which Windows PowerShell Web Access is installed.</span></span>

2.  <span data-ttu-id="df311-409">No painel de conteúdo, clique duas vezes em **Certificados de Servidor**.</span><span class="sxs-lookup"><span data-stu-id="df311-409">In the content pane, double click **Server Certificates**.</span></span>

3.  <span data-ttu-id="df311-410">No painel **Ações**, siga um dos procedimentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="df311-410">In the **Actions** pane, do one of the following.</span></span> <span data-ttu-id="df311-411">Para saber mais sobre como configurar certificados de servidor no IIS, confira [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx) (Configurando certificados de servidor no IIS 7).</span><span class="sxs-lookup"><span data-stu-id="df311-411">For more information about configuring server certificates in IIS, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span></span>

    -   <span data-ttu-id="df311-412">Clique em **Importar** para importar um certificado existente válido de uma localização da sua rede.</span><span class="sxs-lookup"><span data-stu-id="df311-412">Click **Import** to import an existing, valid certificate from a location on your network.</span></span>

    -   <span data-ttu-id="df311-413">Clique em **Criar Solicitação de Certificado** para solicitar um certificado de uma AC, como VeriSign™, Thawte ou GeoTrust®.</span><span class="sxs-lookup"><span data-stu-id="df311-413">Click **Create Certificate Request** to request a certificate from a CA such as VeriSign™, Thawte, or GeoTrust®.</span></span> <span data-ttu-id="df311-414">O nome comum do certificado deve corresponder ao cabeçalho do host na solicitação.</span><span class="sxs-lookup"><span data-stu-id="df311-414">The certificate's common name must match the host header in the request.</span></span> <span data-ttu-id="df311-415">Por exemplo, se o navegador do cliente solicitar http://www.contoso.com/, o nome comum também deverá ser http://www.contoso.com/.</span><span class="sxs-lookup"><span data-stu-id="df311-415">For example, if the client browser requests http://www.contoso.com/, then the common name must also be http://www.contoso.com/.</span></span> <span data-ttu-id="df311-416">Esta é a opção mais segura e recomendada para fornecer um gateway do Windows PowerShell Web Access com um certificado.</span><span class="sxs-lookup"><span data-stu-id="df311-416">This is the most secure and recommended option for providing the Windows PowerShell Web Access gateway with a certificate.</span></span>

    -   <span data-ttu-id="df311-417">Clique em **Criar um Certificado Autoassinado** para criar um certificado que você possa usar imediatamente e que possa ser assinado posteriormente pela AC, se desejado.</span><span class="sxs-lookup"><span data-stu-id="df311-417">Click **Create a Self-Signed Certificate** to create a certificate that you can use immediately, and have signed later by a CA if desired.</span></span> <span data-ttu-id="df311-418">Especifique um nome amigável para o certificado autoassinado, por exemplo, **Windows PowerShell Web Access**.</span><span class="sxs-lookup"><span data-stu-id="df311-418">Specify a friendly name for the self-signed certificate, such as **Windows PowerShell Web Access**.</span></span> <span data-ttu-id="df311-419">Essa opção não é considerada segura e é recomendada somente para um ambiente de testes privado.</span><span class="sxs-lookup"><span data-stu-id="df311-419">This option is not considered secure, and is recommended only for a private test environment.</span></span>

4.  <span data-ttu-id="df311-420">Depois de criar ou obter um certificado, selecione o site ao qual o certificado é aplicado (por exemplo, **Site Padrão**) no painel de árvore do Gerenciador do IIS e clique em **Associações** no painel **Ações**.</span><span class="sxs-lookup"><span data-stu-id="df311-420">After creating or obtaining a certificate, select the website to which the certificate is applied (for example, **Default Web Site**) in the IIS Manager tree pane, and then click **Bindings** in the **Actions** pane.</span></span>

5.  <span data-ttu-id="df311-421">Na caixa de diálogo **Adicionar Associação do Site**, adicione uma associação **https** ao site, caso ainda nenhuma seja exibida.</span><span class="sxs-lookup"><span data-stu-id="df311-421">In the **Add Site Binding** dialog box, add an **https** binding for the site, if one is not already displayed.</span></span> <span data-ttu-id="df311-422">Se você não estiver usando um certificado autoassinado, especifique o nome do host da etapa 3 deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="df311-422">If you are not using a self-signed certificate, specify the host name from step 3 of this procedure.</span></span> <span data-ttu-id="df311-423">Se estiver usando um certificado autoassinado, esta etapa não será necessária.</span><span class="sxs-lookup"><span data-stu-id="df311-423">If you are using a self-signed certificate, this step is not required.</span></span>

6.  <span data-ttu-id="df311-424">Escolha o certificado obtido ou criado na etapa 3 deste procedimento e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="df311-424">Select the certificate that you obtained or created in step 3 of this procedure, and then click **OK**.</span></span>

<a href="" id="BKMK_using"></a>

<span data-ttu-id="df311-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Usando o console do Windows PowerShell baseado na Web</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="df311-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-426">Depois que o Windows PowerShell Web Access é instalado e a configuração do gateway é concluída, como descrito neste tópico, o console do Windows PowerShell baseado na Web está pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="df311-426">After Windows PowerShell Web Access is installed and the gateway configuration is finished as described in this topic, the Windows PowerShell web-based console is ready to use.</span></span> <span data-ttu-id="df311-427">Para saber mais sobre como começar a usar o console baseado na Web, confira [Use the Web-based Windows PowerShell Console (Usar o console do Windows PowerShell baseado na Web)](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="df311-427">For more information about getting started in the web-based console, see [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span></span>

<span data-ttu-id="df311-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Veja também</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="df311-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="df311-429">[Documentação do IIS (Serviços de informações da Internet) 7.0](https://technet.microsoft.com/library/cc753433.aspx)
[Ajuda do Gerenciador do IIS 7.0](https://technet.microsoft.com/library/cc732664.aspx)
[Configurar a segurança do servidor Web (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[Recursos de implantação do IPsec](https://technet.microsoft.com/network/bb531150)</span><span class="sxs-lookup"><span data-stu-id="df311-429">[Internet Information Services (IIS) 7.0 Documentation](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)
[Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec Deployment Resources](https://technet.microsoft.com/network/bb531150)</span></span>

<span data-ttu-id="df311-430"><span>Mostrar:</span> herdado protegido</span><span class="sxs-lookup"><span data-stu-id="df311-430"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="df311-431"><span class="stdr-votetitle">Esta página foi útil?</span></span><span class="sxs-lookup"><span data-stu-id="df311-431"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="df311-432">Sim Não</span><span class="sxs-lookup"><span data-stu-id="df311-432">Yes No</span></span>

<span data-ttu-id="df311-433">Comentários adicionais?</span><span class="sxs-lookup"><span data-stu-id="df311-433">Additional feedback?</span></span>

<span data-ttu-id="df311-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caracteres restantes</span> Enviar Ignorar isto</span><span class="sxs-lookup"><span data-stu-id="df311-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="df311-435"><span class="stdr-thankyou">Obrigado!</span></span><span class="sxs-lookup"><span data-stu-id="df311-435"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="df311-436"><span class="stdr-appreciate">Agradecemos os seus comentários.</span></span><span class="sxs-lookup"><span data-stu-id="df311-436"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="df311-437">Gerenciar seu Perfil</span><span class="sxs-lookup"><span data-stu-id="df311-437">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="df311-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Comentários sobre o Site</a> Comentários sobre o Site</span><span class="sxs-lookup"><span data-stu-id="df311-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="df311-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="df311-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="df311-440">Conte-nos sobre sua experiência...</span><span class="sxs-lookup"><span data-stu-id="df311-440">Tell us about your experience...</span></span>

<span data-ttu-id="df311-441">A página carregou rápido?</span><span class="sxs-lookup"><span data-stu-id="df311-441">Did the page load quickly?</span></span>

<span data-ttu-id="df311-442"><span> Sim<span> </span></span> <span> Não<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="df311-442"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="df311-443">Você gosta do design da página?</span><span class="sxs-lookup"><span data-stu-id="df311-443">Do you like the page design?</span></span>

<span data-ttu-id="df311-444"><span> Sim<span> </span></span> <span> Não<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="df311-444"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="df311-445">Fale mais</span><span class="sxs-lookup"><span data-stu-id="df311-445">Tell us more</span></span>

-   [<span data-ttu-id="df311-446">Boletim informativo Flash</span><span class="sxs-lookup"><span data-stu-id="df311-446">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="df311-447">Entre em contato conosco</span><span class="sxs-lookup"><span data-stu-id="df311-447">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="df311-448">Política de Privacidade</span><span class="sxs-lookup"><span data-stu-id="df311-448">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="df311-449">Termos de Uso</span><span class="sxs-lookup"><span data-stu-id="df311-449">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="df311-450">Marcas comerciais</span><span class="sxs-lookup"><span data-stu-id="df311-450">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="df311-451">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="df311-451">© 2016 Microsoft</span></span>

<span data-ttu-id="df311-452">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="df311-452">© 2016 Microsoft</span></span>

<span data-ttu-id="df311-453">Código e scripts de terceiros, vinculados ou referenciados neste site, são licenciados por terceiros que têm tal código, não pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="df311-453">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="df311-454">Consulte os termos de uso do ASP.NET Ajax CDN – http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="df311-454">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

