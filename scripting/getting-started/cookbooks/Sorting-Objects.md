---
title:  Classificação de objetos
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  8530caa8-3ed4-4c56-aed7-1295dd9ba199
---

# Classificação de objetos
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



<!--HONumber=May16_HO2-->


