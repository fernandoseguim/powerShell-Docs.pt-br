---
title:  Selecionando partes de objetos com Select Object 
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  72e64b1a-d351-4500-9da3-24d8a71d7a92
---

# Selecionar partes de objetos (Select-Object)
Você pode usar o cmdlet **Select-Object** para criar objetos do Windows PowerShell novos e personalizados que contêm as propriedades selecionadas dos objetos usados para criá-los. Digite o seguinte comando para criar um novo objeto que inclui apenas as propriedades Name e FreeSpace da classe WMI Win32_LogicalDisk:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Você não pode ver o tipo de dados depois de emitir esse comando, mas, se você direcionar o resultado para Get-Member depois do Select-Object, verá que há um novo tipo de objeto, um PSCustomObject:

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



<!--HONumber=May16_HO2-->


