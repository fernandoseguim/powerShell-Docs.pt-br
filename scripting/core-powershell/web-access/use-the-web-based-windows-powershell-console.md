#  Usar o Console do Windows PowerShell baseado na Web

Atualizado em: 24 de junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

O Windows PowerShell® Web Access permite que usuários do Windows PowerShell® entrem no site protegido pelo protocolo SSL para usar sessões, cmdlets e scripts do Windows PowerShell para gerenciar um computador remoto. Como o console do Windows PowerShell é executado em um navegador da Web, é possível abri-lo de vários dispositivos clientes, incluindo celulares, tablets, quiosques de computação públicos, computadores laptop ou computadores compartilhados ou emprestados. O console do Windows PowerShell baseado na Web é destinado a um computador remoto especificado por usuários como parte do processo de entrada. Este tópico descreve como entrar e iniciar usando o console baseado na Web do Windows PowerShell Web Access.

Este tópico não descreve como usar o Windows PowerShell ou executar cmdlets ou scripts. Para obter informações sobre como usar o Windows PowerShell e os recursos de script, consulte a seção Consulte também no fim deste tópico.

Neste tópico:

-   [Navegadores e dispositivos clientes compatíveis](#BKMK_browser)

-   [Entrando no Windows PowerShell Web Access](#BKMK_sign)

-   [Saída e tempo limite](#BKMK_timeout)

-   [Diferenças no console do Windows PowerShell baseado na Web](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

O Windows PowerShell Web Access dá suporte aos seguintes navegadores da Internet. Embora navegadores móveis não tenham suporte oficialmente, muitos poderão executar o console do Windows PowerShell baseado na Web. É provável que outros navegadores que aceitam cookies, executam JavaScript e abrem sites HTTPS funcionam, mas não foram oficialmente testados.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navegadores de desktop compatíveis</span></a>

------------------------------------------------------------------------

-   Windows® Internet Explorer® para Microsoft Windows® 8.0, 9.0, 10.0 e 11.0

-   Mozilla Firefox® 10.0.2

-   Google Chrome™ 17.0.963.56m para Windows

-   Apple Safari® 5.1.2 para Windows

-   Apple Safari 5.1.2 para Mac OS®

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Dispositivos ou navegadores móveis minimamente testados</span></a>

------------------------------------------------------------------------

-   Windows Phone 7 e 7.5

-   Navegador Google Android WebKit 3.1 Android 2.2.1 (Kernel 2.6)

-   Apple Safari para iPhone com sistema operacional 5.0.1

-   Apple Safari para iPad 2 com sistema operacional 5.0.1

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisitos de navegador</span></a>

------------------------------------------------------------------------

Para usar o console do Windows PowerShell Web Access baseado na Web, os navegadores devem executar os procedimentos a seguir.

-   Permitir cookies do site do gateway do Windows PowerShell Web Access.

-   Ser capazes de abrir e ler páginas HTTPS.

-   Abrir e executar sites que usam JavaScript.

<a href="" id="BKMK_sign"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Entrando no Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

O administrador do Windows PowerShell Web Access deve fornecer uma URL que é o endereço do site do gateway do Windows PowerShell Web Access da sua organização. Por padrão, o endereço do site é https://&lt;server_name&gt;/pswa. Antes de entrar no Windows PowerShell Web Access, tenha o nome ou o endereço IP do computador remoto que deseja gerenciar. Você deve ser um usuário autorizado no computador remoto e ele deve estar configurado para permitir gerenciamento remoto. Para obter mais informações sobre como configurar o computador para permitir o gerenciamento remoto, consulte [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx) (Habilitar e usar comandos remotos no Windows PowerShell). O método mais simples de configurar o computador para permitir gerenciamento remoto é executar o cmdlet **Enable-PSRemoting -force** no computador, em uma sessão do Windows PowerShell aberta com direitos de usuário elevados (**Executar como Administrador**)).

### Para entrar no Windows PowerShell Web Access

1.  Abra o site do Windows PowerShell Web Access em uma janela ou guia do navegador da Internet.

2.  Na página de entrada do Windows PowerShell Web Access, forneça o nome de usuário de rede, a senha e o nome do computador a ser gerenciado (e em que você é um usuário autorizado). Se o administrador do Windows PowerShell Web Access o instruir para usar um URI para um site ou servidor proxy personalizado, em vez de um nome do computador, selecione **URI de Conexão** no campo **Tipo de conexão** e forneça o URI.

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
    <td><ul>
    <li><p>Se o computador de destino estiver em um grupo de trabalho, use a sintaxe a seguir para fornecer seu nome de usuário e entrar no computador: &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</p></li>
    <li><p>Se o computador de destino for o servidor de gateway, você poderá especificar <strong>localhost</strong> no campo <strong>Nome do computador</strong>.</p></li>
    <li><p>Se o computador de destino for o servidor de gateway e o servidor de gateway estiver em um grupo de trabalho, você poderá usar <strong>localhost</strong> no campo <strong>Nome do computador</strong>, mas não usar localhost\&lt;<em>user_name</em>&gt; no campo <strong>Nome de usuário</strong>. Você deve usar &lt;<em>nome do grupo de trabalho</em>&gt;\&lt;<em>user_name</em>&gt;.</p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  A seção **Configurações de Conexão Opcionais** está relacionada aos requisitos de autorização do computador remoto que você deseja gerenciar. Para obter mais informações sobre os parâmetros equivalentes às configurações de conexão opcionais, consulte [Enter-PSSession cmdlet Help](https://technet.microsoft.com/library/dd315384.aspx) (Ajuda do cmdlet Enter-PSSession).

    Geralmente, as credenciais usadas para passar pelo gateway do Windows PowerShell Web Access são as mesmas reconhecidas pelo computador remoto que você deseja gerenciar. No entanto, se você desejar usar credenciais diferentes para gerenciar o computador remoto especificado na etapa 2, expanda a seção **Configurações de Conexão Opcionais** e forneça as credenciais alternativas. Caso contrário, ignore a etapa 6.

4.  Se o administrador do Windows PowerShell Web Access tiver criado uma configuração de sessão personalizada para usuários do Windows PowerShell Web Access, digite o nome da configuração da sessão no campo **Nome da configuração**. Para obter mais informações sobre configurações de sessão, consulte [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) no site da Microsoft.

5.  Mantenha o **Tipo de autenticação** definido como **Padrão**, a menos que você tenha sido instruído a fazer o contrário pelo administrador do Windows PowerShell Web Access.

6.  Clique em **Entrar**.

<a href="" id="BKMK_timeout"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Saída e tempo limite</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Qualquer uma das ações a seguir encerra uma sessão do Windows PowerShell baseada na Web.

-   Clicar em **Sair** no canto inferior direito do console. (Windows Server 2012 apenas)

-   Clique em **Salvar** ou **Sair** no canto inferior direito do console (Windows Server 2012 R2 apenas). Clicar em **Salvar** salva e fecha a sessão do Windows PowerShell Web Access. Você pode se reconectar à sessão mais tarde. Quando você entra no Windows PowerShell Web Access novamente, o Windows PowerShell Web Access exibe uma lista de suas sessões salvas. Você pode selecionar e se reconectar a uma sessão salva ou iniciar uma nova sessão. O número máximo de sessões abertas, salvas e ativas, a que os usuários têm permissão é configurado pelo administrador do gateway.

    Clicar em **Sair** faz com que você saia da Windows PowerShell Web Access sessão sem salvá-la.

-   Tentar entrar para gerenciar um computador remoto diferente na mesma sessão de navegador ou em uma nova guia da mesma sessão de navegador. (Isso não se aplicará se o servidor de gateway estiver executando Windows Server 2012 R2; Windows PowerShell Web Access em execução em Windows Server 2012 R2 permite várias sessões de usuário em novas guias na mesma sessão do navegador.) Para obter mais informações sobre como usar mais de uma sessão ativa no mesmo computador, consulte “Connecting to multiple target computers simultaneously” (Conectando a vários computadores de destino simultaneamente) na seção [Limitations of the web-based console](#BKMK_limits) (Limitações do console baseado na Web) deste tópico.

-   20 minutos de inatividade na sessão. O administrador do gateway pode personalizar o período de tempo limite de inatividade. Para obter mais informações, consulte [Session management](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt) (Gerenciamento de sessão).

    -   Se os usuários forem desconectados de sessões no console baseado na Web por causa de erros de rede ou outros desligamentos não planejados ou falhas, e não porque você fechou a sessão, as sessões do Windows PowerShell Web Access continuam em execução, conectada ao computador de destino, até decorrer o tempo limite do lado do cliente. Por padrão, esse período de tempo limite é de 20 minutos e é configurado pelo administrador do gateway. A sessão é desconectada após um padrão de 20 minutos ou após o período de tempo limite especificado pelo administrador do gateway, o que for menor.

        Se o servidor de gateway estiver executando o Windows Server 2012 R2, o Windows PowerShell Web Access permitirá que os usuários se reconectem a sessões salvas em um momento posterior, mas você não poderá ver ou se reconectar a sessões salvas até ter expirado o período de tempo limite especificado pelo administrador do gateway.

-   Fechar a janela ou a guia do navegador.

-   Desativar o dispositivo cliente em que o navegador está executando ou desconectá-lo da rede.

-   Executar o comando **Sair** no console Web. Esse comando não funciona se a configuração de sessão a que você está conectado estiver definida para dar suporte ao modo [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) ou estiver em um runspace restrito.

Se desejar entrar novamente, abra a página da Web do Windows PowerShell Web Access outra vez e entre seguindo as etapas descritas em [Para entrar no Windows PowerShell Web Access](#BKMK_signin) neste tópico.

<a href="" id="BKMK_web"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Diferenças no console do Windows PowerShell baseado na Web</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Depois de entrar no Windows PowerShell Web Access, um console do Windows PowerShell baseado na web é aberto na janela ou guia do navegador. Como o console está conectado ao computador especificado durante o processo de entrada, somente aqueles cmdlets ou scripts do Windows PowerShell disponíveis no computador remoto podem ser usados no console. Esta seção descreve outras limitações de consoles do Windows PowerShell Web Access e as diferenças entre os consoles do Windows PowerShell Web Access e o console do **PowerShell.exe** instalado.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Disparidade funcional com o PowerShell.exe</span></a>

------------------------------------------------------------------------

A maioria das funcionalidades do host do Windows PowerShell está disponível no console baseado na Web do Windows PowerShell Web Access, mas há alguns recursos que não estão disponíveis.

-   <span class="label">Exibição do andamento aninhado.</span>  O Windows PowerShell Web Access exibe uma GUI de andamento para os cmdlets que informam o andamento, mas apenas informações de andamento de nível superior são exibidas.

-   <span class="label">Modificação da cor de entrada.</span>  A cor de entrada (do primeiro plano e da tela de fundo) não pode ser alterada. É possível alterar o estilo das mensagens de saída, de aviso, detalhadas e de erro executando um script.

-   <span class="label">PSHostRawUserInterface.</span>  O Windows PowerShell Web Access é implementado sobre o gerenciamento remoto do Windows PowerShell e usa um runspace remoto. O Windows PowerShell Web Access não implementa alguns métodos nessa interface; por exemplo, qualquer comando que grava no console do Windows. Comandos como **PowerTab** não funcionam no Windows PowerShell Web Access.

-   <span class="label">Teclas de função.</span>  O Windows PowerShell Web Access não dá suporte a algumas teclas de função do, em muitos casos, porque os comandos são reservados pelo navegador.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Tecla de função sem suporte</p></th>
<th><p>Ação</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ctrl+C</p></td>
<td><p>No Windows PowerShell Web Access, <strong>Ctrl + C</strong> é usado pelo navegador para copiar o conteúdo. O console oferece um botão <strong>Cancelar</strong> e os usuários também podem usar <strong>Ctrl+Q</strong> para cancelar os comandos.</p></td>
</tr>
<tr class="even">
<td><p>Alt-espaço, e, l</p></td>
<td><p>Rola pelo buffer da tela</p></td>
</tr>
<tr class="odd">
<td><p>Alt+espaço, e, f</p></td>
<td><p>Procura texto no buffer da tela</p></td>
</tr>
<tr class="even">
<td><p>Alt+espaço, e, k</p></td>
<td><p>Seleciona o texto a ser copiado do buffer da tela</p></td>
</tr>
<tr class="odd">
<td><p>Alt+espaço, e, p</p></td>
<td><p>Cola o conteúdo da área de transferência no console do Windows PowerShell</p></td>
</tr>
<tr class="even">
<td><p>Alt+espaço, c</p></td>
<td><p>Fecha o console do Windows PowerShell</p></td>
</tr>
<tr class="odd">
<td><p>Ctrl+Break</p></td>
<td><p>Força a janela do Windows PowerShell a fechar</p></td>
</tr>
<tr class="even">
<td><p>Ctrl+Home</p></td>
<td><p>Exclui do início da linha de comando atual</p></td>
</tr>
<tr class="odd">
<td><p>Ctrl+End</p></td>
<td><p>Exclui para o fim da linha de comando</p></td>
</tr>
<tr class="even">
<td><p>F1</p></td>
<td><p>Move o cursor um caractere para a direita na linha de comando</p></td>
</tr>
<tr class="odd">
<td><p>F2</p></td>
<td><p>Cria um novo comando copiando o último comando até o caractere digitado</p></td>
</tr>
<tr class="even">
<td><p>F3</p></td>
<td><p>Preenche a linha de comando com o conteúdo da última linha de comando</p></td>
</tr>
<tr class="odd">
<td><p>F4</p></td>
<td><p>Exclui caracteres a partir da posição do cursor</p></td>
</tr>
<tr class="even">
<td><p>F5</p></td>
<td><p>Volta na verificação do histórico de comandos. Para acessar comandos no histórico de comandos no Windows PowerShell Web Access, clique nos botões de rolagem do <strong>Histórico</strong> no console baseado na Web.</p></td>
</tr>
<tr class="odd">
<td><p>F7</p></td>
<td><p>Selecione interativamente um comando do histórico de comandos</p></td>
</tr>
<tr class="even">
<td><p>F8</p></td>
<td><p>Verifica os comandos de exibição do histórico que correspondem ao texto atual</p></td>
</tr>
<tr class="odd">
<td><p>F9</p></td>
<td><p>Executa um comando com numeração específica do histórico</p></td>
</tr>
<tr class="even">
<td><p>Page Up</p></td>
<td><p>Executa o primeiro comando no histórico</p></td>
</tr>
<tr class="odd">
<td><p>Page Down</p></td>
<td><p>Executa o último comando no histórico</p></td>
</tr>
<tr class="even">
<td><p>Alt+F7</p></td>
<td><p>Limpa a lista do histórico de comandos</p></td>
</tr>
</tbody>
</table>

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitações do console baseado na Web</span></a>

------------------------------------------------------------------------

-   <span class="label">Salto duplo.</span>   Você pode se deparar com a limitação de salto duplo (ou se conectar a um segundo computador por meio da primeira conexão) se tentar criar ou trabalhar em uma nova sessão usando o Windows PowerShell Web Access. O Windows PowerShell Web Access usa um runspace remoto e, no momento, o **PowerShell.exe** não dá suporte ao estabelecimento de uma conexão remota com um segundo computador de um runspace remoto. Se você tentar se conectar a um segundo computador remoto por meio de uma conexão existente usando o cmdlet **Enter-PSSession**, por exemplo, vários erros poderão ser gerados, como “Não é possível obter recursos da rede”.

    Para evitar erros de salto, o administrador deve configurar a autenticação CredSSP no ambiente de rede da organização. Para obter mais informações sobre a configuração da autenticação CredSSP, consulte [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) (CredSSP para segundo salto remoto) no site da Microsoft. Também é possível fornecer credenciais explícitas quando você deseja gerenciar um segundo computador remoto, é pouco provável que as credenciais implícitas permitam o segundo salto.

-   O Windows PowerShell Web Access usa e tem as mesmas limitações que uma sessão remota do Windows PowerShell. Comandos que chamam diretamente APIs do console do Windows, como aquelas para editores baseados no console ou programas de menu baseados em texto, não funcionam porque os comandos não leem nem gravam pipes padrão de entrada, de saída e de erro. Portanto, os comandos que inicializam um arquivo executável, como **notepad.exe**, ou exibem uma GUI, como <span class="code">OpenGridView</span> ou <span class="code">ogv</span>, não funcionam. Sua experiência é afetada por este comportamento, para você, parece que o Windows PowerShell Web Access não está respondendo ao seu comando.

-   O preenchimento da guia não funciona em uma configuração de sessão com runspace restrito ou que está no modo **NoLanguage**. Embora os administradores possam configurar uma sessão para aceitar o preenchimento da guia, isso não é incentivado por motivos de segurança, pois pode expor as informações a seguir a usuários não autorizados.

    -   Caminhos internos do sistema de arquivos

    -   Pastas compartilhadas em computadores internos

    -   Variáveis no runspace

    -   Tipos carregados ou namespaces .NET Framework

    -   Variáveis de ambiente

-   Os usuários que entraram em uma configuração de sessão **NoLanguage** ou em um runspace restrito no Windows PowerShell Web Access não podem executar o comando **Sair** para encerrar a sessão. Para sair, os usuários devem clicar em **Sair** na página do console.

-   <span class="label">Conectando a vários computadores de destino simultaneamente.</span>   Se o servidor de gateway estiver executando o Windows Server 2012, o Windows PowerShell Web Access permitirá apenas uma conexão de computador remoto por sessão de navegador; ele não permitirá que os usuários entrem uma vez e se conectem a vários computadores remotos usando guias separadas do navegador. Ao abrir uma nova guia ou uma nova janela de navegador, o Windows PowerShell Web Access solicita que você desconecte a sessão atual e inicie uma nova sessão, de forma que possa se conectar ao novo (ou ao mesmo) computador remoto. No entanto, se duas ou mais sessões separadas para computadores remotos diferentes forem desejadas, um recurso no Internet Explorer permitirá criar uma nova sessão. Para iniciar uma nova sessão de navegador no Internet Explorer, pressione **ALT**, abra o menu **Arquivo** e selecione **Nova Sessão**. Em seguida, abra o site do Windows PowerShell Web Access na nova sessão e entre para acessar outro computador remoto.

    Quando o gateway do Windows PowerShell Web Access estiver em execução no Windows Server 2012 R2, os usuários poderão abrir várias conexões com computadores remotos em guias diferentes do navegador. Se você quiser abrir mais de uma conexão a um computador remoto usando o console do Windows PowerShell baseado na Web, entre em contato com o administrador de gateway do Windows PowerShell Web Access para ver se este recurso tem suporte pelo servidor de gateway.

-   <span class="label">Sessões persistentes do Windows PowerShell (reconexão).</span>   Depois que atingir o tempo limite do gateway do Windows PowerShell Web Access, a conexão remota entre o gateway e o computador de destino será fechada. Com isso, todos os cmdlets ou scripts atualmente presentes no processo são interrompidos. Você é incentivado a usar a infraestrutura do Windows PowerShell **-Job** quando estiver executando tarefas longas, para que seja possível iniciar trabalhos, desconectar do computador, reconectar posteriormente e ter trabalhos persistentes. Outro benefício de usar cmdlets **-Job** é que você pode iniciá-los usando o Windows PowerShell Web Access, desconectar-se e reconectar-se posteriormente, executando o Windows PowerShell Web Access ou outro host (como o ISE (Ambiente de Script Integrado) do Windows PowerShell®).

-   <span class="label">Redimensionamento do console.</span>   A janela de console **PowerShell.exe** pode ser redimensionada das três maneiras a seguir.

    -   Arraste e ajuste o tamanho da janela do console com o mouse

    -   Altere as propriedades de altura e largura usando uma GUI para as propriedades do console

    -   Altere a altura e largura das janelas do console com um cmdlet

        A janela do console do Windows PowerShell Web Access pode ser configurada usando os cmdlets da seguinte forma. No exemplo a seguir, um usuário alterar a largura do console do Windows PowerShell Web Access para **20**.

        [Cópia](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "Copy to clipboard.")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        É possível alterar a altura do console de maneira similar.

        Exemplos adicionais para personalizar a exibição do console estão disponíveis no [Blog da Equipe do Windows PowerShell](http://blogs.msdn.com/b/powershell/).

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Consulte Também</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Referência de cmdlets do Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell no Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[Repositório da Central de Scripts do TechNet](http://gallery.technet.microsoft.com/scriptcenter)
[Central de Scripts - Olá, pessoal de script!](https://technet.microsoft.com/scriptcenter)
[Blog da equipe do Windows PowerShell](http://blogs.msdn.com/b/powershell/)

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


