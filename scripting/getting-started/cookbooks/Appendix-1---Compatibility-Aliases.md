---
title: "Apêndice 1   Alias de compatibilidade"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 38a6cb1b0402825b307652e6747ea65baafd1d8b

---

# Apêndice 1: Alias de compatibilidade
O Windows PowerShell tem vários aliases de transição que permitem aos usuários do UNIX e do Cmd usar nomes de comando familiares no Windows PowerShell. Os aliases mais comuns são mostrados na tabela a seguir, junto com o comando do Windows PowerShell por trás do alias e o alias padrão do Windows PowerShell, se houver.

Você pode encontrar o comando do Windows PowerShell para o qual qualquer alias aponta no Windows PowerShell usando o cmdlet Get\-Alias. Por exemplo, digite **get\-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Comando do CMD|Comando UNIX|Comando PS|PS Alias|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get\-ChildItem**|**gci**|
|**cls**|**clear**|**Clear\-Host** (função)|N\/D|
|**del, erase, rmdir**|**rm**|**Remove\-Item**|**ri**|
|**copy**|**cp**|**Copy\-Item**|**ci**|
|**move**|**mv**|**Move\-Item**|**mi**|
|**rename**|**mv**|**Rename\-Item**|**rni**|
|**tipo**|**cat**|**Get\-Content**|**gc**|
|**cd**|**cd**|**Set\-Location**|**sl**|
|**md**|**mkdir**|**New\-Item**|**ni**|
|N\/D|**pushd**|**Push\-Location**|N\/D|
|N\/D|**popd**|**Pop\-Location**|N\/D|




<!--HONumber=Jun16_HO4-->


