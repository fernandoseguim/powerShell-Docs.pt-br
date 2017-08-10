---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: desinstalar o windows powershell web access
ms.openlocfilehash: 7231d5eadceda8e3b28d9a81c2b5dcbe43680ff2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
#  <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="d7a0d-103">Desinstalar o Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="d7a0d-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="d7a0d-104">Atualizado em: 24 de junho de 2013</span><span class="sxs-lookup"><span data-stu-id="d7a0d-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="d7a0d-105">Aplica-se a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d7a0d-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="d7a0d-106">Siga as etapas neste tópico para excluir o site e o aplicativo do Windows PowerShell Web Access do servidor de gateway que está executando o Windows Server 2012 R2 ou Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-106">Follow steps in this topic to delete the Windows PowerShell Web Access website and application from the gateway server that is running either Windows Server 2012 R2 or Windows Server 2012.</span></span> <span data-ttu-id="d7a0d-107">Antes de começar, notifique os usuários do console baseado na Web a respeito da remoção do site.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-107">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

<span data-ttu-id="d7a0d-108">Antes de desinstalar o Windows PowerShell Web Access do servidor de gateway, execute o cmdlet <span class="code">Uninstall-PswaWebApplication</span> para remover o site e os aplicativos Web do Windows PowerShell Web Access ou use o procedimento do Gerenciador do IIS, [Para excluir o site e os aplicativos Web do Windows PowerShell Web Access usando o Gerenciador do IIS](#BKMK_delsite).</span><span class="sxs-lookup"><span data-stu-id="d7a0d-108">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the <span class="code">Uninstall-PswaWebApplication</span> cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [To delete the Windows PowerShell Web Access website and web applications by using IIS Manager](#BKMK_delsite).</span></span>

<span data-ttu-id="d7a0d-109">A desinstalação do Windows PowerShell Web Access não desinstala o IIS nem nenhum outro recurso instalado automaticamente porque o Windows PowerShell Web Access precisa deles para ser executado.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="d7a0d-110">O processo de desinstalação deixa instalados os recursos dos quais o Windows PowerShell Web Access dependia. É possível desinstalar esses recursos separadamente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

<span data-ttu-id="d7a0d-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Desinstalação (rápida) recomendada</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="d7a0d-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="d7a0d-112">Os procedimentos nesta seção o ajudarão a desinstalar o aplicativo Web do Windows PowerShell Web Access e o recurso do Windows PowerShell Web Access usando os cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-112">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using Windows PowerShell cmdlets.</span></span>

###

<span data-ttu-id="d7a0d-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 1: excluir o aplicativo Web</span></a></span><span class="sxs-lookup"><span data-stu-id="d7a0d-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="d7a0d-114">Se você tiver especificado seu próprio nome de site personalizado, adicione o parâmetro <span class="code">WebsiteName</span> ao seu comando e especifique o nome do site.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-114">If you have specified your own, custom website name, add the <span class="code">WebsiteName</span> parameter to your command, and specify the website name.</span></span> <span data-ttu-id="d7a0d-115">Se você tiver usado um aplicativo Web personalizado (não o aplicativo padrão, **pswa**), adicione o parâmetro <span class="code">WebApplicationName</span> ao seu comando e especifique o nome do aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-115">If you have used a custom web application (not the default application, **pswa**, add the <span class="code">WebApplicationName</span> parameter to your command, and specify the name of the web application.</span></span>

#### <a name="to-delete-the-website-and-web-applications-by-using-the-uninstall-pswawebapplication-cmdlet"></a><span data-ttu-id="d7a0d-116">Para excluir o site e os aplicativos Web usando o cmdlet Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="d7a0d-116">To delete the website and web applications by using the Uninstall-PswaWebApplication cmdlet</span></span>

1.  <span data-ttu-id="d7a0d-117">Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="d7a0d-118">Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="d7a0d-119">Na tela **Iniciar** do Windows, clique em **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="d7a0d-120">Digite **Uninstall-PswaWebApplication** e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-120">Type **Uninstall-PswaWebApplication**, and then press **Enter**.</span></span>

3.  <span data-ttu-id="d7a0d-121">Se você estiver usando um certificado de teste, adicione o parâmetro <span class="code">DeleteTestCertificate</span> ao cmdlet, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-121">If you are using a test certificate, add the <span class="code">DeleteTestCertificate</span> parameter to the cmdlet, as shown in the following example.</span></span>

    [<span data-ttu-id="d7a0d-122">Cópia</span><span class="sxs-lookup"><span data-stu-id="d7a0d-122">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "Copy to clipboard.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<span data-ttu-id="d7a0d-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 2: Desinstalar o Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="d7a0d-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="d7a0d-124">Para desinstalar o Windows PowerShell Web Access usando cmdlets do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7a0d-124">To uninstall Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="d7a0d-125">Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="d7a0d-126">Se já houver uma sessão aberta, vá para a etapa seguinte.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="d7a0d-127">Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="d7a0d-128">Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="d7a0d-129">Digite o seguinte e pressione **Enter**, em que *computer_name* representa um servidor remoto do qual você deseja remover o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="d7a0d-130">O parâmetro <span class="code">-Restart</span> reinicia automaticamente os servidores de destino se exigido pela remoção.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-130">The <span class="code">-Restart</span> parameter automatically restarts destination servers if required by the removal.</span></span>

    [<span data-ttu-id="d7a0d-131">Cópia</span><span class="sxs-lookup"><span data-stu-id="d7a0d-131">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "Copy to clipboard.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="d7a0d-132">Para remover funções e recursos de um VHD offline, adicione os parâmetros <span class="code">ComputerName</span> e <span class="code">VHD</span>.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-132">To remove roles and features from an offline VHD, you must add both the <span class="code">-ComputerName</span> parameter and the <span class="code">-VHD</span> parameter.</span></span> <span data-ttu-id="d7a0d-133">O parâmetro <span class="code">-ComputerName</span> contém o nome do servidor em que será montado o VHD e o parâmetro <span class="code">-VHD</span> contém o caminho para o arquivo VHD no servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-133">The <span class="code">-ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">-VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="d7a0d-134">Cópia</span><span class="sxs-lookup"><span data-stu-id="d7a0d-134">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "Copy to clipboard.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

3.  <span data-ttu-id="d7a0d-135">Quando a remoção for concluída, verifique se você removeu o Windows PowerShell Web Access abrindo a página **Todos os Servidores** no Gerenciador do Servidor, selecionando um servidor do qual você removeu o recurso e exibindo o bloco **Funções e Recursos** na página do servidor selecionado.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-135">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span> <span data-ttu-id="d7a0d-136">Você também pode executar o cmdlet <span class="code">Get-WindowsFeature</span> de destino no servidor selecionado (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) para exibir uma lista de funções e recursos que estão instalados no servidor.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-136">You can also run the <span class="code">Get-WindowsFeature</span> cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

<span data-ttu-id="d7a0d-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Desinstalação personalizada</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="d7a0d-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="d7a0d-138">Os procedimentos nesta seção o ajudarão a desinstalar o aplicativo Web do Windows PowerShell Web Access e o recurso do Windows PowerShell Web Access usando o Assistente de Remoção de Funções e Recursos no Gerenciador do Servidor e o console do Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-138">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

###

<span data-ttu-id="d7a0d-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 1: excluir o aplicativo Web</span></a></span><span class="sxs-lookup"><span data-stu-id="d7a0d-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-delete-the-windows-powershell-web-access-website-and-web-applications-by-using-iis-manager"></a><span data-ttu-id="d7a0d-140">Para excluir o site e os aplicativos Web do Windows PowerShell Web Access usando o Gerenciador do IIS</span><span class="sxs-lookup"><span data-stu-id="d7a0d-140">To delete the Windows PowerShell Web Access website and web applications by using IIS Manager</span></span>

1.  <span data-ttu-id="d7a0d-141">Abra o console do Gerenciador do IIS seguindo um destes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-141">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="d7a0d-142">Se já estiver aberto, vá para a etapa seguinte.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-142">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="d7a0d-143">Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-143">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="d7a0d-144">No menu **Ferramentas** no Gerenciador do Servidor, clique em **Gerenciador do IIS (Serviços de Informações da Internet)**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-144">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="d7a0d-145">Na tela **Iniciar** do Windows, digite qualquer parte do nome **Gerenciador do IIS (Serviços de Informações da Internet)**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-145">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="d7a0d-146">Clique no atalho quando ele for exibido nos resultados de **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-146">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="d7a0d-147">No painel da árvore Gerenciador do IIS, selecione o site que está executando o aplicativo Web do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-147">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

3.  <span data-ttu-id="d7a0d-148">No painel **Ações**, em **Gerenciar Site**, clique em **Parar**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-148">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

4.  <span data-ttu-id="d7a0d-149">No painel de árvore, clique com o botão direito do mouse no aplicativo Web no site que está executando o aplicativo Web do Windows PowerShell Web Access e clique em **Remover**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-149">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

5.  <span data-ttu-id="d7a0d-150">No painel de árvore, selecione **Pools de Aplicativos**, selecione a pasta do pool de aplicativos do Windows PowerShell Web Access, clique em **Parar** no painel **Ações** e clique em **Remover** no painel de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-150">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

6.  <span data-ttu-id="d7a0d-151">Feche o Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-151">Close IIS Manager.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="d7a0d-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Observação </span></span><span class="sxs-lookup"><span data-stu-id="d7a0d-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="d7a0d-153">O certificado não é excluído durante a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-153">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="d7a0d-154">Se você tiver criado um certificado autoassinado ou usado um certificado de teste e deseja removê-lo, exclua o certificado no Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-154">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="d7a0d-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 2: Desinstalar o Windows PowerShell Web Access</span></a></span><span class="sxs-lookup"><span data-stu-id="d7a0d-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="d7a0d-156">Para desinstalar o Windows PowerShell Web Access usando o Assistente para Remover Funções e Recursos</span><span class="sxs-lookup"><span data-stu-id="d7a0d-156">To uninstall Windows PowerShell Web Access by using the Remove Roles and Features Wizard</span></span>

1.  <span data-ttu-id="d7a0d-157">Se o Gerenciador do Servidor já estiver aberto, vá para a etapa seguinte.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-157">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="d7a0d-158">Se o Gerenciador do Servidor ainda não estiver aberto, abra-o de uma das maneiras a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-158">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="d7a0d-159">Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-159">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="d7a0d-160">Na tela **Iniciar** do Windows, clique em **Gerenciador do Servidor**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-160">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="d7a0d-161">No menu **Gerenciar**, clique em **Remover Funções e Recursos**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-161">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

3.  <span data-ttu-id="d7a0d-162">Na página **Selecionar servidor de destino**, selecione o servidor ou o VHD offline do qual deseja remover o recurso.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-162">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="d7a0d-163">Para selecionar um VHD offline, primeiro selecione o servidor no qual deseja montar o VHD e depois selecione o arquivo VHD.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-163">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="d7a0d-164">Após selecionar o servidor de destino, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-164">After you have selected the destination server, click **Next**.</span></span>

4.  <span data-ttu-id="d7a0d-165">Clique em **Avançar** novamente para ignorar a página **Remover recursos**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-165">Click **Next** again to skip to the **Remove features** page.</span></span>

5.  <span data-ttu-id="d7a0d-166">Desmarque a caixa de seleção do **Windows PowerShell Web Access** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-166">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

6.  <span data-ttu-id="d7a0d-167">Na página **Confirmar seleções de remoção**, clique em **Remover**.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-167">On the **Confirm removal selections** page, click **Remove**.</span></span>

<span data-ttu-id="d7a0d-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Veja também</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="d7a0d-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="d7a0d-169">[Instalar e usar o Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[Ajuda do Gerenciador do IIS 7.0](https://technet.microsoft.com/library/cc732664.aspx)</span><span class="sxs-lookup"><span data-stu-id="d7a0d-169">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)</span></span>

<span data-ttu-id="d7a0d-170"><span>Mostrar</span>: herdado protegido</span><span class="sxs-lookup"><span data-stu-id="d7a0d-170"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="d7a0d-171"><span class="stdr-votetitle">Esta página foi útil?</span></span><span class="sxs-lookup"><span data-stu-id="d7a0d-171"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="d7a0d-172">Sim Não</span><span class="sxs-lookup"><span data-stu-id="d7a0d-172">Yes No</span></span>

<span data-ttu-id="d7a0d-173">Comentários adicionais?</span><span class="sxs-lookup"><span data-stu-id="d7a0d-173">Additional feedback?</span></span>

<span data-ttu-id="d7a0d-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caracteres restantes</span> Enviar Ignorar isto</span><span class="sxs-lookup"><span data-stu-id="d7a0d-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="d7a0d-175"><span class="stdr-thankyou">Obrigado!</span></span><span class="sxs-lookup"><span data-stu-id="d7a0d-175"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="d7a0d-176"><span class="stdr-appreciate">Agradecemos os seus comentários.</span></span><span class="sxs-lookup"><span data-stu-id="d7a0d-176"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="d7a0d-177">Gerenciar seu Perfil</span><span class="sxs-lookup"><span data-stu-id="d7a0d-177">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="d7a0d-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Comentários sobre o Site</a> Comentários sobre o Site</span><span class="sxs-lookup"><span data-stu-id="d7a0d-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="d7a0d-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="d7a0d-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="d7a0d-180">Conte-nos sobre sua experiência...</span><span class="sxs-lookup"><span data-stu-id="d7a0d-180">Tell us about your experience...</span></span>

<span data-ttu-id="d7a0d-181">A página carregou rápido?</span><span class="sxs-lookup"><span data-stu-id="d7a0d-181">Did the page load quickly?</span></span>

<span data-ttu-id="d7a0d-182"><span> Sim<span> </span></span> <span> Não<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="d7a0d-182"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="d7a0d-183">Você gosta do design da página?</span><span class="sxs-lookup"><span data-stu-id="d7a0d-183">Do you like the page design?</span></span>

<span data-ttu-id="d7a0d-184"><span> Sim<span> </span></span> <span> Não<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="d7a0d-184"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="d7a0d-185">Fale mais</span><span class="sxs-lookup"><span data-stu-id="d7a0d-185">Tell us more</span></span>

-   [<span data-ttu-id="d7a0d-186">Boletim informativo Flash</span><span class="sxs-lookup"><span data-stu-id="d7a0d-186">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="d7a0d-187">Entre em contato conosco</span><span class="sxs-lookup"><span data-stu-id="d7a0d-187">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="d7a0d-188">Política de Privacidade</span><span class="sxs-lookup"><span data-stu-id="d7a0d-188">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="d7a0d-189">Termos de Uso</span><span class="sxs-lookup"><span data-stu-id="d7a0d-189">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="d7a0d-190">Marcas comerciais</span><span class="sxs-lookup"><span data-stu-id="d7a0d-190">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="d7a0d-191">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="d7a0d-191">© 2016 Microsoft</span></span>

<span data-ttu-id="d7a0d-192">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="d7a0d-192">© 2016 Microsoft</span></span>

<span data-ttu-id="d7a0d-193">Código e scripts de terceiros, vinculados ou referenciados neste site, são licenciados por terceiros que têm tal código, não pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-193">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="d7a0d-194">Consulte os termos de uso do ASP.NET Ajax CDN – http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="d7a0d-194">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

