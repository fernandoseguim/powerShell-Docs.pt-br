---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: "Classificação de objetos"
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2017
---
# <a name="sorting-objects"></a>Classificação de objetos
É possível organizar os dados exibidos para facilitar a verificação usando o cmdlet **Sort-Object**. O **Sort-Object** obtém o nome de uma ou mais propriedades para classificar e retorna os dados classificados pelos valores dessas propriedades.

Considere o problema de listagem das instâncias do Win32_SystemDriver. Se quisermos classificar por **Estado** e depois por **Nome**, poderemos fazer isso digitando:

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Embora essa seja uma tela longa, você pode ver os itens com o mesmo estado agrupado juntos:

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

Você também pode classificar os objetos na ordem inversa, especificando o parâmetro **Descending**. Isso inverte a ordem de classificação para que os nomes sejam classificados em ordem alfabética inversa e os números sejam classificados por ordem decrescente.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```

