---
title: Instalar o Windows PowerShell
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
translationtype: Human Translation
ms.sourcegitcommit: f856f170c6e18be8758d52df9b50ac443531fdf2
ms.openlocfilehash: 415e68b372c831ed8dd4535c2968e5a36b5cb65d

---

# Instalar o Windows PowerShell
O Windows® 8 e o Windows Server® 2012 incluem o Windows PowerShell 3.0 e todos os seus pré-requisitos. O sistema também inclui o Mecanismo Windows PowerShell 2.0 para compatibilidade com programas host que não podem usar o Windows PowerShell 3.0.

Este tópico explica como instalar o Windows PowerShell 3.0 em sistemas anteriores e instalar e habilitar os recursos necessários.

Este tópico inclui as seções a seguir:

-   [Instalar o Windows PowerShell no Windows 8 e no Windows Server 2012](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [Instalar o Windows PowerShell no Windows 7 e no Windows Server 2008 R2](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [Instalar o Windows PowerShell no Windows Server 2008](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [Instalar o Windows PowerShell no Server Core](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [Implantar o Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [Instalar o Mecanismo do Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Instalar o Windows PowerShell no Windows 8 e no Windows Server 2012
O Windows PowerShell 3.0 chega instalado, configurado e pronto para uso. O ISE (Ambiente de Script Integrado) do Windows PowerShell está instalado e habilitado. Para obter informações sobre como iniciar o Windows PowerShell, consulte [Starting Windows PowerShell on Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) (Iniciando o Windows PowerShell no Windows 8) e [Starting Windows PowerShell on Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell) (Iniciando o Windows PowerShell no Windows Server 2012).

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Instalar o Windows PowerShell no Windows 7 e no Windows Server 2008 R2
Estas instruções explicam como instalar o Windows PowerShell 3.0 em computadores com o Windows 7 com Service Pack 1 e Windows Server 2008 R2 com Service Pack 1. Há instruções de instalação separadas abaixo para computadores que executam com a opção de instalação Server Core do Windows Server 2008 R2.

#### Preparando para instalar

-   Antes de instalar o Windows Management Framework 3.0, desinstale todas as versões anteriores do Windows Management Framework 3.0.

#### Para instalar o Windows PowerShell 3.0

1.  Instale a instalação completa do Microsoft .NET Framework 4 (dotNetFx40\_Full\_setup.exe) do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Ou, instale o Microsoft .NET Framework 4.5 (dotNetFx45\_Full\_setup.exe) do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

2.  Instale o Windows Management Framework 3.0 do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

Para obter informações sobre como iniciar o Windows PowerShell 3.0, consulte [Starting Windows PowerShell on Earlier Versions of Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md) (Iniciando o Windows PowerShell em versões anteriores do Windows).

## <a name="BKMK_InstallingOnServerCore"></a>Instalar o Windows PowerShell no Server Core
Essas instruções explicam como instalar o Windows PowerShell 3.0 em computadores que executam a opção de instalação Server Core do Windows Server 2008 R2 com Service Pack 1.

Os primeiros passos do procedimento usam os comandos DISM (Gerenciamento e Manutenção de Imagens de Implantação) para instalar o Microsoft .NET Framework 2.0 para Server Core e Windows PowerShell 2.0. Esses programas são pré-requisitos para o Windows Management Framework 3.0, que é instalado em uma etapa posterior.

#### Preparando para instalar

-   Antes de instalar o Windows Management Framework 3.0, desinstale todas as versões anteriores do Windows Management Framework 3.0.

#### Para instalar o Windows PowerShell 3.0

1.  Iniciar Cmd.exe

2.  Execute um dos seguintes comandos DISM. Esses comandos instalam o .NET Framework 2.0 e Windows PowerShell 2.0.

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  Instale a instalação completa do Microsoft .NET Framework 4.0 para Server Core do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).

4.  Instale o Windows Management Framework 3.0 do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>Instalar o Windows PowerShell no Windows Server 2008
Essas instruções explicam como instalar o Windows PowerShell 3.0 em computadores com o Windows Server 2008 com o Service Pack 2.

Em sistemas Windows Server 2008, o Windows Management Framework (Windows PowerShell 2.0, KB 968930) é um pré-requisito para Windows Management Framework 3.0. O recurso de "Proteção Estendida para Autenticação" protege o computador contra ataques de encaminhamento de autenticação e permite que você use parâmetro **UseSSL** ao criar sessões remotas. Para instalar o Windows PowerShell 3.0 e o Mecanismo Windows PowerShell 2.0, utilize o seguinte procedimento.

#### Preparando para instalar

-   Antes de instalar o Windows Management Framework 3.0, desinstale todas as versões anteriores do Windows Management Framework 3.0.

#### Para instalar o Windows PowerShell 3.0

1.  Instale o Microsoft .NET Framework 3.5 com Service Pack 1 no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).

2.  Instale o Windows Management Framework (Windows PowerShell 2.0, KB 968930) do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).

3.  Instale a instalação completa do Microsoft .NET Framework 4 (dotNetFx40\_Full\_setup.exe) do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Ou, instale o Microsoft .NET Framework 4.5 (dotNetFx45\_Full\_setup.exe) do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

4.  Instale a "Proteção Estendida para Autenticação" (KB 968389) de [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).

5.  Instale o Windows Management Framework 3.0 do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## Consulte Também
[Requisitos do Sistema do Windows PowerShell](Windows-PowerShell-System-Requirements.md)
[Iniciando o Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Jun16_HO4-->


