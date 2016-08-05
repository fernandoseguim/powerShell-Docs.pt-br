---
title: "Notas de versão do WMF 5.1 (Preview)"
ms.date: 2016-07-27
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 5eb9eae6257cdb57f4f778b5dddf5aa7ef9d10bb
ms.openlocfilehash: 12f2c084ab92134b733ee037c3d9fbd512af2e4c

---

# Notas de Versão da Preview do Windows Management Framework (WMF) 5.1 #

A Preview do WMF 5.1 inclui os componentes do PowerShell, WMI, o WinRM e o Inventário de Software e Licenciamento (SIL), que estão sendo lançados com o Windows Server 2016. O WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e fornece diversos aprimoramentos ao WMF 5.0 RTM, incluindo:

- Novos cmdlets: usuários e grupos locais; Get-ComputerInfo
- Os aprimoramentos do PowerShellGet incluem a imposição de módulos assinados e a instalação de módulos JEA
- Suporte acrescentado para o PackageManagement para Contêineres, Configuração de CBS, configuração baseada em EXE, pacotes CAB
- Melhorias de depuração para classes DSC e PowerShell
- Aprimoramentos de segurança, incluindo a imposição de módulos de catálogo assinado provenientes do Servidor de Recepção e ao usar cmdlets do PowerShellGet
- Respostas para diversos problemas e solicitações de usuários

**Observações importantes:**

- **A Preview do WMF 5.1 exige o Windows Management Framework (WMF) 4.6**. Instalação terá êxito, mas ocorrerá falha nos principais recursos se o .NET 4.6 não estiver instalado. As instruções estão disponíveis no tópico [Instalar e Configurar WMF 5.1 (Preview)](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure). 
- **Não há suporte para a Preview do WMF 5.1 para implantações de produção** no momento. Ele destina-se a fornecer informações preliminares sobre o que há na versão e lhe dá a oportunidade de fornecer comentários à equipe do PowerShell.
- A Preview do WMF 5.1 pode ser instalada diretamente pelo WMF 5.0.
- Este é um problema conhecido que o WMF 4.0 atualmente é necessário para instalar a Preview do WMF 5.1 no Windows 7 e Windows Server 2008. Esse requisito deve ser removido antes da versão final.
- A instalação de versões futuras do WMF 5.1, incluindo a versão RTM, exigirá a desinstalação da Preview do WMF 5.1.



<!--HONumber=Jul16_HO5-->


