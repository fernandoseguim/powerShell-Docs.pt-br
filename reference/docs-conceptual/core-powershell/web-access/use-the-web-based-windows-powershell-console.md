---
ms.date: 2017-08-23
keywords: powershell, cmdlet
title: usar o console do windows powershell baseado na web
ms.openlocfilehash: a6c9812253309ba1225141cfd48d0f1c8b8785b5
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="use-the-web-based-windows-powershell-console"></a>Usar o Console do Windows PowerShell baseado na Web

Atualizado em: 24 de junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

O Windows PowerShell Web Access permite que os usuários entrem em um site protegido para usar sessões, cmdlets e scripts do Windows PowerShell para gerenciar um computador remoto.

Como o console do Windows PowerShell é executado em um navegador da Web, ele pode ser aberto em uma ampla variedade de dispositivos clientes, ou seja, quase em todos os dispositivos com um navegador da Web funcionando.

O console do Windows PowerShell baseado na Web é destinado a um computador remoto especificado por usuários como parte do processo de entrada. 

Este tópico descreve como entrar e iniciar usando o console baseado na Web do Windows PowerShell Web Access.

Este tópico não descreve como usar o Windows PowerShell ou executar cmdlets ou scripts. Para obter informações de como usar o Windows PowerShell e os recursos de script, veja a seção [Consulte também](#see-also) no fim deste tópico.

## <a name="supported-browsers-and-client-devices"></a>Navegadores e dispositivos clientes compatíveis

O Windows PowerShell Web Access dá suporte aos seguintes navegadores da Internet. Embora navegadores móveis não tenham suporte oficialmente, muitos poderão executar o console do Windows PowerShell baseado na Web. É provável que outros navegadores que aceitam cookies, executam JavaScript e abrem sites HTTPS funcionam, mas não foram oficialmente testados.

### <a name="supported-desktop-computer-browsers"></a>Navegadores de desktop compatíveis

- Windows Internet Explorer para Microsoft Windows 8.0, 9.0, 10.0 e 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m para Windows
- Apple Safari 5.1.2 para Windows
- Apple Safari 5.1.2 para Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Dispositivos ou navegadores móveis minimamente testados

- Windows Phone 7 e 7.5
- Navegador Google Android WebKit 3.1  Android 2.2.1 (Kernel 2.6)
- Apple Safari para iPhone com sistema operacional 5.0.1
- Apple Safari para iPad 2 com sistema operacional 5.0.1

### <a name="browser-requirements"></a>Requisitos de navegador

Para usar o console do Windows PowerShell Web Access baseado na Web, os navegadores devem executar os procedimentos a seguir.

- Permitir cookies do site do gateway do Windows PowerShell Web Access.
- Ser capazes de abrir e ler páginas HTTPS.
- Abrir e executar sites que usam JavaScript.

## <a name="signing-in-to-windows-powershell-web-access"></a>Entrando no Windows PowerShell Web Access

O administrador do Windows PowerShell Web Access deve fornecer uma URL que é o endereço do site do gateway do Windows PowerShell Web Access da sua organização.
Por padrão, o endereço desse site é *https://\<nome_do_servidor\>/pswa*.

Antes de entrar no Windows PowerShell Web Access, tenha o nome ou o endereço IP do computador remoto que deseja gerenciar.
Você deve ser um usuário autorizado no computador remoto e ele deve estar configurado para permitir gerenciamento remoto.
Para obter mais informações sobre como configurar o computador para permitir o gerenciamento remoto, consulte [Enable and Use Remote Commands in Windows PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting) (Habilitar e usar comandos remotos no Windows PowerShell).

O método mais simples de configurar o computador para permitir gerenciamento remoto é executar o cmdlet **Enable-PSRemoting -force** no computador, em uma sessão do Windows PowerShell aberta com direitos de usuário elevados (**Executar como Administrador**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Para entrar no Windows PowerShell Web Access

1. Abra o site do Windows PowerShell Web Access em uma janela ou guia do navegador da Internet.

1. Na página de entrada do Windows PowerShell Web Access, forneça o nome de usuário de rede, a senha e o nome do computador a ser gerenciado (e em que você é um usuário autorizado). Se o administrador do Windows PowerShell Web Access o instruir para usar um URI para um site ou servidor proxy personalizado, em vez de um nome do computador, selecione **URI de Conexão** no campo **Tipo de conexão** e forneça o URI.

    > ![Observação](images/Note.jpeg) **Observação**:
    >
    > - Se o computador de destino estiver em um grupo de trabalho, use a sintaxe a seguir para fornecer seu nome de usuário e entrar no computador:`<workgroup_name>\<user_name>`
    > - Se o computador de destino for o servidor de gateway, você poderá especificar `localhost` no campo Nome do computador
    > - Se o computador de destino for o servidor de gateway e o servidor de gateway estiver em um grupo de trabalho, você deverá usar `<workgroup name>\<user_name>` no campo Nome de usuário. Você pode usar `localhost` no campo Nome do computador.

1. A seção **Configurações de Conexão Opcionais** está relacionada aos requisitos de autorização do computador remoto que você deseja gerenciar. Para obter mais informações sobre os parâmetros que são equivalentes às configurações de conexão opcionais, consulte a ajuda do cmdlet [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession).

    Geralmente, as credenciais usadas para passar pelo gateway do Windows PowerShell Web Access são as mesmas reconhecidas pelo computador remoto que você deseja gerenciar. No entanto, se você desejar usar credenciais diferentes para gerenciar o computador remoto especificado na etapa 2, expanda a seção **Configurações de Conexão Opcionais** e forneça as credenciais alternativas. Caso contrário, ignore a etapa 6.

1. Se o administrador do Windows PowerShell Web Access tiver criado uma configuração de sessão personalizada para usuários do Windows PowerShell Web Access, digite o nome da configuração da sessão no campo **Nome da configuração**. Para saber mais sobre configurações de sessão, confira [about_Session_Configurations](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Mantenha o **Tipo de autenticação** definido como **Padrão**, a menos que você tenha sido instruído a fazer o contrário pelo administrador do Windows PowerShell Web Access.

1. Clique em **Entrar**.

## <a name="signing-out-and-timing-out"></a>Saída e tempo limite

Qualquer uma das ações a seguir encerra uma sessão do Windows PowerShell baseada na Web.

- Clicar em **Sair** no canto inferior direito do console. (Windows Server 2012 apenas)

- Clique em **Salvar** ou **Sair** no canto inferior direito do console (Windows Server 2012 R2 apenas). Clicar em **Salvar** salva e fecha a sessão do Windows PowerShell Web Access. Você pode se reconectar à sessão mais tarde. Quando você entra no Windows PowerShell Web Access novamente, o Windows PowerShell Web Access exibe uma lista de suas sessões salvas. Você pode selecionar e se reconectar a uma sessão salva ou iniciar uma nova sessão. O número máximo de sessões abertas, salvas e ativas, a que os usuários têm permissão é configurado pelo administrador do gateway.

    Clicar em **Sair** faz com que você saia da Windows PowerShell Web Access sessão sem salvá-la.

- Tentar entrar para gerenciar um computador remoto diferente na mesma sessão de navegador ou em uma nova guia da mesma sessão de navegador. (Isso não se aplicará se o servidor de gateway estiver executando Windows Server 2012 R2; Windows PowerShell Web Access em execução em Windows Server 2012 R2 permite várias sessões de usuário em novas guias na mesma sessão do navegador.) Para obter mais informações de como usar mais de uma sessão ativa no mesmo computador, consulte Connecting to multiple target computers simultaneously (Conectando a vários computadores de destino simultaneamente) na seção [Limitations of the web-based console](#limitations-of-the-web-based-console) (Limitações do console baseado na Web) deste tópico.

- 20 minutos de inatividade na sessão. O administrador do gateway pode personalizar o período de tempo limite de inatividade. Para saber mais, confira [Gerenciamento de sessões](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Se os usuários forem desconectados de sessões no console baseado na Web por causa de erros de rede ou outros desligamentos não planejados ou falhas, e não porque você fechou a sessão, as sessões do Windows PowerShell Web Access continuam em execução, conectada ao computador de destino, até decorrer o tempo limite do lado do cliente. Por padrão, esse período de tempo limite é de 20 minutos e é configurado pelo administrador do gateway. A sessão é desconectada após um padrão de 20 minutos ou após o período de tempo limite especificado pelo administrador do gateway, o que for menor.

        Se o servidor de gateway estiver executando o Windows Server 2012 R2, o Windows PowerShell Web Access permitirá que os usuários se reconectem a sessões salvas em um momento posterior, mas você não poderá ver ou se reconectar a sessões salvas até ter expirado o período de tempo limite especificado pelo administrador do gateway.

- Fechar a janela ou a guia do navegador.

- Desativar o dispositivo cliente em que o navegador está executando ou desconectá-lo da rede.

- Executar o comando **Sair** no console Web. Esse comando não funciona se a configuração de sessão a que você está conectado estiver definida para dar suporte ao modo [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) ou estiver em um runspace restrito.

Se desejar entrar novamente, abra a página da Web do Windows PowerShell Web Access novamente e entre seguindo as etapas em [Signing in to Windows PowerShell Web Access](#signing-in-to-windows-powershell-web-access) (Entrando no Windows PowerShell Web Access) neste tópico.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Diferenças no console do Windows PowerShell baseado na Web

Depois de entrar no Windows PowerShell Web Access, um console do Windows PowerShell baseado na web é aberto na janela ou guia do navegador. Como o console está conectado ao computador especificado durante o processo de entrada, somente aqueles cmdlets ou scripts do Windows PowerShell disponíveis no computador remoto podem ser usados no console. Esta seção descreve outras limitações de consoles do Windows PowerShell Web Access e as diferenças entre os consoles do Windows PowerShell Web Access e o console do **PowerShell.exe** instalado.

### <a name="functional-disparity-with-powershellexe"></a>Disparidade funcional com o PowerShell.exe

A maioria das funcionalidades do host do Windows PowerShell está disponível no console baseado na Web do Windows PowerShell Web Access, mas há alguns recursos que não estão disponíveis.

- Exibição do andamento aninhado.

  O Windows PowerShell Web Access exibe uma GUI de andamento para os cmdlets que informam o andamento, mas apenas informações de andamento de nível superior são exibidas.

- Modificação da cor de entrada.

  A cor de entrada (do primeiro plano e da tela de fundo) não pode ser alterada. É possível alterar o estilo das mensagens de saída, de aviso, detalhadas e de erro executando um script.

- PSHostRawUserInterface.

  O Windows PowerShell Web Access é implementado sobre o gerenciamento remoto do Windows PowerShell e usa um runspace remoto. O Windows PowerShell Web Access não implementa alguns métodos nessa interface; por exemplo, qualquer comando que grava no console do Windows. Comandos como **PowerTab** não funcionam no Windows PowerShell Web Access.

- Teclas de função.

  O Windows PowerShell Web Access não dá suporte a algumas teclas de função do, em muitos casos, porque os comandos são reservados pelo navegador.

### <a name="unsupported-shortcut-keys"></a>Teclas de atalho sem suporte

Tecla de função | Ação
-- | --
Ctrl+C | No Windows PowerShell Web Access, **Ctrl + C** é usado pelo navegador para copiar o conteúdo. O console oferece um botão **Cancelar** e os usuários também podem usar **Ctrl+Q** para cancelar os comandos.
Alt-espaço, e, l | Rola pelo buffer da tela
Alt+espaço, e, f | Procura texto no buffer da tela
Alt+espaço, e, k | Seleciona o texto a ser copiado do buffer da tela
Alt+espaço, e, p | Cola o conteúdo da área de transferência no console do Windows PowerShell
Alt+espaço, c | Fecha o console do Windows PowerShell
Ctrl+Break | Força a janela do Windows PowerShell a fechar
Ctrl+Home | Exclui do início da linha de comando atual
Ctrl+End | Exclui para o fim da linha de comando
F1 | Move o cursor um caractere para a direita na linha de comando
F2 | Cria um novo comando copiando o último comando até o caractere digitado
F3 | Preenche a linha de comando com o conteúdo da última linha de comando
F4 | Exclui caracteres a partir da posição do cursor
F5 | Volta na verificação do histórico de comandos. Para acessar comandos no histórico de comandos no Windows PowerShell Web Access, clique nos botões de rolagem do **Histórico** no console baseado na Web.
F7 | Selecione interativamente um comando do histórico de comandos
F8 | Verifica os comandos de exibição do histórico que correspondem ao texto atual
F9 | Executa um comando com numeração específica do histórico
Page Up | Executa o primeiro comando no histórico
Page Down | Executa o último comando no histórico
Alt+F7 | Limpa a lista do histórico de comandos

### <a name="limitations-of-the-web-based-console"></a>Limitações do console baseado na Web

- Salto duplo

    Você pode se deparar com a limitação de salto duplo (ou se conectar a um segundo computador por meio da primeira conexão) se tentar criar ou trabalhar em uma nova sessão usando o Windows PowerShell Web Access. O Windows PowerShell Web Access usa um runspace remoto e, no momento, o **PowerShell.exe** não dá suporte ao estabelecimento de uma conexão remota com um segundo computador de um runspace remoto. Se você tentar se conectar a um segundo computador remoto por meio de uma conexão existente usando o cmdlet **Enter-PSSession**, por exemplo, vários erros poderão ser gerados, como “Não é possível obter recursos da rede”.

    Para evitar erros de salto duplo, o administrador deve configurar a autenticação CredSSP no ambiente de rede da organização. Para obter mais informações sobre a configuração da autenticação CredSSP, consulte [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) (CredSSP para segundo salto remoto) no site da Microsoft. Também é possível fornecer credenciais explícitas quando você deseja gerenciar um segundo computador remoto, é pouco provável que as credenciais implícitas permitam o segundo salto.

- Comunicação remota

    O Windows PowerShell Web Access usa e tem as mesmas limitações que uma sessão remota do Windows PowerShell. Comandos que chamam diretamente APIs do console do Windows, como aquelas para editores baseados no console ou programas de menu baseados em texto, não funcionam porque os comandos não leem nem gravam pipes padrão de entrada, de saída e de erro. Portanto, os comandos que iniciam um arquivo executável, como **notepad.exe** ou exibem uma GUI, como `OpenGridView` ou `ogv`, não funcionam. Sua experiência é afetada por este comportamento, para você, parece que o Windows PowerShell Web Access não está respondendo ao seu comando.

- Preenchimento de guias

    O preenchimento da guia não funciona em uma configuração de sessão com runspace restrito ou que está no modo **NoLanguage**. Embora os administradores possam configurar uma sessão para aceitar o preenchimento da guia, isso não é incentivado por motivos de segurança, pois pode expor as informações a seguir a usuários não autorizados.

    - Caminhos internos do sistema de arquivos

    - Pastas compartilhadas em computadores internos

    - Variáveis no runspace

    - Tipos carregados ou namespaces .NET Framework

    - Variáveis de ambiente

- Sessão **NoLanguage** ou runspace restrito

    Os usuários que entraram em uma configuração de sessão **NoLanguage** ou em um runspace restrito no Windows PowerShell Web Access não podem executar o comando **Sair** para encerrar a sessão. Para sair, os usuários devem clicar em **Sair** na página do console.

- Conectando a vários computadores de destino simultaneamente.

    Se o servidor de gateway estiver executando o Windows Server 2012, o Windows PowerShell Web Access permitirá apenas uma conexão de computador remoto por sessão de navegador; ele não permitirá que os usuários entrem uma vez e se conectem a vários computadores remotos usando guias separadas do navegador. Ao abrir uma nova guia ou uma nova janela de navegador, o Windows PowerShell Web Access solicita que você desconecte a sessão atual e inicie uma nova sessão, de forma que possa se conectar ao novo (ou ao mesmo) computador remoto. Se você desejar duas ou mais sessões separadas para computadores remotos diferentes, um recurso no Internet Explorer permitirá criar uma nova sessão. Para iniciar uma nova sessão de navegador no Internet Explorer, pressione **Alt**, abra o menu **Arquivo** e selecione **Nova Sessão**. Em seguida, abra o site do Windows PowerShell Web Access na nova sessão e entre para acessar outro computador remoto.

    Quando o gateway do Windows PowerShell Web Access estiver em execução no Windows Server 2012 R2, os usuários poderão abrir várias conexões com computadores remotos em guias diferentes do navegador. Se você quiser abrir mais de uma conexão a um computador remoto usando o console do Windows PowerShell baseado na Web, entre em contato com o administrador de gateway do Windows PowerShell Web Access para ver se este recurso tem suporte pelo servidor de gateway.

- Sessões persistentes do Windows PowerShell (reconexão).

    Depois que atingir o tempo limite do gateway do Windows PowerShell Web Access, a conexão remota entre o gateway e o computador de destino será fechada. Com isso, todos os cmdlets ou scripts atualmente presentes no processo são interrompidos. Recomenda-se usar a infraestrutura **-Job** do Windows PowerShell quando você estiver executando tarefas de execução longa, para que seja possível iniciar trabalhos, desconectar do computador, reconectar mais tarde e ter trabalhos persistentes. Outro benefício de usar cmdlets **-Job** é que você pode iniciá-los usando o Windows PowerShell Web Access, além de desconectar-se e reconectar-se mais tarde executando o Windows PowerShell Web Access ou outro host [como o ISE (Ambiente de Script Integrado) do Windows PowerShell®].

- Redimensionamento do console.

    A janela de console **PowerShell.exe** pode ser redimensionada das três maneiras a seguir.

    - Arraste e ajuste o tamanho da janela do console com o mouse

    - Altere as propriedades de altura e largura usando uma GUI para as propriedades do console

    - Altere a altura e largura das janelas do console com um cmdlet

        A janela do console do Windows PowerShell Web Access pode ser configurada usando os cmdlets da seguinte forma. No exemplo a seguir, um usuário muda a largura do console do Windows PowerShell Web Access para **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        É possível alterar a altura do console de maneira similar.

        Exemplos adicionais para personalizar a exibição do console estão disponíveis no [Blog da Equipe do Windows PowerShell](http://blogs.msdn.com/b/powershell/).

## <a name="see-also"></a>Consulte Também

- [Windows PowerShell Cmdlet Reference](https://technet.microsoft.com/library/ee407531(ws.10).aspx) (Referência de cmdlet do Windows PowerShell)
- [Windows PowerShell no Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
- [Repositório do TechNet Script Center](http://gallery.technet.microsoft.com/scriptcenter)
- [Script Center – Olá, pessoal do script!](https://technet.microsoft.com/scriptcenter)
- [Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/) (Blog da equipe do Windows PowerShell)
