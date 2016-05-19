#  Desinstalar o Windows PowerShell Web Access

Atualizado em: 24 de junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

Siga as etapas neste tópico para excluir o site e o aplicativo do Windows PowerShell Web Access do servidor de gateway que está executando o Windows Server 2012 R2 ou Windows Server 2012. Antes de começar, notifique os usuários do console baseado na Web a respeito da remoção do site.

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

Antes de desinstalar o Windows PowerShell Web Access do servidor de gateway, execute o cmdlet <span class="code">Uninstall-PswaWebApplication</span> para remover o site e os aplicativos Web do Windows PowerShell Web Access ou use o procedimento do Gerenciador do IIS, [Para excluir o site e os aplicativos Web do Windows PowerShell Web Access usando o Gerenciador do IIS](#BKMK_delsite).

A desinstalação do Windows PowerShell Web Access não desinstala o IIS nem nenhum outro recurso instalado automaticamente porque o Windows PowerShell Web Access precisa deles para ser executado. O processo de desinstalação deixa instalados os recursos dos quais o Windows PowerShell Web Access dependia. É possível desinstalar esses recursos separadamente, se necessário.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Desinstalação recomendada (rápida)</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Os procedimentos nesta seção o ajudarão a desinstalar o aplicativo Web do Windows PowerShell Web Access e o recurso do Windows PowerShell Web Access usando os cmdlets do Windows PowerShell.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 1: excluir o aplicativo Web</span></a>

------------------------------------------------------------------------

Se você tiver especificado seu próprio nome de site personalizado, adicione o parâmetro <span class="code">WebsiteName</span> ao seu comando e especifique o nome do site. Se você tiver usado um aplicativo Web personalizado (não o aplicativo padrão, **pswa**), adicione o parâmetro <span class="code">WebApplicationName</span> ao seu comando e especifique o nome do aplicativo Web.

#### Para excluir o site e os aplicativos Web usando o cmdlet Uninstall-PswaWebApplication

1.  Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell.

    -   Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas.

    -   Na tela **Iniciar**, clique em **Windows PowerShell**.

2.  Digite **Uninstall-PswaWebApplication** e pressione **Enter**.

3.  Se você estiver usando um certificado de teste, adicione o parâmetro <span class="code">DeleteTestCertificate</span> ao cmdlet, como mostrado no exemplo a seguir.

    [Cópia](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "Copy to clipboard.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 2: desinstalar o Windows PowerShell Web Access</span></a>

------------------------------------------------------------------------

#### Para desinstalar o Windows PowerShell Web Access usando cmdlets do Windows PowerShell

1.  Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados. Se já houver uma sessão aberta, vá para a etapa seguinte.

    -   Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.

    -   Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.

2.  Digite o seguinte e pressione **Enter**, em que *computer_name* representa um servidor remoto do qual você deseja remover o Windows PowerShell Web Access. O parâmetro <span class="code">–Restart</span> reinicia automaticamente os servidores de destino se exigido pela remoção.

    [Cópia](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "Copy to clipboard.")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Para remover funções e recursos de um VHD offline, adicione os parâmetros <span class="code">ComputerName</span> e <span class="code">VHD</span>. O parâmetro <span class="code">-ComputerName</span> contém o nome do servidor em que será montado o VHD e o parâmetro <span class="code">-VHD</span> contém o caminho para o arquivo VHD no servidor especificado.

    [Cópia](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "Copy to clipboard.")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess –VHD <path> -ComputerName <computer_name> -Restart

3.  Quando a remoção for concluída, verifique se você removeu o Windows PowerShell Web Access abrindo a página **Todos os Servidores** no Gerenciador do Servidor, selecionando um servidor do qual você removeu o recurso e exibindo o bloco **Funções e Recursos** na página do servidor selecionado. Você também pode executar o cmdlet <span class="code">Get-WindowsFeature</span> de destino no servidor selecionado (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) para exibir uma lista de funções e recursos que estão instalados no servidor.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Desinstalação personalizada</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Os procedimentos nesta seção o ajudarão a desinstalar o aplicativo Web do Windows PowerShell Web Access e o recurso do Windows PowerShell Web Access usando o Assistente de Remoção de Funções e Recursos no Gerenciador do Servidor e o console do Gerenciador do IIS.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 1: excluir o aplicativo Web</span></a>

------------------------------------------------------------------------

#### Para excluir o site e os aplicativos Web do Windows PowerShell Web Access usando o Gerenciador do IIS

1.  Abra o console do Gerenciador do IIS seguindo um destes procedimentos. Se já estiver aberto, vá para a etapa seguinte.

    -   Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows. No menu **Ferramentas** no Gerenciador do Servidor, clique em **Gerenciador do IIS (Serviços de Informações da Internet)**.

    -   Na tela **Iniciar** do Windows, digite qualquer parte do nome **Gerenciador do IIS (Serviços de Informações da Internet)**. Clique no atalho quando ele for exibido nos resultados de **Aplicativos**.

2.  No painel da árvore Gerenciador do IIS, selecione o site que está executando o aplicativo Web do Windows PowerShell Web Access.

3.  No painel **Ações**, em **Gerenciar Site**, clique em **Parar**.

4.  No painel de árvore, clique com o botão direito do mouse no aplicativo Web no site que está executando o aplicativo Web do Windows PowerShell Web Access e clique em **Remover**.

5.  No painel de árvore, selecione **Pools de Aplicativos**, selecione a pasta do pool de aplicativos do Windows PowerShell Web Access, clique em **Parar** no painel **Ações** e clique em **Remover** no painel de conteúdo.

6.  Feche o Gerenciador do IIS.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Observação </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>O certificado não é excluído durante a desinstalação. Se você tiver criado um certificado autoassinado ou usado um certificado de teste e deseja removê-lo, exclua o certificado no Gerenciador do IIS.</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Etapa 2: desinstalar o Windows PowerShell Web Access</span></a>

------------------------------------------------------------------------

#### Para desinstalar o Windows PowerShell Web Access usando o Assistente para Remover Funções e Recursos

1.  Se o Gerenciador do Servidor já estiver aberto, vá para a etapa seguinte. Se o Gerenciador do Servidor ainda não estiver aberto, abra-o de uma das maneiras a seguir.

    -   Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.

    -   Na tela **Iniciar** do Windows, clique em **Gerenciador do Servidor**.

2.  No menu **Gerenciar**, clique em **Remover Funções e Recursos**.

3.  Na página **Selecionar servidor de destino**, selecione o servidor ou o VHD offline do qual deseja remover o recurso. Para selecionar um VHD offline, primeiro selecione o servidor no qual deseja montar o VHD e depois selecione o arquivo VHD. Após selecionar o servidor de destino, clique em **Avançar**.

4.  Clique em **Avançar** novamente para ignorar a página **Remover recursos**.

5.  Desmarque a caixa de seleção do **Windows PowerShell Web Access** e clique em **Avançar**.

6.  Na página **Confirmar seleções de remoção** clique em **Remover**.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Consulte Também</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Instalar e usar o Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[Ajuda do Gerenciador do IIS 7.0](https://technet.microsoft.com/library/cc732664.aspx)

<span>Mostrar:</span> herdado protegido

<span class="stdr-votetitle">Esta página foi útil?</span>
Sim
Não

Comentários adicionais?

<span class="stdr-count"><span class="stdr-charcnt">1500</span> caracteres restantes</span>
Enviar
Ignorar

<span class="stdr-thankyou">Obrigado!</span> <span class="stdr-appreciate">Agradecemos seus comentários.</span>

[Gerenciar o perfil](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Comentários do site</a>
Comentários do site

<a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a>

Conte-nos sobre sua experiência...

A página carregou rápido?

<span> Sim<span> </span></span> <span> Não<span> </span></span>

Você gosta do design da página?

<span> Sim<span> </span></span> <span> Não<span> </span></span>

Fale mais

-   [Boletim informativo Flash](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [Entre em contato conosco](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [Política de privacidade](https://privacy.microsoft.com/privacystatement)
-   |
-   [Termos de uso](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [Marcas](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

© 2016 Microsoft

© 2016 Microsoft

Código e scripts de terceiros, vinculados ou referenciados neste site, são licenciados por terceiros que têm tal código, não pela Microsoft. Consulte os termos de uso de ASP.NET Ajax CDN – http://www.asp.net/ajaxlibrary/CDN.ashx.
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />


<!--HONumber=May16_HO2-->


