---
title: Recurso Log de DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 62f993e3d3e6ef744fb07920d332d476dfd24fc6
ms.openlocfilehash: 60085295fa7df6179a81cd98859cd33e6923150f

---

# Recurso Log de DSC 

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

[Onde estão os Logs de Eventos de DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Mensagem| Indica a mensagem que você deseja escreve no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de a mensagem do log ser escrita. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemplo

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




<!--HONumber=Sep16_HO3-->


