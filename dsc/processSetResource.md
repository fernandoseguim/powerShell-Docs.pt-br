---
title: Recurso ProcessSet da DSC
ms.date: 2016-05-23
keywords: PowerShell, DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: 012a0e5c4f2a1f60ecea869d588b9c54e0567ced

---

# Recurso WindowsProcess de DSC

> Aplica-se a: Windows PowerShell 5.0

O recurso **ProcessSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell fornece um mecanismo para configurar processos em um nó de destino. Esse recurso é um [recurso composto](authoringResourceComposite.md) que chama o [Recurso do WindowsProcess](windowsProcessResource.md) para cada grupo especificado no parâmetro `GroupName`.

## Sintaxe

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]   
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Argumentos| Uma cadeia de caracteres que contém os argumentos a serem passados ao processo no estado em que se encontram. Se você precisar passar vários argumentos, coloque todos nessa cadeia de caracteres.| 
| Caminho| Os caminhos para os executáveis do processo. Se esses forem os nomes dos arquivos executáveis (caminhos não totalmente qualificados), o recurso DSC pesquisará a variável de ambiente **Path** (`$env:Path`) para localizar os arquivos. Se os valores dessa propriedade forem caminhos totalmente qualificados, a DSC não usará a variável de ambiente **Path** para localizar os arquivos e gerará um erro se qualquer um dos caminhos não existir. Caminhos relativos não são permitidos.| 
| Credential| Indica as credenciais para iniciar o processo.| 
| Ensure| Especifica se os processos existem. Defina essa propriedade como "Present" para garantir que o processo exista. Caso contrário, defina-a como "Absent". O padrão é "Present".| 
| StandardErrorPath| O caminho para o qual os processos gravam o erro padrão. Qualquer arquivo existente será substituído.| 
| StandardInputPath| O fluxo do qual o processo recebe entrada padrão.| 
| StandardOutputPath| O caminho do arquivo para o qual os processos gravam a saída padrão. Qualquer arquivo existente será substituído.| 
| WorkingDirectory| O local usado como diretório de trabalho atual para os processos.| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **_ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`` .| 




<!--HONumber=Aug16_HO3-->


