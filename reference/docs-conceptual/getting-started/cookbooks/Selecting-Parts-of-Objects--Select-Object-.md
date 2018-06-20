---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Selecionar partes de objetos com Select Object
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953881"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="b1a93-103">Selecionar partes de objetos (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="b1a93-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="b1a93-104">Você pode usar o cmdlet **Select-Object** para criar objetos do Windows PowerShell novos e personalizados que contêm as propriedades selecionadas dos objetos usados para criá-los.</span><span class="sxs-lookup"><span data-stu-id="b1a93-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="b1a93-105">Digite o seguinte comando para criar um novo objeto que inclui apenas as propriedades Name e FreeSpace da classe WMI Win32_LogicalDisk:</span><span class="sxs-lookup"><span data-stu-id="b1a93-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="b1a93-106">Não é possível ver o tipo de dados depois de emitir esse comando, mas, se você direcionar o resultado para Get-Member depois do Select-Object, verá que há um novo tipo de objeto, um PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="b1a93-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

<span data-ttu-id="b1a93-107">Select-Object tem muitos usos.</span><span class="sxs-lookup"><span data-stu-id="b1a93-107">Select-Object has many uses.</span></span> <span data-ttu-id="b1a93-108">Um deles é replicar dados que você pode modificar.</span><span class="sxs-lookup"><span data-stu-id="b1a93-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="b1a93-109">Agora podemos manipular o problema que encontramos na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="b1a93-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="b1a93-110">Podemos atualizar o valor de FreeSpace em nossos objetos recém-criados e a saída incluirá o rótulo descritivo:</span><span class="sxs-lookup"><span data-stu-id="b1a93-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```