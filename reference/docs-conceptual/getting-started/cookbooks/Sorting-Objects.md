---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Classificação de objetos
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 272d550a67b206f9924ebe143eca2f5906c0a304
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="sorting-objects"></a><span data-ttu-id="b0e65-103">Classificação de objetos</span><span class="sxs-lookup"><span data-stu-id="b0e65-103">Sorting Objects</span></span>

<span data-ttu-id="b0e65-104">É possível organizar os dados exibidos para facilitar a verificação usando o cmdlet **Sort-Object**.</span><span class="sxs-lookup"><span data-stu-id="b0e65-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="b0e65-105">O **Sort-Object** obtém o nome de uma ou mais propriedades para classificar e retorna os dados classificados pelos valores dessas propriedades.</span><span class="sxs-lookup"><span data-stu-id="b0e65-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="b0e65-106">Considere o problema de listagem das instâncias do Win32_SystemDriver.</span><span class="sxs-lookup"><span data-stu-id="b0e65-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="b0e65-107">Se quisermos classificar por **Estado** e depois por **Nome**, poderemos fazer isso digitando:</span><span class="sxs-lookup"><span data-stu-id="b0e65-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="b0e65-108">Embora essa seja uma tela longa, você pode ver os itens com o mesmo estado agrupado juntos:</span><span class="sxs-lookup"><span data-stu-id="b0e65-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

```output
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

<span data-ttu-id="b0e65-109">Você também pode classificar os objetos na ordem inversa, especificando o parâmetro **Descending**.</span><span class="sxs-lookup"><span data-stu-id="b0e65-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="b0e65-110">Isso inverte a ordem de classificação para que os nomes sejam classificados em ordem alfabética inversa e os números sejam classificados por ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="b0e65-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

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