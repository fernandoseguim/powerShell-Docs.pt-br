---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
title: "Notas de versão do WMF 5.1"
ms.openlocfilehash: f80c1ec5886578e3e43f2c96981f40152db000d1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="windows-management-framework-wmf-51-release-notes" class="xliff"></a>
# Notas de versão do Windows Management Framework (WMF) 5.1 #

O WMF 5.1 inclui os componentes do PowerShell, WMI, do WinRM e do SIL (Inventário de Software e Licenciamento), que foram lançados com o Windows Server 2016.
O WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e fornece diversos aprimoramentos ao WMF 5.0 RTM, incluindo:

- Novos cmdlets: usuários e grupos locais; Get-ComputerInfo
- Os aprimoramentos do PowerShellGet incluem a imposição de módulos assinados e a instalação de módulos JEA
- Suporte acrescentado para o PackageManagement para Contêineres, Configuração de CBS, configuração baseada em EXE, pacotes CAB
- Melhorias de depuração para classes DSC e PowerShell
- Aprimoramentos de segurança, incluindo a imposição de módulos de catálogo assinado provenientes do Servidor de Recepção e ao usar cmdlets do PowerShellGet
- Respostas para diversos problemas e solicitações de usuários

**Observações importantes:**

- **O WMF 5.1 exige o .NET Framework 4.5.2**. A instalação terá êxito, mas ocorrerá falha nos principais recursos se o .NET 4.5.2 não estiver instalado. As instruções estão disponíveis no tópico [Instalar e Configurar WMF 5.1](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure).
- A visualização do WMF 5.1 deve ser desinstalada antes de instalar a versão RTM do WMF 5.1.
- O WMF 5.1 pode ser instalado diretamente sobre o WMF 5.0 ou o WMF 4.0.
- Não é __necessário__ instalar o WMF 4.0 antes de instalar o WMF 5.1 no Windows 7 e no Windows Server 2008 R2. Este era um problema na versão de visualização do WMF 5.1 e ele foi resolvido.  


