---
ms.date: 08/23/2017
keywords: powershell, cmdlet
title: Solucionando problemas de acesso no Windows PowerShell Web Access
ms.openlocfilehash: ef476d8e386e5380cb2c9dda69180dfce8748bf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Solucionando problemas de acesso no Windows PowerShell Web Access

Atualização: 24 de junho de 2013 (revisado em 23 de agosto de 2017)

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

As seções a seguir identificam alguns problemas comuns ao tentar se conectar a um computador remoto usando o Windows PowerShell Web Access e inclui sugestões para resolver os problemas.

## <a name="sign-in-failure"></a>Falha no logon

A falha pode ocorrer com base em um dos fatores a seguir.

- Uma regra de autorização que concede ao usuário acesso ao computador (ou uma configuração de sessão específica no computador remoto) não existe.

  A segurança do Windows PowerShell Web Access é restritiva. Os usuários devem receber acesso explícito a computadores remotos usando regras de autorização.

  Para obter mais informações de como criar regras de autorização, consulte [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) (Regras de autorização e recursos de segurança do Windows PowerShell Web Access).

- O usuário não tem o acesso autorizado ao computador de destino. Isso é determinado pelas listas de controle de acesso (ACLs).

  Para obter mais informações, consulte [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) (Entrando no Windows PowerShell Web Access) ou o Blog da equipe do Windows PowerShell.

- O gerenciamento remoto do Windows PowerShell não deve estar habilitado no computador de destino.

  Verifique se o gerenciamento remoto está habilitado no computador ao qual o usuário está tentando se conectar.

  Para obter mais informações, consulte [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting) (Como configurar seu computador para comunicação remota).

## <a name="internal-server-error"></a>Erro Interno do Servidor

Quando os usuários tentarem entrar no Windows PowerShell Web Access em uma janela do Internet Explorer, página **Erro Interno do Servidor** será exibida ou o *Internet Explorer* deixará de responder.

Esse problema é específico ao Internet Explorer.

### <a name="possible-cause"></a>Causa possível

Isso pode ocorrer com usuários que entraram com um nome de domínio que contém caracteres em chinês, ou quando um ou mais caracteres em chinês fazem parte do nome do servidor de gateway.

#### <a name="workaround"></a>Solução alternativa

