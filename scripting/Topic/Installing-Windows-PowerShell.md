---
title: Instalar o Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
---
# Instalar o Windows PowerShell
[!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] e [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)] incluem [!INCLUDE[psversion3](../Token/psversion3_md.md)] e todos seus pré-requisitos. O sistema também inclui o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)] para fins de compatibilidade com programas de host que não podem usar [!INCLUDE[psversion3](../Token/psversion3_md.md)].

Este tópico explica como instalar o [!INCLUDE[psversion3](../Token/psversion3_md.md)] em sistemas anteriores, e instalar e habilitar os recursos necessários.

Este tópico inclui as seções a seguir:

-   [Instalar o Windows PowerShell no Windows 8 e no Windows Server 2012](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [Instalar o Windows PowerShell no Windows 7 e no Windows Server 2008 R2](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [Instalar o Windows PowerShell no Windows Server 2008](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [Instalar o Windows PowerShell no Server Core](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [Implantar o Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [Instalar o Mecanismo do Windows PowerShell 2.0](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Instalar o Windows PowerShell no Windows 8 e no Windows Server 2012
[!INCLUDE[psversion3](../Token/psversion3_md.md)] já vem instalado, configurado e pronto para usar. [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)] está instalado e habilitado. Para obter informações sobre como iniciar o [!INCLUDE[mshshort](../Token/mshshort_md.md)], consulte [Iniciar o Windows PowerShell no Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) e [Iniciar o Windows PowerShell no Windows Server 2012](https://technet.microsoft.com/en-us/library/4fc0110a-cc0c-42a4-bbb5-3cc89a0fc968).

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Instalar o Windows PowerShell no Windows 7 e no Windows Server 2008 R2
Estas instruções explicam como instalar o [!INCLUDE[psversion3](../Token/psversion3_md.md)] em computadores que executam o [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)] com o Service Pack 1 e o [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] com o Service Pack 1. Há instruções de instalação separadas abaixo para computadores com a opção de instalação Server Core do [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)].

#### Preparando para instalar

-   Antes de instalar o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], desinstale as versões anteriores do Windows Management Framework 3.0.

#### Para instalar o [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Instale a instalação completa do Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Ou então, instale o Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

2.  Instale o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

Para obter informações sobre como iniciar o [!INCLUDE[psversion3](../Token/psversion3_md.md)], consulte [Iniciar o Windows PowerShell em versões anteriores do Windows](../Topic/Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).

## <a name="BKMK_InstallingOnServerCore"></a>Instalar o Windows PowerShell no Server Core
Estas instruções explicam como instalar o [!INCLUDE[psversion3](../Token/psversion3_md.md)] em computadores que executam a opção de instalação Server Core do [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] com o Service Pack 1.

As primeiras etapas no procedimento usam comandos DISM (Gerenciamento e Manutenção de Imagens de Implantação) para instalar o Microsoft [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] Server Core e [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Esses programas são pré-requisitos para [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], que é instalado em uma etapa posterior.

#### Preparando para instalar

-   Antes de instalar o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], desinstale as versões anteriores do Windows Management Framework 3.0.

#### Para instalar o [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Iniciar Cmd.exe

2.  Execute um dos seguintes comandos DISM. Estes comandos instalam o [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] e o [!INCLUDE[psversion2](../Token/psversion2_md.md)].

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  Instale a instalação completa do Microsoft [!INCLUDE[netfx40_short](../Token/netfx40_short_md.md)] para Server Core do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).

4.  Instale o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>Instalar o Windows PowerShell no Windows Server 2008
Estas instruções explicam como instalar o [!INCLUDE[psversion3](../Token/psversion3_md.md)] em computadores que executam o [!INCLUDE[lserver](../Token/lserver_md.md)] com o Service Pack 2.

Em sistemas [!INCLUDE[lserver](../Token/lserver_md.md)], o Windows Management Framework ([!INCLUDE[psversion2](../Token/psversion2_md.md)], KB 968930) é um pré-requisito para o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]. O recurso de "Proteção Estendida para Autenticação" protege o computador contra ataques de encaminhamento de autenticação e permite que você use parâmetro **UseSSL** ao criar sessões remotas. Use o procedimento a seguir para instalar o [!INCLUDE[psversion3](../Token/psversion3_md.md)] e o Mecanismo do [!INCLUDE[psversion2](../Token/psversion2_md.md)].

#### Preparando para instalar

-   Antes de instalar o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], desinstale as versões anteriores do Windows Management Framework 3.0.

#### Para instalar o [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Instale o Microsoft .NET Framework 3.5 com Service Pack 1 no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).

2.  Instale o Windows Management Framework ([!INCLUDE[psversion2](../Token/psversion2_md.md)], KB 968930) no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).

3.  Instale a instalação completa do Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Ou então, instale o Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) no Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

4.  Instale a "Proteção Estendida para Autenticação" (KB 968389) de [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).

5.  Instale o [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] do Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## Consulte Também
[Requisitos do Sistema do Windows PowerShell](../Topic/Windows-PowerShell-System-Requirements.md)
[Iniciando o Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO2-->


