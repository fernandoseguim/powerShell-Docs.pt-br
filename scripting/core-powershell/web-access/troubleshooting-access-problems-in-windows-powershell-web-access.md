---
title: Solucionando problemas de acesso no Windows PowerShell Web Access
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 6366ec9c49f721b758b6a520f68cf2b3c5ee0caf

---

#  Solucionando problemas de acesso no Windows PowerShell Web Access

Atualizado em: 24 de junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

A tabela a seguir identifica alguns problemas comuns que os usuários podem enfrentar ao tentar se conectar a um computador remoto usando o Windows PowerShell Web Access. A tabela também inclui sugestões para resolver problemas.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Problema</p></th>
<th><p>Possível causa e solução</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Falha no logon</p></td>
<td><p>A falha pode ocorrer com base em um dos fatores a seguir.</p>
<ul>
<li><p>Uma regra de autorização que concede ao usuário acesso ao computador (ou uma configuração de sessão específica no computador remoto) não existe. A segurança do Windows PowerShell Web Access é restritiva. Os usuários devem receber acesso explícito a computadores remotos usando regras de autorização. Para obter mais informações, consulte <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access (Regras de autorização e recursos de segurança do Windows PowerShell Web Access)</a> neste guia.</p></li>
<li><p>O usuário não tem o acesso autorizado ao computador de destino. Isso é determinado pelas listas de controle de acesso (ACLs). Para obter mais informações, consulte “Entrando no Windows PowerShell Web Access” em <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Usar o Console do Windows PowerShell baseado na Web</a> ou o <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a> (Blog da Equipe do Windows PowerShell).</p>
<ul>
<li><p>O gerenciamento remoto do Windows PowerShell não deve estar habilitado no computador de destino. Verifique se ele está habilitado no computador ao qual o usuário está tentando se conectar. Para obter mais informações, consulte “How to Configure Your Computer for Remoting” (Como configurar seu computador para comunicação remota) em <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> nos Windows PowerShell About Help Topics (Tópicos da Ajuda sobre o Windows PowerShell).</p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Quando os usuários tentarem entrar no Windows PowerShell Web Access em uma janela do Internet Explorer, eles verão a página <strong>Erro Interno do Servidor</strong> ou o Internet Explorer deixará de responder. Esse problema é específico ao Internet Explorer.</p></td>
<td><p>Isso pode ocorrer com usuários que entraram com um nome de domínio que contém caracteres em chinês, ou quando um ou mais caracteres em chinês fazem parte do nome do servidor de gateway. Para solucionar esse problema, o usuário deve <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">instalar e executar o Internet Explorer 10</a> e depois executar as etapas a seguir.</p>
<ol>
<li><p>Altere a configuração <strong>Modo de Documento</strong> do Internet Explorer para <strong>Padrões do IE10</strong>.</p>
<ol>
<li><p>Pressione <strong>F12</strong> para abrir o console Ferramentas de Desenvolvimento.</p></li>
<li><p>No Internet Explorer 10, clique em <strong>Modo do Navegador</strong> e selecione <strong>Internet Explorer 10</strong>.</p></li>
<li><p>Clique em <strong>Modo de Documento</strong> e clique em <strong>Padrões do IE10</strong>.</p></li>
<li><p>Pressione <strong>F12</strong> novamente para abrir o console Ferramentas de Desenvolvimento.</p></li>
</ol></li>
<li><p>Desabilite a configuração automática de proxy.</p>
<ol>
<li><p>No Internet Explorer 10, clique em <strong>Ferramentas</strong> e clique em <strong>Opções da Internet</strong>.</p></li>
<li><p>Na caixa de diálogo <strong>Opções da Internet</strong>, na guia <strong>Conexões</strong>, clique em <strong>Configurações da LAN</strong>.</p></li>
<li><p>Desmarque a caixa de seleção <strong>Detectar automaticamente as configurações</strong>. Clique em <strong>OK</strong> e clique em <strong>OK</strong> novamente para fechar a caixa de diálogo <strong>Opções da Internet</strong>.</p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>Não é possível conectar a um computador de grupo de trabalho remoto</p></td>
<td><p>Se o computador de destino for membro de um grupo de trabalho, use a sintaxe a seguir para fornecer seu nome de usuário e entrar no computador: &lt;<em>nome_grupotrabalho</em>&gt;\&lt;<em>usuário_nome</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>Não é possível encontrar as ferramentas de gerenciamento do Servidor Web (IIS), embora a função esteja instalada</p></td>
<td><p>Se você instalou o Windows PowerShell Web Access usando o cmdlet <span class="code">Install-WindowsFeature</span>, as ferramentas de gerenciamento não serão instaladas a menos que o parâmetro <span class="code">IncludeManagementTools</span> seja adicionado ao cmdlet. Por exemplo, consulte “To install Windows PowerShell Web Access by using Windows PowerShell cmdlets” (Para instalar o Windows PowerShell Web Access usando cmdlets do Windows PowerShell) em <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a> (Instalar e usar o Windows PowerShell Web Access). Você pode adicionar o console do Gerenciador do IIS e outras ferramentas de gerenciamento do IIS de que precisa selecionando as ferramentas em uma sessão do Assistente de Adição de Funções e Recursos direcionada ao servidor de gateway. O Assistente de Adição de Funções e Recursos é aberto do Gerenciador do Servidor.</p></td>
</tr>
<tr class="odd">
<td><p>O site do Windows PowerShell Web Access não está acessível</p></td>
<td><p>Se o recurso IE ESC (Configuração de Segurança Aprimorada do Internet Explorer) estiver habilitado, você poderá adicionar o site do Windows PowerShell Web Access à lista de sites confiáveis ou desabilitar o IE ESC. Você pode desabilitar o IE ESC no bloco <strong>Propriedades</strong> na página <strong>Servidor Local</strong> no Gerenciador do Servidor.</p></td>
</tr>
<tr class="even">
<td><p>A seguinte mensagem de erro é exibida ao tentar se conectar quando o servidor de gateway é o computador de destino e também está em um grupo de trabalho: <strong>Falha de autorização. Verifique se que você está autorizado a conectar-se ao computador de destino.</strong></p></td>
<td><p>Quando o servidor de gateway também é o servidor de destino, e está em um grupo de trabalho, especifique o nome do usuário, o nome do computador e o nome do grupo de usuários como mostrado na tabela a seguir. Não use um ponto (.) sozinho para representar o nome do computador.</p>
<div>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Cenário</p></th>
<th><p>Parâmetro UserName</p></th>
<th><p>Parâmetro UserGroup</p></th>
<th><p>Parâmetro ComputerName</p></th>
<th><p>Parâmetro ComputerGroup</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>O servidor de gateway está em um domínio</p></td>
<td><p><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em> ou .\<em>user_name</em></p></td>
<td><p><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> ou .\<em>user_group</em></p></td>
<td><p>Nome totalmente qualificado do servidor de gateway ou Localhost</p></td>
<td><p><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> ou .\<em>computer_group</em></p></td>
</tr>
<tr class="even">
<td><p>O servidor de gateway está em um grupo de trabalho</p></td>
<td><p><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em> ou .\<em>user_name</em></p></td>
<td><p><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> ou .\<em>user_group</em></p></td>
<td><p>Nome do servidor</p></td>
<td><p><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> ou .\<em>computer_group</em></p></td>
</tr>
</tbody>
</table>
</div>
<p>Entre em um servidor de gateway como computador de destino usando credenciais formatadas conforme uma das maneiras a seguir.</p>
<ul>
<li><p><em>Server_name</em>\<em>user_name</em></p></li>
<li><p>Localhost\<em>user_name</em></p></li>
<li><p>.\<em>user_name</em></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Uma SID (ID de segurança) é exibida em uma regra de autorização, em vez da sintaxe <em>user_name</em>/<em>computer_name</em> </p></td>
<td><p>A regra não é mais válida ou a consulta aos Serviços de Domínio Active Directory falhou. Uma regra de autorização geralmente não é válida em cenários onde o servidor de gateway já esteve em um grupo de trabalho, mas depois ingressou em um domínio.</p></td>
</tr>
<tr class="even">
<td><p>Não é possível entrar em um computador de destino especificado em regras de autorização como endereço IPv6 com um domínio.</p></td>
<td><p>As regras de autorização não dão suporte a endereços IPv6 no formato de nome de domínio. Para especificar um computador de destino usando um endereço IPv6, use o endereço IPv6 original (que contém dois-pontos) na regra de autorização. Tanto domínios quanto endereços IPv6 numéricos (com dois-pontos) têm suporte como nome do computador de destino na página de entrada do Windows PowerShell Web Access, mas não em regras de autorização. Para obter mais informações sobre endereços IPv6, consulte <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a> (Como o IPv6 Funciona).</p></td>
</tr>
</tbody>
</table>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Consulte Também</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Regras de Autorização e Recursos de Segurança do Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Usar o Console do Windows PowerShell baseado na Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about\_Remote\_Requirements](https://technet.microsoft.com/library/dd315349.aspx)

<span>Mostrar:</span> herdado protegido

<span class="stdr-votetitle">Esta página foi útil?</span>
Sim Não

Comentários adicionais?

<span class="stdr-count"><span class="stdr-charcnt">1500</span> caracteres restantes</span> Enviar Ignorar isso

<span class="stdr-thankyou">Obrigado!</span> <span class="stdr-appreciate">Agradecemos os seus comentários.</span>

[Gerenciar o perfil](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Comentários sobre o Site</a> Comentários sobre o Site

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




<!--HONumber=Jun16_HO4-->


