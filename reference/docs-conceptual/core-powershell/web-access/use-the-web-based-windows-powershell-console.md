---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: usar o console do windows powershell baseado na web
ms.openlocfilehash: 48ed1646c00f909c4e950f197f51a30205060ef0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
#  <a name="use-the-web-based-windows-powershell-console"></a><span data-ttu-id="a5659-103">Usar o Console do Windows PowerShell baseado na Web</span><span class="sxs-lookup"><span data-stu-id="a5659-103">Use the Web-based Windows PowerShell Console</span></span>

<span data-ttu-id="a5659-104">Atualizado em: 24 de junho de 2013</span><span class="sxs-lookup"><span data-stu-id="a5659-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="a5659-105">Aplica-se a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a5659-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="a5659-106">O Windows PowerShell® Web Access permite que usuários do Windows PowerShell® entrem no site protegido pelo protocolo SSL para usar sessões, cmdlets e scripts do Windows PowerShell para gerenciar um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="a5659-106">Windows PowerShell® Web Access lets Windows PowerShell® users sign in to a Secure Sockets Layer (SSL)-secured website to use Windows PowerShell sessions, cmdlets, and scripts to manage a remote computer.</span></span> <span data-ttu-id="a5659-107">Como o console do Windows PowerShell é executado em um navegador da Web, é possível abri-lo de vários dispositivos clientes, incluindo celulares, tablets, quiosques de computação públicos, computadores laptop ou computadores compartilhados ou emprestados.</span><span class="sxs-lookup"><span data-stu-id="a5659-107">Because the Windows PowerShell console runs in a web browser, it can be opened from a variety of client devices, including cell phones, tablet computers, public computing kiosks, laptop computers, or shared or borrowed computers.</span></span> <span data-ttu-id="a5659-108">O console do Windows PowerShell baseado na Web é destinado a um computador remoto especificado por usuários como parte do processo de entrada.</span><span class="sxs-lookup"><span data-stu-id="a5659-108">The web-based Windows PowerShell console is targeted at a remote computer that is specified by users as part of the sign-in process.</span></span> <span data-ttu-id="a5659-109">Este tópico descreve como entrar e iniciar usando o console baseado na Web do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="a5659-109">This topic describes how to sign in to and start using the Windows PowerShell Web Access web-based console.</span></span>

<span data-ttu-id="a5659-110">Este tópico não descreve como usar o Windows PowerShell ou executar cmdlets ou scripts.</span><span class="sxs-lookup"><span data-stu-id="a5659-110">This topic does not describe how to use Windows PowerShell or run cmdlets or scripts.</span></span> <span data-ttu-id="a5659-111">Para obter informações sobre como usar o Windows PowerShell e os recursos de script, consulte a seção Consulte também no fim deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a5659-111">For information about how to use Windows PowerShell, and scripting resources, see the See Also section at the end of this topic.</span></span>

<span data-ttu-id="a5659-112">Neste tópico:</span><span class="sxs-lookup"><span data-stu-id="a5659-112">In this topic:</span></span>

