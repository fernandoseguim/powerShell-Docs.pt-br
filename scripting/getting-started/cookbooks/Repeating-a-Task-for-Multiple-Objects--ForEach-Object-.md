---
title:  Repetindo uma tarefa para vários objetos  ForEach Object 
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  6697a12d-2470-4ed6-b5bb-c35e5d525eb6
---

# Repetir uma tarefa para vários objetos (ForEach-Object)
O cmdlet **ForEach-Object** usa blocos de script e o descritor $_ do objeto de pipeline atual para que você possa executar um comando em cada objeto no pipeline. Isso pode ser usado para executar algumas tarefas complicadas.

Uma situação em que isso pode ser útil é manipular dados para torná-los mais úteis. Por exemplo, a classe Win32_LogicalDisk do WMI pode ser usada para retornar informações de espaço livre para cada disco local. Contudo, os dados são retornados em bytes, o que dificulta a leitura:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Podemos pode converter o valor de FreeSpace em megabytes dividindo cada valor por 1024 duas vezes. Após a primeira divisão, os dados estão em quilobytes e após a segunda divisão estão em megabytes. Você pode fazer isso em um bloco de script do ForEach-Object digitando:

```
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Infelizmente, a saída agora é de dados sem nenhum rótulo associado. Como propriedades WMI como esta são somente leitura, não é possível converter diretamente o FreeSpace. Se você digitar:

```
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Receberá uma mensagem de erro:

```
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Você pode reorganizar os dados usando algumas técnicas avançadas, mas uma abordagem mais simples é criar um novo objeto, usando **Select-Object**.



<!--HONumber=May16_HO2-->


