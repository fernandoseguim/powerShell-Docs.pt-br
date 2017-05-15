---
title: Chave do Registro de DSCAutomationHostEnabled
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: eb5889668136def1b47a4999374711460a08179c
ms.sourcegitcommit: 6057e6d22ef8a2095af610e0d681e751366a9773
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2017
---
>Aplica-se a: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Chave do Registro de DSCAutomationHostEnabled

O DSC usa a chave do Registro **DSCAutomationHostEnabled** em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para habilitar a configuração do computador na inicialização inicial.
O DSCAutomationHostEnabled dá suporte a três modos:

|  O valor de DSCAutomationHostEnabled  |  Descrição   | 
|---|---| 
0 | Desabilite a configuração do computador na inicialização. |
1 | Habilite a configuração do computador na inicialização. |
2 | Habilite a configuração do computador somente se o DSC estiver no estado atual ou pendente. Este é o valor padrão. |

## <a name="see-also"></a>Consulte Também

Para obter um exemplo de como usar esse recurso para executar as configurações na inicialização inicial, veja [Configurar uma máquina virtual na inicialização inicial usando a DSC](bootstrapDsc.md).


