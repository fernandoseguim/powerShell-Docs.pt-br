---
title: Instalar e configurar o WMF 5.1 (Preview)
ms.date: 2016-05-16
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
contributor: kriscv
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 0a53817d6af625822d9183d2a0d5bc7bf4d2b264
ms.openlocfilehash: 058d18deeb3d4926970ea25a157f92ad14836e4b

---

# Instalar e configurar o WMF 5.1 (Preview) #

## Instale o .NET 4.6
Você deve instalar o .NET Framework 4.6 para usar WMF 5.1. Isso é necessário para habilitar os novos recursos de assinatura de catálogo, que afetam várias áreas do carregamento de módulo e script no WMF 5.1. 

O [.NET Framework 4.6 está disponível como 3045560 KB](https://support.microsoft.com/en-us/kb/3045560). Instruções de instalação estão disponíveis no local de download.

> **Observação:** esse é um problema conhecido que o requisito do .NET 4.6 não é detectado pelo instalador da Preview do WMF 5.1, portanto você poderá instalar a Preview do WMF 5.1 antes de instalar o .NET 4.6. Nossos testes mostraram que você pode instalar o .NET 4.6 depois de instalar a Preview do WMF 5.1. A versão final do WMF 5.1 verificará corretamente essa exigência de pré-requisito antes da instalação. 

## Baixe e instale a Preview do WMF 5.1

Baixe o pacote do WMF 5.1 para o sistema operacional e a arquitetura em que você deseja instalá-lo:

| Sistema operacional       | Pré-requisitos | Links de pacote             |
|------------------------|---------------|---------------------------|
| Windows Server 2012 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586)|
| Windows Server 2012    | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823587)|
| Windows Server 2008 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> Atualização de segurança para [assinatura de código do SHA-2](https://technet.microsoft.com/en-us/library/security/3033929) | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) |
| Windows 8.1            | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | **x64:** [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586) </br> **x86:** [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823589) |
| Windows 7 SP1          | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> Atualização de segurança para [assinatura de código do SHA-2](https://technet.microsoft.com/en-us/library/security/3033929) | **x64:** [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) </br> **x86:** [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823590) |


## Instale o WMF 5.1 do Windows Explorer (ou Explorador de Arquivos no Windows Server 2012 R2 ou Windows 8.1)

1. Navegue até a pasta na qual você baixou o arquivo MSU.

2. Clique duas vezes no MSU para executá-lo.

## Instalar o WMF 5.1 do prompt de comando##

1. Depois de baixar o pacote correto para a arquitetura de seu computador, abra uma janela do Prompt de Comando com direitos de usuário elevados (Executar como Administrador). Nas opções de instalação Server Core do Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, por padrão, o Prompt de Comando é aberto com direitos de usuário elevados.

2. Altere os diretórios para a pasta para a qual você baixou ou copiou o pacote de instalação do WMF 5.1.

3. Execute um dos seguintes comandos:
    - Em computadores que executem o Windows Server 2012 R2 ou o Windows 8.1 x64, execute `Win8.1AndW2K12R2-KB3156422-x64.msu /quiet`.
    - Em computadores que executem o Windows Server 2012, execute `W2K12-KB3156423-x64.msu /quiet`.
    - Em computadores que executem o Windows Server 2008 R2 SP1 ou o Windows 7 SP1 x64, execute `Win7AndW2K8R2-KB3156424-x64.msu /quiet`.
    - Em computadores que executem o Windows 8.1 x86, execute `Win8.1-KB3156422-x86.msu /quiet`.
    - Em computadores que executem o Windows 7 SP1 x86, execute `Win7-KB3156424-x86.msu /quiet`.

## Notas de instalação adicionais para o Windows Server 2008 SP1 e o Windows 7 SP1##
Instalação do WMF 5.1 no Windows Server 2008 SP1 ou no Windows 7 SP1 exige a instalação do:
- Service pack mais recente.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)
- O WMF 5.1 exige o [Microsoft .NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560). Você pode instalar o Microsoft .NET Framework 4.6, seguindo as instruções no local de download.
- Atualização de segurança para [assinatura de código do SHA-2](https://technet.microsoft.com/en-us/library/security/3033929). Isso é necessário para usar novos cmdlets do PowerShell para os arquivos de catálogo do windows. 

> **Dependência de WinRM** – a DSC (Configuração de Estado Desejado) do Windows PowerShell depende do WinRM. O WinRM não é habilitado por padrão no Windows Server 2008 R2 e Windows 7. Para habilitar o WinRM, na sessão elevada do Windows PowerShell, execute `Set-WSManQuickConfig`.




<!--HONumber=Jul16_HO5-->


