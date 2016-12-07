---
title: Recurso WindowsProcess de DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 7e8c0d39d4f49d09acef79d789ee54f158e465f8
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-windowsprocess-resource"></a>Recurso WindowsProcess de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **WindowsProcess** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para configurar processos em um nó de destino.

## <a name="syntax"></a>Sintaxe

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

## <a name="properties"></a>Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Argumentos| Indica uma cadeia de caracteres de argumentos para passar para o processo no estado em que se encontra. Se você precisar passar vários argumentos, coloque todos nessa cadeia de caracteres.| 
| Caminho| O caminho para o executável do processo. Se esse for o nome do arquivo do executável (não o caminho totalmente qualificado), o recurso DSC pesquisará a variável de ambiente **caminho** (`$env:Path`) para localizar o arquivo executável. Se o valor dessa propriedade for um caminho totalmente qualificado, o DSC não usará a variável de ambiente **Caminho** para encontrar o arquivo e emitirá um erro se o caminho não existir. Caminhos relativos não são permitidos.| 
| Credential| Indica as credenciais para iniciar o processo.| 
| Ensure| Indica se o processo existe. Defina essa propriedade como "Present" para garantir que o processo exista. Caso contrário, defina-a como "Absent". O padrão é "Present".| 
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"``.| 
| StandardErrorPath| Indica o caminho do diretório para escrever o erro padrão. Qualquer arquivo existente será substituído.| 
| StandardInputPath| Indica o local de entrada padrão.| 
| StandardOutputPath| Indica o local para escrever a saída padrão. Qualquer arquivo existente será substituído.| 
| WorkingDirectory| Indica o local que será usado como diretório de trabalho atual para o processo.| 

