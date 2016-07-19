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
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 97ffa20191016584fc2fba459c457787365d11ee

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

## Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Mensagem| Indica a mensagem que você deseja escreve no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de a mensagem do log ser escrita. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemplo

O exemplo a seguir mostra como incluir uma mensagem no log de eventos Microsoft-Windows-Desired State Configuration/Analytic.

> **Observação**: se você executar [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) com esse recurso configurado, ele sempre gerará **$false**.

```powershell 
Log LogExample
{
    Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
} 
```




<!--HONumber=Jun16_HO4-->


