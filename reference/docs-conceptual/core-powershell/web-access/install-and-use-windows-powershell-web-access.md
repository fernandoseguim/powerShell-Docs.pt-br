---
ms.date: 2017-08-23
keywords: PowerShell, cmdlet
title: instalar e usar o windows powershell web access
ms.openlocfilehash: a4b812e2aa32450bc68f761e7b85e8f2ee2b34ee
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2017
---
# <a name="install-and-use-windows-powershell-web-access"></a>Instalar e usar o Windows PowerShell Web Access

Atualizado em: 5 de novembro de 2013 (editado em: 23 de agosto de 2017)

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Introdução

Introduzido pela primeira vez no Windows Server 2012, o Windows PowerShell Web Access age como um gateway do Windows PowerShell, oferecendo um console baseado na Web do Windows PowerShell destinado a um computador remoto. Ele permite aos profissionais de TI executar comandos e scripts no console do Windows PowerShell em um navegador da Web, sem necessidade de instalar o Windows PowerShell, software de gerenciamento remoto ou plug-in de navegador no dispositivo cliente. Para executar o console do Windows PowerShell baseado na Web, basta um gateway do Windows PowerShell Web Access devidamente configurado e um navegador de dispositivo cliente que dê suporte a JavaScript e aceite cookies.

Exemplos de dispositivos clientes: laptops, computadores pessoais não usados para trabalho, computadores emprestados, tablets, quiosques Web, computadores que não executam sistemas operacionais baseados em Windows e navegadores de celulares. Os profissionais de TI podem realizar tarefas essenciais de gerenciamento em servidores remotos baseados em Windows a partir de dispositivos com acesso a uma conexão com a Internet e um navegador da Web.

Depois de instalar e configurar o gateway com sucesso, os usuários podem acessar um console do Windows PowerShell usando um navegador da Web. Quando os usuários abrem o site seguro do Windows PowerShell Web Access, eles podem executar um console do Windows PowerShell baseado na Web após autenticação bem-sucedida.

O processo de instalação e configuração do Windows PowerShell Web Access inclui três etapas:

