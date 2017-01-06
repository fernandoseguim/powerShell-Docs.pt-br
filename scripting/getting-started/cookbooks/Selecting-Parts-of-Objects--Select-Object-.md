---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: Selecionar partes de objetos com Select Object
ms.technology: powershell
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 5e0ca5110d7e35e49da3db779d9d495ea6b78e67
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="selecting-parts-of-objects-select-object"></a>Selecionar partes de objetos (Select-Object)
Você pode usar o cmdlet **Select-Object** para criar objetos do Windows PowerShell novos e personalizados que contêm as propriedades selecionadas dos objetos usados para criá-los. Digite o seguinte comando para criar um novo objeto que inclui apenas as propriedades Name e FreeSpace da classe WMI Win32_LogicalDisk:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Não é possível ver o tipo de dados depois de emitir esse comando, mas, se você direcionar o resultado para Get-Member depois do Select-Object, verá que há um novo tipo de objeto, um PSCustomObject:

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

Select-Object tem muitos usos. Um deles é replicar dados que você pode modificar. Agora podemos manipular o problema que encontramos na seção anterior. Podemos atualizar o valor de FreeSpace em nossos objetos recém-criados e a saída incluirá o rótulo descritivo:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```

