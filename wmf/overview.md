---
ms.date: 06/12/2018
keywords: wmf,powershell,instalação
title: WMF (Windows Management Framework)
ms.openlocfilehash: 17011f88c364cb56a0c87f092873ccd99db450bc
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36943599"
---
# <a name="windows-management-framework"></a>Windows Management Framework

O WMF (Windows Management Framework) fornece uma interface de gerenciamento consistente para o Windows. O WMF fornece uma maneira perfeita de gerenciar várias versões do cliente Windows e do Windows Server. Os pacotes do instalador do WMF contêm as atualizações da funcionalidade de gerenciamento e estão disponíveis para versões mais antigas do Windows.

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

|Versão do sistema operacional  |[Windows Management Framework 5.1][] |[Windows Management Framework 5.0][] |[Windows Management Framework 4.0][] |[WMF 3.0][]  |[WMF 2.0][] |
|--------------------------|------------|------------|------------|-------------|------------|
|Windows Server 2016       |É fornecido na caixa|            |            |             |            |
|Windows 10                |É fornecido na caixa|É fornecido na caixa|            |             |            |
|Windows Server 2012 R2    |Sim         |Sim         |É fornecido na caixa|             |            |
|Windows 8.1               |Sim         |Sim         |É fornecido na caixa|             |            |
|Windows Server 2012       |Sim         |Sim         |Sim         |É fornecido na caixa |            |
|Windows 8                 |            |            |            |É fornecido na caixa |            |
|Windows Server 2008 R2 SP1|Sim         |Sim         |Sim         |Sim          |É fornecido na caixa|
|Windows 7 SP1             |Sim         |Sim         |Sim         |Sim          |É fornecido na caixa|
|Windows Server 2008 SP2   |            |            |            |Sim          |Sim         |
|Windows Vista             |            |            |            |             |Sim         |
|Windows Server 2003       |            |            |            |             |Sim         |
|Windows XP                |            |            |            |Sim          |            |

**Fornecido na caixa**: os recursos da versão especificada do WMF foram fornecidos na versão indicada do cliente Windows ou do Windows Server.

[Windows Management Framework 5.1]: https://aka.ms/wmf51download
[Windows Management Framework 5.0]: https://aka.ms/wmf5download
[Windows Management Framework 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
