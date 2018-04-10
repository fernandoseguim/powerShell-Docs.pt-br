---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
title: WMF (Windows Management Framework)
ms.openlocfilehash: 715ac6fe5df47066415a65d91a0982fd7070a426
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework"></a>Windows Management Framework

O WMF (Windows Management Framework) é o mecanismo de entrega que fornece uma interface de gerenciamento consistente entre as várias versões do Windows e do Windows Server.
Com a instalação do WMF, os clientes obtêm uma maneira perfeita de interoperar entre combinações de sistemas operacionais em seu ambiente.
O WMF disponibiliza as atualizações à funcionalidade de gerenciamento, em uma determinada versão do Windows e do Windows Server, disponível para instalação em versões anteriores (normalmente, duas versões inferiores) do Windows e do Windows Server.

A instalação do WMF adiciona e/ou atualiza os seguintes recursos:

- Usando o Windows PowerShell
- DSC (Configuração de Estado Desejado) do Windows PowerShell
- ISE (Ambiente de Script Integrado) do Windows PowerShell
- Gerenciamento Remoto do Windows (WinRM)
- Instrumentação de Gerenciamento do Windows (WMI)
- Serviços Web do Windows PowerShell (Extensão do IIS do Management OData)
- SIL (Log de Inventário de Software)
- Provedor CIM do Gerenciador do Servidor

## <a name="wmf-release-notes"></a>Notas de versão do WMF

Para saber mais sobre os vários aprimoramentos do PowerShell e outros componentes de um determinado WMF, consulte os links abaixo para examinar as notas de versão:

- [Windows Management Framework 5.1](5.1/release-notes.md)
- [Windows Management Framework 5.0](5.0/releasenotes.md)
- [Windows Management Framework 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Disponibilidade do WMF entre sistemas operacionais Windows

| Versão do sistema operacional | [Windows Management Framework 5.1](https://aka.ms/wmf51download) | [Windows Management Framework 5.0](https://aka.ms/wmf5download) | [Windows Management Framework 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | É fornecido na caixa |  |  |  |  |
| Windows 10 | É fornecido na caixa | É fornecido na caixa  | | | |
| Windows Server 2012 R2| Sim | Sim | É fornecido na caixa |  |  |
| Windows 8.1 | Sim | Sim |  É fornecido na caixa |  |  |
| Windows Server 2012 | Sim | Sim | Sim |  É fornecido na caixa | |
| Windows 8 |  |  |  | É fornecido na caixa | |
| Windows Server 2008 R2 SP1 | Sim | Sim | Sim |  Sim| É fornecido na caixa |
| Windows 7 SP1  | Sim | Sim | Sim | Sim | É fornecido na caixa |
| Windows Server 2008 SP2 | | | | Sim | Sim |
| Windows Vista | | | | | Sim |
| Windows Server 2003| | | |  | Sim |
| Windows XP | | | |  | Sim |

**"Fornecido na caixa"**: os recursos do `specified WMF` foram fornecidos na versão indicada do Windows e Windows Server.
Portanto, o `specified WMF` não precisa ser instalado nas versões do sistema operacional indicadas.