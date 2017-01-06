---
title: WMF (Windows Management Framework)
ms.date: 2016-12-07
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: b652613561655c4cbd63342b0fcc495195f83a80
ms.sourcegitcommit: b88151841dd44c8ee9296d0855d8b322cbf16076
translationtype: HT
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

- [WMF 5.1 (Visualização)](5.1/release-notes.md)
- [Windows Management Framework 5.0](5.0/releasenotes.md)

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
