---
title:   Recurso WindowsProcess de DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Recurso WindowsProcess de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **WindowsProcess** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para configurar processos em um nó de destino.

## Sintaxe

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Argumentos| Indica uma cadeia de caracteres de argumentos para passar para o processo no estado em que se encontra. Se você precisar passar vários argumentos, coloque todos nessa cadeia de caracteres.| 
| Caminho| Indica o caminho até o executável do processo. Se você definir essa propriedade como o nome do executável, a DSC examinará a variável __Path__. Se você fornecer um nome de domínio totalmente qualificado, o processo deverá existir ali porque a DSC não verificará a variável __Path__ nesse caso.| 
| Credential| Indica as credenciais para iniciar o processo.| 
| Ensure| Indica se o processo existe. Defina essa propriedade como "Present" para garantir que o processo exista. Caso contrário, defina-a como "Absent". O padrão é "Present".| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"``.| 
| StandardErrorPath| Indica o caminho do diretório para escrever o erro padrão. Qualquer arquivo existente será substituído.| 
| StandardInputPath| Indica o local de entrada padrão.| 
| StandardOutputPath| Indica o local para escrever a saída padrão. Qualquer arquivo existente será substituído.| 
| WorkingDirectory| Indica o local que será usado como diretório de trabalho atual para o processo.| 



<!--HONumber=May16_HO3-->


