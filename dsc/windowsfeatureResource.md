---
title: Recurso WindowsFeature de DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 522dbea958a60f76e98abe32e11e6491ea6d457c

---

# Recurso WindowsFeature de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **WindowsFeature** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para garantir que funções e recursos sejam adicionados ou removidos em um nó de destino.

## Sintaxe

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| Nome| Indica o nome da função ou recurso que você deseja garantir que seja adicionado ou removido. É igual à propriedade __Name__ do cmdlet [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx), não o nome de exibição da função ou recurso.| 
| Credential| Indica as credenciais que devem ser usadas para adicionar ou remover a função ou recurso.| 
| Ensure| Indica se a função ou o recurso foi adicionado. Para garantir que a função ou o recurso seja adicionado, defina essa propriedade como "Present"; para garantir que a função ou o recurso seja removido, defina a propriedade como "Absent".| 
| IncludeAllSubFeature| Defina essa propriedade como __$true__ para garantir o estado de todos os sub-recursos necessários com o estado do recurso especificado com a propriedade __Name__.| 
| LogPath| Indica o caminho até um arquivo de log em que você deseja que o provedor de recursos registre a operação.| 
| DependsOn| Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 
| Origem| Indica o local do arquivo de origem que deve ser usado para a instalação, se necessário.| 

## Exemplo
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```




<!--HONumber=Jun16_HO4-->


