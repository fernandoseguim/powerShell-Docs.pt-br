---
ms.date: 2017-08-23
keywords: PowerShell, cmdlet
title: desinstalar o windows powershell web access
ms.openlocfilehash: b6e6a2374e6b4b2be8742019c5f1e4d5b5d1abe3
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2017
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="5f190-103">Desinstalar o Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="5f190-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="5f190-104">Atualizado em: 24 de junho de 2013</span><span class="sxs-lookup"><span data-stu-id="5f190-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="5f190-105">Aplica-se a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="5f190-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="5f190-106">As etapas neste tópico removem o site do Windows PowerShell Web Access e o aplicativo correspondente do servidor de gateway, no qual ele está instalado.</span><span class="sxs-lookup"><span data-stu-id="5f190-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="5f190-107">Notificar os usuários</span><span class="sxs-lookup"><span data-stu-id="5f190-107">Notify users</span></span>

<span data-ttu-id="5f190-108">Antes de começar, notifique os usuários do console baseado na Web a respeito da remoção do site.</span><span class="sxs-lookup"><span data-stu-id="5f190-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="5f190-109">A desinstalação do Windows PowerShell Web Access não desinstala o IIS nem nenhum outro recurso instalado automaticamente porque o Windows PowerShell Web Access precisa deles para ser executado.</span><span class="sxs-lookup"><span data-stu-id="5f190-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="5f190-110">O processo de desinstalação deixa instalados os recursos dos quais o Windows PowerShell Web Access dependia. É possível desinstalar esses recursos separadamente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="5f190-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="5f190-111">Desinstalação recomendada (rápida)</span><span class="sxs-lookup"><span data-stu-id="5f190-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="5f190-112">Os procedimentos nesta seção ajudam a desinstalar:</span><span class="sxs-lookup"><span data-stu-id="5f190-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="5f190-113">o aplicativo Web Windows PowerShell Web Access e</span><span class="sxs-lookup"><span data-stu-id="5f190-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="5f190-114">o recurso do Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="5f190-114">the Windows PowerShell Web Access feature</span></span>
 
<span data-ttu-id="5f190-115">usando cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f190-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="5f190-116">Etapa 1: Excluir o aplicativo Web usando cmdlets</span><span class="sxs-lookup"><span data-stu-id="5f190-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="5f190-117">Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f190-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="5f190-118">Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="5f190-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="5f190-119">Na tela **Iniciar** do Windows, clique em **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="5f190-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="5f190-120">Digite `Uninstall-PswaWebApplication` e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="5f190-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="5f190-121">Se você tiver especificado o seu próprio nome de site personalizado, adicione o parâmetro `-WebsiteName` ao seu comando e especifique o nome do site.</span><span class="sxs-lookup"><span data-stu-id="5f190-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="5f190-122">Se você tiver usado um aplicativo Web personalizado (não o aplicativo padrão, **pswa**), adicione o parâmetro `-WebApplicationName` ao comando e especifique o nome do aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="5f190-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="5f190-123">Se você estiver usando um certificado de teste, adicione o parâmetro `DeleteTestCertificate` ao cmdlet, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f190-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="5f190-124">Etapa 2: Desinstalar o Windows PowerShell Web Access usando cmdlets</span><span class="sxs-lookup"><span data-stu-id="5f190-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="5f190-125">Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados.</span><span class="sxs-lookup"><span data-stu-id="5f190-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="5f190-126">Se já houver uma sessão aberta, vá para a etapa seguinte.</span><span class="sxs-lookup"><span data-stu-id="5f190-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="5f190-127">Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="5f190-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="5f190-128">Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="5f190-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="5f190-129">Digite o seguinte e pressione **Enter**, em que *computer_name* representa um servidor remoto do qual você deseja remover o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="5f190-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="5f190-130">O parâmetro `-Restart` reinicia automaticamente os servidores de destino quando exigido pela remoção.</span><span class="sxs-lookup"><span data-stu-id="5f190-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="5f190-131">Para remover funções e recursos de um VHD offline, adicione os parâmetros `-ComputerName` e `-VHD`.</span><span class="sxs-lookup"><span data-stu-id="5f190-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="5f190-132">O parâmetro `-ComputerName` contém o nome do servidor em que será montado o VHD, e o parâmetro `-VHD` contém o caminho para o arquivo VHD no servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="5f190-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="5f190-133">Quando a remoção for concluída, verifique se você removeu o Windows PowerShell Web Access abrindo a página **Todos os Servidores** no Gerenciador do Servidor, selecionando um servidor do qual você removeu o recurso e exibindo o bloco **Funções e Recursos** na página do servidor selecionado.</span><span class="sxs-lookup"><span data-stu-id="5f190-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="5f190-134">Você também pode executar o cmdlet `Get-WindowsFeature` direcionado ao servidor selecionado (Get-WindowsFeature – ComputerName &lt;*nome_do_computador*&gt;) para exibir uma lista de funções e recursos que estão instalados no servidor.</span><span class="sxs-lookup"><span data-stu-id="5f190-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="5f190-135">Desinstalação personalizada</span><span class="sxs-lookup"><span data-stu-id="5f190-135">Custom uninstallation</span></span>

