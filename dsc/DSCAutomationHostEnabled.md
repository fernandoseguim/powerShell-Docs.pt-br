---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Chave do Registro de DSCAutomationHostEnabled
ms.openlocfilehash: 9fd71120b4959a7b14094922b453b05b217f3736
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
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