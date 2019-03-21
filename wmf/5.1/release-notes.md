---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,instalação
title: Notas de versão do WMF 5.1
ms.openlocfilehash: 61ca854cf8f26a9e96c6c5b5c06f6b54d08fb4ea
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795004"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Notas de versão do Windows Management Framework (WMF) 5.1

O WMF 5.1 inclui os componentes PowerShell, WMI, WinRM e SIL (Log de Inventário de Software) que foram lançados com o Windows Server 2016.
O WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e fornece diversos aprimoramentos ao WMF 5.0 RTM, incluindo:

- Novos cmdlets: usuários e grupos locais; Get-ComputerInfo
- Os aprimoramentos do PowerShellGet incluem a imposição de módulos assinados e a instalação de módulos JEA
- Suporte acrescentado para o PackageManagement para Contêineres, Configuração de CBS, configuração baseada em EXE, pacotes CAB
- Melhorias de depuração para classes DSC e PowerShell
- Aprimoramentos de segurança, incluindo a imposição de módulos de catálogo assinado provenientes do Servidor de Recepção e ao usar cmdlets do PowerShellGet
- Respostas para diversos problemas e solicitações de usuários

**Observações importantes:**

- **O WMF 5.1 exige o .NET Framework 4.5.2** (ou superior). A instalação terá êxito, mas os principais recursos falharão se o .NET 4.5.2 (ou superior) não estiver instalado. As instruções estão disponíveis no tópico [Instalar e configurar o WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure).
- A visualização do WMF 5.1 deve ser desinstalada antes de instalar a versão RTM do WMF 5.1.
- O WMF 5.1 pode ser instalado diretamente sobre o WMF 5.0 ou o WMF 4.0.
- Não é __necessário__ instalar o WMF 4.0 antes de instalar o WMF 5.1 no Windows 7 e no Windows Server 2008 R2. Este era um problema na versão de visualização do WMF 5.1 e ele foi resolvido.