<span data-ttu-id="5f190-136">Os procedimentos nesta seção o ajudarão a desinstalar o aplicativo Web do Windows PowerShell Web Access e o recurso do Windows PowerShell Web Access usando o Assistente de Remoção de Funções e Recursos no Gerenciador do Servidor e o console do Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="5f190-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="5f190-137">Etapa 1: Excluir o aplicativo Web usando o Gerenciador do IIS</span><span class="sxs-lookup"><span data-stu-id="5f190-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="5f190-138">Abra o console do Gerenciador do IIS seguindo um destes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="5f190-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="5f190-139">Se já estiver aberto, vá para a etapa seguinte.</span><span class="sxs-lookup"><span data-stu-id="5f190-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="5f190-140">Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="5f190-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="5f190-141">No menu **Ferramentas** no Gerenciador do Servidor, clique em **Gerenciador do IIS (Serviços de Informações da Internet)**.</span><span class="sxs-lookup"><span data-stu-id="5f190-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="5f190-142">Na tela **Iniciar** do Windows, digite qualquer parte do nome **Gerenciador do IIS (Serviços de Informações da Internet)**.</span><span class="sxs-lookup"><span data-stu-id="5f190-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="5f190-143">Clique no atalho quando ele for exibido nos resultados de **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="5f190-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="5f190-144">No painel da árvore Gerenciador do IIS, selecione o site que está executando o aplicativo Web do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="5f190-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="5f190-145">No painel **Ações**, em **Gerenciar Site**, clique em **Parar**.</span><span class="sxs-lookup"><span data-stu-id="5f190-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="5f190-146">No painel de árvore, clique com o botão direito do mouse no aplicativo Web no site que está executando o aplicativo Web do Windows PowerShell Web Access e clique em **Remover**.</span><span class="sxs-lookup"><span data-stu-id="5f190-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="5f190-147">No painel de árvore, selecione **Pools de Aplicativos**, selecione a pasta do pool de aplicativos do Windows PowerShell Web Access, clique em **Parar** no painel **Ações** e clique em **Remover** no painel de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5f190-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="5f190-148">Feche o Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="5f190-148">Close IIS Manager.</span></span>

> <span data-ttu-id="5f190-149">![Observação de aviso](images/SecurityNote.jpeg)**Observação**:</span><span class="sxs-lookup"><span data-stu-id="5f190-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="5f190-150">O certificado não é excluído durante a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="5f190-150">The certificate is not deleted during uninstallation.</span></span> 
>
> <span data-ttu-id="5f190-151">Se você tiver criado um certificado autoassinado ou usado um certificado de teste e deseja removê-lo, exclua o certificado no Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="5f190-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span> 

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="5f190-152">Etapa 2: Desinstalar o Windows PowerShell Web Access usando o Assistente para Remover Funções e Recursos</span><span class="sxs-lookup"><span data-stu-id="5f190-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="5f190-153">Se o Gerenciador do Servidor já estiver aberto, vá para a etapa seguinte.</span><span class="sxs-lookup"><span data-stu-id="5f190-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="5f190-154">Se o Gerenciador do Servidor ainda não estiver aberto, abra-o de uma das maneiras a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f190-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="5f190-155">Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="5f190-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="5f190-156">Na tela **Iniciar** do Windows, clique em **Gerenciador do Servidor**.</span><span class="sxs-lookup"><span data-stu-id="5f190-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="5f190-157">No menu **Gerenciar**, clique em **Remover Funções e Recursos**.</span><span class="sxs-lookup"><span data-stu-id="5f190-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="5f190-158">Na página **Selecionar servidor de destino**, selecione o servidor ou o VHD offline do qual deseja remover o recurso.</span><span class="sxs-lookup"><span data-stu-id="5f190-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="5f190-159">Para selecionar um VHD offline, primeiro selecione o servidor no qual deseja montar o VHD e depois selecione o arquivo VHD.</span><span class="sxs-lookup"><span data-stu-id="5f190-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="5f190-160">Após selecionar o servidor de destino, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5f190-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="5f190-161">Clique em **Avançar** novamente para ignorar a página **Remover recursos**.</span><span class="sxs-lookup"><span data-stu-id="5f190-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="5f190-162">Desmarque a caixa de seleção do **Windows PowerShell Web Access** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5f190-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="5f190-163">Na página **Confirmar seleções de remoção**, clique em **Remover**.</span><span class="sxs-lookup"><span data-stu-id="5f190-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f190-164">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5f190-164">See Also</span></span>

- [<span data-ttu-id="5f190-165">Instalar e usar o Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="5f190-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="5f190-166">Ajuda do Gerenciador do IIS 7.0</span><span class="sxs-lookup"><span data-stu-id="5f190-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)
