---
ms.date: 2017-08-23
keywords: PowerShell, cmdlet
title: Solucionando problemas de acesso no Windows PowerShell Web Access
ms.openlocfilehash: 08a9fd286ed8a40e9423deb7d29dc0a8ecf8e5b1
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2017
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="0766e-103">Solucionando problemas de acesso no Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="0766e-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="0766e-104">Atualização: 24 de junho de 2013 (revisado em 23 de agosto de 2017)</span><span class="sxs-lookup"><span data-stu-id="0766e-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="0766e-105">Aplica-se a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="0766e-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="0766e-106">As seções a seguir identificam alguns problemas comuns ao tentar se conectar a um computador remoto usando o Windows PowerShell Web Access e inclui sugestões para resolver os problemas.</span><span class="sxs-lookup"><span data-stu-id="0766e-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="0766e-107">Falha no logon</span><span class="sxs-lookup"><span data-stu-id="0766e-107">Sign-in failure</span></span>

<span data-ttu-id="0766e-108">A falha pode ocorrer com base em um dos fatores a seguir.</span><span class="sxs-lookup"><span data-stu-id="0766e-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="0766e-109">Uma regra de autorização que concede ao usuário acesso ao computador (ou uma configuração de sessão específica no computador remoto) não existe.</span><span class="sxs-lookup"><span data-stu-id="0766e-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="0766e-110">A segurança do Windows PowerShell Web Access é restritiva. Os usuários devem receber acesso explícito a computadores remotos usando regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="0766e-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="0766e-111">Para obter mais informações de como criar regras de autorização, consulte [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) (Regras de autorização e recursos de segurança do Windows PowerShell Web Access).</span><span class="sxs-lookup"><span data-stu-id="0766e-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="0766e-112">O usuário não tem o acesso autorizado ao computador de destino.</span><span class="sxs-lookup"><span data-stu-id="0766e-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="0766e-113">Isso é determinado pelas listas de controle de acesso (ACLs).</span><span class="sxs-lookup"><span data-stu-id="0766e-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="0766e-114">Para obter mais informações, consulte [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) (Entrando no Windows PowerShell Web Access) ou o Blog da equipe do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0766e-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="0766e-115">O gerenciamento remoto do Windows PowerShell não deve estar habilitado no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="0766e-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="0766e-116">Verifique se o gerenciamento remoto está habilitado no computador ao qual o usuário está tentando se conectar.</span><span class="sxs-lookup"><span data-stu-id="0766e-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="0766e-117">Para obter mais informações, consulte [How to Configure Your Computer for Remoting](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting) (Como configurar seu computador para comunicação remota).</span><span class="sxs-lookup"><span data-stu-id="0766e-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="0766e-118">Erro Interno do Servidor</span><span class="sxs-lookup"><span data-stu-id="0766e-118">Internal Server Error</span></span>

<span data-ttu-id="0766e-119">Quando os usuários tentarem entrar no Windows PowerShell Web Access em uma janela do Internet Explorer, página **Erro Interno do Servidor** será exibida ou o *Internet Explorer* deixará de responder.</span><span class="sxs-lookup"><span data-stu-id="0766e-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="0766e-120">Esse problema é específico ao Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0766e-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="0766e-121">Causa possível</span><span class="sxs-lookup"><span data-stu-id="0766e-121">Possible cause</span></span>

<span data-ttu-id="0766e-122">Isso pode ocorrer com usuários que entraram com um nome de domínio que contém caracteres em chinês, ou quando um ou mais caracteres em chinês fazem parte do nome do servidor de gateway.</span><span class="sxs-lookup"><span data-stu-id="0766e-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="0766e-123">Solução alternativa</span><span class="sxs-lookup"><span data-stu-id="0766e-123">Workaround</span></span>