1. [Instalar o Windows PowerShell Web Access](#install-windows-powershell-web-access)
1. [Configurar o Gateway](#configure-the-gateway)
1. [Configurar uma regra de autorização restritiva](#configure-a-restrictive-authorization-rule)

Antes de instalar e configurar o Windows PowerShell Web Access, recomendamos ler todo este guia, o qual inclui instruções sobre como instalar, proteger e desinstalar o Windows PowerShell Web Access.
O tópico [Usar o console do Windows PowerShell baseado na Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) descreve como os usuários entram no console baseado na Web, além de abordar limitações e as diferenças entre o console do Windows PowerShell baseado na web e o console **powershell.exe**. Os usuários finais do console baseado na Web devem ler o artigo [Usar o console do Windows PowerShell baseado na Web](use-the-web-based-windows-powershell-console.md), mas não precisam ler o restante desse guia.

Este tópico não fornece diretrizes detalhadas de operações do Servidor Web IIS. Apenas as etapas necessárias para configurar o gateway do Windows PowerShell Web Access estão descritas neste tópico. Para obter mais informações sobre como configurar e proteger sites no IIS, consulte os recursos da documentação do IIS na seção Consulte também.

O diagrama a seguir mostra como funciona o Windows PowerShell Web Access.

![Diagrama de Acesso via Web do Windows PowerShell](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Requisitos de execução do Windows PowerShell Web Access

O Windows PowerShell Web Access requer um servidor Web (IIS), .NET Framework 4.5 e o Windows PowerShell 3.0 ou Windows PowerShell 4.0 em execução no servidor no qual você deseja executar o gateway. Você pode instalar o Windows PowerShell Web Access em um servidor que está executando o Windows Server 2012 R2 ou o Windows Server 2012 usando o Assistente Adicionar Funções e Recursos no Gerenciador do Servidor ou cmdlets de implantação do Windows PowerShell para o Gerenciador do Servidor. Quando você instala o Windows PowerShell Web Access usando o Gerenciador do Servidor ou seus cmdlets de implantação, as funções e os recursos necessários são automaticamente adicionados como parte do processo de instalação.

O Windows PowerShell Web Access permite que usuários remotos acessem computadores em sua organização usando o Windows PowerShell em um navegador da Web. Embora o Windows PowerShell Web Access seja uma ferramenta de gerenciamento avançada e conveniente, o acesso baseado na Web impõe riscos à segurança e deve ser configurado da maneira mais segura possível. Recomendamos que os administradores que configuram o gateway do Windows PowerShell Web Access usem as camadas de segurança disponíveis, as regras de autorização baseadas em cmdlets incluídas no Windows PowerShell Web Access e as camadas de segurança disponíveis no Servidor Web (IIS) e em aplicativos de terceiros. Esta documentação inclui exemplos desprotegidos, recomendados apenas para ambientes de teste, além de exemplos recomendados para implantações seguras.

## <a name="browser-and-client-device-support"></a>Suporte a navegadores e dispositivos clientes

O Windows PowerShell Web Access dá suporte aos seguintes navegadores da Internet.
Embora navegadores móveis não tenham suporte oficialmente, muitos poderão executar o console do Windows PowerShell baseado na Web. É provável que outros navegadores que aceitam cookies, executam JavaScript e abrem sites HTTPS funcionam, mas não foram oficialmente testados.

### <a name="supported-desktop-computer-browsers"></a>Navegadores de desktop compatíveis

- Windows Internet Explorer para Microsoft Windows 8.0, 9.0, 10.0 e 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m para Windows
- Apple Safari 5.1.2 para Windows
- Apple Safari 5.1.2 para Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Dispositivos ou navegadores móveis minimamente testados

- Windows Phone 7 e 7.5
- Navegador Google Android WebKit 3.1 Android 2.2.1 (Kernel 2.6)
- Apple Safari para iPhone com sistema operacional 5.0.1
- Apple Safari para iPad 2 com sistema operacional 5.0.1

### <a name="browser-requirements"></a>Requisitos de navegador

Para usar o console do Windows PowerShell Web Access baseado na Web, os navegadores devem executar os procedimentos a seguir.

- Permitir cookies do site do gateway do Windows PowerShell Web Access.
- Ser capazes de abrir e ler páginas HTTPS.
- Abrir e executar sites que usam JavaScript.

## <a name="recommended-quick-deployment"></a>Implantação rápida recomendada

Você pode instalar o gateway do Windows PowerShell Web Access em um servidor que está executando o Windows Server 2012 R2 ou o Windows Server 2012 usando o cmdlets do Windows PowerShell ou o assistente Adicionar Funções e Recursos que é aberto no Gerenciador do Servidor. Para rápida instalação e configuração, use os cmdlets do Windows PowerShell, conforme descrito nesta seção.

1. [Instalar o Windows PowerShell Web Access](#install-Windows-powershell-web-access)
1. [Configurar o Gateway](#configure-the-gateway)
1. [Configurar uma regra de autorização restritiva](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access"></a>Instalar o Windows PowerShell Web Access

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Para instalar o Windows PowerShell Web Access usando cmdlets do Windows PowerShell

1. Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados.
    - Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.
    - Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.

    >**![Observação](images/note.jpeg) Observação** No Windows PowerShell 3.0 e 4.0, não é preciso importar o módulo de cmdlet do Gerenciador do Servidor para a sessão do Windows PowerShell antes de executar os cmdlets que fazem parte do módulo. Um módulo é importado automaticamente durante a primeira execução de um cmdlet que faça parte do módulo. Além disso, os cmdlets do Windows PowerShell não diferenciam maiúsculas de minúsculas.

1. Digite o seguinte e pressione **Enter**, em que *computer_name* representa um computador remoto no qual você deseja instalar o Windows PowerShell Web Access, se aplicável. O parâmetro `-Restart` reinicia automaticamente os servidores de destino, se necessário.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   >**![Observação](images/note.jpeg) Observação**
   >
   >A instalação do Windows PowerShell Web Access usando cmdlets do Windows PowerShell não adiciona ferramentas de gerenciamento do Servidor Web (IIS) por padrão. Se você deseja instalar as ferramentas de gerenciamento no mesmo servidor que o gateway do Windows PowerShell Web Access, adicione o parâmetro `-IncludeManagementTools` ao comando de instalação (como fornecido nesta etapa). Se você estiver gerenciando o site do Windows PowerShell Web Access de um computador remoto, instale o snap-in do Gerenciador do IIS ao instalar as [Ferramentas de Administração de Servidor Remoto para Windows 8.1](http://go.microsoft.com/fwlink/?LinkID=304145) ou as [Ferramentas de Administração de Servidor Remoto para Windows 8](http://go.microsoft.com/fwlink/p/?LinkID=238560) no computador do qual deseja gerenciar o gateway.
   
   Para instalar funções e recursos em um VHD offline, adicione os parâmetros `-ComputerName` e `-VHD`. O parâmetro `-ComputerName` contém o nome do servidor em que será montado o VHD, e o parâmetro `-VHD` contém o caminho para o arquivo VHD no servidor especificado.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Quando a instalação for concluída, verifique se o Windows PowerShell Web Access foi instalado nos servidores de destino executando o cmdlet **Get-WindowsFeature** em um servidor de destino, em um console do Windows PowerShell que foi aberto com direitos do usuário elevados. Também será possível verificar se o Windows PowerShell Web Access foi instalado no console do Gerenciador do Servidor, selecionando um servidor de destino na página **Todos os Servidores** e exibindo o bloco **Funções e Recursos** do servidor selecionado. Você também pode exibir o arquivo Leiame para o Windows PowerShell Web Access.

1. Após a instalação do Windows PowerShell Web Access, você será solicitado a examinar o arquivo Leiame, que contém instruções de configuração básicas e necessárias para o gateway. Essas instruções de instalação também estão na seção a seguir, [Configurar o Gateway](#configure-the-gateway). O caminho para o arquivo Leiame é **C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt**.

### <a name="configure-the-gateway"></a>Configurar o Gateway

O cmdlet **Install-PswaWebApplication** é uma maneira rápida de configurar o Windows PowerShell Web Access. Embora seja possível adicionar o parâmetro `UseTestCertificate` ao cmdlet `Install-PswaWebApplication` para instalar um certificado SSL autoassinado para fins de teste, isso não é seguro. Para um ambiente de produção seguro, sempre use um certificado SSL válido assinado por uma AC (autoridade de certificação).
Os administradores podem substituir o certificado de teste por um certificado assinado de sua preferência usando o console do Gerenciador do IIS.

Você pode concluir a configuração do aplicativo Web Windows PowerShell Web Access executando o cmdlet `Install-PswaWebApplication` ou seguindo as etapas de configuração baseadas em GUI no Gerenciador do IIS. Por padrão, o cmdlet instala o aplicativo Web, o **pswa** (e um pool de aplicativos para ele, **pswa_pool**), no contêiner **Site Padrão**, como mostrado no Gerenciador do IIS. Se quiser, você poderá instruir o cmdlet a alterar o contêiner do site padrão do aplicativo Web. O Gerenciador do IIS oferece opções de configuração disponíveis para aplicativos Web, como alteração do número da porta ou do certificado SSL (Secure Sockets Layer).

>**![Observação de segurança](images/securitynote.jpeg) Observação de segurança**
> 
>Recomendamos enfaticamente que os administradores configurem o gateway para usar um certificado válido assinado por uma CA. 

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Para configurar o gateway do Windows PowerShell Web Access com um certificado de teste usando Install-PswaWebApplication

1. Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell.

    - Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas.

    - Na tela **Iniciar** do Windows, clique em **Windows PowerShell**.

2. Digite o seguinte e pressione **Enter**.

    **Install-PswaWebApplication -UseTestCertificate**

  >**![Observação de segurança](images/securitynote.jpeg) Observação de segurança**
  >
  >O parâmetro `UseTestCertificate` só deve ser usado em um ambiente de teste privado. Para um ambiente de produção seguro, recomendamos usar um certificado válido assinado por uma AC.

Quando o cmdlet é executado, o aplicativo web Windows PowerShell Web Access é instalado no contêiner Site Padrão do IIS. O cmdlet cria a infraestrutura necessária para executar o Windows PowerShell Web Access no site padrão, `https://<server_name>/pswa`. Para instalar o aplicativo Web em outro site, forneça o nome do site adicionando o parâmetro `WebSiteName`. Para alterar o nome do aplicativo Web (o padrão é `pswa`), adicione o parâmetro `WebApplicationName` .

As configurações a seguir são feitas executando o cmdlet. Você pode alterá-las manualmente no console do Gerenciador do IIS, se desejado.

- Caminho: /pswa
- ApplicationPool: pswa_pool
- EnabledProtocols: http
- PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

**Exemplo**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

Neste exemplo, o site resultante do Windows PowerShell Web Access é https://\<*nome_do_servidor*\>/myWebApp.

>**![Observação](images/note.jpeg) Observação** 
> 
>Você não poderá fazer logon até que todos os usuários tenham obtido acesso ao site adicionando regras de autorização. Para obter mais informações, consulte [Configurar uma regra de autorização restritiva](#configure-a-restrictive-authorization-rule) e [Regras de autorização e recursos de segurança do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Para configurar o gateway do Windows PowerShell Web Access com um certificado original usando o Install-PswaWebApplication e o Gerenciador do IIS

1. Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell.

    - Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas.

    - Na tela **Iniciar** do Windows, clique em **Windows PowerShell**.

2. Digite o seguinte e pressione **Enter**.

    **Install-PswaWebApplication**

    As configurações de gateway a seguir são feitas executando o cmdlet.
    Você pode alterá-las manualmente no console do Gerenciador do IIS, se desejado.
    Também é possível especificar valores para os parâmetros `WebsiteName` e `WebApplicationName` do cmdlet `Install-PswaWebApplication`.

    - Caminho: /pswa

    - ApplicationPool: pswa_pool

    - EnabledProtocols: http

    - PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

3. Abra o console do Gerenciador do IIS seguindo um destes procedimentos.

    - Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows. No menu **Ferramentas** no Gerenciador do Servidor, clique em **Gerenciador do IIS (Serviços de Informações da Internet)**.

    - Na tela **Iniciar** do Windows, clique em **Gerenciador do Servidor**.

4. No painel de árvore do Gerenciador do IIS, expanda o nó do servidor no qual o Windows PowerShell Web Access está instalado até que a pasta **Sites** fique visível. Expanda a pasta **Sites**.

5. Selecione o site no qual você instalou o aplicativo Web Windows PowerShell Web Access. No painel **Ações**, clique em **Associações**.

6. Na caixa de diálogo **Associação do Site**, clique em **Adicionar**.

7. Na caixa de diálogo **Adicionar Associação do Site**, no campo **Tipo**, escolha **https**.

8. No campo **Certificado SSL**, selecione o certificado assinado no menu suspenso. Clique em **OK**. Consulte [Para configurar um certificado SSL no Gerenciador do IIS](#to-configure-an-ssl-certificate-in-iis-Manager) neste tópico para obter mais informações sobre como obter um certificado.

    Agora, o aplicativo Web Windows PowerShell Web Access está configurado para usar o certificado SSL assinado.

    Você pode acessar o Windows PowerShell Web Access ao abrir **https://\<server_name\>/pswa** uma janela do navegador.

>**![Observação](images/note.jpeg) Observação** 
> 
>Você não poderá fazer logon até que todos os usuários tenham obtido acesso ao site adicionando regras de autorização. 
>Para obter mais informações, consulte [Configurar uma regra de autorização restritiva](#configure-a-restrictive-authorization-rule), neste tópico, e [Regras de autorização e recursos de segurança do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>configurar uma regra de autorização restritiva

Depois que o Windows PowerShell Web Access for instalado e o gateway configurado, os usuários poderão abrir a página de entrada em um navegador, mas só poderão entrar depois que o administrador do Windows PowerShell Web Access conceder a eles acesso explicitamente. O controle de acesso do Windows PowerShell Web Access é gerenciado por meio de um conjunto de cmdlets do Windows PowerShell descritos na tabela a seguir. Não há uma GUI comparável para adicionar ou gerenciar regras de autorização. Para saber mais sobre os cmdlets do Windows PowerShell Web Access, confira os tópicos de referência de cmdlet [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md) (Cmdlets do Windows PowerShell Web Access).

Para obter mais detalhes sobre as regras e a segurança de autorização do Windows PowerShell Web Access, confira [Authorization Rules and Security Features of Windows PowerShell Web Access (Recursos de segurança e regras de autorização do Windows PowerShell Web Access)](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Para adicionar uma regra de autorização restritiva

1. Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados.

    - Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.

    - Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.

2. Etapa opcional para restringir o acesso do usuário usando configurações de sessão: verifique se as configurações de sessão que você deseja usar em suas regras já existem. Se elas ainda não foram criadas, siga as instruções de como criar configurações de sessão em [about_Session_Configuration_Files](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Digite o seguinte e pressione **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Essa regra de autorização permite que um usuário específico acesse um computador na rede ao qual tipicamente tem acesso, com acesso a uma configuração de sessão específica, voltada para suas necessidades típicas de script e cmdlet.
   
   No exemplo a seguir, um usuário nomeado `JSmith` no domínio `Contoso` ganha acesso para gerenciar o computador `Contoso_214` e usa uma configuração de sessão nomeada `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Verifique se a regra foi criada executando o cmdlet `Get-PswaAuthorizationRule` ou `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

5. Por exemplo, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Depois de configurar uma regra de autorização, você está pronto para que os usuários autorizados entrem no console baseado na web e comecem a usar o Windows PowerShell Web Access.

## <a name="custom-deployment"></a>Implantação personalizada

Você pode instalar o gateway do Windows PowerShell Web Access em um servidor que está executando o Windows Server 2012 R2 ou o Windows Server 2012 usando o assistente Adicionar Funções e Recursos no Gerenciador do Servidor. Depois de instalar o Windows PowerShell Web Access, você pode personalizar a configuração do gateway no Gerenciador do IIS.

### <a name="install-windows-powershell-web-access"></a>Instalar o Windows PowerShell Web Access

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a>Para instalar o Windows PowerShell Web Access usando o Assistente para Adicionar Funções e Recursos

1. Se o Gerenciador do Servidor já estiver aberto, vá para a etapa seguinte. Se o Gerenciador do Servidor ainda não estiver aberto, abra-o de uma das maneiras a seguir.

    - Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.

    - Na tela **Iniciar** do Windows, clique em **Gerenciador do Servidor**.

2. No menu **Gerenciar**, clique em **Adicionar Funções e Recursos**.

3. Na página **Selecionar tipo de instalação**, selecione **Instalação baseada em função ou recurso**. Clique em **Avançar**.

4. Na página **Selecionar servidor de destino**, escolha um servidor no pool de servidores ou um VHD offline. Para selecionar um VHD offline como servidor de destino, primeiro selecione o servidor no qual deseja montar o VHD e selecione o arquivo VHD. Para obter informações sobre como adicionar servidores ao pool de servidores, consulte a Ajuda do Gerenciador do Servidor. Após selecionar o servidor de destino, clique em **Avançar**.

5. Na página **Selecionar recursos** do assistente, expanda **Windows PowerShell** e escolha **Windows PowerShell Web Access**.

6. O sistema solicitará a adição dos recursos obrigatórios, como o .NET Framework 4.5 e os serviços de função do Servidor Web (IIS). Adicione os recursos obrigatórios e continue.

    >**![Observação](images/note.jpeg) Observação** 
    >
    >A instalação do Windows PowerShell Web Access usando o assistente Adicionar Funções e Recursos também instala o servidor Web (IIS), incluindo o snap-in Gerenciador do IIS. O snap-in e outras ferramentas de gerenciamento do IIS são instalados por padrão quando o assistente Adicionar Funções e Recursos é usado. Se você instalar o Windows PowerShell Web Access usando cmdlets do Windows PowerShell, como descrito no procedimento a seguir, as ferramentas de gerenciamento não serão adicionadas por padrão.

7. Na página **Confirmar seleções de instalação**, se os arquivos de recursos do Windows PowerShell Web Access não estiverem armazenados no servidor de destino selecionado na etapa 4, clique em **Especificar um caminho de origem alternativo** e forneça o caminho para os arquivos de recursos. Caso contrário, clique em **Instalar**.

8. Depois que você clicar em **Instalar**, a página **Progresso da instalação** exibirá o progresso, os resultados e mensagens da instalação, como avisos, falhas ou as etapas de configuração pós-instalação necessárias ao Windows PowerShell Web Access. Após a instalação do Windows PowerShell Web Access, você será solicitado a examinar o arquivo Leiame, que contém instruções de configuração básicas e necessárias para o gateway. Essas instruções também estão incluídas neste tópico. O caminho para o arquivo Leiame é `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>configurar o gateway

As instruções nesta seção referem-se à instalação do aplicativo Web Windows PowerShell Web Access em um subdiretório do seu site e não no diretório raiz. Esse procedimento é o equivalente baseado em GUI das ações executadas pelo cmdlet `Install-PswaWebApplication`. Esta seção também inclui instruções sobre como usar o Gerenciador do IIS para configurar o gateway do Windows PowerShell Web Access como um site raiz.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>Para usar o Gerenciador do IIS a fim de configurar um gateway em um site existente

1. Abra o console do Gerenciador do IIS seguindo um destes procedimentos.

    - Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows. No menu **Ferramentas** no Gerenciador do Servidor, clique em **Gerenciador do IIS (Serviços de Informações da Internet)**.

    - Na tela **Iniciar** do Windows, digite qualquer parte do nome **Gerenciador do IIS (Serviços de Informações da Internet)**. Clique no atalho quando ele for exibido nos resultados de **Aplicativos**.

2. Crie um novo pool de aplicativos para o Windows PowerShell Web Access. Expanda o nó do servidor de gateway no painel de árvore do Gerenciador do IIS, selecione **Pools de Aplicativos** e clique em **Adicionar Pool de Aplicativos** no painel **Ações**.

3. Adicione um novo pool de aplicativos com o nome **pswa_pool** ou forneça outro nome. Clique em **OK**.

4. No painel de árvore do Gerenciador do IIS, expanda o nó do servidor no qual o Windows PowerShell Web Access está instalado até que a pasta **Sites** fique visível. Selecione a pasta **Sites**.

5. Clique com o botão direito do mouse no site (por exemplo, **Site Padrão**) ao qual você deseja adicionar o site do Windows PowerShell Web Access e clique em **Adicionar Aplicativo**.

6. No campo **Alias**, digite pswa ou forneça outro alias. O alias vira o nome do diretório virtual. Por exemplo, **pswa** na URL a seguir, representa o alias especificado nesta etapa: **https://\<server-name\>/pswa**.

7. No campo **Pool de Aplicativos**, selecione o pool de aplicativos criado na etapa 3.

8. No campo **Caminho físico**, procure a localização do aplicativo. Você pode usar a localização padrão, %windir%/Web/PowerShellWebAccess/wwwroot. Clique em **OK**.

9. Siga as etapas no procedimento para configurar um certificado SSL no gerenciador do IIS](#to-configure-an-ssl-certificate-in-iis-Manager) neste tópico.

10. ![](images/SecurityNote.jpeg) Etapa opcional de segurança:

    Com o site selecionado no painel de árvore, clique duas vezes em **Configurações de SSL** no painel de conteúdo. Selecione **Exigir SSL** e, no painel **Ações**, clique em **Aplicar**. Opcionalmente, no painel **Configurações de SSL**, você pode exigir que os usuários que se conectem ao site do Windows PowerShell Web Access tenham certificados de cliente. Os certificados de cliente ajudam a verificar a identidade de um usuário de dispositivo cliente. Para obter mais informações sobre como exigir certificados de cliente que podem aumentar a segurança do Windows PowerShell Web Access, consulte [Regras de autorização e recursos de segurança do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) neste guia.

11. Abra uma sessão de navegador em um dispositivo cliente. Para obter mais informações sobre navegadores e dispositivos com suporte, consulte [Suporte para navegadores e dispositivos cliente](#browser-and-client-device-support) neste tópico.

12. Abra o novo site do Windows PowerShell Web Access, **https://\<*gateway-server-name*\>/pswa**.

    O navegador exibirá a página de entrada do console do Windows PowerShell Web Access.

    >**![Observação](images/note.jpeg) Observação** 
    > 
    >Você não poderá fazer logon até que todos os usuários tenham obtido acesso ao site adicionando regras de autorização. 
    >Para obter mais informações, consulte [Configurar uma regra de autorização restritiva](#configure-a-restrictive-authorization-rule), neste tópico, e [Regras de autorização e recursos de segurança do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. Em uma sessão do Windows PowerShell, aberta com direitos de usuário elevados (Executar como Administrador), execute o script a seguir, no qual *application_pool_name* representa o nome do pool de aplicativos criado na etapa 3, para conferir ao pool de aplicativos direitos de acesso ao arquivo de autorização.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Para exibir os direitos de acesso existentes relativos ao arquivo de autorização, execute o comando a seguir:

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>Para usar o Gerenciador do IIS a fim de configurar o gateway como site raiz com um certificado de teste

1. Abra o console do Gerenciador do IIS seguindo um destes procedimentos.

    - Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows. No menu **Ferramentas** no Gerenciador do Servidor, clique em **Gerenciador do IIS (Serviços de Informações da Internet)**.

    - Na tela **Iniciar** do Windows, digite qualquer parte do nome **Gerenciador do IIS (Serviços de Informações da Internet)**. Clique no atalho quando ele for exibido nos resultados de **Aplicativos**.

2. No painel de árvore do Gerenciador do IIS, expanda o nó do servidor no qual o Windows PowerShell Web Access está instalado até que a pasta **Sites** fique visível. Selecione a pasta **Sites**.

3. No painel **Ações**, clique em **Adicionar Site**.

4. Digite um nome para o site, por exemplo, **Windows PowerShell Web Access**.

5. Um pool de aplicativos será criado automaticamente para o novo site. Para usar outro pool de aplicativos, clique em **Selecionar** para selecionar um pool de aplicativos a ser associado ao novo site. Escolha o pool de aplicativos alternativo na caixa de diálogo **Selecionar Pool de Aplicativos** e clique em **OK**.

6. Na caixa de texto **Caminho físico**, navegue até %*windir*%/Web/PowerShellWebAccess/wwwroot.

7. No campo **Tipo** da área **Associação**, escolha **https**.

8. Atribua um número de porta a um site que ainda não seja usado por outro site ou aplicativo. Para localizar portas abertas, você pode executar o comando **netstat** em uma janela de Prompt de Comando. O número de porta padrão é 443.

    Altere a porta padrão se outro site já estiver usando 443 ou se tiver outros motivos relativos à segurança para alterar esse número. Se outro site em execução no seu servidor de gateway estiver usando a porta selecionada, um aviso será exibido quando você clicar em **OK** na caixa de diálogo **Adicionar Site**. Você deve usar uma porta não utilizada para executar o Windows PowerShell Web Access.

9. Opcionalmente, se necessário para sua organização, especifique um nome de host que faça sentido para a organização e para os usuários, como **www.contoso.com**. Clique em **OK**.

10. Para um ambiente de produção mais seguro, recomendamos enfaticamente fornecer um certificado válido assinado por uma AC. Forneça um certificado SSL, pois os usuários só podem se conectar ao Windows PowerShell Web Access por meio de um site HTTPS. Consulte [Para configurar um certificado SSL no Gerenciador do IIS](#to-configure-an-ssl-certificate-in-iis-Manager) neste tópico para obter mais informações de como obter um certificado.

11. Clique em **OK** para fechar a caixa de diálogo **Adicionar Site**.

12. Em uma sessão do Windows PowerShell, aberta com direitos de usuário elevados (Executar como Administrador), execute o script a seguir, no qual *application_pool_name* representa o nome do pool de aplicativos criado na etapa 4, para conferir ao pool de aplicativos direitos de acesso ao arquivo de autorização.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Para exibir os direitos de acesso existentes relativos ao arquivo de autorização, execute o comando a seguir:

        c:\windows\system32\icacls.exe $authorizationFile

13. Com o novo site selecionado no painel de árvore do Gerenciador do IIS, clique em **Iniciar** no painel **Ações** para iniciar o site.

14. Abra uma sessão de navegador em um dispositivo cliente. Para obter mais informações sobre navegadores e dispositivos com suporte, consulte [Suporte para navegador e dispositivo cliente](#browser-and-client-device-support) neste documento.

15. Abra o novo site do Windows PowerShell Web Access.

    Como o site raiz aponta para a pasta do Windows PowerShell Web Access, o navegador exibirá a página de entrada do Windows PowerShell Web Access quando você abrir **https://\<*gateway_server_name*\>**. Não será preciso adicionar **/pswa** à URL.

    >**![Observação](images/note.jpeg) Observação** 
    > 
    >Você não poderá fazer logon até que todos os usuários tenham obtido acesso ao site adicionando regras de autorização. 
    >Para obter mais informações, consulte [Configurar uma regra de autorização restritiva](#configure-a-restrictive-authorization-rule), neste tópico, e [Regras de autorização e recursos de segurança do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>configurar uma regra de autorização restritiva

Depois que o Windows PowerShell Web Access for instalado e o gateway configurado, os usuários poderão abrir a página de entrada em um navegador, mas só poderão entrar depois que o administrador do Windows PowerShell Web Access conceder a eles acesso explicitamente. O controle de acesso do Windows PowerShell Web Access é gerenciado por meio de um conjunto de cmdlets do Windows PowerShell descritos na tabela a seguir. Não há uma GUI comparável para adicionar ou gerenciar regras de autorização. Para saber mais sobre os cmdlets do Windows PowerShell Web Access, confira os tópicos de referência de cmdlet [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md) (Cmdlets do Windows PowerShell Web Access).

Para obter mais detalhes sobre as regras e a segurança de autorização do Windows PowerShell Web Access, confira [Authorization Rules and Security Features of Windows PowerShell Web Access (Recursos de segurança e regras de autorização do Windows PowerShell Web Access)](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Para adicionar uma regra de autorização restritiva

1. Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados.

    - Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.

    - Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.

2. ![Observação de segurança](images/SecurityNote.jpeg) Etapa opcional para restringir o acesso de usuários usando as configurações de sessão:

    verifique se as configurações de sessão que você deseja usar em suas regras já existem. Se elas ainda não foram criadas, siga as instruções de como criar configurações de sessão em [about_Session_Configuration_Files](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Digite o seguinte e pressione **Enter**.

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    Essa regra de autorização permite que um usuário específico acesse um computador na rede ao qual tipicamente tem acesso, com acesso a uma configuração de sessão específica, voltada para suas necessidades típicas de script e cmdlet. 
    
    No exemplo a seguir, um usuário nomeado `JSmith` no domínio `Contoso` ganha acesso para gerenciar o computador `Contoso_214` e usa uma configuração de sessão nomeada `NewAdminsOnly`.

        Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4. Verifique se a regra foi criada executando o cmdlet `Get-PswaAuthorizationRule` ou `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`. 

    Por exemplo, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Depois de configurar uma regra de autorização, você está pronto para que os usuários autorizados entrem no console baseado na web e comecem a usar o Windows PowerShell Web Access.

## <a name="configure-a-genuine-certificate"></a>Configurar um certificado original

Para um ambiente de produção seguro, sempre use um certificado SSL válido que foi assinado por uma AC (autoridade de certificação). O procedimento nesta seção descreve como obter e aplicar um certificado SSL válido por meio de uma AC.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Para configurar um certificado SSL no Gerenciador do IIS

1. No painel da árvore Gerenciador do IIS, selecione o servidor no qual o Windows PowerShell Web Access está instalado.

2. No painel de conteúdo, clique duas vezes em **Certificados de Servidor**.

3. No painel **Ações**, siga um dos procedimentos a seguir. Para saber mais sobre como configurar certificados de servidor no IIS, confira [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx) (Configurando certificados de servidor no IIS 7).

    - Clique em **Importar** para importar um certificado existente válido de uma localização da sua rede.

    - Clique em **Criar Solicitação de Certificado** para solicitar um certificado de uma AC, como [VeriSign](http://www.verisign.com/), [Thawte](https://www.thawte.com/) ou [GeoTrust](https://www.geotrust.com/). O nome comum do certificado deve corresponder ao cabeçalho do host na solicitação.

      Por exemplo, se o navegador do cliente solicitar http://www.contoso.com/, o nome comum também deverá ser http://www.contoso.com/. Esta é a opção mais segura e recomendada para fornecer um gateway do Windows PowerShell Web Access com um certificado.

    - Clique em **Criar um Certificado Autoassinado** para criar um certificado que você possa usar imediatamente e que possa ser assinado posteriormente pela AC, se desejado. Especifique um nome amigável para o certificado autoassinado, por exemplo, **Windows PowerShell Web Access**. Essa opção não é considerada segura e é recomendada somente para um ambiente de testes privado.

4. Depois de criar ou obter um certificado, selecione o site ao qual o certificado é aplicado (por exemplo, **Site Padrão**) no painel de árvore do Gerenciador do IIS e clique em **Associações** no painel **Ações**.

5. Na caixa de diálogo **Adicionar Associação do Site**, adicione uma associação **https** ao site, caso ainda nenhuma seja exibida. Se você não estiver usando um certificado autoassinado, especifique o nome do host da etapa 3 deste procedimento. Se estiver usando um certificado autoassinado, esta etapa não será necessária.

6. Escolha o certificado obtido ou criado na etapa 3 deste procedimento e clique em **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Usando o console do Windows PowerShell baseado na Web

Depois que o Windows PowerShell Web Access é instalado e a configuração do gateway é concluída, como descrito neste tópico, o console do Windows PowerShell baseado na Web está pronto para uso. Para saber mais sobre como começar a usar o console baseado na Web, confira [Use the Web-based Windows PowerShell Console (Usar o console do Windows PowerShell baseado na Web)](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Consulte Também

- [Documentação do IIS (Serviços de Informações da Internet) 7.0](https://technet.microsoft.com/library/cc753433.aspx)
- [Ajuda do Gerenciador do IIS 7.0](https://technet.microsoft.com/library/cc732664.aspx)
- [Configurar a segurança do servidor Web (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
- [Recursos de implantação de IPsec](https://technet.microsoft.com/network/bb531150)
