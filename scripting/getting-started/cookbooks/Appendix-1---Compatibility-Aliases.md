---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: "Apêndice 1 Aliases de compatibilidade"
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: d789139ef80d4208b56e0b2930f04f824a00537d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="appendix-1---compatibility-aliases"></a>Apêndice 1: Alias de compatibilidade
O Windows PowerShell tem vários aliases de transição que permitem aos usuários do UNIX e do Cmd usar nomes de comando familiares no Windows PowerShell. Os aliases mais comuns são mostrados na tabela a seguir, junto com o comando do Windows PowerShell por trás do alias e o alias padrão do Windows PowerShell, se houver.

Você pode encontrar o comando do Windows PowerShell para o qual qualquer alias aponta de dentro do Windows PowerShell usando o cmdlet Get-Alias. Por exemplo, digite **get-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Comando do CMD|Comando UNIX|Comando PS|PS Alias|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host** (função)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|

