---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Solucionando problemas de acesso no Windows PowerShell Web Access
ms.openlocfilehash: c10e19b177110ff62d44f28b6a523380b55b79e0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
#  <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="90fe3-103">Solucionando problemas de acesso no Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="90fe3-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="90fe3-104">Atualizado em: 24 de junho de 2013</span><span class="sxs-lookup"><span data-stu-id="90fe3-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="90fe3-105">Aplica-se a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="90fe3-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

<span data-ttu-id="90fe3-106">A tabela a seguir identifica alguns problemas comuns que os usuários podem enfrentar ao tentar se conectar a um computador remoto usando o Windows PowerShell Web Access. A tabela também inclui sugestões para resolver problemas.</span><span class="sxs-lookup"><span data-stu-id="90fe3-106">The following table identifies some common problems that users might experience when they are attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="90fe3-107">Problema</span><span class="sxs-lookup"><span data-stu-id="90fe3-107">Problem</span></span></p></th>
<th><p><span data-ttu-id="90fe3-108">Possível causa e solução</span><span class="sxs-lookup"><span data-stu-id="90fe3-108">Possible cause and solution</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="90fe3-109">Falha no logon</span><span class="sxs-lookup"><span data-stu-id="90fe3-109">Sign-in failure</span></span></p></td>
<td><p><span data-ttu-id="90fe3-110">A falha pode ocorrer com base em um dos fatores a seguir.</span><span class="sxs-lookup"><span data-stu-id="90fe3-110">Failure could occur because of any of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="90fe3-111">Uma regra de autorização que concede ao usuário acesso ao computador (ou uma configuração de sessão específica no computador remoto) não existe.</span><span class="sxs-lookup"><span data-stu-id="90fe3-111">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span> <span data-ttu-id="90fe3-112">A segurança do Windows PowerShell Web Access é restritiva. Os usuários devem receber acesso explícito a computadores remotos usando regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="90fe3-112">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span> <span data-ttu-id="90fe3-113">Para obter mais informações, consulte <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access (Regras de autorização e recursos de segurança do Windows PowerShell Web Access)</a> neste guia.</span><span class="sxs-lookup"><span data-stu-id="90fe3-113">For more information about creating authorization rules, see <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a> in this guide.</span></span></p></li>
<li><p><span data-ttu-id="90fe3-114">O usuário não tem o acesso autorizado ao computador de destino.</span><span class="sxs-lookup"><span data-stu-id="90fe3-114">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="90fe3-115">Isso é determinado pelas listas de controle de acesso (ACLs).</span><span class="sxs-lookup"><span data-stu-id="90fe3-115">This is determined by access control lists (ACLs).</span></span> <span data-ttu-id="90fe3-116">Para obter mais informações, consulte “Entrando no Windows PowerShell Web Access” em <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Usar o Console do Windows PowerShell baseado na Web</a> ou o <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a> (Blog da Equipe do Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="90fe3-116">For more information, see “Signing in to Windows PowerShell Web Access” in <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Use the Web-based Windows PowerShell Console</a>, or the <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a>.</span></span></p>
<ul>
<li><p><span data-ttu-id="90fe3-117">O gerenciamento remoto do Windows PowerShell não deve estar habilitado no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="90fe3-117">Windows PowerShell remote management might not be enabled on the destination computer.</span></span> <span data-ttu-id="90fe3-118">Verifique se ele está habilitado no computador ao qual o usuário está tentando se conectar.</span><span class="sxs-lookup"><span data-stu-id="90fe3-118">Verify that it is enabled on the computer to which the user is trying to connect.</span></span> <span data-ttu-id="90fe3-119">Para obter mais informações, consulte “How to Configure Your Computer for Remoting” (Como configurar seu computador para comunicação remota) em <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> nos Windows PowerShell About Help Topics (Tópicos da Ajuda sobre o Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="90fe3-119">For more information, see “How to Configure Your Computer for Remoting” in <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> in the Windows PowerShell About Help Topics.</span></span></p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="90fe3-120">Quando os usuários tentarem entrar no Windows PowerShell Web Access em uma janela do Internet Explorer, eles verão a página <strong>Erro Interno do Servidor</strong> ou o Internet Explorer deixará de responder.</span><span class="sxs-lookup"><span data-stu-id="90fe3-120">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an <strong>Internal Server Error</strong> page, or Internet Explorer stops responding.</span></span> <span data-ttu-id="90fe3-121">Esse problema é específico ao Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="90fe3-121">This issue is specific to Internet Explorer.</span></span></p></td>
<td><p><span data-ttu-id="90fe3-122">Isso pode ocorrer com usuários que entraram com um nome de domínio que contém caracteres em chinês, ou quando um ou mais caracteres em chinês fazem parte do nome do servidor de gateway.</span><span class="sxs-lookup"><span data-stu-id="90fe3-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span> <span data-ttu-id="90fe3-123">Para solucionar esse problema, o usuário deve <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">instalar e executar o Internet Explorer 10</a> e depois executar as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="90fe3-123">To work around this issue, the user should <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">install and run Internet Explorer 10</a>, and then perform the following steps.</span></span></p>
<ol>
<li><p><span data-ttu-id="90fe3-124">Altere a configuração <strong>Modo de Documento</strong> do Internet Explorer para <strong>Padrões do IE10</strong>.</span><span class="sxs-lookup"><span data-stu-id="90fe3-124">Change the Internet Explorer <strong>Document Mode</strong> setting to <strong>IE10 standards</strong>.</span></span></p>
<ol>
<li><p><span data-ttu-id="90fe3-125">Pressione <strong>F12</strong> para abrir o console Ferramentas de Desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="90fe3-125">Press <strong>F12</strong> to open the Developer Tools console.</span></span></p></li>
<li><p><span data-ttu-id="90fe3-126">No Internet Explorer 10, clique em <strong>Modo do Navegador</strong> e selecione <strong>Internet Explorer 10</strong>.</span><span class="sxs-lookup"><span data-stu-id="90fe3-126">In Internet Explorer 10, click <strong>Browser Mode</strong>, and then select <strong>Internet Explorer 10</strong>.</span></span></p></li>
<li><p><span data-ttu-id="90fe3-127">Clique em <strong>Modo de Documento</strong> e clique em <strong>Padrões do IE10</strong>.</span><span class="sxs-lookup"><span data-stu-id="90fe3-127">Click <strong>Document Mode</strong>, and then click <strong>IE10 standards</strong>.</span></span></p></li>
<li><p><span data-ttu-id="90fe3-128">Pressione <strong>F12</strong> novamente para abrir o console Ferramentas de Desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="90fe3-128">Press <strong>F12</strong> again to close the Developer Tools console.</span></span></p></li>
</ol></li>
<li><p><span data-ttu-id="90fe3-129">Desabilite a configuração automática de proxy.</span><span class="sxs-lookup"><span data-stu-id="90fe3-129">Disable automatic proxy configuration.</span></span></p>
<ol>
<li><p><span data-ttu-id="90fe3-130">No Internet Explorer 10, clique em <strong>Ferramentas</strong> e clique em <strong>Opções da Internet</strong>.</span><span class="sxs-lookup"><span data-stu-id="90fe3-130">In Internet Explorer 10, click <strong>Tools</strong>, and then click <strong>Internet Options</strong>.</span></span></p></li>
<li><p><span data-ttu-id="90fe3-131">Na caixa de diálogo <strong>Opções da Internet</strong>, na guia <strong>Conexões</strong>, clique em <strong>Configurações da LAN</strong>.</span><span class="sxs-lookup"><span data-stu-id="90fe3-131">In the <strong>Internet Options</strong> dialog box, on the <strong>Connections</strong> tab, click <strong>LAN settings</strong>.</span></span></p></li>
<li><p><span data-ttu-id="90fe3-132">Desmarque a caixa de seleção <strong>Detectar automaticamente as configurações</strong>.</span><span class="sxs-lookup"><span data-stu-id="90fe3-132">Clear the <strong>Automatically detect settings</strong> check box.</span></span> <span data-ttu-id="90fe3-133">Clique em <strong>OK</strong> e clique em <strong>OK</strong> novamente para fechar a caixa de diálogo <strong>Opções da Internet</strong>.</span><span class="sxs-lookup"><span data-stu-id="90fe3-133">Click <strong>OK</strong>, and then click <strong>OK</strong> again to close the <strong>Internet Options</strong> dialog box.</span></span></p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="90fe3-134">Não é possível conectar a um computador de grupo de trabalho remoto</span><span class="sxs-lookup"><span data-stu-id="90fe3-134">Cannot connect to a remote workgroup computer</span></span></p></td>
<td><p><span data-ttu-id="90fe3-135">Se o computador de destino for membro de um grupo de trabalho, use a sintaxe a seguir para fornecer seu nome de usuário e entrar no computador: &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span><span class="sxs-lookup"><span data-stu-id="90fe3-135">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="90fe3-136">Não é possível encontrar as ferramentas de gerenciamento do Servidor Web (IIS), embora a função esteja instalada</span><span class="sxs-lookup"><span data-stu-id="90fe3-136">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span></p></td>
<td><p><span data-ttu-id="90fe3-137">Se você instalou o Windows PowerShell Web Access usando o cmdlet <span class="code">Install-WindowsFeature</span>, as ferramentas de gerenciamento não serão instaladas a menos que o parâmetro <span class="code">IncludeManagementTools</span> seja adicionado ao cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90fe3-137">If you installed Windows PowerShell Web Access by using the <span class="code">Install-WindowsFeature</span> cmdlet, management tools are not installed unless the <span class="code">IncludeManagementTools</span> parameter is added to the cmdlet.</span></span> <span data-ttu-id="90fe3-138">Por exemplo, consulte “To install Windows PowerShell Web Access by using Windows PowerShell cmdlets” (Para instalar o Windows PowerShell Web Access usando cmdlets do Windows PowerShell) em <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a> (Instalar e usar o Windows PowerShell Web Access).</span><span class="sxs-lookup"><span data-stu-id="90fe3-138">For an example, see “To install Windows PowerShell Web Access by using Windows PowerShell cmdlets” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>.</span></span> <span data-ttu-id="90fe3-139">Você pode adicionar o console do Gerenciador do IIS e outras ferramentas de gerenciamento do IIS de que precisa selecionando as ferramentas em uma sessão do Assistente de Adição de Funções e Recursos direcionada ao servidor de gateway.</span><span class="sxs-lookup"><span data-stu-id="90fe3-139">You can add the IIS Manager console and other IIS management tools that you need by selecting the tools in an Add Roles and Features Wizard session that is targeted at the gateway server.</span></span> <span data-ttu-id="90fe3-140">O Assistente de Adição de Funções e Recursos é aberto do Gerenciador do Servidor.</span><span class="sxs-lookup"><span data-stu-id="90fe3-140">The Add Roles and Features Wizard is opened from within Server Manager.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="90fe3-141">O site do Windows PowerShell Web Access não está acessível</span><span class="sxs-lookup"><span data-stu-id="90fe3-141">The Windows PowerShell Web Access website is not accessible</span></span></p></td>
<td><p><span data-ttu-id="90fe3-142">Se o recurso IE ESC (Configuração de Segurança Aprimorada do Internet Explorer) estiver habilitado, você poderá adicionar o site do Windows PowerShell Web Access à lista de sites confiáveis ou desabilitar o IE ESC.</span><span class="sxs-lookup"><span data-stu-id="90fe3-142">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites, or disable IE ESC.</span></span> <span data-ttu-id="90fe3-143">Você pode desabilitar o IE ESC no bloco <strong>Propriedades</strong> na página <strong>Servidor Local</strong> no Gerenciador do Servidor.</span><span class="sxs-lookup"><span data-stu-id="90fe3-143">You can disable IE ESC in the <strong>Properties</strong> tile on the <strong>Local Server</strong> page in Server Manager.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="90fe3-144">A seguinte mensagem de erro é exibida ao tentar se conectar quando o servidor de gateway é o computador de destino e também está em um grupo de trabalho: <strong>Falha de autorização. Verifique se você está autorizado a se conectar ao computador de destino.</strong></span><span class="sxs-lookup"><span data-stu-id="90fe3-144">The following error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup: <strong>An authorization failure occurred. Verify that you are authorized to connect to the destination computer.</strong></span></span></p></td>
<td><p><span data-ttu-id="90fe3-145">Quando o servidor de gateway também é o servidor de destino, e está em um grupo de trabalho, especifique o nome do usuário, o nome do computador e o nome do grupo de usuários como mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="90fe3-145">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name as shown in the following table.</span></span> <span data-ttu-id="90fe3-146">Não use um ponto (.) sozinho para representar o nome do computador.</span><span class="sxs-lookup"><span data-stu-id="90fe3-146">Do not use a dot (.) by itself to represent the computer name.</span></span></p>
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
<th><p><span data-ttu-id="90fe3-147">Cenário</span><span class="sxs-lookup"><span data-stu-id="90fe3-147">Scenario</span></span></p></th>
<th><p><span data-ttu-id="90fe3-148">Parâmetro UserName</span><span class="sxs-lookup"><span data-stu-id="90fe3-148">UserName Parameter</span></span></p></th>
<th><p><span data-ttu-id="90fe3-149">Parâmetro UserGroup</span><span class="sxs-lookup"><span data-stu-id="90fe3-149">UserGroup Parameter</span></span></p></th>
<th><p><span data-ttu-id="90fe3-150">Parâmetro ComputerName</span><span class="sxs-lookup"><span data-stu-id="90fe3-150">ComputerName Parameter</span></span></p></th>
<th><p><span data-ttu-id="90fe3-151">Parâmetro ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="90fe3-151">ComputerGroup Parameter</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="90fe3-152">O servidor de gateway está em um domínio</span><span class="sxs-lookup"><span data-stu-id="90fe3-152">Gateway server is in a domain</span></span></p></td>
<td><p><span data-ttu-id="90fe3-153"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em> ou .\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="90fe3-153"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="90fe3-154"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> ou .\<em>user_group</em></span><span class="sxs-lookup"><span data-stu-id="90fe3-154"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em>, or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="90fe3-155">Nome totalmente qualificado do servidor de gateway ou Localhost</span><span class="sxs-lookup"><span data-stu-id="90fe3-155">Fully qualified name of gateway server, or Localhost</span></span></p></td>
<td><p><span data-ttu-id="90fe3-156"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> ou .\<em>computer_group</em></span><span class="sxs-lookup"><span data-stu-id="90fe3-156"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em>, or .\<em>computer_group</em></span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="90fe3-157">O servidor de gateway está em um grupo de trabalho</span><span class="sxs-lookup"><span data-stu-id="90fe3-157">Gateway server is in a workgroup</span></span></p></td>
<td><p><span data-ttu-id="90fe3-158"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em> ou .\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="90fe3-158"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="90fe3-159"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> ou .\<em>user_group</em></span><span class="sxs-lookup"><span data-stu-id="90fe3-159"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="90fe3-160">Nome do servidor</span><span class="sxs-lookup"><span data-stu-id="90fe3-160">Server name</span></span></p></td>
<td><p><span data-ttu-id="90fe3-161"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> ou .\<em>computer_group</em></span><span class="sxs-lookup"><span data-stu-id="90fe3-161"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> or .\<em>computer_group</em></span></span></p></td>
</tr>
</tbody>
</table>
</div>
<p><span data-ttu-id="90fe3-162">Entre em um servidor de gateway como computador de destino usando credenciais formatadas conforme uma das maneiras a seguir.</span><span class="sxs-lookup"><span data-stu-id="90fe3-162">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="90fe3-163"><em>Server_name</em>\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="90fe3-163"><em>Server_name</em>\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="90fe3-164">Localhost\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="90fe3-164">Localhost\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="90fe3-165">.\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="90fe3-165">.\<em>user_name</em></span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="90fe3-166">Uma SID (ID de segurança) é exibida em uma regra de autorização, em vez da sintaxe <em>user_name</em>/<em>computer_name</em> </span><span class="sxs-lookup"><span data-stu-id="90fe3-166">A security identifier (SID) is displayed in an authorization rule instead of the syntax <em>user_name</em>/<em>computer_name</em> </span></span></p></td>
<td><p><span data-ttu-id="90fe3-167">A regra não é mais válida ou a consulta aos Serviços de Domínio Active Directory falhou.</span><span class="sxs-lookup"><span data-stu-id="90fe3-167">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="90fe3-168">Uma regra de autorização geralmente não é válida em cenários onde o servidor de gateway já esteve em um grupo de trabalho, mas depois ingressou em um domínio.</span><span class="sxs-lookup"><span data-stu-id="90fe3-168">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="90fe3-169">Não é possível entrar em um computador de destino especificado em regras de autorização como endereço IPv6 com um domínio.</span><span class="sxs-lookup"><span data-stu-id="90fe3-169">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span></p></td>
<td><p><span data-ttu-id="90fe3-170">As regras de autorização não dão suporte a endereços IPv6 no formato de nome de domínio.</span><span class="sxs-lookup"><span data-stu-id="90fe3-170">Authorization rules do not support an IPv6 address in form of a domain name.</span></span> <span data-ttu-id="90fe3-171">Para especificar um computador de destino usando um endereço IPv6, use o endereço IPv6 original (que contém dois-pontos) na regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="90fe3-171">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="90fe3-172">Tanto domínios quanto endereços IPv6 numéricos (com dois-pontos) têm suporte como nome do computador de destino na página de entrada do Windows PowerShell Web Access, mas não em regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="90fe3-172">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> <span data-ttu-id="90fe3-173">Para obter mais informações sobre endereços IPv6, consulte <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a> (Como o IPv6 Funciona).</span><span class="sxs-lookup"><span data-stu-id="90fe3-173">For more information about IPv6 addresses, see <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a>.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="90fe3-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Veja também</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="90fe3-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="90fe3-175">[Regras de autorização e recursos de segurança do Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Usar o console do Windows PowerShell baseado na Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span><span class="sxs-lookup"><span data-stu-id="90fe3-175">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span></span>

<span data-ttu-id="90fe3-176"><span>Mostrar</span>: herdado protegido</span><span class="sxs-lookup"><span data-stu-id="90fe3-176"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="90fe3-177"><span class="stdr-votetitle">Esta página foi útil?</span></span><span class="sxs-lookup"><span data-stu-id="90fe3-177"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="90fe3-178">Sim Não</span><span class="sxs-lookup"><span data-stu-id="90fe3-178">Yes No</span></span>

<span data-ttu-id="90fe3-179">Comentários adicionais?</span><span class="sxs-lookup"><span data-stu-id="90fe3-179">Additional feedback?</span></span>

<span data-ttu-id="90fe3-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caracteres restantes</span> Enviar Ignorar isto</span><span class="sxs-lookup"><span data-stu-id="90fe3-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="90fe3-181"><span class="stdr-thankyou">Obrigado!</span></span><span class="sxs-lookup"><span data-stu-id="90fe3-181"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="90fe3-182"><span class="stdr-appreciate">Agradecemos os seus comentários.</span></span><span class="sxs-lookup"><span data-stu-id="90fe3-182"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="90fe3-183">Gerenciar seu Perfil</span><span class="sxs-lookup"><span data-stu-id="90fe3-183">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="90fe3-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Comentários sobre o Site</a> Comentários sobre o Site</span><span class="sxs-lookup"><span data-stu-id="90fe3-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="90fe3-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="90fe3-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="90fe3-186">Conte-nos sobre sua experiência...</span><span class="sxs-lookup"><span data-stu-id="90fe3-186">Tell us about your experience...</span></span>

<span data-ttu-id="90fe3-187">A página carregou rápido?</span><span class="sxs-lookup"><span data-stu-id="90fe3-187">Did the page load quickly?</span></span>

<span data-ttu-id="90fe3-188"><span> Sim<span> </span></span> <span> Não<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="90fe3-188"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="90fe3-189">Você gosta do design da página?</span><span class="sxs-lookup"><span data-stu-id="90fe3-189">Do you like the page design?</span></span>

<span data-ttu-id="90fe3-190"><span> Sim<span> </span></span> <span> Não<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="90fe3-190"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="90fe3-191">Fale mais</span><span class="sxs-lookup"><span data-stu-id="90fe3-191">Tell us more</span></span>

-   [<span data-ttu-id="90fe3-192">Boletim informativo Flash</span><span class="sxs-lookup"><span data-stu-id="90fe3-192">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="90fe3-193">Entre em contato conosco</span><span class="sxs-lookup"><span data-stu-id="90fe3-193">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="90fe3-194">Política de Privacidade</span><span class="sxs-lookup"><span data-stu-id="90fe3-194">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="90fe3-195">Termos de Uso</span><span class="sxs-lookup"><span data-stu-id="90fe3-195">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="90fe3-196">Marcas comerciais</span><span class="sxs-lookup"><span data-stu-id="90fe3-196">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="90fe3-197">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="90fe3-197">© 2016 Microsoft</span></span>

<span data-ttu-id="90fe3-198">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="90fe3-198">© 2016 Microsoft</span></span>

<span data-ttu-id="90fe3-199">Código e scripts de terceiros, vinculados ou referenciados neste site, são licenciados por terceiros que têm tal código, não pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="90fe3-199">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="90fe3-200">Consulte os termos de uso do ASP.NET Ajax CDN – http://www.asp.net/ajaxlibrary/CDN.ashx.</span><span class="sxs-lookup"><span data-stu-id="90fe3-200">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

