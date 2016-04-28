---
title: Instalar o Mecanismo do Windows PowerShell 2.0
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
---
# Instalar o Mecanismo do Windows PowerShell 2.0
Este tópico explica como instalar o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)].

O [!INCLUDE[psversion3](../Token/psversion3_md.md)] é projetado para serem compatíveis com versões anteriores do [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Cmdlets, provedores, snap-ins, módulos e scripts desenvolvidos para o [!INCLUDE[psversion2](../Token/psversion2_md.md)] são executados sem alterações no [!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)]. No entanto, devido a uma alteração na política de ativação do tempo de execução no Microsoft .NET Framework 4, programas de host do Windows PowerShell que foram desenvolvidos para [!INCLUDE[psversion2](../Token/psversion2_md.md)] e compilados com o CLR (Common Language Runtime) 2.0 não podem ser executado sem modificação em versões posteriores do [!INCLUDE[wps_2](../Token/wps_2_md.md)], que é compilado com o CLR 4.0.

Para manter a compatibilidade com versões anteriores com comandos e programas de host são afetados por essas alterações, os Mecanismos do [!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)] são projetados para execução lado a lado. Além disso, o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] está incluído no [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] e [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]. O Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] se destina a ser usado somente quando um programa de host ou um script existente não puder ser executado porque ele é incompatível com [!INCLUDE[psversion3](../Token/psversion3_md.md)], [!INCLUDE[psversion4](../Token/psversion4_md.md)] ou Microsoft .NET Framework 4. Tais casos devem ser raros.

O Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] é um recurso opcional do [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] e [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)]. Em versões anteriores do Windows, quando você instala o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], a instalação do [!INCLUDE[psversion3](../Token/psversion3_md.md)] substitui completamente a do [!INCLUDE[psversion2](../Token/psversion2_md.md)] no diretório de instalação do [!INCLUDE[wps_2](../Token/wps_2_md.md)]. No entanto, o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] é mantido.

Para obter informações sobre como iniciar o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)], consulte [Iniciar o Mecanismo do Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## No [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] e [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]
No [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] e [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], o recurso do Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] é ativado por padrão. No entanto, para usá-lo, você precisa ativar a opção para Microsoft .NET Framework 3.5, que ele exige. Esta seção também explica como ativar e desativar o recurso do Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)].

#### Para ativar o .NET Framework 3.5

1.  Na tela **Iniciar**, clique em **Recursos do Windows**.

2.  Em **Aplicativos**, clique em **Configurações** e em **Ativar ou desativar recursos do Windows**.

3.  Na caixa **Recursos do Windows**, clique em **.NET Framework 3.5 (inclui o .NET 2.0 e 3.0** para selecioná-la.

    Quando você seleciona **.NET Framework 3.5 (inclui o .NET 2.0 e 3.0**, a caixa é preenchida para indicar que apenas parte do recurso está selecionada. No entanto, isso é suficiente para o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)].

#### Para ativar e desativar o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)]

1.  Na tela **Iniciar**, clique em **Recursos do Windows**.

2.  Em **Aplicativos**, clique em **Configurações** e em **Ativar ou desativar recursos do Windows**.

3.  Na caixa **Recursos do Windows**, expanda o **[!INCLUDE[psversion2](../Token/psversion2_md.md)]** nó e clique na caixa **[!INCLUDE[psversion2](../Token/psversion2_md.md)] Mecanismo** para marcá-la ou desmarcá-la.

## No [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] e [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]
Use os procedimentos a seguir para adicionar os recursos Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] e Microsoft .NET Framework 3.5. O Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] requer o Microsoft .NET Framework 2.0.50727 no mínimo. Esse requisito é atendido pelo Microsoft .NET Framework 3.5.

#### Para adicionar o recurso .NET Framework 3.5

1.  Em **Gerenciador do Servidor**, no menu **Gerenciar** clique em **Adicionar Funções e Recursos**.

    Ou então, no **Gerenciador do Servidor**, clique em **Todos os Servidores**, clique com o botão direito do mouse em um nome do servidor e selecione **Adicionar Funções e Recursos**.

2.  Na página **Tipo de Instalação**, selecione **Instalação baseada em função ou em recurso**.

3.  Sobre a página **Recursos**, expanda o nó **Recursos do .NET 3.5 Framework** e selecione **.NET Framework 3.5 (inclui .NET 2.0 e 3.0)**.

    As outras opções sob aquele nó não são necessárias para o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)].

#### Para adicionar o recurso do Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)]

-   Em **Gerenciador do Servidor**, no menu **Gerenciar** clique em **Adicionar Funções e Recursos**.

    Ou então, no **Gerenciador do Servidor**, clique em **Todos os Servidores**, clique com o botão direito do mouse em um nome do servidor e selecione **Adicionar Funções e Recursos**.

-   Na página **Tipo de Instalação**, selecione **Instalação baseada em função ou em recurso**.

-   Na página **Recursos**, expanda o nó **[!INCLUDE[mshshort](../Token/mshshort_md.md)] (Instalado)** e selecione **[!INCLUDE[psversion2](../Token/psversion2_md.md)] Mecanismo**.

Para obter informações sobre como iniciar o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)], consulte [Iniciar o Mecanismo do Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## Em sistemas anteriores
O pacote do [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) que instala o [!INCLUDE[psversion4](../Token/psversion4_md.md)] em [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)], [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] e [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] inclui o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)]. O Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] está habilitado e pronto para usar, se necessário, sem instalação, configuração ou definições adicionais.

O pacote do [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] que instala o [!INCLUDE[psversion3](../Token/psversion3_md.md)] em [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)], [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] e [!INCLUDE[lserver](../Token/lserver_md.md)] inclui o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)]. O Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] está habilitado e pronto para usar, se necessário, sem instalação, configuração ou definições adicionais.

## Consulte Também
[Requisitos do Sistema do Windows PowerShell](../Topic/Windows-PowerShell-System-Requirements.md)
[Instalar o Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[Iniciando o Windows PowerShell [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
[Iniciando o Mecanismo do Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)



<!--HONumber=Apr16_HO1-->