1. [<span data-ttu-id="0766e-124">Instalar e executar o Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="0766e-124">Install and run Internet Explorer 10</span></span>](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="0766e-125">Altere a configuração **Modo de Documento** do Internet Explorer para os padrões do *IE10*.</span><span class="sxs-lookup"><span data-stu-id="0766e-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="0766e-126">Pressione **F12** para abrir o console de Ferramentas de Desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="0766e-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="0766e-127">No Internet Explorer 10, clique em **Modo do Navegador** e selecione *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="0766e-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="0766e-128">Clique em **Modo de Documento** e, em seguida, em *Padrões do IE10*.</span><span class="sxs-lookup"><span data-stu-id="0766e-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="0766e-129">Pressione **F12** novamente para abrir o console Ferramentas de Desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0766e-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="0766e-130">Desabilite a configuração automática de proxy no Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="0766e-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="0766e-131">Clique em **Ferramentas**e em **Opções da Internet**.</span><span class="sxs-lookup"><span data-stu-id="0766e-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="0766e-132">Na caixa de diálogo **Opções da Internet**, na guia **Conexões**, clique em **Configurações da LAN**.</span><span class="sxs-lookup"><span data-stu-id="0766e-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="0766e-133">Desmarque a caixa de seleção **Detectar automaticamente as configurações**.</span><span class="sxs-lookup"><span data-stu-id="0766e-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="0766e-134">Clique em **OK** e clique em **OK** novamente para fechar a caixa de diálogo *Opções da Internet*.</span><span class="sxs-lookup"><span data-stu-id="0766e-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="0766e-135">Não é possível conectar a um computador de grupo de trabalho remoto</span><span class="sxs-lookup"><span data-stu-id="0766e-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="0766e-136">Se o computador de destino for membro de um grupo de trabalho, use a sintaxe a seguir para fornecer seu nome de usuário e entrar no computador: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="0766e-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="0766e-137">Não é possível encontrar as ferramentas de gerenciamento do Servidor Web (IIS), embora a função esteja instalada</span><span class="sxs-lookup"><span data-stu-id="0766e-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="0766e-138">Se você instalar o Windows PowerShell Web Access usando o cmdlet `Install-WindowsFeature`, as ferramentas de gerenciamento não serão instaladas, a menos que o parâmetro `-IncludeManagementTools` seja adicionado ao cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0766e-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="0766e-139">Por exemplo, consulte [Para instalar o Windows PowerShell Web Access usando cmdlets do Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="0766e-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="0766e-140">Você pode adicionar o console do Gerenciador do IIS e outras ferramentas de gerenciamento do IIS de que precisa, selecionando as ferramentas em uma sessão do **Assistente para Adicionar Funções e Recursos** direcionada ao servidor de gateway.</span><span class="sxs-lookup"><span data-stu-id="0766e-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="0766e-141">O Assistente de Adição de Funções e Recursos é aberto do Gerenciador do Servidor.</span><span class="sxs-lookup"><span data-stu-id="0766e-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="0766e-142">O site do Windows PowerShell Web Access não está acessível</span><span class="sxs-lookup"><span data-stu-id="0766e-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="0766e-143">Se o recurso IE ESC (Configuração de Segurança Aprimorada do Internet Explorer) estiver habilitado, você poderá adicionar o site do Windows PowerShell Web Access à lista de sites confiáveis.</span><span class="sxs-lookup"><span data-stu-id="0766e-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="0766e-144">Uma abordagem menos recomendada, devido a riscos de segurança, é desabilitar o IE ESC.</span><span class="sxs-lookup"><span data-stu-id="0766e-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="0766e-145">Você pode desabilitar o IE ESC no bloco Propriedades na página Servidor Local no Gerenciador do Servidor.</span><span class="sxs-lookup"><span data-stu-id="0766e-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="0766e-146">Ocorreu uma falha de autorização.</span><span class="sxs-lookup"><span data-stu-id="0766e-146">An authorization failure occurred.</span></span> <span data-ttu-id="0766e-147">Verifique se que você está autorizado a conectar-se ao computador de destino.</span><span class="sxs-lookup"><span data-stu-id="0766e-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="0766e-148">A mensagem de erro acima é exibida ao tentar se conectar quando o servidor de gateway é o computador de destino e também está um grupo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0766e-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="0766e-149">Quando o servidor de gateway for o servidor de destino e também estiver em um grupo de trabalho, especifique o nome de usuário, o nome do computador e o nome do grupo de usuários.</span><span class="sxs-lookup"><span data-stu-id="0766e-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="0766e-150">Não use um ponto (.) sozinho para representar o nome do computador.</span><span class="sxs-lookup"><span data-stu-id="0766e-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="0766e-151">Cenários e valores adequados</span><span class="sxs-lookup"><span data-stu-id="0766e-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="0766e-152">Todos os casos</span><span class="sxs-lookup"><span data-stu-id="0766e-152">All cases</span></span>

<span data-ttu-id="0766e-153">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="0766e-153">Parameter</span></span> | <span data-ttu-id="0766e-154">Valor</span><span class="sxs-lookup"><span data-stu-id="0766e-154">Value</span></span>
-- | --
<span data-ttu-id="0766e-155">UserName</span><span class="sxs-lookup"><span data-stu-id="0766e-155">UserName</span></span> | <span data-ttu-id="0766e-156">Nome\_servidor\\nome\_usuário</span><span class="sxs-lookup"><span data-stu-id="0766e-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="0766e-157">Localhost\\nome\_usuário</span><span class="sxs-lookup"><span data-stu-id="0766e-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="0766e-158">.\\nome\_usuário</span><span class="sxs-lookup"><span data-stu-id="0766e-158">.\\user\_name</span></span>
<span data-ttu-id="0766e-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="0766e-159">UserGroup</span></span> | <span data-ttu-id="0766e-160">Nome\_servidor\\grupo\_usuários</span><span class="sxs-lookup"><span data-stu-id="0766e-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="0766e-161">Localhost\\grupo\_usuários</span><span class="sxs-lookup"><span data-stu-id="0766e-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="0766e-162">.\\grupo\_usuários</span><span class="sxs-lookup"><span data-stu-id="0766e-162">.\\user\_group</span></span>
<span data-ttu-id="0766e-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="0766e-163">ComputerGroup</span></span> | <span data-ttu-id="0766e-164">Nome\_servidor\\grupo\_computadores</span><span class="sxs-lookup"><span data-stu-id="0766e-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="0766e-165">Localhost\\grupo\_computadores</span><span class="sxs-lookup"><span data-stu-id="0766e-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="0766e-166">.\\grupo\_computadores</span><span class="sxs-lookup"><span data-stu-id="0766e-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="0766e-167">O servidor de gateway está em um domínio</span><span class="sxs-lookup"><span data-stu-id="0766e-167">Gateway server is in a domain</span></span>

<span data-ttu-id="0766e-168">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="0766e-168">Parameter</span></span> | <span data-ttu-id="0766e-169">Valor</span><span class="sxs-lookup"><span data-stu-id="0766e-169">Value</span></span>
-- | --
<span data-ttu-id="0766e-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="0766e-170">ComputerName</span></span> | <span data-ttu-id="0766e-171">Nome totalmente qualificado do servidor de gateway ou Localhost</span><span class="sxs-lookup"><span data-stu-id="0766e-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="0766e-172">O servidor de gateway está em um grupo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0766e-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="0766e-173">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="0766e-173">Parameter</span></span> | <span data-ttu-id="0766e-174">Valor</span><span class="sxs-lookup"><span data-stu-id="0766e-174">Value</span></span>
-- | --
<span data-ttu-id="0766e-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="0766e-175">ComputerName</span></span> | <span data-ttu-id="0766e-176">Nome do servidor</span><span class="sxs-lookup"><span data-stu-id="0766e-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="0766e-177">Credenciais de gateway</span><span class="sxs-lookup"><span data-stu-id="0766e-177">Gateway credentials</span></span>

<span data-ttu-id="0766e-178">Entre em um servidor de gateway como computador de destino usando credenciais formatadas conforme uma das maneiras a seguir.</span><span class="sxs-lookup"><span data-stu-id="0766e-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="0766e-179">Nome\_servidor\\nome\_usuário</span><span class="sxs-lookup"><span data-stu-id="0766e-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="0766e-180">Localhost\\nome\_usuário</span><span class="sxs-lookup"><span data-stu-id="0766e-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="0766e-181">.\\nome\_usuário</span><span class="sxs-lookup"><span data-stu-id="0766e-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="0766e-182">Um SID (identificador de segurança) é exibido em uma regra de autorização</span><span class="sxs-lookup"><span data-stu-id="0766e-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="0766e-183">Um SID (identificador de segurança) é exibido em uma regra de autorização em vez da sintaxe nome\_usuário/nome\_computador.</span><span class="sxs-lookup"><span data-stu-id="0766e-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="0766e-184">A regra não é mais válida ou a consulta aos Serviços de Domínio Active Directory falhou.</span><span class="sxs-lookup"><span data-stu-id="0766e-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="0766e-185">A regra de autorização geralmente não é válida em cenários em que o servidor de gateway já esteve em um grupo de trabalho, mas depois ingressou em um domínio</span><span class="sxs-lookup"><span data-stu-id="0766e-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="0766e-186">Não é possível entrar com uma regra como um endereço IPv6 com um domínio</span><span class="sxs-lookup"><span data-stu-id="0766e-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="0766e-187">Não é possível entrar em um computador de destino especificado em regras de autorização como endereço IPv6 com um domínio.</span><span class="sxs-lookup"><span data-stu-id="0766e-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="0766e-188">As regras de autorização não dão suporte a endereços IPv6 no formato de nome de domínio.</span><span class="sxs-lookup"><span data-stu-id="0766e-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="0766e-189">Para especificar um computador de destino usando um endereço IPv6, use o endereço IPv6 original (que contém dois-pontos) na regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="0766e-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="0766e-190">Tanto domínios quanto endereços IPv6 numéricos (com dois-pontos) têm suporte como nome do computador de destino na página de entrada do Windows PowerShell Web Access, mas não em regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="0766e-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> 

<span data-ttu-id="0766e-191">Para obter mais informações sobre endereços IPv6, consulte [How IPv6 Works](https://technet.microsoft.com/en-us/library/cc781672(v=ws.10).aspx) (Como o IPv6 Funciona).</span><span class="sxs-lookup"><span data-stu-id="0766e-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/en-us/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="0766e-192">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0766e-192">See Also</span></span>

- <span data-ttu-id="0766e-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) (Regras de autorização e recursos de segurança do Windows PowerShell Web Access)</span><span class="sxs-lookup"><span data-stu-id="0766e-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="0766e-194">[Usar o Console do Windows PowerShell baseado na Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="0766e-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="0766e-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="0766e-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
