---
ms.date: 06/27/2017
keywords: powershell, cmdlet
title: Regras de autorização e recursos de segurança do Windows PowerShell Web Access
ms.openlocfilehash: c426b8cfb10829241ba244a5d840c91e1de9f66e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675891"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Regras de autorização e recursos de segurança do Windows PowerShell Web Access

Atualizado em: 24 de junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

O Windows PowerShell Web Access no Windows Server 2012 R2 e no Windows Server 2012 tem um modelo de segurança restritivo. Os usuários devem ter acesso explícito antes de entrar no gateway do Windows PowerShell Web Access e usar o console do Windows PowerShell baseado na Web.

## <a name="configuring-authorization-rules-and-site-security"></a>Configurando regras de autorização e segurança do site

Depois que o Windows PowerShell Web Access for instalado e o gateway configurado, os usuários poderão abrir a página de entrada em um navegador, mas só poderão entrar depois que o administrador do Windows PowerShell Web Access conceder a eles acesso explicitamente. O controle de acesso do ‘Windows PowerShell Web Access’ é gerenciado por meio de um conjunto de cmdlets do Windows PowerShell descritos na tabela a seguir. Não há uma GUI comparável para adicionar ou gerenciar regras de autorização.
Consulte [Cmdlets do Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Os administradores podem definir as regras de autenticação `{0-n}` para o Windows PowerShell Web Access. A segurança padrão é restritiva, não permissiva. Se não houver regras de autenticação, significa que nenhum usuário tem acesso a coisa alguma.

[Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) e [Test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) no Windows Server 2012 R2 incluem um parâmetro Credential que permite adicionar e testar regras de autorização do Windows PowerShell Web Access por meio de um computador remoto ou de uma sessão ativa do Windows PowerShell Web Access. Assim como com outros cmdlets do Windows PowerShell que têm um parâmetro Credential, você pode especificar um objeto PSCredential como o valor do parâmetro. Para criar um objeto PSCredential que contenha credenciais que você deseja passar para um computador remoto, execute o cmdlet [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential).

Regras de autenticação do Windows PowerShell Web Access são regras da lista de permissões. Cada regra é uma definição de uma conexão permitida entre usuários, computadores de destino e [configurações de sessão](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) do Windows PowerShell específicas (também mencionadas como pontos de extremidade ou _runspaces_) em computadores de destino especificados.
Para obter uma explicação sobre **runspaces** consulte [Começando a usar runspaces do PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> Um usuário só precisa de uma regra para obter acesso. Se um usuário receber acesso a um computador com acesso completo a linguagem ou acesso somente a cmdlets de gerenciamento remoto do Windows PowerShell, do console baseado na Web, o usuário poderá fazer logon (ou saltar) para outros computadores conectados ao primeiro computador de destino. A maneira mais segura de configurar o Windows PowerShell Web Access é permitir o acesso aos usuários apenas a configurações de sessão restritas, que permitem realizar tarefas específicas que normalmente precisam ser executadas remotamente.

Os cmdlets referenciados em [Cmdlets do Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) permitem criar um conjunto de regras de acesso que são usadas para autorizar um usuário no gateway do Windows PowerShell Web Access. As regras são diferentes das listas de controle de acesso (ACLs) no computador de destino e fornecem uma camada adicional de segurança para acesso à Web. A seção a seguir contém mais detalhes sobre segurança.

Se os usuários não puderem passar por nenhuma das camadas de segurança anteriores, eles receberão uma mensagem genérica de "acesso negado" na janela do navegador. Embora os detalhes de segurança sejam registrador no servidor do gateway, os usuários finais não recebem informações sobre quantas camadas de segurança eles ultrapassaram, ou em qual camada ocorreu a falha de logon ou autenticação.

Para obter mais informações de como configurar regras de autorização, consulte [Configurando regras de autorização](#configuring-authorization-rules-and-site-security) neste tópico.

### <a name="security"></a>Segurança

O modelo de segurança do Windows PowerShell Web Access tem quatro camadas entre um usuário final do console baseado na Web e um computador de destino. Os administradores do Windows PowerShell Web Access podem adicionar camadas de segurança por meio de configuração adicional no console do Gerenciador do IIS. Para saber mais sobre como proteger sites no console do Gerenciador do IIS, consulte [Configurar a segurança do servidor Web (IIS 7)](https://technet.microsoft.com/library/cc731278).

Para obter mais informações sobre práticas recomendadas do IIS e sobre como evitar ataques de negação de serviço, consulte [Best Practices for Preventing DoS/Denial of Service Attacks (Práticas recomendadas para evitar ataques DoS/de negação de serviço)](https://technet.microsoft.com/library/cc750213).
Um administrador também pode comprar e instalar outros softwares de autenticação do varejo.

A tabela a seguir descreve as quatro camadas de segurança entre os usuários finais e os computadores de destino.

|Nível|Camada|
|-|-|
|1|[recursos de segurança do servidor Web do IIS](#iis-web-server-security-features)|
|2|[autenticação de gateway baseada em formulários do Windows PowerShell Web Access](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[regras de autorização do Windows PowerShell Web Access](#windows-powershell-web-access-authorization-rules)|
|4|[regras de autorização e autenticação de destino](#target-authentication-and-authorization-rules)|

Informações detalhadas sobre cada camada podem ser encontradas nos seguintes títulos:

#### <a name="iis-web-server-security-features"></a>Recursos de segurança do servidor Web do IIS

Os usuários do Windows PowerShell Web Access sempre devem fornecer um nome de usuário e uma senha para autenticar suas contas no gateway. No entanto, os administradores do Windows PowerShell Web Access também podem ativar ou desativar a autenticação de certificado opcional do cliente, consulte [instalar e usar o Windows PowerShell Web Access](install-and-use-windows-powershell-web-access.md) para habilitar um certificado de teste e, posteriormente, como configurar um certificado original.

O recurso opcional de certificado de cliente exige que os usuários finais tenham um certificado de cliente válido (além de seus nomes de usuário e senhas) e faz parte da configuração do Servidor Web (IIS). Quando a camada de certificados cliente estiver habilitada, a página de entrada do Windows PowerShell Web Access solicitará que os usuários forneçam certificados válidos antes que suas credenciais de entrada sejam avaliadas. A autenticação de certificados clientes verifica automaticamente o certificado de cliente. Se um certificado válido não for encontrado, o Windows PowerShell Web Access informará os usuários a respeito, para que eles possam fornecer o certificado. Se um certificado de cliente válido for encontrado, o Windows PowerShell Web Access abrirá a página de entrada para que os usuários forneçam seus respectivos nomes de usuário e suas senhas.

Este é um exemplo de configurações de segurança adicionais oferecidas pelo servidor Web do IIS. Para saber mais sobre outros recursos de segurança do IIS, confira [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278) (Configurar a segurança do servidor Web (IIS 7)).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Autenticação de gateway baseada em formulários do Windows PowerShell Web Access

A página de entrada do Windows PowerShell Web Access requer um conjunto de credenciais (nome de usuário e senha) e oferece aos usuários a opção de fornecer outras credenciais para o computador de destino.
Se o usuário não fornecer credenciais alternativas, o nome de usuário primário e a respectiva senha usados para conexão com o gateway também serão utilizados para se conectar ao computador cliente.

As credenciais necessárias são autenticadas no gateway do Windows PowerShell Web Access. Essas credenciais devem ser contas de usuário válidas no servidor de gateway local do Windows PowerShell Web Access ou no Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Regras de autorização do Windows PowerShell Web Access

Depois que um usuário é autenticado no gateway, o Windows PowerShell Web Access verifica as regras de autorização para confirmar se o usuário tem acesso ao computador de destino solicitado. Após a autorização bem-sucedida, as credenciais do usuário são passadas para o computador de destino.

Essas regras serão avaliadas apenas depois que um usuário for autenticado pelo gateway e antes de ser autenticado em um computador de destino.

#### <a name="target-authentication-and-authorization-rules"></a>Autenticação de destino e regras de autorização

A camada final de segurança do Windows PowerShell Web Access é a própria configuração de segurança do computador de destino. Os usuários devem ter os direitos de acesso apropriados configurados no computador de destino e nas regras de autorização do Windows PowerShell Web Access para executar um console do Windows PowerShell baseado na Web que afete um computador de destino via Windows PowerShell Web Access.

Essa camada oferece os mesmos mecanismos de segurança que avaliariam tentativas de conexão se usuários tentassem criar uma sessão remota do Windows PowerShell para um computador de destino por meio do Windows PowerShell, executando os cmdlets [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) ou [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession).

Por padrão, o Windows PowerShell Web Access usa o nome de usuário principal e a respectiva senha para autenticação no gateway e no computador de destino. A página de entrada baseada na Web, em uma seção intitulada **Configurações opcionais de conexão**, oferece ao usuário a opção de fornecer outras credenciais para o computador de destino, caso necessário. Se o usuário não fornecer credenciais alternativas, o nome de usuário primário e a respectiva senha usados para conexão com o gateway também serão utilizados para se conectar ao computador cliente.

As regras de autorização podem ser usadas para permitir que os usuários acessem uma configuração de sessão específica. Você pode criar configurações de sessão ou _runspaces restritos_ para o Windows PowerShell Web Access e permitir que usuários específicos se conectem apenas a configurações de sessão específicas quando entrarem no Windows PowerShell Web Access. Você pode usar ACLs (listas de controle de acesso) para determinar quais usuários têm acesso a pontos de extremidade específicos e restringir ainda mais o acesso ao ponto de extremidade para um conjunto específico de usuários, usando as regras de autorização descritas nesta seção. Para obter mais informações sobre runspaces restritos, consulte [Creating a constrained runspace](https://msdn.microsoft.com/library/dn614668) (Criando um runspace restrito).

### <a name="configuring-authorization-rules"></a>Configurando regras de autorização

Provavelmente os administradores querem a mesma regra de autorização para usuários do Windows PowerShell Web Access que já estejam definidas no ambiente de gerenciamento remoto do Windows PowerShell. O primeiro procedimento nesta seção descreve como adiciona uma regra de autorização segura que concede acesso a um usuário (que faz logon para gerenciar um computador) em uma única configuração de sessão. O segundo procedimento descreve como remover uma regra de autorização que não é mais necessária.

Se você pretende usar configurações de sessão personalizadas para permitir que usuários específicos trabalhem apenas dentro de runspaces restritos no Windows PowerShell Web Access, crie configurações de sessão personalizadas antes de adicionar regras de autorização que façam referência a elas. Não é possível usar os cmdlets do Windows PowerShell Web Access para criar configurações de sessão personalizadas. Para saber mais de como criar configurações de sessão personalizadas, confira [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Os cmdlets do Windows PowerShell Web Access dão suporte a um caractere curinga, o asterisco ( \* ). Não há suporte aos caracteres-curinga com cadeias. Use um asterisco pro propriedade (usuários, computadores ou configurações de sessão).

> [!NOTE]
> Para saber outras formas de usar regras de autorização para conceder acesso a usuários e ajudar a proteger o ambiente do Windows PowerShell Web Access, consulte [Outros exemplos de cenários de regras de autorização](#other-authorization-rule-scenario-examples) neste tópico.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Para adicionar uma regra de autorização restritiva

1. Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados.

   - Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.

   - Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.

2. **Etapa opcional** Para restringir o acesso de usuários usando configurações de sessão:

   Verifique se as configurações de sessão que você deseja usar já existem em suas regras.

   Se elas ainda não foram criadas, siga as instruções de como criar configurações de sessão em [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Essa regra de autorização permite que um usuário específico acesse um computador na rede ao qual tipicamente tem acesso, com acesso a uma configuração de sessão específica, voltada para suas necessidades típicas de script e cmdlet. Digite o seguinte e pressione **Enter**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - No exemplo a seguir, um usuário nomeado _JSmith_ no domínio _Contoso_ ganha acesso para gerenciar o computador _Contoso_214_ e usa uma configuração de sessão nomeada _NewAdminsOnly_.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Verifique se a regra foi criada executando o cmdlet **Get-PswaAuthorizationRule**, ou `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`.
   Por exemplo, `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Para remover uma regra de autorização

1. Se uma sessão do Windows PowerShell ainda não estiver aberta, consulte a etapa 1 de [Para adicionar uma regra de autorização restritiva](#to-add-a-restrictive-authorization-rule) nesta seção.

2. Digite o seguinte e pressione **Enter**, em que *ID da regra* representa o número da ID exclusiva que você deseja remover.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   De forma alternativa, se você não souber o número da ID, mas souber o nome amigável da regra que deseja remover, poderá obter o nome da regra e redirecioná-la para o cmdlet `Remove-PswaAuthorizationRule` para remover a regra, como mostrado no seguinte exemplo:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> Você não precisará confirmar se deseja excluir a regra de autorização especificada; a regra será excluída quando você pressionar **Enter**. Verifique se deseja remover a regra de autorização antes de executar o cmdlet `Remove-PswaAuthorizationRule`.

#### <a name="other-authorization-rule-scenario-examples"></a>Outros exemplos de cenários de regras de autorização

Toda sessão do Windows PowerShell usa uma configuração de sessão. Se não houver nenhuma configuração especificada para uma sessão, o Windows PowerShell usará a configuração de sessão interna padrão do Windows PowerShell, chamada Microsoft.PowerShell. A configuração de sessão padrão inclui todos os cmdlets disponíveis em um computador. Os administradores podem restringir o acesso a todos os computadores definindo uma sessão de configuração com um runspace restrito (um intervalo limitado de cmdlets e tarefas que seus usuários finais podem executar). Um usuário com acesso a um computador com acesso à linguagem completa ou somente aos cmdlets de gerenciamento remoto do Windows PowerShell poderá se conectar a outros computadores conectados ao primeiro computador. A definição de um runspace restrito pode evitar que usuários acessem outros computadores do runspace permitido do Windows PowerShell e aumentará a segurança do seu ambiente do Windows PowerShell Web Access. A configuração de sessão pode ser distribuída (por meio de Política de Grupo) entre todos os computadores que os administradores desejam tornar acessíveis através do Windows PowerShell Web Access. Para saber mais sobre configurações de sessão, confira [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx). Veja a seguir alguns exemplos desse cenário.

- Um administrador cria um ponto de extremidade, chamado **PswaEndpoint**, com um runspace restrito. Em seguida, o administrador cria uma regra, `*,*,PswaEndpoint` e distribui o ponto de extremidade para outros computadores. A regra permite o acesso de todos os usuários a todos os computadores com o ponto de extremidade **PswaEndpoint**.
  Se essa for a única regra de autorização definida no conjunto de regras, os computadores sem esse ponto de extremidade não poderão ser acessados.

- O administrador criou um ponto de extremidade com um runspace restrito chamado **PswaEndpoint** e deseja restringir o acesso a usuários específicos. O administrador cria um grupo de usuários chamado **Level1Support** e define a seguinte regra: **Level1Support,\*,PswaEndpoint**. A regra concede acesso a todos os usuários no grupo **Level1Support** a todos os computadores com a configuração **PswaEndpoint**. De modo semelhante, o acesso pode ser restrito a um conjunto específico de computadores.

- Alguns administradores concedem a certos usuários mais acesso do que outros. Por exemplo, um administrador cria dois grupos de usuários: **Admins** e **BasicSupport**. O administrador também cria um ponto de extremidade com um runspace restrito chamado **PswaEndpoint** e define duas regras: **Admins,\*,\*** e **BasicSupport,\*,PswaEndpoint**. A primeira regra fornece a todos os usuários do grupo **Admin** acesso a todos os computadores e a segunda regra fornece a todos os usuários do grupo **BasicSupport** acesso apenas aos computadores com **PswaEndpoint**.

- Um administrador configurou um ambiente de teste privado e deseja permitir que todos os usuários da rede autorizados acessem todos os computadores na rede aos quais têm acesso normalmente, com acesso a todas as configurações de sessão que acessam tipicamente. Como esse é um ambiente de teste privado, o administrador cria uma regra de autorização que não é segura. - O administrador executa o cmdlet `Add-PswaAuthorizationRule * * *`, que usa o caractere curinga **\*** para representar todos os usuários, todos os computadores e todas as configurações. - Essa regra equivale ao seguinte: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Essa regra não é recomendada em um ambiente seguro. Ela ignora a camada de segurança de regras de autorização fornecida pelo Windows PowerShell Web Access.

- Um administrador deve permitir que os usuários se conectem a computadores de destino em um ambiente que inclua tanto grupos de trabalho quanto domínios, onde os computadores de grupos de trabalho sejam ocasionalmente usados para se conectar a computadores de destino em domínios, e os computadores em domínios sejam ocasionalmente usados para se conectar a computadores de destino em grupos de trabalho. O administrador tem um servidor de gateway, *PswaServer*, em um grupo de trabalho; e o computador de destino *srv1.contoso.com* está em um domínio. O usuário *Chris* é um usuário local autorizado tanto no servidor de gateway de grupo de trabalho quanto no computador de destino. Seu nome de usuário no servidor de grupo de trabalho é *carlosLocal* e seu nome de usuário no computador de destino é *contoso\\carlos*. Para autorizar o acesso de Carlos a srv1.contoso.com, o administrador adiciona a regra a seguir.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

O exemplo da regra anterior autentica Carlos no servidor de gateway e depois autoriza seu acesso ao *srv1*. Na página de entrada, Carlos deve fornecer um segundo conjunto de credenciais na área **Configurações de conexão opcional** (*contoso\\carlos*). O servidor de gateway usa o conjunto adicional de credenciais para efetuar a autenticação do usuário no computador de destino, *srv1.contoso.com*.

No cenário anterior, o Windows PowerShell Web Access só estabelece uma conexão bem-sucedida com o computador de destino quando as etapas a seguir são executadas com êxito e quando ele é autorizado por pelo menos uma regra de autorização.

1. Autenticação no servidor de gateway de grupo de trabalho adicionando um nome de usuário no formato *nome_do_servidor*\\*nome_de_usuário* à regra de autorização

2. Autenticação no computador de destino usando credenciais alternativas fornecidas na página de entrada, na área **Configurações opcionais de conexão**

   > [!NOTE]
   > Se o gateway e os computadores de destino estiverem em domínios ou grupos de trabalho diferentes, uma relação de confiança deverá ser estabelecida entre os dois computadores de grupo de trabalho, entre os dois domínios ou entre o grupo de trabalho e o domínio. Essa relação não pode ser configurada usando cmdlets de regras de autorização do Windows PowerShell Web Access. As regras de autorização não definem uma relação de confiança entre computadores. Elas só podem autorizar usuários a se conectar a computadores de destino e a configurações de sessão específicos. Para obter mais informações sobre como configurar uma relação de confiança entre diferentes domínios, consulte [Criando relações de confiança entre domínios e florestas](https://technet.microsoft.com/library/cc794775.aspx).
   > Para obter mais informações sobre como adicionar computadores de grupo de trabalho a uma lista de hosts confiáveis, consulte [Gerenciamento remoto com o Gerenciador do Servidor](https://technet.microsoft.com/library/dd759202.aspx).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Usando um único conjunto de regras de autorização para vários sites

As regras de autorização são armazenadas em um arquivo XML. Por padrão, o nome do caminho do arquivo XML é `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

O caminho para o arquivo XML de regras de autorização é armazenado no arquivo **powwa.config**, encontrado em `$env:windir\Web\PowershellWebAccess\data`. O administrador pode alterar a referência ao caminho padrão em **powwa.config** de acordo com preferências ou requisitos. O fato de o administrador poder alterar a localização do arquivo permite que muitos gateways do Windows PowerShell Web Access usem as mesmas regras de autorização, caso essa configuração seja necessária.

## <a name="session-management"></a>Gerenciamento de sessões

Por padrão, o Windows PowerShell Web Access limita um usuário a três sessões ao mesmo tempo. Você pode editar o arquivo **web.config** do aplicativo Web no Gerenciador do IIS para dar suporte a um número diferente de sessões por usuário. O caminho para o arquivo **web.config** é `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

Por padrão, o servidor Web do IIS é configurado para reiniciar o pool de aplicativos quando alguma configuração é editada. Por exemplo, o pool de aplicativos é reiniciado quando são feitas alterações no arquivo **web.config**. >Como o **Windows PowerShell Web Access** usa estados de sessão na memória, >os usuários conectados a sessões do **Windows PowerShell Web Access** perdem suas sessões quando o pool de aplicativos é reiniciado.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Configurando parâmetros padrão na página de entrada

Se o gateway do Windows PowerShell Web Access estiver em execução no Windows Server 2012 R2, você poderá configurar valores padrão para as configurações exibidas na página de entrada do Windows PowerShell Web Access. Você pode configurar valores no arquivo **web.config** descrito no parágrafo anterior. Valores padrão para configurações de página de entrada são encontrados na seção **appSettings** do arquivo web.config; a seguir, um exemplo da seção **appSettings**. Os valores válidos para muitas dessas configurações são os mesmos para os parâmetros correspondentes do cmdlet [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) no Windows PowerShell.

Por exemplo, a chave `defaultApplicationName`, mostrada no bloco de código a seguir, é o valor da variável preferencial **$PSSessionApplicationName** no computador de destino.

```xml
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
```

### <a name="time-outs-and-unplanned-disconnections"></a>Tempos limite e desconexões não planejadas

Atingido o tempo limite das sessões do Windows PowerShell Web Access. No Windows PowerShell Web Access em execução no Windows Server 2012, uma mensagem de tempo limite é exibida aos usuários conectados após 15 minutos de inatividade da sessão. Se o usuário não responder em até cinco minutos após a exibição dessa mensagem, a sessão será encerrada e o usuário será desconectado. Você pode alterar os períodos de tempo limite para sessões nas configurações do site no Gerenciador do IIS.

No Windows PowerShell Web Access em execução no Windows Server 2012 R2, as sessões atingem seu tempo limite, por padrão, após 20 minutos de inatividade. Se os usuários forem desconectados de sessões no console baseado na Web devido a erros de rede ou outros desligamentos ou falhas não planejados, e não porque eles fecharam as sessões, as sessões do Windows PowerShell Web Access continuam em execução, conectadas aos computadores de destino, até decorrer o tempo limite do lado do cliente. A sessão é desconectada após um padrão de 20 minutos ou após o período de tempo limite especificado pelo administrador do gateway, o que for menor.

Se o servidor de gateway estiver executando Windows Server 2012 R2, o Windows PowerShell Web Access permitirá que os usuários se reconectem a sessões salvas mais tarde, mas quando erros de rede, desligamentos não planejados ou outras falhas desconectam as sessões, os usuários não podem ver nem se reconectar a sessões salvas até ter expirado o tempo limite especificado pelo administrador do gateway.

## <a name="see-also"></a>Consulte Também

[Instalar e usar o Windows PowerShell Web Access](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Cmdlets do Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