-   [<span data-ttu-id="a5659-113">Navegadores e dispositivos cliente compatíveis</span><span class="sxs-lookup"><span data-stu-id="a5659-113">Supported browsers and client devices</span></span>](#BKMK_browser)

-   [<span data-ttu-id="a5659-114">Entrando no Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="a5659-114">Signing in to Windows PowerShell Web Access</span></span>](#BKMK_sign)

-   [<span data-ttu-id="a5659-115">Saída e tempo limite</span><span class="sxs-lookup"><span data-stu-id="a5659-115">Signing out and timing out</span></span>](#BKMK_timeout)

-   [<span data-ttu-id="a5659-116">Diferenças no console do Windows PowerShell baseado na Web</span><span class="sxs-lookup"><span data-stu-id="a5659-116">Differences in the web-based Windows PowerShell console</span></span>](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

<span data-ttu-id="a5659-117">O Windows PowerShell Web Access dá suporte aos seguintes navegadores da Internet.</span><span class="sxs-lookup"><span data-stu-id="a5659-117">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="a5659-118">Embora navegadores móveis não tenham suporte oficialmente, muitos poderão executar o console do Windows PowerShell baseado na Web.</span><span class="sxs-lookup"><span data-stu-id="a5659-118">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="a5659-119">É provável que outros navegadores que aceitam cookies, executam JavaScript e abrem sites HTTPS funcionam, mas não foram oficialmente testados.</span><span class="sxs-lookup"><span data-stu-id="a5659-119">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="a5659-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navegadores de computador desktop compatíveis</span></a></span><span class="sxs-lookup"><span data-stu-id="a5659-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="a5659-121">Windows® Internet Explorer® para Microsoft Windows® 8.0, 9.0, 10.0 e 11.0</span><span class="sxs-lookup"><span data-stu-id="a5659-121">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="a5659-122">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="a5659-122">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="a5659-123">Google Chrome™ 17.0.963.56m para Windows</span><span class="sxs-lookup"><span data-stu-id="a5659-123">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="a5659-124">Apple Safari® 5.1.2 para Windows</span><span class="sxs-lookup"><span data-stu-id="a5659-124">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="a5659-125">Apple Safari 5.1.2 para Mac OS®</span><span class="sxs-lookup"><span data-stu-id="a5659-125">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="a5659-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navegadores ou dispositivos móveis minimamente testados</span></a></span><span class="sxs-lookup"><span data-stu-id="a5659-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="a5659-127">Windows Phone 7 e 7.5</span><span class="sxs-lookup"><span data-stu-id="a5659-127">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="a5659-128">Navegador Google Android WebKit 3.1 Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="a5659-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="a5659-129">Apple Safari para iPhone com sistema operacional 5.0.1</span><span class="sxs-lookup"><span data-stu-id="a5659-129">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="a5659-130">Apple Safari para iPad 2 com sistema operacional 5.0.1</span><span class="sxs-lookup"><span data-stu-id="a5659-130">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="a5659-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisitos de navegador</span></a></span><span class="sxs-lookup"><span data-stu-id="a5659-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="a5659-132">Para usar o console do Windows PowerShell Web Access baseado na Web, os navegadores devem executar os procedimentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5659-132">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="a5659-133">Permitir cookies do site do gateway do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="a5659-133">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="a5659-134">Ser capazes de abrir e ler páginas HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a5659-134">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="a5659-135">Abrir e executar sites que usam JavaScript.</span><span class="sxs-lookup"><span data-stu-id="a5659-135">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_sign"></a>

<span data-ttu-id="a5659-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Entrando no Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="a5659-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing in to Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="a5659-137">O administrador do Windows PowerShell Web Access deve fornecer uma URL que é o endereço do site do gateway do Windows PowerShell Web Access da sua organização.</span><span class="sxs-lookup"><span data-stu-id="a5659-137">Your Windows PowerShell Web Access administrator should provide you with a URL that is the address of your organization’s Windows PowerShell Web Access gateway website.</span></span> <span data-ttu-id="a5659-138">Por padrão, o endereço do site é https://&lt;server_name&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="a5659-138">By default, this website address is https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="a5659-139">Antes de entrar no Windows PowerShell Web Access, tenha o nome ou o endereço IP do computador remoto que deseja gerenciar.</span><span class="sxs-lookup"><span data-stu-id="a5659-139">Before you sign in to Windows PowerShell Web Access, be sure that you have the name or IP address of the remote computer that you want to manage.</span></span> <span data-ttu-id="a5659-140">Você deve ser um usuário autorizado no computador remoto e ele deve estar configurado para permitir gerenciamento remoto.</span><span class="sxs-lookup"><span data-stu-id="a5659-140">You must be an authorized user on the remote computer, and it must be configured to allow remote management.</span></span> <span data-ttu-id="a5659-141">Para obter mais informações sobre como configurar o computador para permitir o gerenciamento remoto, consulte [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx) (Habilitar e usar comandos remotos no Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="a5659-141">For more information about configuring your computer to allow remote management, see [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span></span> <span data-ttu-id="a5659-142">O método mais simples de configurar o computador para permitir gerenciamento remoto é executar o cmdlet **Enable-PSRemoting -force** no computador, em uma sessão do Windows PowerShell aberta com direitos de usuário elevados (**Executar como Administrador**).</span><span class="sxs-lookup"><span data-stu-id="a5659-142">The simplest method of configuring your computer to allow remote management is to run the **Enable-PSRemoting -force** cmdlet on the computer, in a Windows PowerShell session that has been opened with elevated user rights (**Run as Administrator**).</span></span>

### <a name="to-sign-in-to-windows-powershell-web-access"></a><span data-ttu-id="a5659-143">Para entrar no Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="a5659-143">To sign in to Windows PowerShell Web Access</span></span>

1.  <span data-ttu-id="a5659-144">Abra o site do Windows PowerShell Web Access em uma janela ou guia do navegador da Internet.</span><span class="sxs-lookup"><span data-stu-id="a5659-144">Open the Windows PowerShell Web Access website in an Internet browser window or tab.</span></span>

2.  <span data-ttu-id="a5659-145">Na página de entrada do Windows PowerShell Web Access, forneça o nome de usuário de rede, a senha e o nome do computador a ser gerenciado (e em que você é um usuário autorizado).</span><span class="sxs-lookup"><span data-stu-id="a5659-145">On the Windows PowerShell Web Access sign-in page, provide your network user name, password, and the name of the computer that you want to manage (and on which you are an authorized user).</span></span> <span data-ttu-id="a5659-146">Se o administrador do Windows PowerShell Web Access o instruir para usar um URI para um site ou servidor proxy personalizado, em vez de um nome do computador, selecione **URI de Conexão** no campo **Tipo de conexão** e forneça o URI.</span><span class="sxs-lookup"><span data-stu-id="a5659-146">If the Windows PowerShell Web Access administrator has instructed you to use a URI to a custom site or proxy server instead of a computer name, select **Connection URI** in the **Connection type** field, and then provide the URI.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="a5659-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Observação </span></span><span class="sxs-lookup"><span data-stu-id="a5659-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><ul>
    <li><p><span data-ttu-id="a5659-148">Se o computador de destino for membro de um grupo de trabalho, use a sintaxe a seguir para fornecer seu nome de usuário e entrar no computador:&lt;<em>nome_do_grupo_de_trabalho</em>&gt;\&lt;<em>nome_de_usuário</em>&gt;.</span><span class="sxs-lookup"><span data-stu-id="a5659-148">If the destination computer is in a workgroup, use the following syntax to provide your user name and sign in to the computer:&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    <li><p><span data-ttu-id="a5659-149">Se o computador de destino for o servidor de gateway, você poderá especificar <strong>localhost</strong> no campo <strong>Nome do computador</strong>.</span><span class="sxs-lookup"><span data-stu-id="a5659-149">If the destination computer is the gateway server, you can specify <strong>localhost</strong> in the <strong>Computer name</strong> field.</span></span></p></li>
    <li><p><span data-ttu-id="a5659-150">Se o computador de destino for o servidor de gateway e o servidor de gateway estiver em um grupo de trabalho, você poderá usar <strong>localhost</strong> no campo <strong>Nome do computador</strong>, mas não usar localhost\&lt;<em>nome_de_usuário</em>&gt; no campo <strong>Nome de usuário</strong>.</span><span class="sxs-lookup"><span data-stu-id="a5659-150">If the destination computer is the gateway server, and the gateway server is in a workgroup, you can use <strong>localhost</strong> in the <strong>Computer name</strong> field, but do not use localhost\&lt;<em>user_name</em>&gt; in the <strong>User name</strong> field.</span></span> <span data-ttu-id="a5659-151">Você deve usar &lt;<em>nome do grupo de trabalho</em>&gt;\&lt;<em>nome_de_usuário</em>&gt;.</span><span class="sxs-lookup"><span data-stu-id="a5659-151">You must use &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  <span data-ttu-id="a5659-152">A seção **Configurações de Conexão Opcionais** está relacionada aos requisitos de autorização do computador remoto que você deseja gerenciar.</span><span class="sxs-lookup"><span data-stu-id="a5659-152">The **Optional Connection Settings** section relates to the authorization requirements of the remote computer that you want to manage.</span></span> <span data-ttu-id="a5659-153">Para saber mais sobre os parâmetros equivalentes às configurações de conexão opcionais, confira [Ajuda do cmdlet Enter-PSSession](https://technet.microsoft.com/library/dd315384.aspx).</span><span class="sxs-lookup"><span data-stu-id="a5659-153">For more information about the parameters that are equivalent to optional connection settings, see the [Enter-PSSession cmdlet Help](https://technet.microsoft.com/library/dd315384.aspx).</span></span>

    <span data-ttu-id="a5659-154">Geralmente, as credenciais usadas para passar pelo gateway do Windows PowerShell Web Access são as mesmas reconhecidas pelo computador remoto que você deseja gerenciar.</span><span class="sxs-lookup"><span data-stu-id="a5659-154">Typically, the credentials you use to pass through the Windows PowerShell Web Access gateway are the same that are recognized by the remote computer that you want to manage.</span></span> <span data-ttu-id="a5659-155">No entanto, se você desejar usar credenciais diferentes para gerenciar o computador remoto especificado na etapa 2, expanda a seção **Configurações de Conexão Opcionais** e forneça as credenciais alternativas.</span><span class="sxs-lookup"><span data-stu-id="a5659-155">However, if you want to use different credentials to manage the remote computer that you specified in step 2, expand the **Optional Connection Settings** section, and provide the alternate credentials.</span></span> <span data-ttu-id="a5659-156">Caso contrário, ignore a etapa 6.</span><span class="sxs-lookup"><span data-stu-id="a5659-156">Otherwise, skip to step 6.</span></span>

4.  <span data-ttu-id="a5659-157">Se o administrador do Windows PowerShell Web Access tiver criado uma configuração de sessão personalizada para usuários do Windows PowerShell Web Access, digite o nome da configuração da sessão no campo **Nome da configuração**.</span><span class="sxs-lookup"><span data-stu-id="a5659-157">If the Windows PowerShell Web Access administrator has created a custom session configuration for Windows PowerShell Web Access users, type the name of the session configuration name in the **Configuration name** field.</span></span> <span data-ttu-id="a5659-158">Para saber mais sobre configurações de sessão, confira [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) no site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a5659-158">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) on the Microsoft website.</span></span>

5.  <span data-ttu-id="a5659-159">Mantenha o **Tipo de autenticação** definido como **Padrão**, a menos que você tenha sido instruído a fazer o contrário pelo administrador do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="a5659-159">Keep the **Authentication type** set to **Default** unless you have been instructed to do otherwise by the Windows PowerShell Web Access administrator.</span></span>

6.  <span data-ttu-id="a5659-160">Clique em **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="a5659-160">Click **Sign in**.</span></span>

<a href="" id="BKMK_timeout"></a>

<span data-ttu-id="a5659-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Saída e tempo limite</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="a5659-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing out and timing out</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="a5659-162">Qualquer uma das ações a seguir encerra uma sessão do Windows PowerShell baseada na Web.</span><span class="sxs-lookup"><span data-stu-id="a5659-162">Any of the following signs you out of a web-based Windows PowerShell session.</span></span>

-   <span data-ttu-id="a5659-163">Clicar em **Sair** no canto inferior direito do console.</span><span class="sxs-lookup"><span data-stu-id="a5659-163">Clicking **Sign out** in the lower right corner of the console.</span></span> <span data-ttu-id="a5659-164">(Windows Server 2012 apenas)</span><span class="sxs-lookup"><span data-stu-id="a5659-164">(Windows Server 2012 only)</span></span>

-   <span data-ttu-id="a5659-165">Clique em **Salvar** ou **Sair** no canto inferior direito do console (Windows Server 2012 R2 apenas).</span><span class="sxs-lookup"><span data-stu-id="a5659-165">Clicking **Save** or **Exit** in the lower right corner of the console (Windows Server 2012 R2 only).</span></span> <span data-ttu-id="a5659-166">Clicar em **Salvar** salva e fecha a sessão do Windows PowerShell Web Access. Você pode se reconectar à sessão mais tarde.</span><span class="sxs-lookup"><span data-stu-id="a5659-166">Clicking **Save** saves and closes your Windows PowerShell Web Access session; you can reconnect to the session later.</span></span> <span data-ttu-id="a5659-167">Quando você entra no Windows PowerShell Web Access novamente, o Windows PowerShell Web Access exibe uma lista de suas sessões salvas. Você pode selecionar e se reconectar a uma sessão salva ou iniciar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="a5659-167">When you sign in to Windows PowerShell Web Access again, Windows PowerShell Web Access displays a list of your saved sessions; you can either select and reconnect to a saved session, or start a new session.</span></span> <span data-ttu-id="a5659-168">O número máximo de sessões abertas, salvas e ativas, a que os usuários têm permissão é configurado pelo administrador do gateway.</span><span class="sxs-lookup"><span data-stu-id="a5659-168">The maximum number of open sessions that users are allowed, both saved and active, is configured by the gateway administrator.</span></span>

    <span data-ttu-id="a5659-169">Clicar em **Sair** faz com que você saia da Windows PowerShell Web Access sessão sem salvá-la.</span><span class="sxs-lookup"><span data-stu-id="a5659-169">Clicking **Exit** signs you out of the Windows PowerShell Web Access session without saving it.</span></span>

-   <span data-ttu-id="a5659-170">Tentar entrar para gerenciar um computador remoto diferente na mesma sessão de navegador ou em uma nova guia da mesma sessão de navegador.</span><span class="sxs-lookup"><span data-stu-id="a5659-170">Attempting to sign in to manage a different remote computer in the same browser session, or in a new tab of the same browser session.</span></span> <span data-ttu-id="a5659-171">(Isso não se aplicará se o servidor de gateway estiver executando Windows Server 2012 R2; Windows PowerShell Web Access em execução em Windows Server 2012 R2 permite várias sessões de usuário em novas guias na mesma sessão do navegador.) Para obter mais informações sobre como usar mais de uma sessão ativa no mesmo computador, consulte “Connecting to multiple target computers simultaneously” (Conectando a vários computadores de destino simultaneamente) na seção [Limitations of the web-based console](#BKMK_limits) (Limitações do console baseado na Web) deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a5659-171">(This does not apply if the gateway server is running Windows Server 2012 R2; Windows PowerShell Web Access running on Windows Server 2012 R2 does allow multiple user sessions in new tabs in the same browser session.) For more information about how to use more than one active session on the same computer, see “Connecting to multiple target computers simultaneously” in the [Limitations of the web-based console](#BKMK_limits) section of this topic.</span></span>

-   <span data-ttu-id="a5659-172">20 minutos de inatividade na sessão.</span><span class="sxs-lookup"><span data-stu-id="a5659-172">20 minutes of inactivity in the session.</span></span> <span data-ttu-id="a5659-173">O administrador do gateway pode personalizar o período de tempo limite de inatividade. Para saber mais, confira [Gerenciamento de sessões](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span><span class="sxs-lookup"><span data-stu-id="a5659-173">The gateway administrator can customize the inactivity time-out period; for more information, see [Session management](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span></span>

    -   <span data-ttu-id="a5659-174">Se os usuários forem desconectados de sessões no console baseado na Web por causa de erros de rede ou outros desligamentos não planejados ou falhas, e não porque você fechou a sessão, as sessões do Windows PowerShell Web Access continuam em execução, conectada ao computador de destino, até decorrer o tempo limite do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="a5659-174">If you are disconnected from a session in the web-based console because of a network error or other unplanned shutdown or failure, and not because you have closed the session yourself, the Windows PowerShell Web Access session continues to run, connected to the target computer, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="a5659-175">Por padrão, esse período de tempo limite é de 20 minutos e é configurado pelo administrador do gateway.</span><span class="sxs-lookup"><span data-stu-id="a5659-175">By default, this time-out period is 20 minutes, and is configured by the gateway administrator.</span></span> <span data-ttu-id="a5659-176">A sessão é desconectada após um padrão de 20 minutos ou após o período de tempo limite especificado pelo administrador do gateway, o que for menor.</span><span class="sxs-lookup"><span data-stu-id="a5659-176">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

        <span data-ttu-id="a5659-177">Se o servidor de gateway estiver executando o Windows Server 2012 R2, o Windows PowerShell Web Access permitirá que os usuários se reconectem a sessões salvas em um momento posterior, mas você não poderá ver ou se reconectar a sessões salvas até ter expirado o período de tempo limite especificado pelo administrador do gateway.</span><span class="sxs-lookup"><span data-stu-id="a5659-177">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but you cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

-   <span data-ttu-id="a5659-178">Fechar a janela ou a guia do navegador.</span><span class="sxs-lookup"><span data-stu-id="a5659-178">Closing the browser window or tab.</span></span>

-   <span data-ttu-id="a5659-179">Desativar o dispositivo cliente em que o navegador está executando ou desconectá-lo da rede.</span><span class="sxs-lookup"><span data-stu-id="a5659-179">Turning off the client device on which the browser is running, or disconnecting it from the network.</span></span>

-   <span data-ttu-id="a5659-180">Executar o comando **Sair** no console Web.</span><span class="sxs-lookup"><span data-stu-id="a5659-180">Running the **Exit** command in the web console.</span></span> <span data-ttu-id="a5659-181">Esse comando não funciona se a configuração de sessão a que você está conectado estiver definida para dar suporte ao modo [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) ou estiver em um runspace restrito.</span><span class="sxs-lookup"><span data-stu-id="a5659-181">This command does not work if the session configuration to which you are connected to is configured to support [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) mode, or is in a restricted runspace.</span></span>

<span data-ttu-id="a5659-182">Se desejar entrar novamente, abra a página da Web do Windows PowerShell Web Access outra vez e entre seguindo as etapas descritas em [Para entrar no Windows PowerShell Web Access](#BKMK_signin) neste tópico.</span><span class="sxs-lookup"><span data-stu-id="a5659-182">If you want to sign in again, open the Windows PowerShell Web Access web page again, and sign in by following the steps in [To sign in to Windows PowerShell Web Access](#BKMK_signin) in this topic.</span></span>

<a href="" id="BKMK_web"></a>

<span data-ttu-id="a5659-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Diferenças no console do Windows PowerShell baseado na Web</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="a5659-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Differences in the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="a5659-184">Depois de entrar no Windows PowerShell Web Access, um console do Windows PowerShell baseado na web é aberto na janela ou guia do navegador.</span><span class="sxs-lookup"><span data-stu-id="a5659-184">After signing in to Windows PowerShell Web Access, a web-based Windows PowerShell console opens in your browser window or tab.</span></span> <span data-ttu-id="a5659-185">Como o console está conectado ao computador especificado durante o processo de entrada, somente aqueles cmdlets ou scripts do Windows PowerShell disponíveis no computador remoto podem ser usados no console.</span><span class="sxs-lookup"><span data-stu-id="a5659-185">Because the console is connected to the remote computer that you specified during the sign-in process, only those Windows PowerShell cmdlets or scripts that are available on the remote computer can be used in the console.</span></span> <span data-ttu-id="a5659-186">Esta seção descreve outras limitações de consoles do Windows PowerShell Web Access e as diferenças entre os consoles do Windows PowerShell Web Access e o console do **PowerShell.exe** instalado.</span><span class="sxs-lookup"><span data-stu-id="a5659-186">This section describes other limitations of Windows PowerShell Web Access consoles, and differences between Windows PowerShell Web Access consoles and the installed **PowerShell.exe** console.</span></span>

###

<span data-ttu-id="a5659-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Disparidade funcional com o PowerShell.exe</span></a></span><span class="sxs-lookup"><span data-stu-id="a5659-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Functional disparity with PowerShell.exe</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="a5659-188">A maioria das funcionalidades do host do Windows PowerShell está disponível no console baseado na Web do Windows PowerShell Web Access, mas há alguns recursos que não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a5659-188">The majority of Windows PowerShell host functionality is available in the Windows PowerShell Web Access web-based console, but there are some features that are not available.</span></span>

-   <span data-ttu-id="a5659-189"><span class="label">Exibições do andamento aninhado.</span></span><span class="sxs-lookup"><span data-stu-id="a5659-189"><span class="label">Nested progress displays.</span></span></span>  <span data-ttu-id="a5659-190">O Windows PowerShell Web Access exibe uma GUI de andamento para os cmdlets que informam o andamento, mas apenas informações de andamento de nível superior são exibidas.</span><span class="sxs-lookup"><span data-stu-id="a5659-190">Windows PowerShell Web Access displays a progress GUI for cmdlets that report progress, but only top-level progress information is displayed.</span></span>

-   <span data-ttu-id="a5659-191"><span class="label">Modificação da cor de entrada.</span></span><span class="sxs-lookup"><span data-stu-id="a5659-191"><span class="label">Input color modification.</span></span></span>  <span data-ttu-id="a5659-192">A cor de entrada (do primeiro plano e da tela de fundo) não pode ser alterada.</span><span class="sxs-lookup"><span data-stu-id="a5659-192">The input color (both foreground and background) cannot be changed.</span></span> <span data-ttu-id="a5659-193">É possível alterar o estilo das mensagens de saída, de aviso, detalhadas e de erro executando um script.</span><span class="sxs-lookup"><span data-stu-id="a5659-193">The style of output, warning, verbose, and error messages can all be changed by running a script.</span></span>

-   <span data-ttu-id="a5659-194"><span class="label">PSHostRawUserInterface.</span></span><span class="sxs-lookup"><span data-stu-id="a5659-194"><span class="label">PSHostRawUserInterface.</span></span></span>  <span data-ttu-id="a5659-195">O Windows PowerShell Web Access é implementado sobre o gerenciamento remoto do Windows PowerShell e usa um runspace remoto.</span><span class="sxs-lookup"><span data-stu-id="a5659-195">Windows PowerShell Web Access is implemented over Windows PowerShell remote management, and uses a remote runspace.</span></span> <span data-ttu-id="a5659-196">O Windows PowerShell Web Access não implementa alguns métodos nessa interface; por exemplo, qualquer comando que grava no console do Windows.</span><span class="sxs-lookup"><span data-stu-id="a5659-196">Windows PowerShell Web Access does not implement some methods in this interface; for example, any command that writes to the Windows console.</span></span> <span data-ttu-id="a5659-197">Comandos como **PowerTab** não funcionam no Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="a5659-197">Commands such as **PowerTab** do not work in Windows PowerShell Web Access.</span></span>

-   <span data-ttu-id="a5659-198"><span class="label">Teclas de função.</span></span><span class="sxs-lookup"><span data-stu-id="a5659-198"><span class="label">Function keys.</span></span></span>  <span data-ttu-id="a5659-199">O Windows PowerShell Web Access não dá suporte a algumas teclas de função do, em muitos casos, porque os comandos são reservados pelo navegador.</span><span class="sxs-lookup"><span data-stu-id="a5659-199">Windows PowerShell Web Access does not support some function keys, in many cases because the commands are reserved by the browser.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="a5659-200">Tecla de função sem suporte</span><span class="sxs-lookup"><span data-stu-id="a5659-200">Unsupported Function Key</span></span></p></th>
<th><p><span data-ttu-id="a5659-201">Ação</span><span class="sxs-lookup"><span data-stu-id="a5659-201">Action</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="a5659-202">Ctrl+C</span><span class="sxs-lookup"><span data-stu-id="a5659-202">Ctrl+C</span></span></p></td>
<td><p><span data-ttu-id="a5659-203">No Windows PowerShell Web Access, <strong>Ctrl + C</strong> é usado pelo navegador para copiar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a5659-203">In Windows PowerShell Web Access, <strong>Ctrl+C</strong> is used by the browser to copy content.</span></span> <span data-ttu-id="a5659-204">O console oferece um botão <strong>Cancelar</strong> e os usuários também podem usar <strong>Ctrl+Q</strong> para cancelar os comandos.</span><span class="sxs-lookup"><span data-stu-id="a5659-204">The console offers a <strong>Cancel</strong> button, and users can also use <strong>Ctrl+Q</strong> to cancel commands.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a5659-205">Alt-espaço, e, l</span><span class="sxs-lookup"><span data-stu-id="a5659-205">Alt-space, e, l</span></span></p></td>
<td><p><span data-ttu-id="a5659-206">Rola pelo buffer da tela</span><span class="sxs-lookup"><span data-stu-id="a5659-206">Scroll through the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a5659-207">Alt+espaço, e, f</span><span class="sxs-lookup"><span data-stu-id="a5659-207">Alt+Space, e, f</span></span></p></td>
<td><p><span data-ttu-id="a5659-208">Procura texto no buffer da tela</span><span class="sxs-lookup"><span data-stu-id="a5659-208">Search for text in the screen buffer</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a5659-209">Alt+espaço, e, k</span><span class="sxs-lookup"><span data-stu-id="a5659-209">Alt+Space, e, k</span></span></p></td>
<td><p><span data-ttu-id="a5659-210">Seleciona o texto a ser copiado do buffer da tela</span><span class="sxs-lookup"><span data-stu-id="a5659-210">Select text to be copied from the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a5659-211">Alt+espaço, e, p</span><span class="sxs-lookup"><span data-stu-id="a5659-211">Alt+Space, e, p</span></span></p></td>
<td><p><span data-ttu-id="a5659-212">Cola o conteúdo da área de transferência no console do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5659-212">Paste clipboard contents into the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a5659-213">Alt+espaço, c</span><span class="sxs-lookup"><span data-stu-id="a5659-213">Alt+Space, c</span></span></p></td>
<td><p><span data-ttu-id="a5659-214">Fecha o console do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5659-214">Close the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a5659-215">Ctrl+Break</span><span class="sxs-lookup"><span data-stu-id="a5659-215">Ctrl+Break</span></span></p></td>
<td><p><span data-ttu-id="a5659-216">Força a janela do Windows PowerShell a fechar</span><span class="sxs-lookup"><span data-stu-id="a5659-216">Force the Windows PowerShell window to close</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a5659-217">Ctrl+Home</span><span class="sxs-lookup"><span data-stu-id="a5659-217">Ctrl+Home</span></span></p></td>
<td><p><span data-ttu-id="a5659-218">Exclui do início da linha de comando atual</span><span class="sxs-lookup"><span data-stu-id="a5659-218">Deletes from the beginning of the current command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a5659-219">Ctrl+End</span><span class="sxs-lookup"><span data-stu-id="a5659-219">Ctrl+End</span></span></p></td>
<td><p><span data-ttu-id="a5659-220">Exclui para o fim da linha de comando</span><span class="sxs-lookup"><span data-stu-id="a5659-220">Deletes to end of the command line</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a5659-221">F1</span><span class="sxs-lookup"><span data-stu-id="a5659-221">F1</span></span></p></td>
<td><p><span data-ttu-id="a5659-222">Move o cursor um caractere para a direita na linha de comando</span><span class="sxs-lookup"><span data-stu-id="a5659-222">Move cursor one character to the right on your command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a5659-223">F2</span><span class="sxs-lookup"><span data-stu-id="a5659-223">F2</span></span></p></td>
<td><p><span data-ttu-id="a5659-224">Cria um novo comando copiando o último comando até o caractere digitado</span><span class="sxs-lookup"><span data-stu-id="a5659-224">Creates a new command by copying your last command up to the character that you type</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a5659-225">F3</span><span class="sxs-lookup"><span data-stu-id="a5659-225">F3</span></span></p></td>
<td><p><span data-ttu-id="a5659-226">Preenche a linha de comando com o conteúdo da última linha de comando</span><span class="sxs-lookup"><span data-stu-id="a5659-226">Complete the command line with content from your last command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a5659-227">F4</span><span class="sxs-lookup"><span data-stu-id="a5659-227">F4</span></span></p></td>
<td><p><span data-ttu-id="a5659-228">Exclui caracteres a partir da posição do cursor</span><span class="sxs-lookup"><span data-stu-id="a5659-228">Deletes characters from cursor position</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a5659-229">F5</span><span class="sxs-lookup"><span data-stu-id="a5659-229">F5</span></span></p></td>
<td><p><span data-ttu-id="a5659-230">Volta na verificação do histórico de comandos.</span><span class="sxs-lookup"><span data-stu-id="a5659-230">Scan backward through your command history.</span></span> <span data-ttu-id="a5659-231">Para acessar comandos no histórico de comandos no Windows PowerShell Web Access, clique nos botões de rolagem do <strong>Histórico</strong> no console baseado na Web.</span><span class="sxs-lookup"><span data-stu-id="a5659-231">To access commands in the command history in Windows PowerShell Web Access, click the <strong>History</strong> scroll buttons in the web-based console.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a5659-232">F7</span><span class="sxs-lookup"><span data-stu-id="a5659-232">F7</span></span></p></td>
<td><p><span data-ttu-id="a5659-233">Selecione interativamente um comando do histórico de comandos</span><span class="sxs-lookup"><span data-stu-id="a5659-233">Interactively select a command from your command history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a5659-234">F8</span><span class="sxs-lookup"><span data-stu-id="a5659-234">F8</span></span></p></td>
<td><p><span data-ttu-id="a5659-235">Verifica os comandos de exibição do histórico que correspondem ao texto atual</span><span class="sxs-lookup"><span data-stu-id="a5659-235">Scan history displaying commands that match current text</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a5659-236">F9</span><span class="sxs-lookup"><span data-stu-id="a5659-236">F9</span></span></p></td>
<td><p><span data-ttu-id="a5659-237">Executa um comando com numeração específica do histórico</span><span class="sxs-lookup"><span data-stu-id="a5659-237">Run a specific numbered command from history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a5659-238">Page Up</span><span class="sxs-lookup"><span data-stu-id="a5659-238">Page Up</span></span></p></td>
<td><p><span data-ttu-id="a5659-239">Executa o primeiro comando no histórico</span><span class="sxs-lookup"><span data-stu-id="a5659-239">Run the first command in the history</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a5659-240">Page Down</span><span class="sxs-lookup"><span data-stu-id="a5659-240">Page Down</span></span></p></td>
<td><p><span data-ttu-id="a5659-241">Executa o último comando no histórico</span><span class="sxs-lookup"><span data-stu-id="a5659-241">Run the last command in the history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a5659-242">Alt+F7</span><span class="sxs-lookup"><span data-stu-id="a5659-242">Alt+F7</span></span></p></td>
<td><p><span data-ttu-id="a5659-243">Limpa a lista do histórico de comandos</span><span class="sxs-lookup"><span data-stu-id="a5659-243">Clear the command history list</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="a5659-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitações do console baseado na Web</span></a></span><span class="sxs-lookup"><span data-stu-id="a5659-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitations of the web-based console</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="a5659-245"><span class="label">Salto duplo.</span></span><span class="sxs-lookup"><span data-stu-id="a5659-245"><span class="label">Double-hop.</span></span></span>   <span data-ttu-id="a5659-246">Você pode se deparar com a limitação de salto duplo (ou se conectar a um segundo computador por meio da primeira conexão) se tentar criar ou trabalhar em uma nova sessão usando o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="a5659-246">You can encounter the double-hop (or connecting to a second computer from the first connection) limitation if you try to create or work on a new session by using Windows PowerShell Web Access.</span></span> <span data-ttu-id="a5659-247">O Windows PowerShell Web Access usa um runspace remoto e, no momento, o **PowerShell.exe** não dá suporte ao estabelecimento de uma conexão remota com um segundo computador de um runspace remoto.</span><span class="sxs-lookup"><span data-stu-id="a5659-247">Windows PowerShell Web Access uses a remote runspace, and currently, **PowerShell.exe** does not support establishing a remote connection to a second computer from a remote runspace.</span></span> <span data-ttu-id="a5659-248">Se você tentar se conectar a um segundo computador remoto por meio de uma conexão existente usando o cmdlet **Enter-PSSession**, por exemplo, vários erros poderão ser gerados, como “Não é possível obter recursos da rede”.</span><span class="sxs-lookup"><span data-stu-id="a5659-248">If you attempt to connect to a second remote computer from an existing connection by using the **Enter-PSSession** cmdlet, for example, you can get various errors, such as “Cannot get network resources.”</span></span>

    <span data-ttu-id="a5659-249">Para evitar erros de salto, o administrador deve configurar a autenticação CredSSP no ambiente de rede da organização.</span><span class="sxs-lookup"><span data-stu-id="a5659-249">To avoid double-hop errors, your administrator should configure CredSSP authentication in your organization’s network environment.</span></span> <span data-ttu-id="a5659-250">Para obter mais informações sobre a configuração da autenticação CredSSP, consulte [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) (CredSSP para segundo salto remoto) no site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a5659-250">For more information about configuring CredSSP authentication, see [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) on the Microsoft website.</span></span> <span data-ttu-id="a5659-251">Também é possível fornecer credenciais explícitas quando você deseja gerenciar um segundo computador remoto, é pouco provável que as credenciais implícitas permitam o segundo salto.</span><span class="sxs-lookup"><span data-stu-id="a5659-251">You can also provide explicit credentials when you want to manage a second remote computer; implicit credentials are unlikely to allow the second hop.</span></span>

-   <span data-ttu-id="a5659-252">O Windows PowerShell Web Access usa e tem as mesmas limitações que uma sessão remota do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5659-252">Windows PowerShell Web Access uses and has the same limitations as a remote Windows PowerShell session.</span></span> <span data-ttu-id="a5659-253">Comandos que chamam diretamente APIs do console do Windows, como aquelas para editores baseados no console ou programas de menu baseados em texto, não funcionam porque os comandos não leem nem gravam pipes padrão de entrada, de saída e de erro.</span><span class="sxs-lookup"><span data-stu-id="a5659-253">Commands that directly call Windows console APIs, such as those for console-based editors or text-based menu programs, do not work because the commands do not read or write to standard input, output, and error pipes.</span></span> <span data-ttu-id="a5659-254">Portanto, os comandos que inicializam um arquivo executável, como **notepad.exe**, ou exibem uma GUI, como <span class="code">OpenGridView</span> ou <span class="code">ogv</span>, não funcionam.</span><span class="sxs-lookup"><span data-stu-id="a5659-254">Therefore, commands that launch an executable file, such as **notepad.exe**, or display a GUI, such as <span class="code">OpenGridView</span> or <span class="code">ogv</span>, do not work.</span></span> <span data-ttu-id="a5659-255">Sua experiência é afetada por este comportamento, para você, parece que o Windows PowerShell Web Access não está respondendo ao seu comando.</span><span class="sxs-lookup"><span data-stu-id="a5659-255">Your experience is affected by this behavior; to you, it appears that Windows PowerShell Web Access is not responding to your command.</span></span>

-   <span data-ttu-id="a5659-256">O preenchimento da guia não funciona em uma configuração de sessão com runspace restrito ou que está no modo **NoLanguage**.</span><span class="sxs-lookup"><span data-stu-id="a5659-256">Tab completion does not work in a session configuration with a restricted runspace or one that is in **NoLanguage** mode.</span></span> <span data-ttu-id="a5659-257">Embora os administradores possam configurar uma sessão para aceitar o preenchimento da guia, isso não é incentivado por motivos de segurança, pois pode expor as informações a seguir a usuários não autorizados.</span><span class="sxs-lookup"><span data-stu-id="a5659-257">Although administrators can configure a session to support tab completion, it is discouraged for security reasons, because it can expose the following information to unauthorized users.</span></span>

    -   <span data-ttu-id="a5659-258">Caminhos internos do sistema de arquivos</span><span class="sxs-lookup"><span data-stu-id="a5659-258">Internal file system paths</span></span>

    -   <span data-ttu-id="a5659-259">Pastas compartilhadas em computadores internos</span><span class="sxs-lookup"><span data-stu-id="a5659-259">Shared folders on internal computers</span></span>

    -   <span data-ttu-id="a5659-260">Variáveis no runspace</span><span class="sxs-lookup"><span data-stu-id="a5659-260">Variables in the runspace</span></span>

    -   <span data-ttu-id="a5659-261">Tipos carregados ou namespaces .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a5659-261">Loaded types or.NET Framework namespaces</span></span>

    -   <span data-ttu-id="a5659-262">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="a5659-262">Environment variables</span></span>

-   <span data-ttu-id="a5659-263">Os usuários que entraram em uma configuração de sessão **NoLanguage** ou em um runspace restrito no Windows PowerShell Web Access não podem executar o comando **Sair** para encerrar a sessão.</span><span class="sxs-lookup"><span data-stu-id="a5659-263">Users who are signed in to a **NoLanguage** session configuration or a restricted runspace in Windows PowerShell Web Access cannot run the **Exit** command to end the session.</span></span> <span data-ttu-id="a5659-264">Para sair, os usuários devem clicar em **Sair** na página do console.</span><span class="sxs-lookup"><span data-stu-id="a5659-264">To sign out, users should click **Sign Out** on the console page.</span></span>

-   <span data-ttu-id="a5659-265"><span class="label">Conectando a vários computadores de destino simultaneamente.</span></span><span class="sxs-lookup"><span data-stu-id="a5659-265"><span class="label">Connecting to multiple target computers simultaneously.</span></span></span>   <span data-ttu-id="a5659-266">Se o servidor de gateway estiver executando o Windows Server 2012, o Windows PowerShell Web Access permitirá apenas uma conexão de computador remoto por sessão de navegador; ele não permitirá que os usuários entrem uma vez e se conectem a vários computadores remotos usando guias separadas do navegador.</span><span class="sxs-lookup"><span data-stu-id="a5659-266">If the gateway server is running Windows Server 2012, Windows PowerShell Web Access allows only one remote computer connection per browser session; it does not allow users to sign in once, and connect to multiple remote computers by using separate browser tabs.</span></span> <span data-ttu-id="a5659-267">Ao abrir uma nova guia ou uma nova janela de navegador, o Windows PowerShell Web Access solicita que você desconecte a sessão atual e inicie uma nova sessão, de forma que possa se conectar ao novo (ou ao mesmo) computador remoto.</span><span class="sxs-lookup"><span data-stu-id="a5659-267">When you open a new tab or new browser window, Windows PowerShell Web Access prompts you to disconnect your current session and start a new session, so that you can connect to the new (or the same) remote computer.</span></span> <span data-ttu-id="a5659-268">No entanto, se duas ou mais sessões separadas para computadores remotos diferentes forem desejadas, um recurso no Internet Explorer permitirá criar uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="a5659-268">If two or more separate sessions to different remote computers are desired, however, a feature in Internet Explorer lets you create a new session.</span></span> <span data-ttu-id="a5659-269">Para iniciar uma nova sessão de navegador no Internet Explorer, pressione **Alt**, abra o menu **Arquivo** e selecione **Nova Sessão**.</span><span class="sxs-lookup"><span data-stu-id="a5659-269">To start a new browser session in Internet Explorer, press **ALT**, open the **File** menu, and then select **New Session**.</span></span> <span data-ttu-id="a5659-270">Em seguida, abra o site do Windows PowerShell Web Access na nova sessão e entre para acessar outro computador remoto.</span><span class="sxs-lookup"><span data-stu-id="a5659-270">Then, open the Windows PowerShell Web Access website in the new session, and sign in to access another remote computer.</span></span>

    <span data-ttu-id="a5659-271">Quando o gateway do Windows PowerShell Web Access estiver em execução no Windows Server 2012 R2, os usuários poderão abrir várias conexões com computadores remotos em guias diferentes do navegador.</span><span class="sxs-lookup"><span data-stu-id="a5659-271">When the Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, users can open multiple connections to remote computers in different browser tabs.</span></span> <span data-ttu-id="a5659-272">Se você quiser abrir mais de uma conexão a um computador remoto usando o console do Windows PowerShell baseado na Web, entre em contato com o administrador de gateway do Windows PowerShell Web Access para ver se este recurso tem suporte pelo servidor de gateway.</span><span class="sxs-lookup"><span data-stu-id="a5659-272">If you want to open more than one connection to a remote computer by using the web-based Windows PowerShell console, check with your Windows PowerShell Web Access gateway administrator to see if this feature is supported by the gateway server.</span></span>

-   <span data-ttu-id="a5659-273"><span class="label">Sessões persistentes do Windows PowerShell (reconexão).</span></span><span class="sxs-lookup"><span data-stu-id="a5659-273"><span class="label">Persistent Windows PowerShell sessions (Reconnection).</span></span></span>   <span data-ttu-id="a5659-274">Depois que atingir o tempo limite do gateway do Windows PowerShell Web Access, a conexão remota entre o gateway e o computador de destino será fechada.</span><span class="sxs-lookup"><span data-stu-id="a5659-274">After you time out of the Windows PowerShell Web Access gateway, the remote connection between the gateway and the target computer is closed.</span></span> <span data-ttu-id="a5659-275">Com isso, todos os cmdlets ou scripts atualmente presentes no processo são interrompidos.</span><span class="sxs-lookup"><span data-stu-id="a5659-275">This stops any cmdlets or scripts that are currently in process.</span></span> <span data-ttu-id="a5659-276">Você é incentivado a usar a infraestrutura do Windows PowerShell **-Job** quando estiver executando tarefas longas, para que seja possível iniciar trabalhos, desconectar do computador, reconectar posteriormente e ter trabalhos persistentes.</span><span class="sxs-lookup"><span data-stu-id="a5659-276">You are encouraged to use the Windows PowerShell **-Job** infrastructure when you are performing long-running tasks, so that you can start jobs, disconnect from the computer, reconnect later, and have jobs persist.</span></span> <span data-ttu-id="a5659-277">Outro benefício de usar cmdlets **-Job** é que você pode iniciá-los usando o Windows PowerShell Web Access, desconectar-se e reconectar-se posteriormente, executando o Windows PowerShell Web Access ou outro host (como o ISE (Ambiente de Script Integrado) do Windows PowerShell®).</span><span class="sxs-lookup"><span data-stu-id="a5659-277">Another benefit of using **-Job** cmdlets is that you can start them by using Windows PowerShell Web Access, sign out, and then reconnect later, either by running Windows PowerShell Web Access or another host (such as Windows PowerShell® Integrated Scripting Environment (ISE)).</span></span>

-   <span data-ttu-id="a5659-278"><span class="label">Redimensionamento do console.</span></span><span class="sxs-lookup"><span data-stu-id="a5659-278"><span class="label">Console resizing.</span></span></span>   <span data-ttu-id="a5659-279">A janela de console **PowerShell.exe** pode ser redimensionada das três maneiras a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5659-279">The **PowerShell.exe** console window can be resized in the following three ways.</span></span>

    -   <span data-ttu-id="a5659-280">Arraste e ajuste o tamanho da janela do console com o mouse</span><span class="sxs-lookup"><span data-stu-id="a5659-280">Drag and adjust the console window size with a mouse</span></span>

    -   <span data-ttu-id="a5659-281">Altere as propriedades de altura e largura usando uma GUI para as propriedades do console</span><span class="sxs-lookup"><span data-stu-id="a5659-281">Change the height and width properties by using a GUI for console properties</span></span>

    -   <span data-ttu-id="a5659-282">Altere a altura e largura das janelas do console com um cmdlet</span><span class="sxs-lookup"><span data-stu-id="a5659-282">Changing the height and width of console windows with a cmdlet</span></span>

        <span data-ttu-id="a5659-283">A janela do console do Windows PowerShell Web Access pode ser configurada usando os cmdlets da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="a5659-283">The console window for Windows PowerShell Web Access can be configured by using the cmdlets as follows.</span></span> <span data-ttu-id="a5659-284">No exemplo a seguir, um usuário muda a largura do console do Windows PowerShell Web Access para **20**.</span><span class="sxs-lookup"><span data-stu-id="a5659-284">In the following example, a user changes the width of Windows PowerShell Web Access console to **20**.</span></span>

        [<span data-ttu-id="a5659-285">Cópia</span><span class="sxs-lookup"><span data-stu-id="a5659-285">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "Copy to clipboard.")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        <span data-ttu-id="a5659-286">É possível alterar a altura do console de maneira similar.</span><span class="sxs-lookup"><span data-stu-id="a5659-286">You can change the height of the console in a similar manner.</span></span>

        <span data-ttu-id="a5659-287">Exemplos adicionais para personalizar a exibição do console estão disponíveis no [Blog da Equipe do Windows PowerShell](http://blogs.msdn.com/b/powershell/).</span><span class="sxs-lookup"><span data-stu-id="a5659-287">Additional examples for customizing the console view are available in the [Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/).</span></span>

<span data-ttu-id="a5659-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Veja também</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="a5659-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="a5659-289">[Referência de cmdlet do Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell no Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[Repositório Script Center no TechNet](http://gallery.technet.microsoft.com/scriptcenter)
[Script Center – Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Blog da equipe do Windows PowerShell](http://blogs.msdn.com/b/powershell/)</span><span class="sxs-lookup"><span data-stu-id="a5659-289">[Windows PowerShell Cmdlet Reference](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell on Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet Script Center Repository](http://gallery.technet.microsoft.com/scriptcenter)
[Script Center - Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/)</span></span>

<span data-ttu-id="a5659-290"><span>Mostrar</span>: herdado protegido</span><span class="sxs-lookup"><span data-stu-id="a5659-290"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="a5659-291"><span class="stdr-votetitle">Esta página foi útil?</span></span><span class="sxs-lookup"><span data-stu-id="a5659-291"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="a5659-292">Sim Não</span><span class="sxs-lookup"><span data-stu-id="a5659-292">Yes No</span></span>

<span data-ttu-id="a5659-293">Comentários adicionais?</span><span class="sxs-lookup"><span data-stu-id="a5659-293">Additional feedback?</span></span>

<span data-ttu-id="a5659-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caracteres restantes</span> Enviar Ignorar isto</span><span class="sxs-lookup"><span data-stu-id="a5659-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="a5659-295"><span class="stdr-thankyou">Obrigado!</span></span><span class="sxs-lookup"><span data-stu-id="a5659-295"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="a5659-296"><span class="stdr-appreciate">Agradecemos os seus comentários.</span></span><span class="sxs-lookup"><span data-stu-id="a5659-296"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="a5659-297">Gerenciar seu Perfil</span><span class="sxs-lookup"><span data-stu-id="a5659-297">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="a5659-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Comentários sobre o Site</a> Comentários sobre o Site</span><span class="sxs-lookup"><span data-stu-id="a5659-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="a5659-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="a5659-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="a5659-300">Conte-nos sobre sua experiência...</span><span class="sxs-lookup"><span data-stu-id="a5659-300">Tell us about your experience...</span></span>

<span data-ttu-id="a5659-301">A página carregou rápido?</span><span class="sxs-lookup"><span data-stu-id="a5659-301">Did the page load quickly?</span></span>

<span data-ttu-id="a5659-302"><span> Sim<span> </span></span> <span> Não<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="a5659-302"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="a5659-303">Você gosta do design da página?</span><span class="sxs-lookup"><span data-stu-id="a5659-303">Do you like the page design?</span></span>

<span data-ttu-id="a5659-304"><span> Sim<span> </span></span> <span> Não<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="a5659-304"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="a5659-305">Fale mais</span><span class="sxs-lookup"><span data-stu-id="a5659-305">Tell us more</span></span>

-   [<span data-ttu-id="a5659-306">Boletim informativo Flash</span><span class="sxs-lookup"><span data-stu-id="a5659-306">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="a5659-307">Entre em contato conosco</span><span class="sxs-lookup"><span data-stu-id="a5659-307">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="a5659-308">Política de Privacidade</span><span class="sxs-lookup"><span data-stu-id="a5659-308">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="a5659-309">Termos de Uso</span><span class="sxs-lookup"><span data-stu-id="a5659-309">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="a5659-310">Marcas comerciais</span><span class="sxs-lookup"><span data-stu-id="a5659-310">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="a5659-311">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="a5659-311">© 2016 Microsoft</span></span>

<span data-ttu-id="a5659-312">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="a5659-312">© 2016 Microsoft</span></span>

<span data-ttu-id="a5659-313">Código e scripts de terceiros, vinculados ou referenciados neste site, são licenciados por terceiros que têm tal código, não pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a5659-313">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="a5659-314">Consulte os termos de uso do ASP.NET Ajax CDN – http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="a5659-314">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

