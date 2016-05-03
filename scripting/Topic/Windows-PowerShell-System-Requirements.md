---
title: Requisitos do Sistema do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
---
# Requisitos do Sistema do Windows PowerShell
Este tópico lista os requisitos de sistema para o [!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)], bem como para recursos especiais, como o [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)], comandos CIM e fluxos de trabalho.

[!INCLUDE[winblue_client_1](../Token/winblue_client_1_md.md)] e [!INCLUDE[winblue_server_1](../Token/winblue_server_1_md.md)] incluem todos os programas necessários. Este tópico foi criado para usuários de versões anteriores do Windows.

## Requisitos de sistema operacional
O [!INCLUDE[psversion4](../Token/psversion4_md.md)] executa nas seguintes versões do Windows.

-   [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], instalado por padrão

-   [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], instalado por padrão

-   [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] com Service Pack 1, instale o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) para executar o [!INCLUDE[psversion4](../Token/psversion4_md.md)]

-   [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] com Service Pack 1, instale o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) para executar o [!INCLUDE[psversion4](../Token/psversion4_md.md)]

O [!INCLUDE[psversion3](../Token/psversion3_md.md)] executa nas seguintes versões do Windows.

-   [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], instalado por padrão

-   [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], instalado por padrão

-   [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] com Service Pack 1, instale o [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) para executar o [!INCLUDE[psversion3](../Token/psversion3_md.md)]

-   [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] com Service Pack 1, instale o [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) para executar o [!INCLUDE[psversion3](../Token/psversion3_md.md)]

-   [!INCLUDE[lserver](../Token/lserver_md.md)] com Service Pack 2, instale o [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) para executar o [!INCLUDE[psversion3](../Token/psversion3_md.md)]

## Requisitos do Microsoft .NET Framework
O [!INCLUDE[psversion4](../Token/psversion4_md.md)] requer a instalação completa do Microsoft .NET Framework 4.5. [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] e [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] incluem o Microsoft .NET Framework 4.5 por padrão.

O [!INCLUDE[psversion3](../Token/psversion3_md.md)] requer a instalação completa do Microsoft .NET Framework 4. [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] e [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] incluem o Microsoft .NET Framework 4.5 por padrão, que atende a esse requisito.

Para instalar o Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) consulte [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) no Centro de Download da Microsoft.

Para instalar a instalação completa do Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) consulte [Microsoft .NET Framework 4 (Instalador da Web)](http://go.microsoft.com/fwlink/?LinkID=212931) no Centro de Download da Microsoft.

## WS-Management 3.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)] requerem o WS-Management 3.0, que dá suporte ao serviço WinRM e o protocolo WSMan. Este programa está incluído em [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], Windows Management Framework 4.0 e [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)].

## Instrumentação de Gerenciamento do Windows 3.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)] requerem o WMI (Instrumentação de Gerenciamento do Windows) 3.0. Este programa está incluído em [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], Windows Management Framework 4.0 e [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]. Se este programa não estiver instalado no computador, os recursos que exigem o WMI, como comandos CIM, não serão executados.

## Common Language Runtime 4.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)] são compilados em CLR (Common Language Runtime) 4.0.

## Requisitos da interface gráfica do usuário
O [!INCLUDE[wps_2](../Token/wps_2_md.md)] é um aplicativo baseado em console que não requer uma interface do usuário gráfica. Como tal, é ele adequado para computadores que não têm telas, monitores ou uma interface do usuário, como as opções de instalação Server Core do [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] ou [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)].

No entanto, alguns itens, como os seguintes, exigem uma interface do usuário gráfica. Para obter mais detalhes, consulte o tópico de ajuda para cada item.

-   [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

-   Cmdlets

    1.  [Out-GridView](https://technet.microsoft.com/en-us/library/70915a86-d753-464e-8349-cba02316154c)

    2.  [Show-Command](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [Show-ControlPanelItem](https://technet.microsoft.com/en-us/library/0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [Show-EventLog](https://technet.microsoft.com/en-us/library/a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   Parâmetros

    1.  Parâmetro **ShowWindow** do cmdlet [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a).

    2.  Parâmetro **ShowSecurityDescriptorUi** dos cmdlets [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) e [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea).

## Requisitos do Mecanismo do Windows PowerShell
O [!INCLUDE[psversion4](../Token/psversion4_md.md)] é projetado para ser compatível com versões anteriores do [!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Cmdlets, provedores, snap-ins, módulos e scripts desenvolvidos para o [!INCLUDE[psversion2](../Token/psversion2_md.md)] e [!INCLUDE[psversion3](../Token/psversion3_md.md)] são executados sem alterações no [!INCLUDE[psversion4](../Token/psversion4_md.md)].

No entanto, devido a uma alteração na política de ativação do tempo de execução no Microsoft .NET Framework 4, programas de host do [!INCLUDE[wps_2](../Token/wps_2_md.md)] que foram desenvolvidos para [!INCLUDE[psversion2](../Token/psversion2_md.md)] e compilados com o CLR (Common Language Runtime) 2.0 não podem ser executado sem modificação no [!INCLUDE[psversion3](../Token/psversion3_md.md)], que é compilado com o CLR 4.0.

O Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] requer o Microsoft .NET Framework 2.0.50727 no mínimo. Esse requisito é atendido pelo Microsoft .NET Framework 3.5 Service Pack 1. Esse requisito não é atendido pelo Microsoft .NET Framework 4 e versões posteriores do Microsoft .NET Framework.

Para obter informações sobre como adicionar ou instalar o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] e adicionar ou instalar as versões necessárias do Microsoft .NET Framework, consulte [Instalar o Mecanismo do Windows PowerShell 2.0](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md). Para obter informações sobre como iniciar o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)], consulte [Iniciar o Mecanismo do Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## Ambiente de Pré-instalação do Windows
[!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] e [!INCLUDE[psversion4](../Token/psversion4_md.md)] são executados no Windows PE (Ambiente de Pré-Instalação do Windows). No entanto, não há suporte para os seguintes cmdlets.

-   [Cmdlets do BITS (Serviço de Transferência Inteligente em Segundo Plano)](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/b4985b11-82bf-487d-928d-becd96fc0419)

-   [Get-WinEvent[PSITPro5_Diagnostic]](https://technet.microsoft.com/en-us/library/5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545)

Além disso, o serviço do **WinRm** não está presente no Windows PE.

## Consulte Também
[Introdução ao Windows PowerShell](../Topic/Getting-Started-with-Windows-PowerShell.md)
[Instalar o Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[Iniciando o Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO2-->


