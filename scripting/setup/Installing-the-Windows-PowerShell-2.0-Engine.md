---
title: Instalar o Mecanismo do Windows PowerShell 2.0
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 8a61e974e7f7ea479ecc447c2db91c677cd8931f

---

# Instalar o Mecanismo do Windows PowerShell 2.0
Este tópico explica como instalar o Mecanismo Windows PowerShell 2.0.

O Windows PowerShell 3.0 é projetado para ser compatível com o Windows PowerShell 2.0. Cmdlets, provedores, snap\-ins, módulos e scripts escritos para o Windows PowerShell 2.0 e o Windows PowerShell 3.0 são executados sem alteração no Windows PowerShell 4.0. No entanto, devido a uma mudança na política de ativação de tempo de execução no Microsoft .NET Framework 4, programas host do Windows PowerShell escritos para o Windows PowerShell 2.0 e compilados com CLR (Common Language Runtime) 2.0 não podem ser executados sem modificações nas versões posteriores do Windows PowerShell, que é compilado com CLR 4.0.

Para manter a compatibilidade com versões anteriores de comandos e programas host afetados por essas alterações, os mecanismos do Windows PowerShell 2.0, Windows PowerShell 3.0 e Windows PowerShell 4.0 são projetados para funcionar lado a lado. Além disso, o Mecanismo Windows PowerShell 2.0 está incluído no Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 e Windows Management Framework 3.0. O Mecanismo Windows PowerShell 2.0 deve ser usado somente quando um programa de script ou host existente não puder ser executado porque é incompatível com o Windows PowerShell 3.0, Windows PowerShell 4.0 ou Microsoft .NET Framework 4. Tais casos devem ser raros.

O Mecanismo Windows PowerShell 2.0 é um recurso opcional do Windows Server 2012 R2, Windows 8.1, Windows® 8 e Windows Server® 2012. Em versões anteriores do Windows, quando você instala o Windows Management Framework 3.0, a instalação do Windows PowerShell 3.0 substitui completamente a instalação do Windows PowerShell 2.0 no diretório de instalação do Windows PowerShell. No entanto, o Mecanismo Windows PowerShell 2.0 é mantido.

Para obter informações sobre como iniciar o Mecanismo do Windows PowerShell 2.0, consulte [Iniciando o Mecanismo do Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## No Windows 8.1 e Windows 8
No Windows 8.1 e Windows 8, o recurso do mecanismo Windows PowerShell 2.0 é ativado por padrão. No entanto, para usá-lo, você precisa ativar a opção para Microsoft .NET Framework 3.5, que ele exige. Esta seção também explica como ativar e desativar o recurso do mecanismo Windows PowerShell 2.0.

#### Para ativar o .NET Framework 3.5

1.  Na tela **Iniciar**, clique em **Recursos do Windows**.

2.  Em **Aplicativos**, clique em **Configurações** e em **Ativar ou desativar recursos do Windows**.

3.  Na caixa **Recursos do Windows**, clique em **.NET Framework 3.5 (inclui o .NET 2.0 e 3.0** para selecioná-la.

    Quando você seleciona **.NET Framework 3.5 (inclui o .NET 2.0 e 3.0**, a caixa é preenchida para indicar que apenas parte do recurso está selecionada. No entanto, isso é suficiente para o Mecanismo Windows PowerShell 2.0.

#### Para ativar ou desativar o Mecanismo Windows PowerShell 2.0

1.  Na tela **Iniciar**, clique em **Recursos do Windows**.

2.  Em **Aplicativos**, clique em **Configurações** e em **Ativar ou desativar recursos do Windows**.

3.  Na caixa **Recursos do Windows**, expanda o nó **Windows PowerShell 2.0** e clique na caixa **Mecanismo Windows PowerShell 2.0** para selecioná-la ou limpá-la.

## No Windows Server 2012 R2 e Windows Server 2012
Use os seguintes procedimentos para adicionar os recursos dos Mecanismos Windows PowerShell 2.0 e Microsoft .NET Framework 3.5. O Mecanismo do Windows PowerShell 2.0 requer o Microsoft .NET Framework 2.0.50727 no mínimo. Esse requisito é atendido pelo Microsoft .NET Framework 3.5.

#### Para adicionar o recurso .NET Framework 3.5

1.  Em **Gerenciador do Servidor**, no menu **Gerenciar** clique em **Adicionar Funções e Recursos**.

    Se preferir, no **Gerenciador do Servidor**, clique em **Todos os Servidores**, clique com o botão direito do mouse em um nome do servidor e selecione **Adicionar Funções e Recursos**.

2.  Na página **Tipo de Instalação**, selecione **Instalação baseada em função ou em recurso**.

3.  Sobre a página **Recursos**, expanda o nó **Recursos do .NET 3.5 Framework** e selecione **.NET Framework 3.5 (inclui .NET 2.0 e 3.0)**.

    As outras opções nesse esse nó não são necessárias ao Mecanismo Windows PowerShell 2.0.

#### Para adicionar o recurso do Mecanismo Windows PowerShell 2.0

-   Em **Gerenciador do Servidor**, no menu **Gerenciar** clique em **Adicionar Funções e Recursos**.

    Se preferir, no **Gerenciador do Servidor**, clique em **Todos os Servidores**, clique com o botão direito do mouse em um nome do servidor e selecione **Adicionar Funções e Recursos**.

-   Na página **Tipo de Instalação**, selecione **Instalação baseada em função ou em recurso**.

-   Na página **Recursos**, expanda o nó **Windows PowerShell (Instalado)** e selecione **Mecanismo do Windows PowerShell 2.0**.

Para obter informações sobre como iniciar o Mecanismo do Windows PowerShell 2.0, consulte [Iniciando o Mecanismo do Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## Em sistemas anteriores
O pacote [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) que instala o Windows PowerShell 4.0 no Windows 7, Windows Server 2008 R2 e Windows Server 2012, inclui o Mecanismo Windows PowerShell 2.0. O Mecanismo Windows PowerShell 2.0 está habilitado e pronto para uso, se necessário, sem instalação ou configuração adicional.

O pacote Windows Management Framework 3.0 que instala o Windows PowerShell 3.0 no Windows 7, Windows Server 2008 R2 e Windows Server 2008, inclui o Mecanismo Windows PowerShell 2.0. O Mecanismo Windows PowerShell 2.0 está habilitado e pronto para uso, se necessário, sem instalação ou configuração adicional.

## Consulte Também
[Requisitos do Sistema do Windows PowerShell](Windows-PowerShell-System-Requirements.md)
[Instalando o Windows PowerShell](Installing-Windows-PowerShell.md)
[Iniciando o Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
[Iniciando o Mecanismo do Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md)




<!--HONumber=Jun16_HO4-->


