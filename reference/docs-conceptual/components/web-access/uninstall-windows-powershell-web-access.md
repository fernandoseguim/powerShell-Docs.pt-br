---
ms.date: 08/23/2017
keywords: powershell, cmdlet
title: desinstalar o windows powershell web access
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400531"
---
# <a name="uninstall-windows-powershell-web-access"></a>Desinstalar o Windows PowerShell Web Access

Atualizado: 24 de junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

As etapas neste tópico removem o site do Windows PowerShell Web Access e o aplicativo correspondente do servidor de gateway, no qual ele está instalado.

## <a name="notify-users"></a>Notificar os usuários

Antes de começar, notifique os usuários do console baseado na Web a respeito da remoção do site.

A desinstalação do Windows PowerShell Web Access não desinstala o IIS nem nenhum outro recurso instalado automaticamente porque o Windows PowerShell Web Access precisa deles para ser executado.
O processo de desinstalação deixa instalados os recursos dos quais o Windows PowerShell Web Access dependia. É possível desinstalar esses recursos separadamente, se necessário.

## <a name="recommended-quick-uninstallation"></a>Desinstalação recomendada (rápida)

Os procedimentos nesta seção ajudam a desinstalar:

- o aplicativo Web Windows PowerShell Web Access e
- o recurso do Windows PowerShell Web Access

usando cmdlets do Windows PowerShell.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Etapa 1: Excluir o aplicativo web usando cmdlets

1. Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell.

    -   Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas.

    -   Na tela **Iniciar** do Windows, clique em **Windows PowerShell**.

2. Digite `Uninstall-PswaWebApplication` e pressione **Enter**.
   1. Se você tiver especificado o seu próprio nome de site personalizado, adicione o parâmetro `-WebsiteName` ao seu comando e especifique o nome do site.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Se você tiver usado um aplicativo Web personalizado (não o aplicativo padrão, **pswa**), adicione o parâmetro `-WebApplicationName` ao comando e especifique o nome do aplicativo Web.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Se você estiver usando um certificado de teste, adicione o parâmetro `DeleteTestCertificate` ao cmdlet, como mostrado no exemplo a seguir.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Etapa 2: Desinstalar o Windows PowerShell Web Access usando cmdlets

1. Execute uma das ações a seguir para abrir uma sessão do Windows PowerShell com direitos de usuário elevados. Se já houver uma sessão aberta, vá para a etapa seguinte.

    -   Na área de trabalho do Windows, clique com o botão direito do mouse em **Windows PowerShell** na barra de tarefas e clique em **Executar como Administrador**.

    -   Na tela **Iniciar** do Windows, clique com o botão direito do mouse em **Windows PowerShell** e clique em **Executar como Administrador**.

1. Digite o seguinte e pressione **Enter**, em que *computer_name* representa um servidor remoto do qual você deseja remover o Windows PowerShell Web Access. O parâmetro `-Restart` reinicia automaticamente os servidores de destino quando exigido pela remoção.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Para remover funções e recursos de um VHD offline, adicione os parâmetros `-ComputerName` e `-VHD` . O parâmetro `-ComputerName` contém o nome do servidor em que será montado o VHD, e o parâmetro `-VHD` contém o caminho para o arquivo VHD no servidor especificado.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Quando a remoção for concluída, verifique se você removeu o Windows PowerShell Web Access abrindo a página **Todos os Servidores** no Gerenciador do Servidor, selecionando um servidor do qual você removeu o recurso e exibindo o bloco **Funções e Recursos** na página do servidor selecionado.

    Você também pode executar o cmdlet `Get-WindowsFeature` direcionado ao servidor selecionado (Get-WindowsFeature – ComputerName &lt;*nome_do_computador*&gt;) para exibir uma lista de funções e recursos que estão instalados no servidor.

## <a name="custom-uninstallation"></a>Desinstalação personalizada

Os procedimentos nesta seção o ajudarão a desinstalar o aplicativo Web do Windows PowerShell Web Access e o recurso do Windows PowerShell Web Access usando o Assistente de Remoção de Funções e Recursos no Gerenciador do Servidor e o console do Gerenciador do IIS.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Etapa 1: Excluir o aplicativo web usando o Gerenciador do IIS


1. Abra o console do Gerenciador do IIS seguindo um destes procedimentos. Se já estiver aberto, vá para a etapa seguinte.

    -   Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows. No menu **Ferramentas** no Gerenciador do Servidor, clique em **Gerenciador do IIS (Serviços de Informações da Internet)**.

    -   Na tela **Iniciar** do Windows, digite qualquer parte do nome **Gerenciador do IIS (Serviços de Informações da Internet)**. Clique no atalho quando ele for exibido nos resultados de **Aplicativos**.

1. No painel da árvore Gerenciador do IIS, selecione o site que está executando o aplicativo Web do Windows PowerShell Web Access.

1. No painel **Ações**, em **Gerenciar Site**, clique em **Parar**.

1. No painel de árvore, clique com o botão direito do mouse no aplicativo Web no site que está executando o aplicativo Web do Windows PowerShell Web Access e clique em **Remover**.

1. No painel de árvore, selecione **Pools de Aplicativos**, selecione a pasta do pool de aplicativos do Windows PowerShell Web Access, clique em **Parar** no painel **Ações** e clique em **Remover** no painel de conteúdo.

1. Feche o Gerenciador do IIS.

> ![Observação de aviso](images/SecurityNote.jpeg)**Observação**:
>
> O certificado não é excluído durante a desinstalação.
>
> Se você tiver criado um certificado autoassinado ou usado um certificado de teste e deseja removê-lo, exclua o certificado no Gerenciador do IIS.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Etapa 2: Desinstalar o Windows PowerShell Web Access usando o Assistente de recursos e remover funções

1. Se o Gerenciador do Servidor já estiver aberto, vá para a etapa seguinte. Se o Gerenciador do Servidor ainda não estiver aberto, abra-o de uma das maneiras a seguir.

    -   Na área de trabalho do Windows, inicie o Gerenciador do Servidor clicando em **Gerenciador do Servidor** na barra de tarefas do Windows.

    -   Na tela **Iniciar** do Windows, clique em **Gerenciador do Servidor**.

1. No menu **Gerenciar**, clique em **Remover Funções e Recursos**.

1. Na página **Selecionar servidor de destino**, selecione o servidor ou o VHD offline do qual deseja remover o recurso. Para selecionar um VHD offline, primeiro selecione o servidor no qual deseja montar o VHD e depois selecione o arquivo VHD. Após selecionar o servidor de destino, clique em **Avançar**.

1. Clique em **Avançar** novamente para ignorar a página **Remover recursos**.

1. Desmarque a caixa de seleção do **Windows PowerShell Web Access** e clique em **Avançar**.

1. Na página **Confirmar seleções de remoção**, clique em **Remover**.

## <a name="see-also"></a>Consulte Também

- [Instalar e usar o Windows PowerShell Web Access](install-and-use-windows-powershell-web-access.md)
- [Ajuda do Gerenciador do IIS 7.0](https://technet.microsoft.com/library/cc732664.aspx)