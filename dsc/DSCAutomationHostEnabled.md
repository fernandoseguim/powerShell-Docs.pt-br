
---
título: chave do Registro de DSCAutomationHostEnabled ms.date: 2016-05-16 palavras-chave: powershell, DSC descrição:  
ms.topic:  article author:  eslesar manager:  dongill ms.prod:  powershell
---

>Aplica-se a: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Chave do Registro de DSCAutomationHostEnabled

O DSC usa a chave do Registro **DSCAutomationHostEnabled** em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para configurar automaticamente o computador na inicialização inicial.
O DSCAutomationHostEnabled dá suporte a três modos:

|  O valor de DSCAutomationHostEnabled  |  Descrição   | 
|---|---| 
0 | Desabilite a configuração do computador na inicialização. |
1 | Habilite a configuração do computador na inicialização. |
2 | Habilite a configuração do computador somente se o DSC estiver no estado atual ou pendente. Este é o valor padrão. |

## <a name="see-also"></a>Consulte Também

Para obter um exemplo de como usar esse recurso para executar as configurações na inicialização inicial, veja [Configurar uma máquina virtual na inicialização inicial usando a DSC](bootstrapDsc.md).