1. [Instalar e executar o Internet Explorer 10](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Altere a configuração **Modo de Documento** do Internet Explorer para os padrões do *IE10*.
   1. Pressione **F12** para abrir o console de Ferramentas de Desenvolvedor
   1. No Internet Explorer 10, clique em **Modo do Navegador** e selecione *Internet Explorer 10*.
   1. Clique em **Modo de Documento** e, em seguida, em *Padrões do IE10*.
   1. Pressione **F12** novamente para abrir o console Ferramentas de Desenvolvimento.
1. Desabilite a configuração automática de proxy no Internet Explorer 10.
   1. Clique em **Ferramentas**e em **Opções da Internet**.
   1. Na caixa de diálogo **Opções da Internet**, na guia **Conexões**, clique em **Configurações da LAN**.
   1. Desmarque a caixa de seleção **Detectar automaticamente as configurações**. Clique em **OK** e clique em **OK** novamente para fechar a caixa de diálogo *Opções da Internet*.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Não é possível conectar a um computador de grupo de trabalho remoto

Se o computador de destino for membro de um grupo de trabalho, use a sintaxe a seguir para fornecer seu nome de usuário e entrar no computador: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Não é possível encontrar as ferramentas de gerenciamento do Servidor Web (IIS), embora a função esteja instalada

Se você instalar o Windows PowerShell Web Access usando o cmdlet `Install-WindowsFeature`, as ferramentas de gerenciamento não serão instaladas, a menos que o parâmetro `-IncludeManagementTools` seja adicionado ao cmdlet.

Por exemplo, consulte [Para instalar o Windows PowerShell Web Access usando cmdlets do Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

Você pode adicionar o console do Gerenciador do IIS e outras ferramentas de gerenciamento do IIS de que precisa, selecionando as ferramentas em uma sessão do **Assistente para Adicionar Funções e Recursos** direcionada ao servidor de gateway.
O Assistente de Adição de Funções e Recursos é aberto do Gerenciador do Servidor.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>O site do Windows PowerShell Web Access não está acessível

Se o recurso IE ESC (Configuração de Segurança Aprimorada do Internet Explorer) estiver habilitado, você poderá adicionar o site do Windows PowerShell Web Access à lista de sites confiáveis.

Uma abordagem menos recomendada, devido a riscos de segurança, é desabilitar o IE ESC.
Você pode desabilitar o IE ESC no bloco Propriedades na página Servidor Local no Gerenciador do Servidor.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Ocorreu uma falha de autorização. Verifique se que você está autorizado a conectar-se ao computador de destino.

A mensagem de erro acima é exibida ao tentar se conectar quando o servidor de gateway é o computador de destino e também está um grupo de trabalho.

Quando o servidor de gateway for o servidor de destino e também estiver em um grupo de trabalho, especifique o nome de usuário, o nome do computador e o nome do grupo de usuários.
Não use um ponto (.) sozinho para representar o nome do computador.

### <a name="scenarios-and-proper-values"></a>Cenários e valores adequados

#### <a name="all-cases"></a>Todos os casos

Parâmetro | Valor
-- | --
UserName | Nome\_servidor\\nome\_usuário<br/>Localhost\\nome\_usuário<br/>.\\nome\_usuário
UserGroup | Nome\_servidor\\grupo\_usuários<br/>Localhost\\grupo\_usuários<br/>.\\grupo\_usuários
ComputerGroup | Nome\_servidor\\grupo\_computadores<br/>Localhost\\grupo\_computadores<br/>.\\grupo\_computadores

#### <a name="gateway-server-is-in-a-domain"></a>O servidor de gateway está em um domínio

Parâmetro | Valor
-- | --
ComputerName | Nome totalmente qualificado do servidor de gateway ou Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>O servidor de gateway está em um grupo de trabalho

Parâmetro | Valor
-- | --
ComputerName | Nome do servidor

### <a name="gateway-credentials"></a>Credenciais de gateway

Entre em um servidor de gateway como computador de destino usando credenciais formatadas conforme uma das maneiras a seguir.

- Nome\_servidor\\nome\_usuário
- Localhost\\nome\_usuário
- .\\nome\_usuário

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>Um SID (identificador de segurança) é exibido em uma regra de autorização

Um SID (identificador de segurança) é exibido em uma regra de autorização em vez da sintaxe nome\_usuário/nome\_computador.

A regra não é mais válida ou a consulta aos Serviços de Domínio Active Directory falhou.
A regra de autorização geralmente não é válida em cenários em que o servidor de gateway já esteve em um grupo de trabalho, mas depois ingressou em um domínio

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Não é possível entrar com uma regra como um endereço IPv6 com um domínio

Não é possível entrar em um computador de destino especificado em regras de autorização como endereço IPv6 com um domínio.

As regras de autorização não dão suporte a endereços IPv6 no formato de nome de domínio.

Para especificar um computador de destino usando um endereço IPv6, use o endereço IPv6 original (que contém dois-pontos) na regra de autorização.
Tanto domínios quanto endereços IPv6 numéricos (com dois-pontos) têm suporte como nome do computador de destino na página de entrada do Windows PowerShell Web Access, mas não em regras de autorização.

Para obter mais informações sobre endereços IPv6, consulte [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx) (Como o IPv6 Funciona).

## <a name="see-also"></a>Consulte Também

- [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) (Regras de autorização e recursos de segurança do Windows PowerShell Web Access)
- [Usar o Console do Windows PowerShell baseado na Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)