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
ms.sourcegitcommit: 26da6c80568327faadc6746099ac9869f2018fcf
ms.openlocfilehash: 8a10903c421f62311a28c9f32e352bba75f21052

---

# Instalar e configurar o WMF 5.1 (Preview) #

***Observação:*** 
*este conteúdo é um espaço reservado. Os links a seguir apontam para o WMF versão 5.0 e serão atualizados quando os binários forem lançados.*

Baixe o pacote do WMF 5.1 para o sistema operacional e a arquitetura em que você deseja instalá-lo:

| Sistema operacional       | Arquitetura | Nome do pacote              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


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

> **Dependência de WinRM** – a DSC (Configuração de Estado Desejado) do Windows PowerShell depende do WinRM. O WinRM não é habilitado por padrão no Windows Server 2008 R2 e Windows 7. Para habilitar o WinRM, na sessão elevada do Windows PowerShell, execute `Set-WSManQuickConfig`.




<!--HONumber=Jul16_HO2-->


