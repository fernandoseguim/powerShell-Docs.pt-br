# Regras de autorização e recursos de segurança do Windows PowerShell Web Access

Atualizado em: 24 de junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell® Web Access em Windows Server® 2012 R2 e Windows Server® 2012 têm um modelo de segurança restritivo. Os usuários devem ter acesso explícito antes de entrar no gateway do Windows PowerShell Web Access e usar o console do Windows PowerShell baseado na Web.

-   [Configurando regras de autorização e segurança do site](#BKMK_auth)

-   [Gerenciamento de sessões](#BKMK_sesmgmt)


Depois que o Windows PowerShell Web Access for instalado e o gateway configurado, os usuários poderão abrir a página de entrada em um navegador, mas só poderão entrar depois que o administrador do Windows PowerShell Web Access conceder a eles acesso explicitamente. O controle de acesso do Windows PowerShell Web Access é gerenciado por meio de um conjunto de cmdlets do Windows PowerShell descritos na tabela a seguir. Não há uma GUI comparável para adicionar ou gerenciar regras de autorização. Para obter mais informações sobre os cmdlets do Windows PowerShell Web Access, consulte os tópicos de referência de cmdlet [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx) (Cmdlets do Windows PowerShell Web Access).

Os administradores podem definir as regras de autenticação 0-*n* para o Windows PowerShell Web Access. A segurança padrão é restritiva, não permissiva. Se não houver regras de autenticação, significa que nenhum usuário tem acesso a coisa alguma.

Add-PswaAuthorizationRule e Test-PswaAuthorizationRule no Windows Server 2012 R2 incluem um parâmetro Credential que permite adicionar e testar regras de autorização do Windows PowerShell Web Access por meio de um computador remoto ou de dentro de uma sessão ativa do Windows PowerShell Web Access. Assim como com outros cmdlets do Windows PowerShell que têm um parâmetro Credential, você pode especificar um objeto PSCredential como o valor do parâmetro. Para criar um objeto PSCredential que contenha credenciais que você deseja passar para um computador remoto, execute o cmdlet [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx).

Regras de autenticação do Windows PowerShell Web Access são regras da lista branca. Cada regra é uma definição de uma conexão permitida entre usuários, computadores de destino e [configurações de sessão](https://technet.microsoft.com/library/dd819508.aspx) do Windows PowerShell específicas (também referenciadas como pontos de extremidade ou runspaces) em computadores especificados.

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Observação de segurança </span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Um usuário só precisa de uma regra para obter acesso. Se um usuário receber acesso a um computador com acesso completo a linguagem ou acesso somente a cmdlets de gerenciamento remoto do Windows PowerShell, do console baseado na Web, o usuário poderá fazer logon (ou saltar) para outros computadores conectados ao primeiro computador de destino. A maneira mais segura de configurar o Windows PowerShell Web Access é permitir aos usuários acesso apenas às configurações de sessão restritas (também chamadas pontos de extremidade ou runspaces), que permitem realizar tarefas específicas que normalmente precisam ser executadas remotamente.</p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Nome</p></th>
<th><p>Descrição</p></th>
<th><p>Parâmetros</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/library/jj592890.aspx">Add-PswaAuthorizationRule</a></p></td>
<td><p>Adiciona uma nova regra de autorização ao conjunto de regras de autorização do Windows PowerShell Web Access.</p></td>
<td><ul>
<li><p>ComputerGroupName</p></li>
<li><p>ComputerName</p></li>
<li><p>ConfigurationName</p></li>
<li><p>RuleName</p></li>
<li><p>UserGroupName</p></li>
<li><p>UserName</p></li>
<li><p>Credencial (Windows Server 2012 R2 e posterior)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/library/jj592893.aspx">Remove-PswaAuthorizationRule</a></p></td>
<td><p>Remove uma regra de autorização especificada do Windows PowerShell Web Access.</p></td>
<td><ul>
<li><p>Id</p></li>
<li><p>RuleName</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/library/jj592891.aspx">Get-PswaAuthorizationRule</a></p></td>
<td><p>Retorna um conjunto de regras de autorização do Windows PowerShell Web Access. Quando é usado sem parâmetros, o cmdlet retorna todas as regras.</p></td>
<td><ul>
<li><p>Id</p></li>
<li><p>RuleName</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/library/jj592892.aspx">Test-PswaAuthorizationRule</a></p></td>
<td><p>Avalia as regras de autorização para determinar se uma solicitação específica de acesso a configurações de usuário, computador ou sessão foi autorizada. Por padrão, se nenhum parâmetro for adicionado, o cmdlet avaliará todas as regras de autorização. Adicionando parâmetros, os administradores podem especificar uma regra de autorização ou um subconjunto de regras para testar.</p></td>
<td><ul>
<li><p>ComputerName</p></li>
<li><p>ConfigurationName</p></li>
<li><p>RuleName</p></li>
<li><p>UserName</p></li>
<li><p>Credencial (Windows Server 2012 R2 e posterior)</p></li>
</ul></td>
</tr>
</tbody>
</table>

Os cmdlets anteriores criam um conjunto de regras de acesso que são usadas para autorizar um usuário no gateway do Windows PowerShell Web Access. As regras são diferentes das listas de controle de acesso (ACLs) no computador de destino e fornecem uma camada adicional de segurança para acesso à Web. A seção a seguir contém mais detalhes sobre segurança.

Se os usuários não puderem passar por nenhuma das camadas de segurança anteriores, eles receberão uma mensagem genérica de "acesso negado" na janela do navegador. Embora os detalhes de segurança sejam registrador no servidor do gateway, os usuários finais não recebem informações sobre quantas camadas de segurança eles ultrapassaram, ou em qual camada ocorreu a falha de logon ou autenticação.

Para obter mais informações sobre como configurar regras de autorização, consulte [Configurando regras de autorização](#BKMK_configrules) neste tópico.

<a href="" id="BKMK_sec"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Segurança</span></a>

------------------------------------------------------------------------

O modelo de segurança do Windows PowerShell Web Access tem quatro camadas entre um usuário final do console baseado na Web e um computador de destino. Os administradores do Windows PowerShell Web Access podem adicionar camadas de segurança por meio de configuração adicional no console do Gerenciador do IIS. Para obter mais informações sobre como proteger sites no console do Gerenciador do IIS, consulte [Configurar a segurança do servidor Web (IIS 7)](https://technet.microsoft.com/library/cc731278(v=ws.10).aspx). Para obter mais informações sobre práticas recomendadas do IIS e sobre como evitar ataques de negação de serviço, consulte [Best Practices for Preventing DoS/Denial of Service Attacks (Práticas recomendadas para evitar ataques DoS/de negação de serviço)](https://technet.microsoft.com/library/cc750213.aspx). Um administrador também pode adquirir e instalar outros softwares comerciais de autenticação.

A tabela a seguir descreve as quatro camadas de segurança entre os usuários finais e os computadores de destino.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Ordem</p></th>
<th><p>Camada</p></th>
<th><p>Descrição</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Recursos de segurança do Servidor Web (IIS), como autenticação de certificado de cliente</p></td>
<td><p>Os usuários do Windows PowerShell Web Access sempre devem fornecer um nome de usuário e uma senha para autenticar suas contas no gateway. Entretanto, administradores do Windows PowerShell Web Access também podem ativar ou desativar a autenticação opcional de certificados clientes (consulte a etapa 10 de “To use IIS Manager to configure the gateway in an existing website” (Para usar o gerenciador de IIS a fim de configurar o gateway em um site existente) em <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access (Instalar e usar o Windows PowerShell Web Access)</a>). O recurso opcional de certificado de cliente exige que os usuários finais tenham um certificado de cliente válido (além de seus nomes de usuário e senhas) e faz parte da configuração do Servidor Web (IIS). Quando a camada de certificados cliente estiver habilitada, a página de entrada do Windows PowerShell Web Access solicitará que os usuários forneçam certificados válidos antes que suas credenciais de entrada sejam avaliadas. A autenticação de certificados clientes verifica automaticamente o certificado de cliente.</p>
<p>Se um certificado válido não for encontrado, o Windows PowerShell Web Access informará os usuários a respeito, para que eles possam fornecer o certificado. Se um certificado de cliente válido for encontrado, o Windows PowerShell Web Access abrirá a página de entrada para que os usuários forneçam seus respectivos nomes de usuário e suas senhas.</p>
<p>Este é um exemplo de configurações de segurança adicionais oferecidas pelo Servidor Web (IIS). Para obter mais informações sobre outros recursos de segurança do IIS, consulte <a href="https://technet.microsoft.com/library/cc731278(ws.10).aspx">Configure Web Server Security (IIS 7) (Configurar a segurança do Servidor Web (IIS 7))</a>.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Autenticação de gateway baseada em formulários do Windows PowerShell Web Access</p></td>
<td><p>A página de entrada do Windows PowerShell Web Access requer um conjunto de credenciais (nome de usuário e senha) e oferece aos usuários a opção de fornecer outras credenciais para o computador de destino. Se o usuário não fornecer credenciais alternativas, o nome de usuário primário e a respectiva senha usados para conexão com o gateway também serão utilizados para se conectar ao computador cliente.</p>
<p>As credenciais necessárias são autenticadas no gateway do Windows PowerShell Web Access. Essas credenciais devem ser contas de usuário válidas no servidor de gateway local do Windows PowerShell Web Access ou no Active Directory®.</p>
<p>Depois que um usuário é autenticado no gateway, o Windows PowerShell Web Access verifica as regras de autorização para confirmar se o usuário tem acesso ao computador de destino solicitado. Após a autorização bem-sucedida, as credenciais do usuários são passadas para o computador de destino.</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>Regras de autorização do Windows PowerShell Web Access</p></td>
<td><p>Depois que um usuário é autenticado no gateway, o Windows PowerShell Web Access verifica as regras de autorização para confirmar se o usuário tem acesso ao computador de destino solicitado. Após a autorização bem-sucedida, as credenciais do usuários são passadas para o computador de destino.</p>
<p>Essas regras serão avaliadas apenas depois que um usuário for autenticado pelo gateway e antes de ser autenticado em um computador de destino.</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>Autenticação de destino e regras de autorização</p></td>
<td><p>A camada final de segurança do Windows PowerShell Web Access é a própria configuração de segurança do computador de destino. Os usuários devem ter os direitos de acesso apropriados configurados no computador de destino e nas regras de autorização do Windows PowerShell Web Access para executar um console do Windows PowerShell baseado na Web que afete um computador de destino via Windows PowerShell Web Access.</p>
<p>Essa camada oferece os mesmos mecanismos de segurança que avaliariam tentativas de conexão se usuários tentassem criar uma sessão remota do Windows PowerShell para um computador de destino por meio do Windows PowerShell, executando os cmdlets <strong>Enter-PSSession</strong> ou <strong>New-PSSession</strong>.</p>
<p>Por padrão, o Windows PowerShell Web Access usa o nome de usuário principal e a respectiva senha para autenticação no gateway e no computador de destino. A página de entrada baseada na Web, em uma seção intitulada <strong>Configurações opcionais de conexão</strong>, oferece ao usuário a opção de fornecer outras credenciais para o computador de destino, caso necessário. Se o usuário não fornecer credenciais alternativas, o nome de usuário primário e a respectiva senha usados para conexão com o gateway também serão utilizados para se conectar ao computador cliente.</p>
<p>As regras de autorização podem ser usadas para permitir que os usuários acessem uma configuração de sessão específica. Você pode criar configurações de sessão ou runspaces restritos para o Windows PowerShell Web Access e permitir que usuários específicos se conectem apenas a configurações de sessão específicas quando entrarem no Windows PowerShell Web Access. Você pode usar ACLs (listas de controle de acesso) para determinar quais usuários têm acesso a pontos de extremidade específicos e restringir ainda mais o acesso ao ponto de extremidade para um conjunto específico de usuários, usando as regras de autorização descritas nesta seção. Para obter mais informações sobre runspaces restritos, consulte <a href="https://msdn.microsoft.com/library/windows/desktop/ee706589.aspx">Constrained Runspaces (Runspaces restritos)</a> no MSDN.</p></td>
</tr>
</tbody>
</table>

<a href="" id="BKMK_configrules"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configurando regras de autorização</span></a>

------------------------------------------------------------------------

Provavelmente os administradores querem a mesma regra de autorização para usuários do Windows PowerShell Web Access que já estejam definidas no ambiente de gerenciamento remoto do Windows PowerShell. O primeiro procedimento nesta seção descreve como adiciona uma regra de autorização segura que concede acesso a um usuário (que faz logon para gerenciar um computador) em uma única configuração de sessão. O segundo procedimento descreve como remover uma regra de autorização que não é mais necessária.

Se você pretende usar configurações de sessão personalizadas para permitir que usuários específicos trabalhem apenas dentro de runspaces restritos no Windows PowerShell Web Access, crie configurações de sessão personalizadas antes de adicionar regras de autorização que façam referência a elas. Não é possível usar os cmdlets do Windows PowerShell Web Access para criar configurações de sessão personalizadas. Para obter mais informações sobre como criar configurações de sessão personalizadas, consulte [about\_Session\_Configuration\_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) no MSDN.

Os cmdlets do Windows PowerShell Web Access dão suporte a um caractere curinga, o asterisco ( * ). Não há suporte aos caracteres-curinga com cadeias. Use um asterisco pro propriedade (usuários, computadores ou configurações de sessão).

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
<td><p>Para saber como usar regras de autorização de outras maneiras para conceder acesso a usuários e ajudar a proteger o ambiente do Windows PowerShell Web Access, consulte <a href="#BKMK_others">Outros exemplos de cenário de regras de autorização</a> neste tópico.</p></td>
</tr>
</tbody>
</table>

#### Para adicionar uma regra de autorização restritiva

1.  Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados.

    -   Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.

    -   Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.

2.  <span class="label">Etapa opcional para restringir o acesso dos usuários por meio de configurações de sessão:</span> verifique se as configurações de sessão que você deseja usar em suas regras já existem. Se elas ainda não foram criadas, siga as instruções sobre como criar configurações de sessão em [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) no MSDN.

3.  Digite o seguinte e pressione **Enter**.

    [Cópia](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_1079478f-cd51-4d35-8022-4b532a9d57a4'); "Copy to clipboard.")

        Add-PswaAuthorizationRule –UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    Essa regra de autorização permite que um usuário específico acesse um computador na rede ao qual tipicamente tem acesso, com acesso a uma configuração de sessão específica, voltada para as necessidades típicas de script e cmdlet do usuário. No exemplo a seguir, um usuário nomeado <span class="code">JSmith</span> no domínio <span class="code">Contoso</span> ganha acesso para gerenciar o computador <span class="code">Contoso_214</span> e usa uma configuração de sessão nomeada <span class="code">NewAdminsOnly</span>.

    [Cópia](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4e760377-e401-4ef4-988f-7a0aec1b2a90'); "Copy to clipboard.")

        Add-PswaAuthorizationRule –UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  Verifique se a regra foi criada ao executar o cmdlet **Get-PswaAuthorizationRule** ou **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer\_name&gt;. Por exemplo, **Test-PswaAuthorizationRule –UserName Contoso\\JSmith –ComputerName Contoso\_214**.

#### Para remover uma regra de autorização

1.  Se uma sessão do Windows PowerShell ainda não estiver aberta, consulte a etapa 1 de [Para adicionar uma regra de autorização não restritiva](#BKMK_arar) nesta seção.

2.  Digite o seguinte e pressione **Enter**, em que *ID da regra* representa o número da ID exclusiva que você deseja remover.

    [Cópia](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0daef66d-0ecf-47fb-a8a0-d4dbceb8409d'); "Copy to clipboard.")

        Remove-PswaAuthorizationRule -ID <rule ID>

    De forma alternativa, se você não souber o número da ID, mas souber o nome amigável da regra que deseja remover, você poderá obter o nome da regra e redirecioná-la para o cmdlet <span class="code">Remove-PswaAuthorizationRule</span> para remover a regra, como mostrado no seguinte exemplo: Get-PswaAuthorizationRule -RuleName &lt;*nome da regra*&gt; | Remove-PswaAuthorizationRule.

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
    <td><p>Você não precisará confirmar se deseja excluir a regra de autorização especificada; a regra será excluída quando você pressionar <strong>Enter</strong>. Certifique-se de remover a regra de autorização antes de executar o cmdlet <strong>Remove-PswaAuthorizationRule</strong>.</p></td>
    </tr>
    </tbody>
    </table>

<a href="" id="BKMK_others"></a>
####

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Outros exemplos de cenários de regras de autorização</span></a>

------------------------------------------------------------------------

Toda sessão do Windows PowerShell usa uma configuração de sessão. Se não houver nenhuma configuração especificada para uma sessão, o Windows PowerShell usará a configuração de sessão interna padrão do Windows PowerShell, chamada Microsoft.PowerShell. A configuração de sessão padrão inclui todos os cmdlets disponíveis em um computador. Os administradores podem restringir o acesso a todos os computadores definindo uma sessão de configuração com um runspace restrito (um intervalo limitado de cmdlets e tarefas que seus usuários finais podem executar). Um usuário com acesso a um computador com acesso à linguagem completa ou somente aos cmdlets de gerenciamento remoto do Windows PowerShell poderá se conectar a outros computadores conectados ao primeiro computador. A definição de um runspace restrito pode evitar que usuários acessem outros computadores do runspace permitido do Windows PowerShell e aumentará a segurança do seu ambiente do Windows PowerShell Web Access. A configuração de sessão pode ser distribuída (por meio de Política de Grupo) entre todos os computadores que os administradores desejam tornar acessíveis através do Windows PowerShell Web Access. Para obter mais informações sobre configurações de sessão, consulte [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx). Veja a seguir alguns exemplos desse cenário.

-   Um administrador cria um ponto de extremidade, chamado **PswaEndpoint**, com um runspace restrito. Em seguida, ele cria uma regra, **\*,\*,PswaEndpoint** e distribui o ponto de extremidade entre outros computadores. A regra permite o acesso de todos os usuários a todos os computadores com o ponto de extremidade **PswaEndpoint**. Se essa for a única regra de autorização definida no conjunto de regras, os computadores sem esse ponto de extremidade não poderão ser acessados.

-   O administrador criou um ponto de extremidade com um runspace restrito chamado **PswaEndpoint** e deseja restringir o acesso a usuários específicos. O administrador cria um grupo de usuários chamado **Level1Support** e define a seguinte regra: **Level1Support,\*,PswaEndpoint**. A regra concede acesso a todos os usuários no grupo **Level1Support** a todos os computadores com a configuração **PswaEndpoint**. De modo semelhante, o acesso pode ser restrito a um conjunto específico de computadores.

-   Alguns administradores concedem a certos usuários mais acesso do que outros. Por exemplo, um administrador cria dois grupos de usuários: **Admins** e **BasicSupport**. O administrador também cria um ponto de extremidade com um runspace restrito chamado **PswaEndpoint** e define duas regras: **Admins,\*,\*** e **BasicSupport,\*,PswaEndpoint**. A primeira regra fornece a todos os usuários do grupo **Admin** acesso a todos os computadores e a segunda regra fornece a todos os usuários do grupo **BasicSupport** acesso apenas aos computadores com **PswaEndpoint**.

-   Um administrador configurou um ambiente de teste privado e deseja permitir que todos os usuários da rede autorizados acessem todos os computadores na rede aos quais têm acesso normalmente, com acesso a todas as configurações de sessão que acessam tipicamente. Como esse é um ambiente de teste privado, o administrador cria uma regra de autorização que não é segura. O administrador executa o cmdlet <span class="code">Add-PswaAuthorizationRule \* \* \*</span>, que usa o caractere curinga **\*** para representar todos os usuários, todos os computadores e todas as configurações. Essa regra é o equivalente ao seguinte: <span class="code">Add-PswaAuthorizationRule –UserName \* -ComputerName \* -ConfigurationName \*</span>.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Observação de segurança </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Essa regra não é recomendada em um ambiente seguro. Ela ignora a camada de segurança de regras de autorização fornecida pelo Windows PowerShell Web Access.</p></td>
    </tr>
    </tbody>
    </table>

-   Um administrador deve permitir que os usuários se conectem a computadores de destino em um ambiente que inclua tanto grupos de trabalho quanto domínios, onde os computadores de grupos de trabalho sejam ocasionalmente usados para se conectar a computadores de destino em domínios, e os computadores em domínios sejam ocasionalmente usados para se conectar a computadores de destino em grupos de trabalho. O administrador tem um servidor de gateway, *PswaServer*, em um grupo de trabalho; e o computador de destino *srv1.contoso.com* está em um domínio. O usuário *Chris* é um usuário local autorizado tanto no servidor de gateway de grupo de trabalho quanto no computador de destino. Seu nome de usuário no servidor de grupo de trabalho é *carlosLocal* e seu nome de usuário no computador de destino é *contoso\\carlos*. Para autorizar o acesso de Carlos a srv1.contoso.com, o administrador adiciona a regra a seguir.

    [Cópia](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_8d183d3d-1c19-44b8-9297-530b0efc7c79'); "Copy to clipboard.")

        Add-PswaAuthorizationRule –userName PswaServer\chrisLocal –computerName srv1.contoso.com –configurationName Microsoft.PowerShell

    O exemplo da regra anterior autentica Carlos no servidor de gateway e depois autoriza seu acesso ao *srv1*. Na página de entrada, Carlos deve fornecer um segundo conjunto de credenciais na área **Configurações opcionais de conexão** (*contoso\\carlos*). O servidor de gateway usa o conjunto adicional de credenciais para efetuar a autenticação do usuário no computador de destino, *srv1.contoso.com*.

    No cenário anterior, o Windows PowerShell Web Access só estabelece uma conexão bem-sucedida com o computador de destino quando as etapas a seguir são executadas com êxito e quando ele é autorizado por pelo menos uma regra de autorização.

    1.  Autenticação no servidor de gateway de grupo de trabalho adicionando um nome de usuário no formato *server_name*\\*user_name* à regra de autorização

    2.  Autenticação no computador de destino usando credenciais alternativas fornecidas na página de entrada, na área **Configurações opcionais de conexão**

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
    <td><p>Se o gateway e os computadores de destino estiverem em domínios ou grupos de trabalho diferentes, uma relação de confiança deverá ser estabelecida entre os dois computadores de grupo de trabalho, entre os dois domínios ou entre o grupo de trabalho e o domínio. Essa relação não pode ser configurada usando cmdlets de regras de autorização do Windows PowerShell Web Access. As regras de autorização não definem uma relação de confiança entre computadores. Elas só podem autorizar usuários a se conectar a computadores de destino e a configurações de sessão específicos. Para obter mais informações sobre como configurar uma relação de confiança entre diferentes domínios, consulte <a href="https://technet.microsoft.com/library/cc794775.aspx">Creating Domain and Forest Trusts</a> (Criando relações de confiança entre domínios e florestas). Para obter mais informações sobre como adicionar computadores de grupo de trabalho a uma lista de hosts confiáveis, consulte <a href="https://technet.microsoft.com/library/dd759202.aspx">Remote Management with Server Manager (Gerenciamento remoto com o Gerenciador do Servidor)</a>.</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Usando um único conjunto de regras de autorização para vários sites</span></a>

------------------------------------------------------------------------

As regras de autorização são armazenadas em um arquivo XML. Por padrão, o nome do caminho do arquivo XML é %windir%\\Web\\PowershellWebAccess\\data\\AuthorizationRules.xml.

O caminho para o arquivo XML de regras de autorização é armazenado no arquivo **powwa.config**, encontrado em %windir%\\Web\\PowershellWebAccess\\data. O administrador pode alterar a referência ao caminho padrão em **powwa.config** de acordo com preferências ou requisitos. O fato de o administrador poder alterar a localização do arquivo permite que muitos gateways do Windows PowerShell Web Access usem as mesmas regras de autorização, caso essa configuração seja necessária.

<a href="" id="BKMK_sesmgmt"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Gerenciamento de sessões</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Por padrão, o Windows PowerShell Web Access limita um usuário a três sessões ao mesmo tempo. Você pode editar o arquivo **web.config** do aplicativo Web no Gerenciador do IIS para dar suporte a número diferente de sessões por usuário. O caminho para o arquivo **web.config** é $Env:Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config.

Por padrão, o Servidor Web (IIS) é configurado para reiniciar o pool de aplicativos quando alguma configuração é editada. Por exemplo, o pool de aplicativos é reiniciado quando são feitas alterações no arquivo **web.config**. Como o Windows PowerShell Web Access usa estados de sessão na memória, usuários conectados a sessões do Windows PowerShell Web Access perdem suas sessões quando o pool de aplicativos é reiniciado.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configurando parâmetros padrão na página de entrada</span></a>

------------------------------------------------------------------------

Se o gateway do Windows PowerShell Web Access estiver em execução no Windows Server 2012 R2, você poderá configurar valores padrão para as configurações exibidas na página de entrada do Windows PowerShell Web Access. Você pode configurar valores no arquivo **web.config** descrito no parágrafo anterior. Valores padrão para configurações de página de entrada são encontrados na seção **appSettings** do arquivo web.config; a seguir, um exemplo da seção **appSettings**. Os valores válidos para muitas dessas configurações são os mesmos para os parâmetros correspondentes do cmdlet [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) no Windows PowerShell. Por exemplo, a chave <span class="code">defaultApplicationName</span>, conforme mostrado no seguinte bloco de código, é o valor da variável preferência **$PSSessionApplicationName** no computador de destino.

[Cópia](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_6ccfd0a1-485a-4ac5-9636-89ebab501bef'); "Copy to clipboard.")

    <appSettings>
            <add key="maxSessionsAllowedPerUser" value="3"/>
            <add key="defaultPortNumber" value="5985"/>
            <add key="defaultSSLPortNumber" value="5986"/>
            <add key="defaultApplicationName" value="WSMAN"/>
            <add key="defaultUseSslSelection" value="0"/>
            <add key="defaultAuthenticationType" value="0"/>
            <add key="defaultAllowRedirection" value="0"/>
            <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
    </appSettings>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Tempos limite e desconexões não planejadas</span></a>

------------------------------------------------------------------------

Atingido o tempo limite das sessões do Windows PowerShell Web Access. No Windows PowerShell Web Access em execução no Windows Server 2012, uma mensagem de tempo limite é exibida aos usuários conectados após 15 minutos de inatividade da sessão. Se o usuário não responder em até cinco minutos após a exibição dessa mensagem, a sessão será encerrada e o usuário será desconectado. Você pode alterar os períodos de tempo limite para sessões nas configurações do site no Gerenciador do IIS.

No Windows PowerShell Web Access em execução no Windows Server 2012 R2, as sessões atingem seu tempo limite, por padrão, após 20 minutos de inatividade. Se os usuários forem desconectados de sessões no console baseado na Web devido a erros de rede ou outros desligamentos ou falhas não planejados, e não porque eles fecharam as sessões, as sessões do Windows PowerShell Web Access continuam em execução, conectadas aos computadores de destino, até decorrer o tempo limite do lado do cliente. A sessão é desconectada após um padrão de 20 minutos ou após o período de tempo limite especificado pelo administrador do gateway, o que for menor.

Se o servidor de gateway estiver executando Windows Server 2012 R2, o Windows PowerShell Web Access permitirá que os usuários se reconectem a sessões salvas mais tarde, mas quando erros de rede, desligamentos não planejados ou outras falhas desconectam as sessões, os usuários não podem ver nem se reconectar a sessões salvas até ter expirado o tempo limite especificado pelo administrador do gateway.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Consulte Também</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Instalar e usar o Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
[Cmdlets do Windows PowerShell Web Access](https://technet.microsoft.com/library/hh918342.aspx)

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


