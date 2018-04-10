---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Recurso Log de DSC
ms.openlocfilehash: f1a528767508d4a0e7f0ea2e58fd27a6a4d7ec75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-log-resource"></a>Recurso Log de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso __Log__ na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para escrever mensagens no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

OBSERVAÇÃO: por padrão, somente os logs Operacionais da DSC são habilitados.
Antes que o log Analítico esteja disponível ou visível, ele deve ser habilitado.
Veja o artigo a seguir.

[Onde estão os logs de eventos de DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>Propriedades
|  Propriedade  |  Descrição   |
|---|---|
| Mensagem| Indica a mensagem que você deseja escreve no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.|
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de a mensagem do log ser escrita. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como incluir uma mensagem no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.

> **Observação**: se você executar [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) com esse recurso configurado, ele sempre gerará **$false**.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```