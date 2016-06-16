---
title:  Requisitos do Sistema do Windows PowerShell
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
---

# Requisitos do Sistema do Windows PowerShell
Este tópico lista os requisitos do sistema para o Windows PowerShell 3.0 e Windows PowerShell 4.0 e recursos especiais, como o ISE (Ambiente de Script Integrado) do Windows PowerShell, comandos CIM e fluxos de trabalho.

O Windows® 8.1 e o Windows Server® 2012 R2 incluem todos os programas necessários. Este tópico foi criado para usuários de versões anteriores do Windows.

## Requisitos de sistema operacional
O Windows PowerShell 4.0 é executado nas seguintes versões do Windows.

-   Windows 8.1, instalado por padrão

-   Windows Server 2012 R2, instalado por padrão

-   Windows® 7 com Service Pack 1, instale o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) para executar o Windows PowerShell 4.0

-   Windows Server® 2008 R2 com Service Pack 1, instale o [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) para executar o Windows PowerShell 4.0

O Windows PowerShell 3.0 é executado nas seguintes versões do Windows.

-   Windows 8, instalado por padrão

-   Windows Server 2012, instalado por padrão

-   Windows® 7 com Service Pack 1, instale o [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) para executar o Windows PowerShell 3.0

-   Windows Server® 2008 R2 com Service Pack 1, instale o [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) para executar o Windows PowerShell 3.0

-   Windows Server 2008 com Service Pack 2, instale o [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) para executar o Windows PowerShell 3.0

## Requisitos do Microsoft .NET Framework
O Windows PowerShell 4.0 requer a instalação completa do Microsoft .NET Framework 4.5. O Windows 8.1 e o Windows Server 2012 R2 incluem o Microsoft .NET Framework 4.5 por padrão.

O Windows PowerShell 3.0 requer a instalação completa do Microsoft .NET Framework 4. O Windows 8 e o Windows Server 2012 incluem o Microsoft .NET Framework 4.5 por padrão, o que atende a esse requisito.

Para instalar o Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) consulte [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) no Centro de Download da Microsoft.

Para instalar a instalação completa do Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) consulte [Microsoft .NET Framework 4 (Instalador da Web)](http://go.microsoft.com/fwlink/?LinkID=212931) no Centro de Download da Microsoft.

## WS-Management 3.0
O Windows PowerShell 3.0 e Windows PowerShell 4.0 requerem o WS-Management 3.0, que dá suporte ao serviço WinRM e ao protocolo WSMan. Esse programa está incluído no Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 e Windows Management Framework 3.0.

## Instrumentação de Gerenciamento do Windows 3.0
O Windows PowerShell 3.0 e o Windows PowerShell 4.0 exigem a WMI (Instrumentação de Gerenciamento do Windows) 3.0. Esse programa está incluído no Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 e Windows Management Framework 3.0. Se este programa não estiver instalado no computador, os recursos que exigem o WMI, como comandos CIM, não serão executados.

## Common Language Runtime 4.0
O Windows PowerShell 3.0 e o Windows PowerShell 4.0 são compilados no CLR (Common Language Runtime) 4.0.

## Requisitos da interface gráfica do usuário
O Windows PowerShell é um aplicativo baseado em console que não requer uma interface do usuário gráfica. Como tal, é ele adequado para computadores que não têm telas, monitores ou uma interface do usuário, como as opções de instalação Server Core do Windows Server 2012 R2 ou Windows Server 2012.

No entanto, alguns itens, como os seguintes, exigem uma interface do usuário gráfica. Para obter mais detalhes, consulte o tópico de ajuda para cada item.

-   Ambiente de script integrado do Windows PowerShell (ISE)

-   Cmdlets

    1.  [Out-GridView](https://technet.microsoft.com/en-us/library/70915a86-d753-464e-8349-cba02316154c)

    2.  [Show-Command](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [Show-ControlPanelItem](https://technet.microsoft.com/en-us/library/0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [Show-EventLog](https://technet.microsoft.com/en-us/library/a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   Parâmetros

    1.  Parâmetro **ShowWindow** do cmdlet [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a).

    2.  Parâmetro **ShowSecurityDescriptorUI** dos cmdlets [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) e [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea).

## Requisitos do Mecanismo do Windows PowerShell
O Windows PowerShell 4.0 é projetado para ser compatível com o PowerShell 3.0 e o Windows PowerShell 2.0. Cmdlets, provedores, snap-ins, módulos e scripts escritos para o Windows PowerShell 2.0 e Windows PowerShell 3.0 são executados sem alteração no Windows PowerShell 4.0.

No entanto, devido a uma mudança na política de ativação de tempo de execução no Microsoft .NET Framework 4, os programas host do Windows PowerShell escritos para o Windows PowerShell 2.0 e compilados com o CLR (Common Language Runtime) 2.0 não podem ser executados sem modificações no Windows PowerShell 3.0, que é compilado com o CLR 4.0.

O mecanismo do Windows PowerShell 2.0 requer o Microsoft .NET Framework 2.0.50727 no mínimo. Esse requisito é atendido pelo Microsoft .NET Framework 3.5 Service Pack 1. Esse requisito não é atendido pelo Microsoft .NET Framework 4 e versões posteriores do Microsoft .NET Framework.

Para obter informações sobre como adicionar ou instalar o mecanismo do Windows PowerShell 2.0 e adicionar ou instalar as versões necessárias do Microsoft .NET Framework, consulte [Installing the Windows PowerShell 2.0 Engine](Installing-the-Windows-PowerShell-2.0-Engine.md) (Instalando o mecanismo do Windows PowerShell 2.0). Para obter informações sobre como iniciar o mecanismo do Windows PowerShell 2.0, consulte [Iniciando o Mecanismo do Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## Ambiente de Pré-instalação do Windows
O Windows PowerShell 2.0, o Windows PowerShell 3.0 e o Windows PowerShell 4.0 são executados no Windows PE (Ambiente de Pré-Instalação do Windows). No entanto, não há suporte para os seguintes cmdlets.

-   [Cmdlets do BITS (Serviço de Transferência Inteligente em Segundo Plano)](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/b4985b11-82bf-487d-928d-becd96fc0419)

-   [Get-WinEvent](https://technet.microsoft.com/en-us/library/5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545)

Além disso, o serviço do **WinRM** não está presente no Windows PE.

## Consulte Também
[Introdução ao Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)

[Instalar o Windows PowerShell](Installing-Windows-PowerShell.md)

[Iniciando o Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=May16_HO2-->


