---
title: Recurso Environment de DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 20a7711604033b5ff1484dbb526df2642a9a1738

---

# Recurso Environment de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso __Environment__ na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar as variáveis de ambiente do sistema.

## Sintaxe
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| Nome| Indica o nome da variável de ambiente para a qual você deseja garantir um estado específico.| 
| Ensure| Indica se existe uma variável. Defina essa propriedade como __Present__ para criar a variável de ambiente caso ela não exista ou para garantir que seu valor corresponda ao que é fornecido por meio da propriedade __Value__ se a variável já existir. Defina-a como __Absent__ para excluir a variável se ela existir.| 
| Caminho| Define a variável de ambiente que está sendo configurada. Defina essa propriedade como __$true__ se a variável for a variável __Path__; caso contrário, defina-a como __$false__. O padrão é __$false__. Se a variável que estiver sendo configurada for a variável __Path__, o valor fornecido por meio da propriedade __Value__ será acrescentado ao valor existente.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 
| Valor| O valor que será atribuído à variável de ambiente.| 

## Exemplo

O exemplo a seguir assegura que __TestEnvironmentVariable__ esteja presente e tenha o valor __TestValue__. Se não estiver presente, será criado.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```




<!--HONumber=Jun16_HO4-->


