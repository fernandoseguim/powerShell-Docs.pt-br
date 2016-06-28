---
title: Recurso nxService de DSC para Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 3835495705297616a41329bcfdaad42b464115d8

---

# Recurso nxService de DSC para Linux

O recurso **nxService** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar serviços em um nó do Linux.

## Sintaxe

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | system }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## Propriedades
|  Propriedade |  Descrição | 
|---|---|
| Nome| O nome do serviço/daemon que será configurado.| 
| Controlador| O tipo de controlador de serviço que deve ser usado ao configurar o serviço.| 
| Habilitada| Indica se o serviço começa na inicialização.| 
| Estado| Indica se o serviço está em execução. Defina essa propriedade como "Stopped" para garantir que o serviço não esteja em execução. Defina-a como "Running" para garantir que o serviço esteja em execução.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 


## Informações adicionais

O recurso **nxService** não criará uma definição de serviço ou um script para o serviço se não existir. É possível usar o recurso **nxFile** de Configuração de Estado Desejado do PowerShell para gerenciar a existência ou o conteúdo do arquivo ou script de definição de serviço.

## Exemplo

O exemplo a seguir mostra a configuração do serviço “httpd” (para o Apache HTTP Server), registrado com o controlador de serviço **SystemD**.

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```




<!--HONumber=Jun16_HO4-->


